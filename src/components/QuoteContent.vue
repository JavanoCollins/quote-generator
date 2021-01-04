<template>
    <div v-if="showContainer" class="quote-content">
        <!-- Quote -->
        <div class="quote-text">
            <i class="fas fa-quote-left"></i>
            <span id="quote">{{ quote }}</span>
        </div>
        <!-- Author -->
        <div class="quote-author">
            <span id="author">- {{ author }}</span>
        </div>
        <div class="button-container">
            <TwitterBtn @click="tweetQuote" />
            <NewQuoteBtn @click="getQuote" />
        </div>
    </div>
    <Loader v-bind="loader" v-if="loader"/> 
</template>

<script>
import TwitterBtn from "./TwitterBtn";
import NewQuoteBtn from "./NewQuoteBtn";
import Loader from "./Loader";

export default {
    components: {
        TwitterBtn,
        NewQuoteBtn,
        Loader,
    },
    created() {
        this.getQuote();
    },
    data() {
        return {
            quote: "",
            author: "",
            proxyUrl: "https://rocky-lowlands-97929.herokuapp.com/",
            apiUrl:
                "http://api.forismatic.com/api/1.0/?method=getQuote&lang=en&format=json",
                loader: null,
                showContainer: null
        };
    },
    methods: {
        async getQuote() {
            this.showLoadingSpinner()
            try {
                const response = await fetch(this.proxyUrl + this.apiUrl);
                const data = await response.json();

                if (data.quoteAuthor === "") {
                    this.author = "Unknown";
                } else {
                    this.author = data.quoteAuthor;
                }

                this.quote = data.quoteText;
            } catch (error) {
                this.getQuote();
            }
            this.showContent()
        },
        tweetQuote() {
            const quoteText = this.quote;
            const authorText = this.author;
            const twitterUrl = `https://twitter.com/intent/tweet?text=${quoteText} - ${authorText}`;
            window.open(twitterUrl, "_blank");
        },
        showLoadingSpinner() {
            this.loader = true;
            this.showContainer = false;
        },
        showContent() {
            this.loader = false;
            this.showContainer = true;
        },
    },
};
</script>

<style scoped>
.fa-quote-left {
    font-size: 4rem;
    margin-right: 0.5rem;
}

.quote-text {
    margin-bottom: 1rem;
}

#quote {
    font-size: 2.5rem;
    text-align: left;
    line-height: 1.4;
}

#author {
    font-size: 1.8rem;
    font-style: italic;
    color: #444;
}

.button-container {
    display: flex;
    justify-content: space-between;
    margin: 1.5rem 0 0;
}

@media screen and (max-width: 500px) {
    .fa-quote-left {
        font-size: 1.5rem;
    }

    #quote {
        font-size: 1.2rem;
    }

    #author {
        font-size: .8rem;
    }
}
</style>