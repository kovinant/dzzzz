css:
.reveal {
    opacity: 0;
    transition: 0.3s opacity ease-in-out;
    background: orange;
    padding: 20px;
    min-height: 200px;
    box-sizing: border-box;
    color: white;
    font-size: 24px;
  }
  
  .reveal_active {
    opacity: 1;
  }
  .content {
    height: 200vh; 
}
.reveal {
    margin-top: 80vh; 
    height: 100px;
    background-color: yellow;
}
.reveal_active {
    background-color: green;
}
js:
let scrollLocked = false;
let unlockScrollTimeout;
let processedReveals = new Set();

document.addEventListener('scroll', function() {
    if (scrollLocked) {
        return;
    }

    const reveals = document.querySelectorAll('.reveal');
    let stopScroll = false;

    reveals.forEach(function(reveal) {
        const windowHeight = window.innerHeight;
        const elementTop = reveal.getBoundingClientRect().top;
        const elementBottom = reveal.getBoundingClientRect().bottom;
        const elementVisible = 150; 
        
        if (elementTop < windowHeight - elementVisible && elementTop > -elementVisible && !processedReveals.has(reveal)) {
            reveal.classList.add('reveal_active');
            stopScroll = true;
            processedReveals.add(reveal);
        }

 
        if (elementBottom < 0 || elementTop > windowHeight) {
            reveal.classList.remove('reveal_active');
            processedReveals.delete(reveal);
        }
    });

    if (stopScroll) {
        scrollLocked = true;
        document.body.style.overflow = 'hidden';


        unlockScrollTimeout = setTimeout(() => {
            scrollLocked = false;
            document.body.style.overflow = '';
        }, 2000); 
    }
});
