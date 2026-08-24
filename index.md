---
layout: default
---

<section class="hero">
    <div class="container hero-container">
        <div class="hero-content">
            <h1 class="hero-title">Unleash <span class="text-gradient">Quant Power</span></h1>
            <p class="hero-subtitle">{{ site.description }}</p>
            <div class="hero-actions">
                <a href="https://github.com/helmsmantrading/HelmsmanTrading" class="btn btn-primary">Get Started</a>
                <a href="#architecture" class="btn btn-outline">Explore Architecture</a>
            </div>
        </div>
        <div class="hero-graphic">
            <!-- Decorative elements for the dark premium feel -->
            <div class="glow-orb"></div>
            <img src="/assets/images/logo/logo-dark.png" alt="Helmsman Trading Shield" class="hero-image floating">
        </div>
    </div>
</section>

<section id="features" class="section">
    <div class="container">
        <h2 class="section-title">Core Features</h2>
        <p class="section-subtitle">A professional-grade setup built to prevent catastrophic drawdowns and execute reliably.</p>
        
        <div class="features-grid">
            <div class="feature-card glass-panel">
                <div class="feature-icon">📊</div>
                <h3>L1 Data Lake</h3>
                <p>Consolidated 1-minute SIP data from Polygon and structured IEX integration for reliable VWAP and 40+ modular indicators.</p>
            </div>
            
            <div class="feature-card glass-panel">
                <div class="feature-icon">🧠</div>
                <h3>L2 Plugin Skills</h3>
                <p>Easily expand strategies. Drop a new Python file in the skills directory, decorate with <code>@register</code>, and the system auto-discovers it.</p>
            </div>
            
            <div class="feature-card glass-panel">
                <div class="feature-icon">🛡️</div>
                <h3>L4 Risk Engine</h3>
                <p>Iron-clad risk management. Enforces maximum heat limits, position sizing, and dynamic stop-losses to protect your equity from erratic signals.</p>
            </div>
            
            <div class="feature-card glass-panel">
                <div class="feature-icon">🌉</div>
                <h3>L5 Broker Bridge</h3>
                <p>Trade with confidence across Alpaca (Live/Paper), Tradier, or fully offline with PaperSim. Pydantic-typed DTOs ensure API conformance.</p>
            </div>
        </div>
    </div>
</section>

<section id="architecture" class="section section-darker">
    <div class="container">
        <h2 class="section-title">The Stack</h2>
        <div class="architecture-content">
            <div class="glass-panel code-panel">
                <div class="code-header">
                    <span class="dot red"></span>
                    <span class="dot yellow"></span>
                    <span class="dot green"></span>
                    <span class="file-name">src/server.py</span>
                </div>
                <pre><code><span class="keyword">@mcp.tool</span>()
<span class="keyword">def</span> <span class="function">confirm_trade</span>(preview_id: <span class="type">str</span>) -> <span class="type">dict</span>:
    <span class="comment">"""[TOOL L5] FASE 2: Esegue un trade preventivato."""</span>
    <span class="keyword">if</span> is_kill_switch_active():
        <span class="keyword">return</span> {<span class="string">"error"</span>: <span class="string">"KILL-SWITCH ATTIVO."</span>}
        
    <span class="comment"># Re-validate with L4 Risk Engine before execution</span>
    new_order = risk_engine.evaluate_intent(intent, market_data)
    
    <span class="comment"># Prevent slippage</span>
    <span class="keyword">if</span> new_order.size != old_order.size:
        <span class="keyword">return</span> {<span class="string">"error"</span>: <span class="string">"Slippage bloccato."</span>}
        
    <span class="keyword">return</span> broker_adapter.submit_order(new_order)</code></pre>
            </div>
            <div class="architecture-text">
                <h3>Built for Control</h3>
                <p>Helmsman doesn't just throw market orders at an API. It uses a <strong>two-phase commit</strong> pattern for AI trading:</p>
                <ul>
                    <li><strong>Preview:</strong> The AI proposes an intent. L4 calculates precise size and risk.</li>
                    <li><strong>Human Gate:</strong> You approve the exact parameters.</li>
                    <li><strong>Confirm:</strong> L5 executes the order, re-verifying market conditions instantly.</li>
                </ul>
            </div>
        </div>
    </div>
</section>

<section id="faq" class="section">
    <div class="container">
        <h2 class="section-title">Frequently Asked Questions</h2>
        <div class="faq-list">
            {% for item in site.faq_en %}
            <details class="faq-item glass-panel">
                <summary>{{ item.question }}</summary>
                <div class="faq-answer">
                    <p>{{ item.answer }}</p>
                </div>
            </details>
            {% endfor %}
        </div>
    </div>
</section>
