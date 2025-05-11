<script>
  import { onMount } from 'svelte';
  import { fade } from 'svelte/transition';
  
  let email = '';
  let password = '';
  let showPassword = false;
  let isMobile = false;
  
  // Check if the device is mobile
  const checkMobile = () => {
    isMobile = window.innerWidth < 768;
  };
  
  onMount(() => {
    checkMobile();
    window.addEventListener('resize', checkMobile);
    
    return () => {
      window.removeEventListener('resize', checkMobile);
    };
  });
  
  const handleLogin = (e) => {
    e.preventDefault();
    // Handle login logic here
    console.log('Login attempt with:', { email, password });
  };
  
  const handleGoogleLogin = () => {
    // Handle Google login logic here
    console.log('Google login attempt');
  };
</script>

<div class="auth-container">
  {#if !isMobile}
  <div class="hero-section" transition:fade={{ duration: 300 }}>
    <div class="hero-content">
      <h1>Take Your Garden to the Next Level</h1>
      <p>From Seed to Harvest: Smart Farming Solutions for Every Stage and Achieve Consistent Results with Precision Monitoring and Automated Farming Tools</p>
      
      <div class="dots">
        <span class="dot active"></span>
        <span class="dot"></span>
        <span class="dot"></span>
      </div>
    </div>
  </div>
  {/if}
  
  <div class="form-section" transition:fade={{ duration: 300 }}>
    <div class="logo-container">
      <!-- <img src="https://hebbkx1anhila5yf.public.blob.vercel-storage.com/image-b3cGLCiEl8FHrEA1aCuyHM6SZfgPyx.png" alt="Robectron Logo" class="logo" /> -->
    </div>
    
    <div class="form-container">
      <h2>Welcome Back</h2>
      <p class="subtitle">Glad to see you again<br>Login to your account below</p>
      
      <form on:submit={handleLogin}>
        <div class="form-group">
          <label for="email">Email</label>
          <input 
            type="email" 
            id="email" 
            bind:value={email} 
            placeholder="johndoe@example.com" 
            required
          />
        </div>
        
        <div class="form-group">
          <label for="password">Password</label>
          <div class="password-input">
            <input 
              type={showPassword ? "text" : "password"} 
              id="password" 
              bind:value={password} 
              placeholder="Enter Password" 
              required
            />
            <button 
              type="button" 
              class="toggle-password" 
              on:click={() => showPassword = !showPassword}
              aria-label={showPassword ? "Hide password" : "Show password"}
            >
              {#if showPassword}
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"></path><line x1="1" y1="1" x2="23" y2="23"></line></svg>
              {:else}
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path><circle cx="12" cy="12" r="3"></circle></svg>
              {/if}
            </button>
          </div>
        </div>
        
        <div class="forgot-password">
          <a href="/forgot-password">Forgot Password?</a>
        </div>
        
        <button type="submit" class="btn-primary">Login</button>
        
        <div class="divider">
          <span class="line"></span>
          <span class="or">or</span>
          <span class="line"></span>
        </div>
        
        <button type="button" class="btn-google" on:click={handleGoogleLogin}>
          <svg viewBox="0 0 24 24" width="16" height="16" xmlns="http://www.w3.org/2000/svg">
            <g transform="matrix(1, 0, 0, 1, 27.009001, -39.238998)">
              <path fill="#4285F4" d="M -3.264 51.509 C -3.264 50.719 -3.334 49.969 -3.454 49.239 L -14.754 49.239 L -14.754 53.749 L -8.284 53.749 C -8.574 55.229 -9.424 56.479 -10.684 57.329 L -10.684 60.329 L -6.824 60.329 C -4.564 58.239 -3.264 55.159 -3.264 51.509 Z"/>
              <path fill="#34A853" d="M -14.754 63.239 C -11.514 63.239 -8.804 62.159 -6.824 60.329 L -10.684 57.329 C -11.764 58.049 -13.134 58.489 -14.754 58.489 C -17.884 58.489 -20.534 56.379 -21.484 53.529 L -25.464 53.529 L -25.464 56.619 C -23.494 60.539 -19.444 63.239 -14.754 63.239 Z"/>
              <path fill="#FBBC05" d="M -21.484 53.529 C -21.734 52.809 -21.864 52.039 -21.864 51.239 C -21.864 50.439 -21.724 49.669 -21.484 48.949 L -21.484 45.859 L -25.464 45.859 C -26.284 47.479 -26.754 49.299 -26.754 51.239 C -26.754 53.179 -26.284 54.999 -25.464 56.619 L -21.484 53.529 Z"/>
              <path fill="#EA4335" d="M -14.754 43.989 C -12.984 43.989 -11.404 44.599 -10.154 45.789 L -6.734 42.369 C -8.804 40.429 -11.514 39.239 -14.754 39.239 C -19.444 39.239 -23.494 41.939 -25.464 45.859 L -21.484 48.949 C -20.534 46.099 -17.884 43.989 -14.754 43.989 Z"/>
            </g>
          </svg>
          Login with Google
        </button>
      </form>
      
      <div class="signup-link">
        Don't have an account? <a href="/signup">Sign up</a>
      </div>
      
      {#if isMobile}
      <div class="mobile-nav">
        <a href="/" class="nav-item active">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path><polyline points="9 22 9 12 15 12 15 22"></polyline></svg>
        </a>
        <a href="/categories" class="nav-item">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7"></rect><rect x="14" y="3" width="7" height="7"></rect><rect x="14" y="14" width="7" height="7"></rect><rect x="3" y="14" width="7" height="7"></rect></svg>
        </a>
        <a href="/favorites" class="nav-item">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path></svg>
        </a>
        <a href="/cart" class="nav-item">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="9" cy="21" r="1"></circle><circle cx="20" cy="21" r="1"></circle><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"></path></svg>
        </a>
        <a href="/menu" class="nav-item">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></svg>
        </a>
      </div>
      {/if}
    </div>
  </div>
</div>

<style>
  /* Mobile-first approach */
  .auth-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    width: 100%;
    /* background-color: #f9f9f9; */
    background-color: rgb(32, 31, 31);
  }
  
  .logo-container {
    display: flex;
    justify-content: center;
    margin-bottom: 1rem;
  }
  
  .logo {
    width: 80px;
    height: auto;
    margin-top: 2rem;
  }
  
  .form-section {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 1rem;
    background-color: #f9f9f9;
  }
  
  .form-container {
    width: 100%;
    max-width: 400px;
    padding: 1rem;
  }
  
  h2 {
    font-size: 1.5rem;
    font-weight: 700;
    text-align: center;
    margin-bottom: 0.5rem;
  }
  
  .subtitle {
    text-align: center;
    color: #666;
    font-size: 0.875rem;
    margin-bottom: 1.5rem;
  }
  
  .form-group {
    margin-bottom: 1rem;
  }
  
  label {
    display: block;
    margin-bottom: 0.5rem;
    font-size: 0.875rem;
    font-weight: 500;
  }
  
  input {
    width: 100%;
    padding: 0.75rem 1rem;
    border: 1px solid #ddd;
    border-radius: 0.5rem;
    background-color: #f5f5f5;
    font-size: 0.875rem;
  }
  
  input:focus {
    outline: none;
    border-color: #ff6b00;
    box-shadow: 0 0 0 2px rgba(255, 107, 0, 0.1);
  }
  
  .password-input {
    position: relative;
  }
  
  .toggle-password {
    position: absolute;
    right: 1rem;
    top: 50%;
    transform: translateY(-50%);
    background: none;
    border: none;
    color: #999;
    cursor: pointer;
    padding: 0;
  }
  
  .forgot-password {
    text-align: right;
    margin-bottom: 1rem;
  }
  
  .forgot-password a {
    color: #ff6b00;
    font-size: 0.75rem;
    text-decoration: none;
  }
  
  .btn-primary {
    width: 100%;
    padding: 0.75rem;
    background-color: #ff6b00;
    color: white;
    border: none;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.2s;
  }
  
  .btn-primary:hover {
    background-color: #e05e00;
  }
  
  .divider {
    display: flex;
    align-items: center;
    margin: 1.5rem 0;
  }
  
  .line {
    flex: 1;
    height: 1px;
    background-color: #ddd;
  }
  
  .or {
    padding: 0 1rem;
    color: #666;
    font-size: 0.75rem;
  }
  
  .btn-google {
    width: 100%;
    padding: 0.75rem;
    background-color: #222;
    color: white;
    border: none;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    transition: background-color 0.2s;
  }
  
  .btn-google:hover {
    background-color: #333;
  }
  
  .signup-link {
    text-align: center;
    margin-top: 1.5rem;
    font-size: 0.875rem;
    color: #666;
  }
  
  .signup-link a {
    color: #ff6b00;
    text-decoration: none;
    font-weight: 500;
  }
  
  .mobile-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: white;
    padding: 0.75rem 1rem;
    box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.05);
    margin-top: 2rem;
  }
  
  .nav-item {
    color: #999;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-decoration: none;
    font-size: 0.75rem;
  }
  
  .nav-item.active {
    color: #ff6b00;
  }
  
  /* Desktop styles */
  @media (min-width: 768px) {
    .auth-container {
      flex-direction: row;
      height: 100vh;
    }
    
    .hero-section {
      flex: 1;
      /* background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('https://hebbkx1anhila5yf.public.blob.vercel-storage.com/image-AtQU4JUShP14MByeIG9mj6rrEXZTEK.png'); */
      background-size: cover;
      background-position: center;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      padding: 2rem;
    }
    
    .hero-content {
      max-width: 500px;
      text-align: center;
    }
    
    .hero-content h1 {
      font-size: 2.5rem;
      font-weight: 700;
      margin-bottom: 1rem;
    }
    
    .hero-content p {
      font-size: 1rem;
      margin-bottom: 2rem;
      line-height: 1.6;
    }
    
    .dots {
      display: flex;
      justify-content: center;
      gap: 0.5rem;
    }
    
    .dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background-color: rgba(255, 255, 255, 0.5);
    }
    
    .dot.active {
      background-color: white;
    }
    
    .form-section {
      flex: 1;
      justify-content: center;
      padding: 2rem;
    }
    
    .logo {
      width: 100px;
    }
    
    h2 {
      font-size: 2rem;
    }
    
    .subtitle {
      font-size: 1rem;
    }
  }
  
  @media (min-width: 1024px) {
    .form-container {
      max-width: 450px;
    }
    
    .hero-content h1 {
      font-size: 3rem;
    }
    
    .hero-content p {
      font-size: 1.125rem;
    }
  }
</style>