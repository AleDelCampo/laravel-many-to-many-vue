<script>
export default {
    name: 'AppFooter',

    data(){
        return{
            members:[
                {
                    nome: "Alessandro",
                    cognome: "Del Campo"
                }
            ],

            emails:[,
                "alessandrodelcampo@gmail.com"
            ],

            socials:[
                "fa-facebook",
                "fa-x-twitter",
                "fa-instagram",
                "fa-google-plus-g",
                "fa-tiktok",
                "fa-youtube"
            ]
        }
    }
}
</script>


<template>

    <footer class="bg-footer">
        <div class="container py-5">


            <div id="footer-title">
              Portfolio di Alessandro Del Campo
            </div>

            <div class="row">

                <div class="col d-flex flex-column align-items-center">

                    <div class="col-title">
                        Members
                    </div>

                    <div class="components">
                        <ul>
                            <li v-for="member in members">
                                <div class="name">
                                    {{ member.nome }}
                                    {{ member.cognome }}
                                </div>
                            </li>
                        </ul>
                    </div>
                </div>

                <div class="col d-flex flex-column align-items-center">

                    <div class="col-title">
                        Contact
                    </div>

                    <div class="emails">
                        <ul>
                            <li class="fw-bold" v-for="email in emails">
                                {{ email }}
                            </li>
                        </ul>
                    </div>

                </div>

                <div class="col d-flex flex-column align-items-center">
                    <div class="col-title">
                        Social
                    </div>

                    <div id="social-grid">
                        <div v-for="social in socials" class="icon">
                            <i class="fa-brands" :class="social"></i>
                        </div>
                    </div>
                </div>

            </div>
        </div>
        
        <hr style="border-top: 4px solid #fd2dfd;">

        <div class="container py-4">
            <h6 class="text-center mb-3">
                La creazione di questi progetti sono nati per lo scopo didattico in Boolean®, riportati oggi qui per mostrarli a te!! 
            </h6>

            <div id="copyright">
                Copyright© 2024, Boolean®.
            </div>
        </div>

    </footer>

</template>

<style lang="scss" scoped>

footer {
    color: black;
}

#footer-title{
    font-size:1.6em;
    font-weight: bold;
    text-align: center;

    margin-bottom: 20px;
}

.col-title{
    font-size:1.2em;
    font-weight: 600;   

    margin-bottom: 10px;
}

ul{
    margin: 0;
    padding: 0;
    
    display: flex;
    flex-direction: column;
    align-items:center;
    row-gap:5px;

    font-size: .8em;
    list-style-type: none;
    opacity: .8;
}

.components{

    li{
        display: flex;
        gap:8px;

        div {
            font-weight: bold;
        }
       
    }
}

.bg-footer {
    background-color: #f0f3ff;
}

#social-grid{

    max-width: 200px;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap:10px;

    .icon{
        display: flex;
        justify-content: center;
        align-items: center;

        width: 50px;
        height: 50px;

        border:2px solid #fd25fd;

        font-size:1.3em;

        transition: all .3s ease-in-out;

        
    }
    
    .icon:hover{

        background-color: white;

        color:black;

        cursor: pointer;

    }
   
}

#copyright{
    text-align: center;
    font-weight: bold;
    font-size: .7em;
    opacity: .8;
}
</style>