<script>
    import { enhance } from '$app/forms';

    /** @type {import('./$types').ActionData} */
    export let form;
</script>

<svelte:head>
    <title>Sign in</title>
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

<div class="auth-page">
    <div class="container page">
        <div class="row">
            <div class="col-md-6 offset-md-3 col-xs-12">
                <div id="forms-titre">Login</div>
                <p class="text-xs-center"></p>

                <form use:enhance method="POST">
                    <fieldset class="form-group">
                        <input
                                class="form-control form-control-lg"
                                name="username"
                                type="text"
                                required
                                placeholder="Your Name"
                        />
                    </fieldset>
                    <fieldset class="from-group">
                        <input
                                class="form-control form-control-lg"
                                name="password"
                                type="password"
                                required
                                placeholder="Password"
                        />
                    </fieldset>
                    <button class="btn btn-lg btn-success" type="submit">Sign in</button>
                    <br><br>
                    <button>
                        <a href="/register">Need an account?</a>
                    </button>
                    <button>
                        <a href="/">Back home</a>
                    </button>
                </form>
            </div>
        </div>
    </div>
</div>
