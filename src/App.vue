<template>
    <div id="app">
        <h1 id="title">Fantastic Quotes</h1>
        <QuoteContainer />
        <!-- <Loader /> -->
    </div>
</template>

<script>
import QuoteContainer from "./components/QuoteContainer";
export default {
    name: "App",
    components: {
        QuoteContainer,
    },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat&display=swap");

html {
    box-sizing: border-box;
}

#title {
    font-size: 3rem;
}

body {
    margin: 0;
    padding: 0;
    min-height: 100vh;
    background-color: #ffffff;
    background-image: url("data:image/svg+xml,%3Csvg width='70' height='70' viewBox='0 0 70 70' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23000000' fill-opacity='0.17' fill-rule='evenodd'%3E%3Cpath d='M0 0h35v35H0V0zm5 5h25v25H5V5zm5 5h15v15H10V10zm5 5h5v5h-5v-5zM40 5h25v25H40V5zm5 5h15v15H45V10zm5 5h5v5h-5v-5zM70 35H35v35h35V35zm-5 5H40v25h25V40zm-5 5H45v15h15V45zm-5 5h-5v5h5v-5zM30 40H5v25h25V40zm-5 5H10v15h15V45zm-5 5h-5v5h5v-5z'/%3E%3C/g%3E%3C/svg%3E");
    color: #000;
    font-family: Montserrat, sans-serif;
    font-weight: 700;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

button {
    padding: 0.6rem 1.4rem;
    background-color: rgb(59, 59, 59);
    color: #fff;
    border: none;
    border-radius: 5px;
    font-size: 1rem;
    box-shadow: 0px 4px 0px -1px rgba(0, 0, 0, 0.44);
    cursor: pointer;
    transition: all 0.2s;
    outline: none;
}

button:hover {
    background-color: rgb(90, 90, 90);
    transition: all 0.2s;
}

button:active {
    transform: translate(0, 0.3rem);
    box-shadow: 0px 1px rgba(0, 0, 0, 0.44);
}

@media screen and (max-width: 500px) {
    #title {
        font-size: 1.5rem;
    }

    button {
        padding: 0.4rem .6rem;
        font-size: .6rem;
    }
}
</style>
