let todasCategorias = ["Saúde", "moda", "economia"]
let botao = document.getElementById("btn");

botao.addEventListener("click", () => {

let categorias = document.getElementById("categorias")
let noticias = document.getElementById('noticias')
noticias.setAttribute("id", 'noticias')



    var item;
        for (item = 0; item < todasCategorias.length; item++) {
        let novacategoria = document.createElement("div")
        novacategoria.innerHTML = todasCategorias[item];
        novacategoria.setAttribute("id", todasCategorias[item])
        novacategoria.className = 'categoria'
        categorias.appendChild(novacategoria);
        console.log(categorias);

        let categoria = document.getElementById(todasCategorias[item])

        categoria.addEventListener("mouseover", () => {
            categoria.style.color = "#427e3f";
        });

        categoria.addEventListener("mouseout", () => {
            categoria.style.color = "black";
        });

        categoria.addEventListener('click', () => {
            noticias.innerHTML = ''
            for(x=0; x < 3; x++){
                criaNoticia(x);
            }
        })

        botao.disabled = true;

    };
       
});




function criaNoticia(num){
    let noticia = document.createElement('div')
    noticia.setAttribute('id',num);

    /* Btn Fechar*/
    let btnFechar = document.createElement("button")
    btnFechar.innerHTML = 'X'
    btnFechar.className = 'btn-fechar'
    btnFechar.setAttribute("id", num)
    btnFechar.addEventListener('click',() => {
        fecharNote(event)
    })
    noticia.appendChild(btnFechar)

    /*Título da noticia*/
    let pTitle = document.createElement('p')
    pTitle.innerHTML = (num + 1) + 'º Noticia'
    pTitle.className = 'title-note'
    pTitle.setAttribute("id", 'pTitle')
    noticia.appendChild(pTitle)

    /*Imagem da noticia*/
    let img = document.createElement("img");
    numImg = Math.floor(Math.random() * 500)
    img.src = "https://picsum.photos/600/400/?image=" + numImg;
    img.setAttribute("id", 'img')
    noticia.appendChild(img)

    /*noticia*/
    let p = document.createElement('p')
    p.innerHTML = 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi scelerisque pretium nibh vitae convallis. Nulla facilisi. In hac habitasse platea dictumst. Integer a varius odio. In imperdiet tincidunt diam. Curabitur quis posuere elit. Nulla commodo, lacus at hendrerit dignissim, elit ipsum mattis ligula, tempor congue sem dolor sed urna. Maecenas eu egestas metus. Phasellus interdum lobortis magna, tempor dapibus elit euismod in. Morbi in facilisis justo. Nam arcu lacus, finibus vel massa at, aliquam ultrices sem. Morbi gravida libero vel lacinia facilisis.'
    p.className = 'note'
    p.setAttribute("id", 'note')
    noticia.appendChild(p)


    /* Btn like*/
    let btnLike = document.createElement("button")
    btnLike.innerHTML = 'Gostei'
    btnLike.className = 'btn-like'
    btnLike.addEventListener('click',() => {
        btnLike.className = 'btn-like-on'
    })
    noticia.appendChild(btnLike)

    /* Btn deslike*/
    let btnDeslike = document.createElement("button")
    btnDeslike.innerHTML = 'Não Gostei'
    btnDeslike.className = 'btn-deslike'
    btnDeslike.setAttribute("id", 'btnDeslike')
    btnDeslike.addEventListener('click',() => {
        btnDeslike.className = 'btn-like-off'
    })
    noticia.appendChild(btnDeslike)
    
    

    noticia.className = 'noticia'
    noticias.appendChild(noticia)
}

function fecharNote(event){
    document.getElementById(event.target.id).remove()
}



// LSA IR NO ACERTE
