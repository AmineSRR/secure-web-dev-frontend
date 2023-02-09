<script>
  import { enhance } from '$app/forms';
  /** @type {import('./$types').ActionData} */
  export let form;
</script>

<svelte:head>
  <title>Register</title>
  <style>
    fieldset {
      margin-bottom: 30px;
      border: 1px solid #ccc;
      border-radius: 5px;
      padding: 20px;
    }

    input[type="text"],
    input[type="email"],
    input[type="password"] {
      font-size: 18px;
      padding: 10px;
      width: 100%;
      box-sizing: border-box;
      border: none;
      border-bottom: 1px solid #ccc;
      border-radius: 5px;
      margin-bottom: 20px;
    }

    input[type="text"]:focus,
    input[type="email"]:focus,
    input[type="password"]:focus {
      border-color: #555;
      outline: 0;
    }

    .btn {
      font-size: 18px;
      padding: 10px 20px;
      border-radius: 5px;
      background-color: #555;
      color: #fff;
      cursor: pointer;
      width: 100%;
      margin-top: 20px;
    }

    .btn:hover {
      background-color: #333;
    }

    #forms-titre {
      font-size: 36px;
      margin-bottom: 20px;
      text-align: center;
    }

    button a {
      color: #555;
      text-decoration: none;
    }

    p {
      text-align: center;
      margin-top: 20px;
    }
  </style>
  </svelte:head>

  <form use:enhance method="POST">
    <div id="forms-titre">Register</div>
    <fieldset class="form-group">
      <input
              class="form-control form-control-lg"
              name="username"
              type="text"
              required
              placeholder="Your Name"
      />
    </fieldset>
    <fieldset class="form-group">
      <input
              class="form-control form-control-lg"
              name="email"
              type="email"
              required
              placeholder="Email"
      />
    </fieldset>
    <fieldset class="form-group">
      <input
              class="form-control form-control-lg"
              name="password"
              type="password"
              required
              placeholder="Password"
      />
    </fieldset>
    <button class="btn btn-lg btn-success">Sign up</button>
    <button>
    <a href="../login/+page.svelte">Déjà un compte?</a>
    </button>
    <button>
      <a href="/">Back home</a>
    </button>
</form>
