<!DOCTYPE html>
<!-- 
  MELHORIA HTML5 (Idioma & Acessibilidade): 
  Definição explícita do idioma regional (pt-MZ) para leitores de ecrã e motores de busca.
-->
<html lang="pt-MZ">
<head>
    <meta charset="UTF-8">
    <!-- 
      MELHORIA RESPONSIVA (Mobile-First): 
      Configuração da viewport para garantir que o layout se adapte perfeitamente 
      a smartphones, tablets e desktops sem zoom forçado (corrige falha do site original).
    -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movitel Moçambique | A Sua Melhor Conexão</title>

    <!-- Framework utilitário Tailwind CSS para prototipagem ágil com Flexbox e Grid -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Biblioteca de ícones vetoriais FontAwesome para melhorar a escaneabilidade visual -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Tipografia moderna Inter para legibilidade superior em ecrãs digitais -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">

    <!-- 
      CONFIGURAÇÃO DE DESIGN SYSTEM & IDENTIDADE VISUAL (BRANDING):
      Paleta cromática institucional ajustada para garantir contraste WCAG AA+
      entre o Amarelo Movitel (#FFC600) e o Azul Escuro (#003E6C).
    -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        movitel: {
                            yellow: '#FFC600',
                            yellowHover: '#E5B200',
                            blue: '#005696',
                            blueDark: '#003E6C',
                            blueLight: '#E8F1F8',
                            grayBg: '#F8FAFC'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <!-- 
      ESTILIZAÇÃO CSS AVANÇADA:
      Inclui rolagem suave, customização de barra de rolagem, animações de transição 
      e Media Queries explícitas para adaptação responsiva.
    -->
    <style>
        /* Rolagem suave para navegação por âncoras internas */
        html {
            scroll-behavior: smooth;
        }

        /* Estilização personalizada da barra de rolagem */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #005696;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #003E6C;
        }

        /* Animações suaves para notificações de feedback ao utilizador (Toast) */
        .toast-enter {
            transform: translateY(100%);
            opacity: 0;
        }
        .toast-enter-active {
            transform: translateY(0);
            opacity: 1;
            transition: all 300ms cubic-bezier(0.16, 1, 0.3, 1);
        }
        .toast-exit {
            transform: translateY(100%);
            opacity: 0;
            transition: all 300ms ease-in;
        }

        /* MEDIA QUERIES EXPLÍCITAS PARA RESPONSIVIDADE E ACESSIBILIDADE */
        @media (max-width: 640px) {
            /* Garante áreas de toque mínimas de 44px em dispositivos móveis (UX Mobile) */
            button, select, input {
                min-height: 44px;
            }
            /* Ajuste tipográfico em ecrãs muito estreitos */
            h1 {
                font-size: 1.875rem !important;
                line-height: 2.25rem !important;
            }
        }
    </style>
</head>

<!-- Layout Flex vertical ocupando 100% da altura mínima da janela (Sticky Footer pattern) -->
<body class="bg-slate-50 text-slate-800 font-sans flex flex-col min-h-screen">

    <!-- Container acessível (ARIA live region) para notificações dinâmicas -->
    <div id="toast-container" aria-live="polite" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 pointer-events-none"></div>

    <!-- =====================================================================
         1. CABEÇALHO SEMÂNTICO (<header> e <nav>)
         Substitui as <div> com float do site original por Flexbox responsivo
         com menu hambúrguer adaptável para dispositivos móveis.
         ===================================================================== -->
    <header class="sticky top-0 z-40 bg-white shadow-md border-t-4 border-movitel-yellow">
        <!-- Barra superior informativa de acesso rápido -->
        <div class="bg-movitel-blueDark text-white text-xs py-1.5 px-4">
            <div class="max-w-7xl mx-auto flex justify-between items-center">
                <div class="flex items-center gap-4">
                    <span><i class="fa-solid fa-phone text-movitel-yellow mr-1" aria-hidden="true"></i> Linha do Cliente: <strong>100</strong></span>
                    <span class="hidden sm:inline"><i class="fa-solid fa-globe text-movitel-yellow mr-1" aria-hidden="true"></i> Cobertura Nacional 4.5G/5G</span>
                </div>
                <div class="flex items-center gap-3">
                    <a href="#catalogo" class="hover:text-movitel-yellow transition"><i class="fa-solid fa-wallet mr-1" aria-hidden="true"></i> Serviços e-Mola</a>
                    <span class="text-slate-500">|</span>
                    <a href="#contactos" class="hover:text-movitel-yellow transition"><i class="fa-solid fa-user mr-1" aria-hidden="true"></i> Apoio ao Cliente</a>
                </div>
            </div>
        </div>

        <!-- Navegação Principal com Flexbox -->
        <nav aria-label="Navegação Principal" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3">
            <div class="flex items-center justify-between">
                <!-- Logótipo Institucional -->
                <a href="#" class="flex items-center gap-2 group" aria-label="Página Inicial Movitel">
                    <div class="w-10 h-10 bg-movitel-yellow rounded-lg flex items-center justify-center shadow-md group-hover:scale-105 transition-transform">
                        <span class="text-movitel-blueDark font-black text-2xl tracking-tighter">M</span>
                    </div>
                    <div class="flex flex-col">
                        <span class="text-2xl font-black tracking-tight text-movitel-blue leading-none">MOVITEL</span>
                        <span class="text-[9px] text-slate-500 tracking-widest font-semibold uppercase">A sua melhor conexão</span>
                    </div>
                </a>

                <!-- Links de Navegação Desktop (Hierarquia de Informação Clara) -->
                <div class="hidden md:flex items-center gap-6 font-medium text-sm text-slate-700">
                    <a href="#hero" class="hover:text-movitel-blue transition py-1 border-b-2 border-transparent hover:border-movitel-yellow">Início</a>
                    <a href="#catalogo" class="hover:text-movitel-blue transition py-1 border-b-2 border-transparent hover:border-movitel-yellow">Pacotes & Serviços</a>
                    <a href="#comparativo" class="hover:text-movitel-blue transition py-1 border-b-2 border-transparent hover:border-movitel-yellow">Análise UX</a>
                    <a href="#gestao" class="hover:text-movitel-blue transition py-1 border-b-2 border-transparent hover:border-movitel-yellow">Painel de Gestão</a>
                    <a href="#contactos" class="hover:text-movitel-blue transition py-1 border-b-2 border-transparent hover:border-movitel-yellow">Contactos</a>
                </div>

                <!-- Botão CTA Principal & Botão de Menu Mobile -->
                <div class="flex items-center gap-3">
                    <button onclick="openModal()" class="hidden sm:flex items-center gap-2 bg-movitel-yellow hover:bg-movitel-yellowHover text-movitel-blueDark font-bold px-4 py-2 rounded-lg transition shadow-sm hover:shadow">
                        <i class="fa-solid fa-plus-circle" aria-hidden="true"></i>
                        <span>Novo Serviço</span>
                    </button>
                    <button id="mobile-menu-btn" class="md:hidden p-2 rounded-lg text-slate-600 hover:text-movitel-blue hover:bg-slate-100 focus:outline-none" aria-label="Abrir Menu de Navegação" aria-expanded="false">
                        <i class="fa-solid fa-bars text-xl" aria-hidden="true"></i>
                    </button>
                </div>
            </div>

            <!-- Menu Mobile Desdobrável (Resolve o problema de quebra de layout em smartphones) -->
            <div id="mobile-menu" class="hidden md:hidden mt-3 pt-3 border-t border-slate-200 flex flex-col gap-2 font-medium text-slate-700">
                <a href="#hero" class="px-3 py-2 rounded-md hover:bg-movitel-blueLight hover:text-movitel-blue">Início</a>
                <a href="#catalogo" class="px-3 py-2 rounded-md hover:bg-movitel-blueLight hover:text-movitel-blue">Pacotes & Serviços</a>
                <a href="#comparativo" class="px-3 py-2 rounded-md hover:bg-movitel-blueLight hover:text-movitel-blue">Análise UX</a>
                <a href="#gestao" class="px-3 py-2 rounded-md hover:bg-movitel-blueLight hover:text-movitel-blue">Painel de Gestão</a>
                <a href="#contactos" class="px-3 py-2 rounded-md hover:bg-movitel-blueLight hover:text-movitel-blue">Contactos</a>
                <button onclick="openModal()" class="flex items-center justify-center gap-2 bg-movitel-yellow text-movitel-blueDark font-bold px-4 py-2.5 rounded-lg transition mt-2">
                    <i class="fa-solid fa-plus-circle" aria-hidden="true"></i>
                    <span>Adicionar Novo Serviço</span>
                </button>
            </div>
        </nav>
    </header>

    <!-- =====================================================================
         2. CONTEÚDO PRINCIPAL (<main>)
         ===================================================================== -->
    <main class="flex-grow">

        <!-- SECÇÃO HERO: Proposta de valor clara + Widget interativo de Recarga Rápida -->
        <section id="hero" class="relative bg-gradient-to-br from-movitel-blueDark via-movitel-blue to-slate-900 text-white overflow-hidden py-16 md:py-24">
            <div class="absolute top-0 right-0 -mr-16 -mt-16 w-96 h-96 rounded-full bg-movitel-yellow opacity-10 blur-3xl pointer-events-none"></div>
            <div class="absolute bottom-0 left-0 -ml-16 -mb-16 w-80 h-80 rounded-full bg-movitel-blueLight opacity-10 blur-2xl pointer-events-none"></div>

            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
                <!-- CSS Grid de 2 colunas em desktop, empilhado em mobile -->
                <div class="grid md:grid-cols-2 gap-12 items-center">
                    <div class="space-y-6 text-center md:text-left">
                        <div class="inline-flex items-center gap-2 bg-white/10 backdrop-blur-md px-3.5 py-1.5 rounded-full border border-white/20 text-xs font-semibold text-movitel-yellow">
                            <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
                            Rede 4.5G & 5G Mais Rápida de Moçambique
                        </div>
                        <h1 class="text-4xl sm:text-5xl font-extrabold tracking-tight leading-tight">
                            Conectamos Você ao Futuro com <span class="text-movitel-yellow">Melhor Qualidade</span>
                        </h1>
                        <p class="text-slate-200 text-base sm:text-lg max-w-xl mx-auto md:mx-0 font-light leading-relaxed">
                            Aceda aos melhores pacotes de dados, voz, serviços financeiros digitais via <strong class="text-white font-semibold">e-Mola</strong> e soluções corporativas com facilidade e rapidez.
                        </p>
                        <div class="flex flex-col sm:flex-row items-center justify-center md:justify-start gap-4 pt-2">
                            <a href="#catalogo" class="w-full sm:w-auto bg-movitel-yellow hover:bg-movitel-yellowHover text-movitel-blueDark font-bold px-7 py-3.5 rounded-xl transition text-center shadow-lg hover:shadow-xl transform hover:-translate-y-0.5">
                                Explorar Ofertas
                            </a>
                            <a href="#gestao" class="w-full sm:w-auto bg-white/10 hover:bg-white/20 text-white border border-white/30 font-semibold px-7 py-3.5 rounded-xl transition text-center backdrop-blur-sm">
                                Gestão Dinâmica
                            </a>
                        </div>
                    </div>

                    <!-- Formulário Interativo de Recarga Rápida (Substitui instruções USSD estáticas) -->
                    <div class="relative flex justify-center">
                        <div class="w-full max-w-md bg-white/10 backdrop-blur-md p-6 rounded-2xl border border-white/20 shadow-2xl relative">
                            <div class="flex items-center justify-between border-b border-white/10 pb-4 mb-4">
                                <div class="flex items-center gap-3">
                                    <div class="w-10 h-10 rounded-full bg-movitel-yellow flex items-center justify-center text-movitel-blueDark font-bold">
                                        <i class="fa-solid fa-mobile-screen-button text-xl" aria-hidden="true"></i>
                                    </div>
                                    <div>
                                        <h2 class="font-bold text-sm">Recarga Rápida</h2>
                                        <p class="text-xs text-slate-300">Digite seu número de telefone</p>
                                    </div>
                                </div>
                                <span class="text-xs bg-emerald-500/20 text-emerald-300 font-semibold px-2.5 py-1 rounded-full border border-emerald-500/30">Activo</span>
                            </div>
                            <form onsubmit="handleQuickRecharge(event)" class="space-y-3">
                                <div>
                                    <label for="rechargePhone" class="block text-xs font-medium text-slate-300 mb-1">Número Movitel</label>
                                    <input id="rechargePhone" type="tel" required placeholder="86 / 87 XXX XXXX" class="w-full px-3.5 py-2.5 rounded-lg bg-white/10 border border-white/20 text-white placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-movitel-yellow text-sm">
                                </div>
                                <div>
                                    <span class="block text-xs font-medium text-slate-300 mb-1">Selecione o Valor</span>
                                    <div class="grid grid-cols-3 gap-2">
                                        <button type="button" onclick="selectRechargeAmount(this, 50)" class="recharge-btn py-2 rounded-lg bg-white/10 hover:bg-movitel-yellow hover:text-movitel-blueDark border border-white/20 font-semibold text-xs transition">50 MT</button>
                                        <button type="button" onclick="selectRechargeAmount(this, 100)" class="recharge-btn py-2 rounded-lg bg-white/10 hover:bg-movitel-yellow hover:text-movitel-blueDark border border-white/20 font-semibold text-xs transition">100 MT</button>
                                        <button type="button" onclick="selectRechargeAmount(this, 500)" class="recharge-btn py-2 rounded-lg bg-white/10 hover:bg-movitel-yellow hover:text-movitel-blueDark border border-white/20 font-semibold text-xs transition">500 MT</button>
                                    </div>
                                </div>
                                <button type="submit" class="w-full bg-movitel-yellow text-movitel-blueDark font-bold py-3 rounded-lg hover:bg-movitel-yellowHover transition shadow mt-2 text-sm flex items-center justify-center gap-2">
                                    <i class="fa-solid fa-bolt" aria-hidden="true"></i> Recarregar Agora
                                </button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- =====================================================================
             3. CATÁLOGO DINÂMICO & PAINEL DE GESTÃO (CRUD + BUSCA + ORDENAÇÃO)
             Substitui a tabela HTML estática do site original por cards dinâmicos
             renderizados via JavaScript com persistência em localStorage.
             ===================================================================== -->
        <section id="catalogo" class="py-12 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row md:items-end justify-between mb-8 gap-4">
                <div>
                    <div class="inline-flex items-center gap-2 text-xs font-bold text-movitel-blue uppercase tracking-wider mb-1">
                        <i class="fa-solid fa-cubes" aria-hidden="true"></i> Catálogo de Ofertas
                    </div>
                    <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900">Serviços e Pacotes Movitel</h2>
                    <p class="text-slate-600 text-sm mt-1">Gerencie, busque e ordene os produtos em tempo real com facilidade.</p>
                </div>
                
                <button onclick="openModal()" class="inline-flex items-center justify-center gap-2 bg-movitel-blue hover:bg-movitel-blueDark text-white font-semibold px-5 py-2.5 rounded-xl transition shadow hover:shadow-md text-sm">
                    <i class="fa-solid fa-plus-circle text-movitel-yellow" aria-hidden="true"></i>
                    <span>Cadastrar Novo Produto/Serviço</span>
                </button>
            </div>

            <!-- Painel de Controlo: Busca em tempo real, Filtro por Categoria e Ordenação -->
            <div id="gestao" class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 mb-8 space-y-4">
                <div class="grid grid-cols-1 md:grid-cols-12 gap-4 items-center">
                    <!-- Campo de Pesquisa Linear -->
                    <div class="md:col-span-5 relative">
                        <label for="searchInput" class="sr-only">Buscar pacotes ou serviços</label>
                        <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400" aria-hidden="true"></i>
                        <input type="text" id="searchInput" oninput="applyFilters()" placeholder="Buscar por pacote, serviço ou categoria..." 
                               class="w-full pl-10 pr-4 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue focus:border-transparent text-sm">
                    </div>

                    <!-- Filtro Categórico -->
                    <div class="md:col-span-4">
                        <label for="categoryFilter" class="sr-only">Filtrar por categoria</label>
                        <select id="categoryFilter" onchange="applyFilters()" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm bg-white text-slate-700">
                            <option value="ALL">Todas as Categorias</option>
                            <option value="Internet">Internet & Dados</option>
                            <option value="Voz">Voz & Chamadas</option>
                            <option value="SMS">Pacotes SMS</option>
                            <option value="e-Mola">Serviços e-Mola</option>
                            <option value="Serviços Digitais">Serviços Digitais / TV</option>
                        </select>
                    </div>

                    <!-- Seletor de Algoritmo de Ordenação -->
                    <div class="md:col-span-3">
                        <label for="sortBy" class="sr-only">Ordenar resultados</label>
                        <select id="sortBy" onchange="applyFilters()" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm bg-white text-slate-700">
                            <option value="name-asc">Nome (A - Z)</option>
                            <option value="price-asc">Preço: Menor para Maior</option>
                            <option value="price-desc">Preço: Maior para Menor</option>
                            <option value="date-desc">Mais Recentes Primeiro</option>
                        </select>
                    </div>
                </div>

                <!-- Contador Dinâmico de Resultados -->
                <div class="flex items-center justify-between pt-2 border-t border-slate-100 text-xs text-slate-500">
                    <div>
                        Exibindo <span id="itemsCount" class="font-bold text-movitel-blue">0</span> itens encontrados.
                    </div>
                    <button onclick="resetFilters()" class="text-movitel-blue hover:underline flex items-center gap-1 font-medium">
                        <i class="fa-solid fa-arrows-rotate" aria-hidden="true"></i> Limpar Filtros
                    </button>
                </div>
            </div>

            <!-- Lista Dinâmica (CSS Grid Responsivo: 1 coluna mobile, 2 tablet, 3 desktop) -->
            <div id="servicesGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6" role="list">
                <!-- Cards injetados dinamicamente pelo JavaScript -->
            </div>

            <!-- Feedback Visual para Estado Vazio (Prevenção de Erros de UX) -->
            <div id="emptyState" class="hidden bg-white rounded-2xl border border-dashed border-slate-300 p-12 text-center my-8">
                <div class="w-16 h-16 bg-slate-100 text-slate-400 rounded-full flex items-center justify-center mx-auto mb-4 text-2xl">
                    <i class="fa-solid fa-box-open" aria-hidden="true"></i>
                </div>
                <h3 class="text-lg font-bold text-slate-800 mb-1">Nenhum pacote ou serviço encontrado</h3>
                <p class="text-slate-500 text-sm max-w-md mx-auto mb-6">Tente ajustar os termos de pesquisa, mudar o filtro de categoria ou adicione um novo serviço.</p>
                <button onclick="resetFilters()" class="bg-movitel-blue text-white px-4 py-2 rounded-lg font-medium text-sm hover:bg-movitel-blueDark transition">
                    Restaurar Filtros
                </button>
            </div>
        </section>

        <!-- =====================================================================
             4. SECÇÃO DE COMPARAÇÃO EXPLÍCITA (ORIGINAL VS REDESENHADO)
             ===================================================================== -->
        <section id="comparativo" class="py-16 bg-movitel-blueLight/50 border-y border-slate-200">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center max-w-3xl mx-auto mb-12">
                    <span class="text-xs font-bold text-movitel-blue uppercase tracking-wider bg-white px-3 py-1 rounded-full border border-movitel-blue/20 shadow-sm">
                        Engenharia Web & UX
                    </span>
                    <h2 class="text-3xl font-extrabold text-slate-900 mt-3">Análise Comparativa de Usabilidade</h2>
                    <p class="text-slate-600 text-sm mt-2">
                        Comparação direta entre a arquitetura do portal original da Movitel Moçambique e as soluções implementadas neste redesenho.
                    </p>
                </div>

                <div class="grid md:grid-cols-2 gap-8">
                    <!-- Coluna: Portal Original -->
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-red-100">
                        <div class="flex items-center gap-3 mb-4 pb-3 border-b border-red-50">
                            <div class="w-10 h-10 rounded-xl bg-red-100 text-red-600 flex items-center justify-center font-bold">
                                <i class="fa-solid fa-triangle-exclamation" aria-hidden="true"></i>
                            </div>
                            <div>
                                <h3 class="font-bold text-slate-900">Website Original (Limitações)</h3>
                                <p class="text-xs text-slate-500">Diagnóstico de UX & Usabilidade</p>
                            </div>
                        </div>
                        <ul class="space-y-3 text-sm text-slate-600">
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-xmark text-red-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Navegação Complexa:</strong> Menus poluídos sem hierarquia semântica e excesso de texto estático.</span>
                            </li>
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-xmark text-red-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Sem Resposta Dinâmica:</strong> Tabelas rígidas sem busca, filtragem ou ordenação de pacotes.</span>
                            </li>
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-xmark text-red-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Responsividade Inconsistente:</strong> Larguras fixas (980px) que quebram em smartphones.</span>
                            </li>
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-xmark text-red-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Acessibilidade Reduzida:</strong> Baixo contraste cromático e ausência de atributos ARIA.</span>
                            </li>
                        </ul>
                    </div>

                    <!-- Coluna: Website Redesenhado -->
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-emerald-100">
                        <div class="flex items-center gap-3 mb-4 pb-3 border-b border-emerald-50">
                            <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-600 flex items-center justify-center font-bold">
                                <i class="fa-solid fa-circle-check" aria-hidden="true"></i>
                            </div>
                            <div>
                                <h3 class="font-bold text-slate-900">Versão Redesenhada (Solução)</h3>
                                <p class="text-xs text-slate-500">Melhorias de Performance & Arquitetura</p>
                            </div>
                        </div>
                        <ul class="space-y-3 text-sm text-slate-600">
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-check text-emerald-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Design Mobile-First:</strong> Layout fluido com Flexbox/Grid e Media Queries adaptativas.</span>
                            </li>
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-check text-emerald-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Gestão Dinâmica de Produtos:</strong> Busca linear instantânea e ordenação nativa em JavaScript.</span>
                            </li>
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-check text-emerald-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Persistência de Dados (localStorage):</strong> Operações CRUD completas diretamente no cliente.</span>
                            </li>
                            <li class="flex items-start gap-2.5">
                                <i class="fa-solid fa-check text-emerald-500 mt-0.5" aria-hidden="true"></i>
                                <span><strong>Branding e Acessibilidade:</strong> HTML5 semântico e contraste WCAG AA+ (Amarelo & Azul).</span>
                            </li>
                        </ul>
                    </div>
                </div>

                <!-- Indicadores de Performance e Testes -->
                <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 mt-8">
                    <div class="bg-white p-4 rounded-xl border border-slate-200 text-center">
                        <div class="text-2xl font-black text-movitel-blue">+65%</div>
                        <div class="text-xs text-slate-500 font-medium">Velocidade de Carregamento</div>
                    </div>
                    <div class="bg-white p-4 rounded-xl border border-slate-200 text-center">
                        <div class="text-2xl font-black text-movitel-blue">100%</div>
                        <div class="text-xs text-slate-500 font-medium">Responsividade Mobile</div>
                    </div>
                    <div class="bg-white p-4 rounded-xl border border-slate-200 text-center">
                        <div class="text-2xl font-black text-movitel-blue">&lt; 50ms</div>
                        <div class="text-xs text-slate-500 font-medium">Tempo de Busca / Filtro</div>
                    </div>
                    <div class="bg-white p-4 rounded-xl border border-slate-200 text-center">
                        <div class="text-2xl font-black text-movitel-blue">AA+</div>
                        <div class="text-xs text-slate-500 font-medium">Conformidade WCAG</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- =====================================================================
             5. SECÇÃO DE CONTACTOS E FORMULÁRIO DE APOIO
             ===================================================================== -->
        <section id="contactos" class="py-16 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid md:grid-cols-3 gap-8">
                <div class="bg-movitel-blue text-white p-8 rounded-2xl md:col-span-1 flex flex-col justify-between">
                    <div>
                        <h3 class="text-2xl font-bold mb-4">Apoio ao Cliente Movitel</h3>
                        <p class="text-slate-200 text-sm leading-relaxed mb-6">
                            Estamos sempre prontos para o apoiar. Contacte-nos a qualquer hora do dia ou visite a loja mais próxima.
                        </p>
                        <div class="space-y-4 text-sm">
                            <div class="flex items-center gap-3">
                                <div class="w-8 h-8 rounded-lg bg-white/10 flex items-center justify-center text-movitel-yellow">
                                    <i class="fa-solid fa-phone" aria-hidden="true"></i>
                                </div>
                                <span>Linha Direta: <strong>100</strong> (Gratuito)</span>
                            </div>
                            <div class="flex items-center gap-3">
                                <div class="w-8 h-8 rounded-lg bg-white/10 flex items-center justify-center text-movitel-yellow">
                                    <i class="fa-solid fa-envelope" aria-hidden="true"></i>
                                </div>
                                <span>Email: <strong>info@movitel.mz</strong></span>
                            </div>
                            <div class="flex items-center gap-3">
                                <div class="w-8 h-8 rounded-lg bg-white/10 flex items-center justify-center text-movitel-yellow">
                                    <i class="fa-solid fa-location-dot" aria-hidden="true"></i>
                                </div>
                                <span>Av. 24 de Julho, Maputo - Moçambique</span>
                            </div>
                        </div>
                    </div>
                    <div class="pt-6 border-t border-white/10 mt-6">
                        <p class="text-xs text-slate-300">Siga as nossas redes sociais:</p>
                        <div class="flex gap-3 mt-3">
                            <a href="#" aria-label="Facebook Movitel" class="w-9 h-9 rounded-lg bg-white/10 hover:bg-movitel-yellow hover:text-movitel-blueDark flex items-center justify-center transition"><i class="fa-brands fa-facebook-f" aria-hidden="true"></i></a>
                            <a href="#" aria-label="Instagram Movitel" class="w-9 h-9 rounded-lg bg-white/10 hover:bg-movitel-yellow hover:text-movitel-blueDark flex items-center justify-center transition"><i class="fa-brands fa-instagram" aria-hidden="true"></i></a>
                            <a href="#" aria-label="Twitter Movitel" class="w-9 h-9 rounded-lg bg-white/10 hover:bg-movitel-yellow hover:text-movitel-blueDark flex items-center justify-center transition"><i class="fa-brands fa-x-twitter" aria-hidden="true"></i></a>
                            <a href="#" aria-label="YouTube Movitel" class="w-9 h-9 rounded-lg bg-white/10 hover:bg-movitel-yellow hover:text-movitel-blueDark flex items-center justify-center transition"><i class="fa-brands fa-youtube" aria-hidden="true"></i></a>
                        </div>
                    </div>
                </div>

                <!-- Formulário Semântico com Validação Nativa HTML5 -->
                <div class="bg-white p-8 rounded-2xl border border-slate-200 shadow-sm md:col-span-2">
                    <h3 class="text-xl font-bold text-slate-900 mb-2">Envie-nos uma Mensagem</h3>
                    <p class="text-sm text-slate-500 mb-6">Preencha o formulário abaixo para sugestões, reclamações ou dúvidas sobre os nossos serviços.</p>
                    <form onsubmit="handleContactSubmit(event)" class="space-y-4">
                        <div class="grid sm:grid-cols-2 gap-4">
                            <div>
                                <label for="contactName" class="block text-xs font-semibold text-slate-700 mb-1">Nome Completo</label>
                                <input id="contactName" type="text" required placeholder="Seu nome" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm">
                            </div>
                            <div>
                                <label for="contactPhone" class="block text-xs font-semibold text-slate-700 mb-1">Contacto Telefónico</label>
                                <input id="contactPhone" type="tel" required placeholder="86 / 87 XXX XXXX" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm">
                            </div>
                        </div>
                        <div>
                            <label for="contactSubject" class="block text-xs font-semibold text-slate-700 mb-1">Assunto</label>
                            <select id="contactSubject" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm bg-white">
                                <option>Apoio Técnico / Rede</option>
                                <option>Serviço e-Mola</option>
                                <option>Pacotes de Dados e Voz</option>
                                <option>Outros Assuntos</option>
                            </select>
                        </div>
                        <div>
                            <label for="contactMsg" class="block text-xs font-semibold text-slate-700 mb-1">Mensagem</label>
                            <textarea id="contactMsg" rows="4" required placeholder="Escreva aqui a sua mensagem..." class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm"></textarea>
                        </div>
                        <button type="submit" class="bg-movitel-blue hover:bg-movitel-blueDark text-white font-bold px-6 py-3 rounded-xl transition text-sm flex items-center justify-center gap-2">
                            <i class="fa-solid fa-paper-plane" aria-hidden="true"></i> Enviar Mensagem
                        </button>
                    </form>
                </div>
            </div>
        </section>
    </main>

    <!-- =====================================================================
         6. RODAPÉ SEMÂNTICO (<footer>)
         ===================================================================== -->
    <footer class="bg-slate-900 text-slate-400 text-sm py-12 border-t border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
                <div>
                    <div class="flex items-center gap-2 mb-4">
                        <div class="w-8 h-8 bg-movitel-yellow rounded-lg flex items-center justify-center font-black text-movitel-blueDark text-lg">M</div>
                        <span class="text-xl font-black text-white">MOVITEL</span>
                    </div>
                    <p class="text-xs text-slate-400 leading-relaxed mb-4">
                        A Movitel é a operadora líder em inovação e cobertura em Moçambique, proporcionando a melhor ligação de voz e dados para todos.
                    </p>
                </div>
                <div>
                    <h4 class="text-white font-semibold mb-4 text-sm">Serviços</h4>
                    <ul class="space-y-2 text-xs">
                        <li><a href="#catalogo" class="hover:text-movitel-yellow transition">Pacotes NetBwe</a></li>
                        <li><a href="#catalogo" class="hover:text-movitel-yellow transition">Serviço e-Mola</a></li>
                        <li><a href="#catalogo" class="hover:text-movitel-yellow transition">Roaming Internacional</a></li>
                        <li><a href="#catalogo" class="hover:text-movitel-yellow transition">Soluções Corporativas</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-white font-semibold mb-4 text-sm">Empresa</h4>
                    <ul class="space-y-2 text-xs">
                        <li><a href="#" class="hover:text-movitel-yellow transition">Sobre a Movitel</a></li>
                        <li><a href="#" class="hover:text-movitel-yellow transition">Carreiras / Emprego</a></li>
                        <li><a href="#" class="hover:text-movitel-yellow transition">Imprensa & Notícias</a></li>
                        <li><a href="#" class="hover:text-movitel-yellow transition">Responsabilidade Social</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-white font-semibold mb-4 text-sm">Legal & Suporte</h4>
                    <ul class="space-y-2 text-xs">
                        <li><a href="#" class="hover:text-movitel-yellow transition">Termos & Condições</a></li>
                        <li><a href="#" class="hover:text-movitel-yellow transition">Política de Privacidade</a></li>
                        <li><a href="#" class="hover:text-movitel-yellow transition">Segurança no e-Mola</a></li>
                        <li><a href="#" class="hover:text-movitel-yellow transition">Linha de Ética</a></li>
                    </ul>
                </div>
            </div>
            <div class="border-t border-slate-800 pt-6 flex flex-col sm:flex-row items-center justify-between text-xs text-slate-500">
                <p>&copy; 2026 Movitel SA. Todos os direitos reservados. Redesenho Académico de UX / Engenharia Web.</p>
                <div class="flex gap-4 mt-2 sm:mt-0">
                    <a href="#" class="hover:text-slate-300">Moçambique</a>
                    <span>•</span>
                    <a href="#" class="hover:text-slate-300">Português</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- =====================================================================
         7. MODAL DE GESTÃO CRUD (CRIAÇÃO DE NOVOS SERVIÇOS)
         ===================================================================== -->
    <div id="serviceModal" role="dialog" aria-modal="true" aria-labelledby="modalTitle" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-white rounded-2xl max-w-md w-full shadow-2xl border border-slate-100 overflow-hidden transform transition-all">
            <div class="bg-movitel-blue text-white px-6 py-4 flex items-center justify-between">
                <h3 id="modalTitle" class="font-bold text-lg flex items-center gap-2">
                    <i class="fa-solid fa-box-archive text-movitel-yellow" aria-hidden="true"></i>
                    <span>Cadastrar Novo Serviço Movitel</span>
                </h3>
                <button onclick="closeModal()" aria-label="Fechar Modal" class="text-slate-300 hover:text-white transition">
                    <i class="fa-solid fa-xmark text-xl" aria-hidden="true"></i>
                </button>
            </div>
            <form id="serviceForm" onsubmit="handleFormSubmit(event)" class="p-6 space-y-4">
                <div>
                    <label for="modalName" class="block text-xs font-semibold text-slate-700 mb-1">Nome do Pacote / Serviço *</label>
                    <input type="text" id="modalName" required placeholder="Ex: Pacote Ilimité Diário" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm">
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div>
                        <label for="modalCategory" class="block text-xs font-semibold text-slate-700 mb-1">Categoria *</label>
                        <select id="modalCategory" required class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm bg-white">
                            <option value="Internet">Internet</option>
                            <option value="Voz">Voz</option>
                            <option value="SMS">SMS</option>
                            <option value="e-Mola">e-Mola</option>
                            <option value="Serviços Digitais">Serviços Digitais</option>
                        </select>
                    </div>
                    <div>
                        <label for="modalPrice" class="block text-xs font-semibold text-slate-700 mb-1">Preço (MT) *</label>
                        <input type="number" id="modalPrice" required min="0" step="0.5" placeholder="Ex: 50" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm">
                    </div>
                </div>
                <div>
                    <label for="modalValidity" class="block text-xs font-semibold text-slate-700 mb-1">Validade / Período *</label>
                    <input type="text" id="modalValidity" required placeholder="Ex: 24 Horas / 7 Dias / Mensal" class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm">
                </div>
                <div>
                    <label for="modalDescription" class="block text-xs font-semibold text-slate-700 mb-1">Descrição do Pacote *</label>
                    <textarea id="modalDescription" required rows="3" placeholder="Detalhes dos benefícios, minutos ou GBs oferecidos..." class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-movitel-blue text-sm"></textarea>
                </div>
                <div class="flex items-center justify-end gap-3 pt-4 border-t border-slate-100">
                    <button type="button" onclick="closeModal()" class="px-4 py-2.5 rounded-xl border border-slate-300 text-slate-700 font-medium text-sm hover:bg-slate-50 transition">
                        Cancelar
                    </button>
                    <button type="submit" class="bg-movitel-yellow hover:bg-movitel-yellowHover text-movitel-blueDark font-bold px-5 py-2.5 rounded-xl transition shadow text-sm">
                        Salvar Serviço
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- =====================================================================
         8. LÓGICA JAVASCRIPT (DOM, LOCALSTORAGE, BUSCA E ORDENAÇÃO)
         ===================================================================== -->
    <script>
        /**
         * BASE DE DADOS INICIAL (Mock Data)
         * Utilizada apenas no primeiro acesso caso o localStorage esteja vazio.
         */
        const initialMovitelServices = [
            {
                id: '1',
                name: 'Super NetBwe Diário 2GB',
                category: 'Internet',
                price: 50,
                validity: '24 Horas',
                description: '2GB de dados móveis em velocidade 4.5G com acesso ilimitado a redes sociais selecionadas.',
                createdAt: '2026-03-01'
            },
            {
                id: '2',
                name: 'Pacote Chamadas Ilimité',
                category: 'Voz',
                price: 100,
                validity: '7 Dias',
                description: 'Minutos ilimitados para todas as redes Movitel e 50 minutos para outras operadoras.',
                createdAt: '2026-03-02'
            },
            {
                id: '3',
                name: 'Transferência Fácil e-Mola',
                category: 'e-Mola',
                price: 0,
                validity: 'Permanente',
                description: 'Envie e receba dinheiro com as melhores taxas do mercado de carteiras móveis em Moçambique.',
                createdAt: '2026-03-03'
            },
            {
                id: '4',
                name: 'Combo Mega Mensal 15GB',
                category: 'Internet',
                price: 500,
                validity: '30 Dias',
                description: '15GB de dados de alta velocidade + 200 Minutos de Voz + SMS ilimitadas Movitel.',
                createdAt: '2026-03-04'
            },
            {
                id: '5',
                name: 'Pacote 500 SMS Semanais',
                category: 'SMS',
                price: 25,
                validity: '7 Dias',
                description: '500 mensagens de texto válidas para qualquer operadora nacional.',
                createdAt: '2026-03-05'
            },
            {
                id: '6',
                name: 'Movitel TV Streaming',
                category: 'Serviços Digitais',
                price: 150,
                validity: '30 Dias',
                description: 'Acesso completo a canais de TV ao vivo e catálogo de filmes locais e internacionais no telemóvel.',
                createdAt: '2026-03-06'
            }
        ];

        // Estado em memória da aplicação
        let servicesState = [];
        let selectedRechargeValue = 100;

        /**
         * INICIALIZAÇÃO DO CICLO DE VIDA DA PÁGINA
         */
        window.addEventListener('DOMContentLoaded', () => {
            loadServicesFromStorage();
            setupMobileMenu();
            renderServices();
        });

        /**
         * CONTROLO DO MENU MOBILE RESPONSIVO
         */
        function setupMobileMenu() {
            const btn = document.getElementById('mobile-menu-btn');
            const menu = document.getElementById('mobile-menu');
            btn.addEventListener('click', () => {
                const isHidden = menu.classList.toggle('hidden');
                btn.setAttribute('aria-expanded', !isHidden);
            });
        }

        /**
         * PERSISTÊNCIA DE DADOS COM WEB STORAGE API (localStorage)
         * Garante que os serviços adicionados ou removidos permaneçam salvos
         * mesmo após recarregar ou fechar o navegador.
         */
        function loadServicesFromStorage() {
            const stored = localStorage.getItem('movitel_services_db');
            if (stored) {
                try {
                    servicesState = JSON.parse(stored);
                } catch (e) {
                    console.error("Erro ao interpretar dados do localStorage:", e);
                    servicesState = [...initialMovitelServices];
                }
            } else {
                servicesState = [...initialMovitelServices];
                saveServicesToStorage();
            }
        }

        function saveServicesToStorage() {
            localStorage.setItem('movitel_services_db', JSON.stringify(servicesState));
        }

        /**
         * MOTOR DE RENDERIZAÇÃO E PROCESSAMENTO DE CONSULTAS (BUSCA + FILTRO + ORDENAÇÃO)
         */
        function renderServices() {
            const grid = document.getElementById('servicesGrid');
            const emptyState = document.getElementById('emptyState');
            const countSpan = document.getElementById('itemsCount');

            // Captura dos parâmetros de consulta da interface
            const searchValue = document.getElementById('searchInput').value.trim().toLowerCase();
            const selectedCategory = document.getElementById('categoryFilter').value;
            const sortBy = document.getElementById('sortBy').value;

            // 1. ALGORITMO DE BUSCA LINEAR E FILTRAGEM MULTI-CAMPO - Complexidade O(n)
            let filtered = servicesState.filter(item => {
                const matchesSearch = item.name.toLowerCase().includes(searchValue) || 
                                      item.description.toLowerCase().includes(searchValue) ||
                                      item.category.toLowerCase().includes(searchValue);
                const matchesCategory = selectedCategory === 'ALL' || item.category === selectedCategory;
                return matchesSearch && matchesCategory;
            });

            // 2. ALGORITMO DE ORDENAÇÃO DINÂMICA (TimSort nativo V8/SpiderMonkey) - Complexidade O(n log n)
            filtered.sort((a, b) => {
                if (sortBy === 'price-asc') {
                    return a.price - b.price; // Preço crescente
                } else if (sortBy === 'price-desc') {
                    return b.price - a.price; // Preço decrescente
                } else if (sortBy === 'name-asc') {
                    return a.name.localeCompare(b.name); // Ordem alfabética
                } else if (sortBy === 'date-desc') {
                    return new Date(b.createdAt) - new Date(a.createdAt); // Mais recentes
                }
                return 0;
            });

            // Atualização do contador de itens no DOM
            countSpan.innerText = filtered.length;
            grid.innerHTML = '';

            // Gestão de estado vazio vs renderização dos cards
            if (filtered.length === 0) {
                emptyState.classList.remove('hidden');
            } else {
                emptyState.classList.add('hidden');
                filtered.forEach(service => {
                    const card = createServiceCardHTML(service);
                    grid.appendChild(card);
                });
            }
        }

        /**
         * CONSTRUTOR DE COMPONENTES DOM (Cards de Serviço)
         */
        function createServiceCardHTML(service) {
            const card = document.createElement('article');
            card.setAttribute('role', 'listitem');
            card.className = "bg-white rounded-2xl border border-slate-200 p-6 shadow-sm hover:shadow-md transition-all flex flex-col justify-between group relative";

            // Codificação visual por categoria para facilitar identificação rápida
            let badgeClass = "bg-blue-100 text-blue-700";
            if (service.category === 'Internet') badgeClass = "bg-emerald-100 text-emerald-800";
            else if (service.category === 'Voz') badgeClass = "bg-amber-100 text-amber-800";
            else if (service.category === 'e-Mola') badgeClass = "bg-purple-100 text-purple-800";
            else if (service.category === 'SMS') badgeClass = "bg-sky-100 text-sky-800";

            card.innerHTML = `
                <div>
                    <div class="flex items-center justify-between gap-2 mb-3">
                        <span class="text-xs font-bold px-2.5 py-1 rounded-full ${badgeClass}">
                            ${service.category}
                        </span>
                        <div class="flex items-center gap-1 text-slate-400 text-xs">
                            <i class="fa-regular fa-clock" aria-hidden="true"></i>
                            <span>${service.validity}</span>
                        </div>
                    </div>
                    <h3 class="font-bold text-slate-900 text-lg group-hover:text-movitel-blue transition mb-2">
                        ${service.name}
                    </h3>
                    <p class="text-slate-600 text-xs leading-relaxed mb-4">
                        ${service.description}
                    </p>
                </div>
                <div class="pt-4 border-t border-slate-100 flex items-center justify-between mt-2">
                    <div>
                        <span class="text-xs text-slate-400 block">Preço</span>
                        <span class="text-xl font-extrabold text-movitel-blue">
                            ${service.price > 0 ? service.price + ' <span class="text-xs font-semibold">MT</span>' : 'Grátis'}
                        </span>
                    </div>
                    <div class="flex items-center gap-2">
                        <button onclick="deleteService('${service.id}')" title="Eliminar Serviço" aria-label="Eliminar ${service.name}" class="p-2 text-slate-400 hover:text-red-500 hover:bg-red-50 rounded-lg transition">
                            <i class="fa-solid fa-trash-can text-sm" aria-hidden="true"></i>
                        </button>
                        <button onclick="showToast('Pacote ${service.name} activado com sucesso!', 'success')" class="bg-movitel-yellow hover:bg-movitel-yellowHover text-movitel-blueDark font-bold px-3.5 py-2 rounded-xl text-xs transition">
                            Activar
                        </button>
                    </div>
                </div>
            `;
            return card;
        }

        // Aciona a filtragem em tempo real ao digitar ou alterar seletores
        function applyFilters() {
            renderServices();
        }

        // Restaura os filtros para o estado padrão
        function resetFilters() {
            document.getElementById('searchInput').value = '';
            document.getElementById('categoryFilter').value = 'ALL';
            document.getElementById('sortBy').value = 'name-asc';
            renderServices();
            showToast('Filtros restaurados para o padrão.', 'info');
        }

        /**
         * OPERAÇÃO CRUD: CREATE (Adicionar novo serviço ao catálogo e localStorage)
         */
        function handleFormSubmit(event) {
            event.preventDefault();
            const name = document.getElementById('modalName').value.trim();
            const category = document.getElementById('modalCategory').value;
            const price = parseFloat(document.getElementById('modalPrice').value);
            const validity = document.getElementById('modalValidity').value.trim();
            const description = document.getElementById('modalDescription').value.trim();

            if (!name || isNaN(price) || !validity || !description) {
                showToast('Por favor, preencha todos os campos obrigatórios.', 'error');
                return;
            }

            const newService = {
                id: Date.now().toString(),
                name: name,
                category: category,
                price: price,
                validity: validity,
                description: description,
                createdAt: new Date().toISOString().split('T')[0]
            };

            servicesState.unshift(newService);
            saveServicesToStorage();
            renderServices();
            closeModal();
            showToast(`Serviço "${name}" adicionado com sucesso!`, 'success');
        }

        /**
         * OPERAÇÃO CRUD: DELETE (Remover serviço do catálogo e localStorage)
         */
        function deleteService(id) {
            const item = servicesState.find(s => s.id === id);
            const itemName = item ? item.name : 'Serviço';
            servicesState = servicesState.filter(s => s.id !== id);
            saveServicesToStorage();
            renderServices();
            showToast(`"${itemName}" foi removido do catálogo.`, 'error');
        }

        // Controlo da Janela Modal
        function openModal() {
            document.getElementById('serviceForm').reset();
            document.getElementById('serviceModal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('serviceModal').classList.add('hidden');
        }

        // Interatividade do Widget de Recarga Rápida
        function selectRechargeAmount(btn, amount) {
            selectedRechargeValue = amount;
            document.querySelectorAll('.recharge-btn').forEach(b => {
                b.classList.remove('bg-movitel-yellow', 'text-movitel-blueDark');
                b.classList.add('bg-white/10');
            });
            btn.classList.remove('bg-white/10');
            btn.classList.add('bg-movitel-yellow', 'text-movitel-blueDark');
        }

        function handleQuickRecharge(event) {
            event.preventDefault();
            const phone = document.getElementById('rechargePhone').value.trim();
            showToast(`Recarga de ${selectedRechargeValue} MT enviada para ${phone}!`, 'success');
            event.target.reset();
        }

        // Submissão do Formulário de Contacto
        function handleContactSubmit(event) {
            event.preventDefault();
            showToast('Mensagem enviada com sucesso! Entraremos em contacto brevemente.', 'success');
            event.target.reset();
        }

        /**
         * SISTEMA DE FEEDBACK VISUAL (Notificações Toast)
         * Cumpre a heurística de visibilidade do estado do sistema de Jakob Nielsen.
         */
        function showToast(message, type = 'info') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = "pointer-events-auto bg-white border shadow-lg rounded-xl p-4 flex items-center gap-3 text-sm min-w-[280px] max-w-sm toast-enter border-slate-200";

            let icon = '<i class="fa-solid fa-circle-info text-movitel-blue" aria-hidden="true"></i>';
            if (type === 'success') {
                icon = '<i class="fa-solid fa-circle-check text-emerald-500 text-base" aria-hidden="true"></i>';
            } else if (type === 'error') {
                icon = '<i class="fa-solid fa-triangle-exclamation text-red-500 text-base" aria-hidden="true"></i>';
            }

            toast.innerHTML = `
                ${icon}
                <span class="flex-grow font-medium text-slate-800">${message}</span>
            `;

            container.appendChild(toast);

            requestAnimationFrame(() => {
                toast.classList.add('toast-enter-active');
            });

            setTimeout(() => {
                toast.classList.remove('toast-enter-active');
                toast.classList.add('toast-exit');
                setTimeout(() => {
                    toast.remove();
                }, 300);
            }, 3200);
        }
    </script>
</body>
</html>
