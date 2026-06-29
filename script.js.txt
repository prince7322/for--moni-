// Loading Screen
window.addEventListener("load", () => {
    const loading = document.getElementById("loading");

    setTimeout(() => {
        loading.style.opacity = "0";
        loading.style.visibility = "hidden";
    }, 2500);
});

// Auto Play Music (Browser permission ke baad chalega)
const music = document.getElementById("bgMusic");

document.addEventListener("click", () => {
    if (music) {
        music.play().catch(() => {});
    }
}, { once: true });

// Floating Hearts
function createHeart() {
    const heart = document.createElement("div");
    heart.innerHTML = "❤️";
    heart.style.position = "fixed";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.top = "100vh";
    heart.style.fontSize = (20 + Math.random() * 20) + "px";
    heart.style.pointerEvents = "none";
    heart.style.zIndex = "9999";
    heart.style.transition = "transform 6s linear, opacity 6s";

    document.body.appendChild(heart);

    setTimeout(() => {
        heart.style.transform = "translateY(-120vh)";
        heart.style.opacity = "0";
    }, 100);

    setTimeout(() => {
        heart.remove();
    }, 6000);
}

setInterval(createHeart, 700);

// Smooth fade-in for gallery
const images = document.querySelectorAll(".gallery img");

const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = "1";
            entry.target.style.transform = "scale(1)";
        }
    });
});

images.forEach(img => {
    img.style.opacity = "0";
    img.style.transform = "scale(0.9)";
    img.style.transition = "0.8s";
    observer.observe(img);
});

console.log("❤️ Happy Birthday Moni - From Rohit ❤️");