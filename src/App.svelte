<script>
    import { FirebaseApp, User } from "sveltefire";
    import firebase from "firebase/app";
    import "firebase/firestore";
    import "firebase/auth";
    import Chats from "./components/Chats.svelte";
    import AuthForm from "./components/AuthForm.svelte";

    let firebaseConfig = {
        apiKey: "AIzaSyBqrogO-SSYb93oci_U9yMkQebazrjptrs",
        authDomain: "svelte-chat-3158d.firebaseapp.com",
        databaseURL: "https://svelte-chat-3158d.firebaseio.com",
        projectId: "svelte-chat-3158d",
        storageBucket: "svelte-chat-3158d.appspot.com",
        messagingSenderId: "740602269363",
        appId: "1:740602269363:web:a159df3e8c10f84edaeac6",
    }
    firebase.initializeApp(firebaseConfig);
</script>

<style>
    .app {
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        max-height: 100vh;
    }
</style>

<main class="container section app">
    <FirebaseApp {firebase}>
        <User let:user let:auth>
            <Chats {user} />
            <button
                class="button is-fullwidth"
                on:click={() => auth.signOut()}>Leave Chat</button>
            <div slot="signed-out">
                <AuthForm {auth} />
            </div>
        </User>
    </FirebaseApp>
</main>