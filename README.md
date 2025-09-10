<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dashboard SDR - Conversões & Perdas</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body class="bg-gray-100 text-gray-800">

  <div class="max-w-7xl mx-auto p-6 space-y-12">

    <!-- Conversões -->
    <header class="text-center">
      <h1 class="text-3xl font-bold text-indigo-700">📊 Panorama da Conversão</h1>
      <p class="mt-2 text-gray-600">Visão consolidada do funil SDR → Comercial.</p>
    </header>

    <!-- Cards Resumo Conversão -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div class="bg-white shadow-md rounded-2xl p-6 text-center">
        <h2 class="text-xl font-semibold text-gray-700">Leads Qualificados</h2>
        <p class="mt-2 text-3xl font-bold text-indigo-600">2.832</p>
      </div>
      <div class="bg-white shadow-md rounded-2xl p-6 text-center">
        <h2 class="text-xl font-semibold text-gray-700">Ganhos Comerciais</h2>
        <p class="mt-2 text-3xl font-bold text-green-600">101</p>
      </div>
      <div class="bg-white shadow-md rounded-2xl p-6 text-center">
        <h2 class="text-xl font-semibold text-gray-700">Taxa de Conversão</h2>
        <p class="mt-2 text-3xl font-bold text-blue-600">3,57%</p>
      </div>
    </div>

    <!-- Gráfico Conversão + Filtro -->
    <section>
      <div class="flex items-center justify-between">
        <h2 class="text-2xl font-bold text-indigo-700">Conversão por Segmento</h2>
        <select id="segmentFilter" class="ml-4 p-2 border rounded">
          <option value="all">Todos os Segmentos</option>
          <option value="Blips - Sorvete">Blips - Sorvete</option>
          <option value="Blips - CV">Blips - CV</option>
          <option value="Blips - Fitness">Blips - Fitness</option>
          <option value="Ideal - Pipeline">Ideal - Pipeline</option>
          <option value="Blips - Construcao">Blips - Construcao</option>
          <option value="Blips - Food">Blips - Food</option>
        </select>
      </div>
      <canvas id="conversionChart" class="bg-white p-4 rounded-2xl shadow-md mt-4"></canvas>
    </section>

    <!-- Tabela Conversão -->
    <section>
      <h2 class="text-2xl font-bold text-indigo-700 mb-4">📋 Dados Segmentados</h2>
      <div class="overflow-x-auto bg-white shadow-md rounded-2xl">
        <table class="min-w-full text-left text-sm" id="conversionTable">
          <thead class="bg-indigo-600 text-white">
            <tr>
              <th class="px-6 py-3">Segmento</th>
              <th class="px-6 py-3">Leads SDR</th>
              <th class="px-6 py-3">Vendas</th>
              <th class="px-6 py-3">Taxa Conversão</th>
            </tr>
          </thead>
          <tbody class="divide-y divide-gray-200">
            <tr><td class="px-6 py-3">Blips - Sorvete</td><td>1000</td><td>33</td><td>3,30%</td></tr>
            <tr><td class="px-6 py-3">Blips - CV</td><td>661</td><td>9</td><td>1,36%</td></tr>
            <tr><td class="px-6 py-3">Blips - Fitness</td><td>419</td><td>7</td><td>1,67%</td></tr>
            <tr><td class="px-6 py-3">Ideal - Pipeline</td><td>112</td><td>33</td><td>29,46%</td></tr>
            <tr><td class="px-6 py-3">Blips - Construcao</td><td>593</td><td>16</td><td>2,70%</td></tr>
            <tr><td class="px-6 py-3">Blips - Food</td><td>47</td><td>3</td><td>6,38%</td></tr>
          </tbody>
        </table>
      </div>
    </section>

    <!-- PERDAS -->
    <header class="text-center mt-12">
      <h1 class="text-3xl font-bold text-red-700">❌ Visão de Perdas</h1>
      <p class="mt-2 text-gray-600">Análise dos leads perdidos por segmento e principais motivos.</p>
    </header>

    <!-- Cards Resumo Perdas -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div class="bg-white shadow-md rounded-2xl p-6 text-center">
        <h2 class="text-xl font-semibold text-gray-700">Total Perdidos</h2>
        <p class="mt-2 text-3xl font-bold text-red-600">712</p>
      </div>
      <div class="bg-white shadow-md rounded-2xl p-6 text-center">
        <h2 class="text-xl font-semibold text-gray-700">Valor Total</h2>
        <p class="mt-2 text-3xl font-bold text-red-600">R$ 34,48M</p>
      </div>
      <div class="bg-white shadow-md rounded-2xl p-6 text-center">
        <h2 class="text-xl font-semibold text-gray-700">Ticket Médio</h2>
        <p class="mt-2 text-3xl font-bold text-orange-600">R$ 40.048</p>
      </div>
    </div>

    <!-- Gráfico Motivos de Perda -->
    <section>
      <h2 class="text-2xl font-bold text-red-700">Motivos de Perda (Consolidado)</h2>
      <canvas id="lossReasonsChart" class="bg-white p-4 rounded-2xl shadow-md mt-4"></canvas>
    </section>

    <!-- Exemplos Segmentados -->
    <section>
      <h2 class="text-2xl font-bold text-red-700 mb-4">📋 Perdas por Segmento</h2>
      <div class="overflow-x-auto bg-white shadow-md rounded-2xl">
        <table class="min-w-full text-left text-sm">
          <thead class="bg-red-600 text-white">
            <tr>
              <th class="px-6 py-3">Segmento</th>
              <th class="px-6 py-3">Leads Perdidos</th>
              <th class="px-6 py-3">Valor Total</th>
              <th class="px-6 py-3">Ticket Médio</th>
              <th class="px-6 py-3">Motivo Mais Frequente</th>
            </tr>
          </thead>
          <tbody class="divide-y divide-gray-200">
            <tr><td class="px-6 py-3">Blips - CV</td><td>84</td><td>R$ 3,41M</td><td>R$ 40k</td><td>Falta de Retorno</td></tr>
            <tr><td class="px-6 py-3">Estética</td><td>45</td><td>R$ 4,36M</td><td>R$ 97k</td><td>Sem Interesse</td></tr>
            <tr><td class="px-6 py-3">Food</td><td>144</td><td>R$ 4,80M</td><td>R$ 33k</td><td>Sem Retorno</td></tr>
            <tr><td class="px-6 py-3">Sorvete</td><td>190</td><td>R$ 8,00M</td><td>R$ 42k</td><td>Falta de Retorno</td></tr>
            <tr><td class="px-6 py-3">Fitness</td><td>41</td><td>R$ 1,76M</td><td>R$ 42k</td><td>Sem Retorno</td></tr>
            <tr><td class="px-6 py-3">Construção</td><td>68</td><td>R$ 5,91M</td><td>R$ 86k</td><td>Sem Retorno</td></tr>
            <tr><td class="px-6 py-3">Pizza</td><td>41</td><td>R$ 1,85M</td><td>R$ 45k</td><td>Falta de Retorno</td></tr>
            <tr><td class="px-6 py-3">Ideal</td><td>72</td><td>R$ 3,68M</td><td>R$ 51k</td><td>Sem Retorno</td></tr>
            <tr><td class="px-6 py-3">Confecção</td><td>27</td><td>R$ 2,11M</td><td>R$ 78k</td><td>Falta de Retorno</td></tr>
          </tbody>
        </table>
      </div>
    </section>

  </div>

  <!-- Scripts Gráficos -->
  <script>
    const conversionData = [
      { segmento: 'Blips - Sorvete', leads: 1000, vendas: 33, taxa: '3,30%' },
      { segmento: 'Blips - CV', leads: 661, vendas: 9, taxa: '1,36%' },
      { segmento: 'Blips - Fitness', leads: 419, vendas: 7, taxa: '1,67%' },
      { segmento: 'Ideal - Pipeline', leads: 112, vendas: 33, taxa: '29,46%' },
      { segmento: 'Blips - Construcao', leads: 593, vendas: 16, taxa: '2,70%' },
      { segmento: 'Blips - Food', leads: 47, vendas: 3, taxa: '6,38%' }
    ];

    // Gráfico de Conversão
    const ctx = document.getElementById('conversionChart').getContext('2d');
    let conversionChart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: conversionData.map(d => d.segmento),
        datasets: [
          { label: 'Leads SDR', data: conversionData.map(d => d.leads), backgroundColor: 'rgba(99, 102, 241, 0.6)' },
          { label: 'Vendas', data: conversionData.map(d => d.vendas), backgroundColor: 'rgba(16, 185, 129, 0.6)' }
        ]
      }
    });

    // Filtro de Segmento (apenas conversão)
    document.getElementById('segmentFilter').addEventListener('change', function() {
      const selected = this.value;
      let filteredData = selected === 'all' ? conversionData : conversionData.filter(d => d.segmento === selected);

      // Atualiza gráfico
      conversionChart.data.labels = filteredData.map(d => d.segmento);
      conversionChart.data.datasets[0].data = filteredData.map(d => d.leads);
      conversionChart.data.datasets[1].data = filteredData.map(d => d.vendas);
      conversionChart.update();

      // Atualiza tabela
      const tbody = document.querySelector('#conversionTable tbody');
      tbody.innerHTML = '';
      filteredData.forEach(d => {
        tbody.innerHTML += `<tr><td class="px-6 py-3">${d.segmento}</td><td>${d.leads}</td><td>${d.vendas}</td><td>${d.taxa}</td></tr>`;
      });
    });

    // Motivos de Perda (total = 712)
    new Chart(document.getElementById('lossReasonsChart'), {
      type: 'pie',
      data: {
        labels: [
          'Falta de Retorno (230)',
          'Problemas de Crédito (120)',
          'Cadastro Duplicado (80)',
          'Fora do Portfólio (72)',
          'Sem Contato Inicial (55)',
          'Sem Interesse (50)',
          'Contato Futuro (50)',
          'Outros (55)'
        ],
        datasets: [{
          data: [230, 120, 80, 72, 55, 50, 50, 55],
          backgroundColor: [
            'rgba(239, 68, 68, 0.7)',
            'rgba(251, 191, 36, 0.7)',
            'rgba(59, 130, 246, 0.7)',
            'rgba(16, 185, 129, 0.7)',
            'rgba(139, 92, 246, 0.7)',
            'rgba(245, 158, 11, 0.7)',
            'rgba(34, 197, 94, 0.7)',
            'rgba(107, 114, 128, 0.7)'
          ]
        }]
      }
    });
  </script>

</body>
</html>
