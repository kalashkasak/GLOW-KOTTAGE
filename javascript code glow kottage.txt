document.addEventListener('DOMContentLoaded', () => {
  const cart = [];

  const buttons = document.querySelectorAll('.product-card button');
  buttons.forEach((btn, index) => {
    btn.addEventListener('click', () => {
      const name = btn.parentElement.querySelector('h3').innerText;
      const price = btn.parentElement.querySelector('p').innerText;
      cart.push({ name, price });
      alert(`${name} added to cart!`);
    });
  });

  const customForm = document.getElementById('customCandleForm');
  customForm.addEventListener('submit', (e) => {
    e.preventDefault();
    const scent = document.getElementById('scent').value;
    const size = document.getElementById('size').value;
    const labelText = document.getElementById('labelText').value;
    const customCandle = {
      name: `${size.charAt(0).toUpperCase() + size.slice(1)} ${scent} Candle`,
      price: size === 'small' ? '$12.00' : size === 'medium' ? '$18.00' : '$25.00',
      label: labelText
    };
    cart.push(customCandle);
    alert(`Custom candle added to cart!\n"${customCandle.label}"`);
    customForm.reset();
  });
});
