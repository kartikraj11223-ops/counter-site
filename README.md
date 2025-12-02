# counter-site<!DOCTYPE html>
<html lang="en">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
html, body {
  margin:0;
  padding:0;
  overflow-x:hidden;
  font-family: 'Segoe UI', Arial, sans-serif;
  background:#f5f5f5;
}
* { box-sizing: border-box; }

.responsive-box {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  margin: 0;
  padding: 10px 5px; /* minimal padding */
  justify-content: space-between;
}

.responsive-item {
  width: 32%;
  background: #ffffff;
  border-radius: 12px;
  text-align: center;
  padding: 20px 10px;
  border: 1px solid #ddd;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  margin-bottom: 10px;
}

.responsive-title {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 10px;
  color: #333;
}

.responsive-number {
  font-size: 36px;
  font-weight: 900;
  color: #0077ff;
  transition: color 0.3s;
}

.responsive-number:hover {
  color: #0056b3;
}

@media (max-width: 768px) {
  .responsive-item { width: 48%; } /* 2 per row on tablet */
  .responsive-number { font-size: 32px; }
}

@media (max-width: 480px) {
  .responsive-item { width: 100%; } /* stacked on mobile */
  .responsive-number { font-size: 28px; }
}
</style>
</head>
<body>
<div class="responsive-box">
  <div class="responsive-item">
    <div class="responsive-title">Corporate Event</div>
    <div class="responsive-number" data-target="1000">0</div>
  </div>
  <div class="responsive-item">
    <div class="responsive-title">Exhibition</div>
    <div class="responsive-number" data-target="1500">0</div>
  </div>
  <div class="responsive-item">
    <div class="responsive-title">Printing Work</div>
    <div class="responsive-number" data-target="2000">0</div>
  </div>
</div>

<script>
const nums = document.querySelectorAll(".responsive-number");
nums.forEach(num=>{
  const target = +num.dataset.target;
  let count = 0;
  let step = Math.ceil(target/100);
  const speed = 20;

  const run = setInterval(()=>{
    count += step;
    if(count >= target){ num.textContent = target; clearInterval(run);}
    else { num.textContent = count; }
  }, speed);
});
</script>
</body>
</html>
