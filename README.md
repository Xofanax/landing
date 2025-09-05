<!DOCTYPE html>
</div>
<div>
<div class="card" style="padding:22px;margin-bottom:16px">
<h3 style="margin:0 0 8px">Atendimento</h3>
<p class="muted">Seg–Sex, 9h às 18h</p>
<p class="muted">E-mail: <a href="mailto:contato@suaempresa.com">contato@suaempresa.com</a></p>
<p class="muted">WhatsApp: <a href="https://wa.me/5599999999999" target="_blank" rel="noopener">(99) 99999-9999</a></p>
</div>
<div class="card" style="padding:22px">
<h3 style="margin:0 0 8px">Cobertura</h3>
<p class="muted">Atendemos ENEL, CEMIG, CPFL, NEOENERGIA e ENERGISA (consulte CEP).</p>
</div>
</div>
</div>
</section>
</main>


<a class="btn whats" href="https://wa.me/5599999999999?text=Quero%20economizar%20na%20minha%20conta%20de%20luz" target="_blank" rel="noopener" aria-label="Fale no WhatsApp">💬 WhatsApp</a>


<footer>
<div class="container" style="display:flex;justify-content:space-between;gap:18px;flex-wrap:wrap">
<div>© <span id="y"></span> NeoEnergia+ Assinatura — CNPJ 00.000.000/0001-00</div>
<div><a href="#" class="muted">Política de Privacidade</a> • <a href="#" class="muted">Termos de Uso</a></div>
</div>
</footer>


<script>
// Simulação simples (12% a 20% conforme heurística básica pela distribuidora)
const ranges = { padrao:[0.12,0.18], enel:[0.12,0.18], cemig:[0.13,0.19], cpfl:[0.12,0.17], neoenergia:[0.12,0.20], energisa:[0.11,0.18] };
const fmt = v => v.toLocaleString('pt-BR',{style:'currency',currency:'BRL'});
document.getElementById('btn-simular').addEventListener('click', () => {
const gasto = parseFloat(document.getElementById('gasto').value||0);
const dist = document.getElementById('distribuidora').value;
if(!gasto || gasto < 50 || dist === 'padrao'){ alert('Informe os dados para simular.'); return; }
const [min,max] = ranges[dist] || ranges.padrao;
const ecoMin = gasto*min;
const ecoMax = gasto*max;
document.getElementById('eco').textContent = `${fmt(ecoMin)} a ${fmt(ecoMax)}`;
document.getElementById('resultado').hidden = false;
document.getElementById('resultado').scrollIntoView({behavior:'smooth',block:'center'});
});


// Lead (exemplo: envia para WhatsApp com pré-texto; em produção, integrar com API/CRM)
function sendLead(e){
e.preventDefault();
const data = Object.fromEntries(new FormData(e.target).entries());
const msg = `Olá! Quero assinar energia por assinatura.%0A`+
`Nome: ${encodeURIComponent(data.nome)}%0A`+
`WhatsApp: ${encodeURIComponent(data.telefone)}%0A`+
`E-mail: ${encodeURIComponent(data.email)}%0A`+
`Gasto médio: R$ ${encodeURIComponent(data.gasto2||'-')}`;
const phone = '5599999999999'; // <- Substituir pelo seu DDI+DDD+número
window.open(`https://wa.me/${phone}?text=${msg}`, '_blank');
document.getElementById('form-ok').hidden = false;
e.target.reset();
}


document.getElementById('y').textContent = new Date().getFullYear();
</script>


<!-- SEO básico e dados estruturados -->
<script type="application/ld+json">
{
"@context": "https://schema.org",
"@type": "LocalBusiness",
"name": "NeoEnergia+ Assinatura",
"image": "",
"telephone": "+55 99 99999-9999",
"email": "contato@suaempresa.com",
"address": {"@type":"PostalAddress","addressCountry":"BR"},
"url": "https://www.seudominio.com.br",
"description": "Assine energia renovável e reduza sua conta de luz sem obras.",
"areaServed": ["ENEL","CEMIG","CPFL","NEOENERGIA","ENERGISA"]
}
</script>
</body>
</html>
