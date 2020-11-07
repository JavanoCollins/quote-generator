<template>
    <div class="quote-container" id="quote-container">
        <QuoteContent />
    </div>
</template>

<script>
import QuoteContent from "./QuoteContent";
export default {
    components: {
        QuoteContent,
    },
};
</script>

<style scoped>
/* Quote Container */
.quote-container {
    padding: 3rem 4rem;
    box-shadow: 0px 10px 15px 4px rgba(0, 0, 0, 0.616);
    border-radius: 8px;
    width: auto;
    max-width: 700px;
    background-color: rgba(255, 255, 255, 0.5);
}

@media screen and (max-width: 500px) {
    .quote-container {
        padding: 1rem 2rem;
        box-shadow: 0px 10px 15px 4px rgba(0, 0, 0, 0.616);
        border-radius: 8px;
        width: auto;
        max-width: 280px;
        background-color: rgba(255, 255, 255, 0.5);
    }
}
</style>