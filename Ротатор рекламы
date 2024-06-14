document.addEventListener('DOMContentLoaded', () => {
    const rotators = document.querySelectorAll('.rotator');

    rotators.forEach(rotator => {
        let activeIndex = 0;
        const cases = rotator.querySelectorAll('.rotator__case');
        
        function rotateCase() {
            const activeCase = cases[activeIndex];
            activeCase.classList.remove('rotator__case_active');
            
            activeIndex = (activeIndex + 1) % cases.length;
            const nextCase = cases[activeIndex];
            nextCase.classList.add('rotator__case_active');
            nextCase.style.color = nextCase.getAttribute('data-color');
            
            setTimeout(rotateCase, nextCase.getAttribute('data-speed'));
        }
        
        setTimeout(rotateCase, cases[activeIndex].getAttribute('data-speed'));
    });
});
