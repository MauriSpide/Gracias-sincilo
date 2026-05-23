<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gracias por escuchar — MauriSpide</title>
    <meta name="description" content="Gracias por escuchar 'Yo Soy MauriSpide', el primer sencillo de MauriSpide. Tu apoyo significa todo.">

    <!-- Open Graph -->
    <meta property="og:title" content="Gracias por escuchar — MauriSpide">
    <meta property="og:description" content="Gracias por apoyar este sueño desde el inicio. Cada reproducción significa muchísimo.">
    <meta property="og:type" content="music.song">

    <!-- Twitter Card -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="Gracias por escuchar — MauriSpide">
    <meta name="twitter:description" content="Gracias por apoyar este sueño desde el inicio.">

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300&family=DM Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&display=swap" rel="stylesheet">

    <style>
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        :root {
            --bg:           #070604;
            --card-bg:      rgba(14, 11, 8, 0.45);
            --card-border:  rgba(200, 168, 78, 0.16);
            --gold:         #c8a84e;
            --gold-bright:  #f3d882;
            --gold-dim:     #a48537;
            --text:         #f5ebd6;
            --text-dim:     #bfae96;
            --text-muted:   #7d6c56;
            --glow-color:   rgba(200, 168, 78, 0.12);
        }

        html, body { height: 100%; }

        body {
            background-color: var(--bg);
            background-image: radial-gradient(circle at 50% 50%, rgba(18, 14, 11, 0.8) 0%, var(--bg) 100%);
            font-family: 'DM Sans', sans-serif;
            color: var(--text);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow-x: hidden;
            position: relative;
        }

        /* ─── Ambient spotlight tracking mouse ─── */
        .mouse-glow {
            position: fixed;
            width: 600px;
            height: 600px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(200, 168, 78, 0.035) 0%, transparent 70%);
            pointer-events: none;
            z-index: 1;
            transform: translate(-50%, -50%);
            opacity: 0;
            transition: opacity 0.8s ease;
            mix-blend-mode: screen;
        }

        /* ─── Background orbs ─── */
        .bg {
            position: fixed;
            inset: 0;
            z-index: 0;
            overflow: hidden;
        }
        .bg::before {
            content: '';
            position: absolute;
            width: 800px; height: 800px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(200,168,78,0.06) 0%, transparent 70%);
            top: -250px; left: -200px;
            animation: orb1 24s ease-in-out infinite;
        }
        .bg::after {
            content: '';
            position: absolute;
            width: 650px; height: 650px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(160,110,40,0.04) 0%, transparent 70%);
            bottom: -150px; right: -150px;
            animation: orb2 30s ease-in-out infinite;
        }
        @keyframes orb1 {
            0%,100% { transform: translate(0,0) scale(1); }
            40%     { transform: translate(120px,60px) scale(1.15); }
            70%     { transform: translate(-30px,100px) scale(0.92); }
        }
        @keyframes orb2 {
            0%,100% { transform: translate(0,0) scale(1); }
            55%     { transform: translate(-90px,-70px) scale(1.22); }
        }

        /* ─── Grain texture overlay ─── */
        .grain {
            position: fixed;
            inset: 0;
            z-index: 2;
            pointer-events: none;
            opacity: 0.025;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
            background-size: 200px;
        }

        /* ─── Floating music embers ─── */
        .notes {
            position: fixed;
            inset: 0;
            z-index: 2;
            pointer-events: none;
            overflow: hidden;
        }
        .note {
            position: absolute;
            color: var(--gold);
            opacity: 0;
            filter: blur(0.4px);
            animation: floatUp var(--dur, 10s) ease-in-out infinite var(--del, 0s);
        }
        @keyframes floatUp {
            0%    { transform: translateY(105vh) rotate(0deg) scale(0.8);   opacity: 0; }
            12%   { opacity: 0.35; }
            80%   { opacity: 0.15; }
            100%  { transform: translateY(-8vh) rotate(220deg) scale(1.2);  opacity: 0; }
        }

        /* ─── Layout Container ─── */
        .container {
            position: relative;
            z-index: 10;
            width: 90%;
            max-width: 660px;
            padding: 30px 0 50px;
        }

        /* ─── 3D Vinyl Player Centerpiece ─── */
        .player-container {
            display: flex;
            justify-content: center;
            margin-bottom: 34px;
            opacity: 0;
            animation: riseIn 0.85s cubic-bezier(.16,1,.3,1) forwards 0.15s;
        }
        .player-wrapper {
            position: relative;
            width: 290px;
            height: 180px;
            display: flex;
            align-items: center;
        }
        
        /* Album sleeve */
        .album-jacket {
            width: 150px;
            height: 150px;
            background: linear-gradient(135deg, #120f0c 0%, #1c1813 100%);
            border: 1px solid rgba(200, 168, 78, 0.28);
            border-radius: 6px;
            position: absolute;
            left: 15px;
            z-index: 5;
            transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.6s ease;
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .jacket-inner {
            position: relative;
            width: 100%;
            height: 100%;
            padding: 14px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            text-align: center;
            z-index: 2;
        }
        .jacket-svg {
            position: absolute;
            inset: 0;
            width: 100%;
            height: 100%;
            opacity: 0.85;
            pointer-events: none;
            z-index: 1;
        }
        .jacket-title {
            font-family: 'Cormorant Garamond', Georgia, serif;
            font-size: 15px;
            font-weight: 400;
            color: var(--text-dim);
            letter-spacing: 0.12em;
            text-transform: uppercase;
            margin-top: 8px;
        }
        .jacket-artist {
            font-family: 'Cormorant Garamond', Georgia, serif;
            font-size: 20px;
            font-weight: 700;
            color: var(--gold-bright);
            letter-spacing: 0.05em;
            text-shadow: 0 0 10px rgba(200, 168, 78, 0.2);
        }
        .jacket-catalog {
            font-size: 8px;
            color: var(--text-muted);
            letter-spacing: 0.15em;
            margin-bottom: 4px;
        }
        
        /* Spinning vinyl */
        .vinyl-record-wrap {
            width: 140px;
            height: 140px;
            position: absolute;
            left: 70px;
            z-index: 4;
            transform: translateX(0);
            transition: transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .vinyl {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: 
                radial-gradient(circle at 50% 50%, transparent 35%, #0b0907 35%),
                repeating-conic-gradient(#120f0d 0deg, #221c17 4deg, #120f0d 8deg);
            border: 1px solid rgba(200,168,78,0.18);
            box-shadow: 
                0 0 0 1px rgba(200,168,78,0.05),
                0 8px 25px rgba(0,0,0,0.55);
            position: relative;
            animation: spin 12s linear infinite;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .vinyl-label {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            background: radial-gradient(circle, #dbbf74 0%, #a68433 100%);
            border: 2px solid #0b0907;
            box-shadow: inset 0 0 8px rgba(0,0,0,0.4);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }
        .vinyl-label::after {
            content: '';
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: var(--bg);
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.8);
        }
        .label-grooves {
            position: absolute;
            inset: 3px;
            border-radius: 50%;
            border: 1px dashed rgba(0,0,0,0.12);
        }

        /* Tonearm/Stylus Needle */
        .tonearm {
            position: absolute;
            right: 40px;
            top: 5px;
            width: 60px;
            height: 90px;
            transform-origin: 15px 15px;
            transform: rotate(-38deg);
            transition: transform 0.9s cubic-bezier(0.16, 1, 0.3, 1);
            z-index: 6;
            pointer-events: none;
        }
        .tonearm-base {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: radial-gradient(circle, #221c17 0%, #0d0a08 100%);
            border: 1.5px solid rgba(200,168,78,0.4);
            box-shadow: 0 4px 10px rgba(0,0,0,0.5);
            position: relative;
        }
        .tonearm-base::after {
            content: '';
            position: absolute;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: var(--gold);
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            border: 1px solid #120f0d;
        }
        .tonearm-arm {
            position: absolute;
            top: 15px;
            left: 13px;
            width: 4px;
            height: 60px;
            background: linear-gradient(90deg, #d5b866 0%, #aa8537 100%);
            transform: rotate(18deg);
            transform-origin: top center;
            border-radius: 2px;
            box-shadow: 1px 1px 3px rgba(0,0,0,0.3);
        }
        .tonearm-arm::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: -2px;
            width: 8px;
            height: 12px;
            background: #221c17;
            border: 1px solid var(--gold);
            border-radius: 1px;
            transform: rotate(-18deg);
        }

        /* Interactive player states */
        .player-wrapper.active .vinyl-record-wrap {
            transform: translateX(65px);
        }
        .player-wrapper.active .tonearm {
            transform: rotate(5deg);
        }
        
        .player-wrapper:hover .vinyl-record-wrap {
            transform: translateX(85px) scale(1.03);
        }
        .player-wrapper:hover .tonearm {
            transform: rotate(8deg);
        }
        .player-wrapper:hover .album-jacket {
            transform: translateY(-5px) rotate(-1.5deg);
            box-shadow: 0 15px 35px rgba(0,0,0,0.65);
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* ─── Glassmorphic Card ─── */
        .card {
            position: relative;
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: 28px;
            padding: 58px 50px 48px;
            text-align: center;
            backdrop-filter: blur(28px);
            -webkit-backdrop-filter: blur(28px);
            box-shadow:
                0 0 0 1px rgba(255,255,255,0.015),
                0 30px 100px rgba(0,0,0,0.7),
                inset 0 1px 0 rgba(200,168,78,0.12);
            opacity: 0;
            transform: translateY(28px);
            animation: riseInCard 1.1s cubic-bezier(.16,1,.3,1) forwards 0.35s;
            transition: transform 0.5s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.5s, border-color 0.5s;
            z-index: 10;
        }
        
        /* Subtle interactive lighting spot inside the card */
        .card::before {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: inherit;
            background: radial-gradient(350px circle at var(--mouse-x, 50%) var(--mouse-y, 50%), rgba(200,168,78,0.055), transparent 85%);
            pointer-events: none;
            z-index: -1;
            transition: background 0.15s ease;
        }

        @keyframes riseInCard {
            from { opacity: 0; transform: translateY(40px) scale(0.98); }
            to   { opacity: 1; transform: translateY(0) scale(1); }
        }

        @keyframes riseIn {
            from { opacity: 0; transform: translateY(24px); }
            to   { opacity: 1; transform: translateY(0); }
        }

        /* ─── Gold Rule ─── */
        .rule {
            width: 50px; height: 1.5px;
            background: linear-gradient(90deg, transparent, var(--gold-bright), transparent);
            margin: 0 auto 30px;
            opacity: 0;
            animation: expandRule 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards 0.6s;
        }
        @keyframes expandRule {
            from { opacity: 0; transform: scaleX(0.1); }
            to   { opacity: 1; transform: scaleX(1); }
        }

        /* ─── Typography ─── */
        .headline {
            font-family: 'Cormorant Garamond', Georgia, serif;
            font-size: clamp(32px, 6vw, 54px);
            font-weight: 600;
            line-height: 1.15;
            letter-spacing: -0.01em;
            background: linear-gradient(135deg, var(--text) 30%, var(--gold-bright) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 12px;
            opacity: 0;
            animation: riseIn 0.9s cubic-bezier(0.16, 1, 0.3, 1) forwards 0.72s;
        }

        .song-name {
            font-family: 'DM Sans', sans-serif;
            font-size: clamp(12px, 1.8vw, 14px);
            font-weight: 500;
            color: var(--gold);
            letter-spacing: 0.28em;
            text-transform: uppercase;
            margin-bottom: 34px;
            opacity: 0;
            animation: riseIn 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards 0.88s;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-wrap: wrap;
            gap: 8px;
        }

        /* Beautiful interactive live dot badge */
        .live-dot-container {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            font-size: 10px;
            font-weight: 600;
            letter-spacing: 0.1em;
            color: var(--text-muted);
            border: 1px solid rgba(200, 168, 78, 0.15);
            padding: 3px 8px;
            border-radius: 100px;
            background: rgba(200, 168, 78, 0.03);
            vertical-align: middle;
            margin-left: 8px;
        }
        .live-dot {
            width: 6px; height: 6px;
            background-color: var(--gold);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--gold);
            animation: pulseGlow 1.8s infinite;
        }
        @keyframes pulseGlow {
            0%, 100% { opacity: 0.4; transform: scale(0.9); }
            50% { opacity: 1; transform: scale(1.15); box-shadow: 0 0 12px var(--gold-bright); }
        }

        .body {
            font-size: clamp(14px, 2.2vw, 16px);
            line-height: 1.8;
            color: var(--text-dim);
            font-weight: 300;
            max-width: 460px;
            margin: 0 auto 38px;
            opacity: 0;
            animation: riseIn 0.8s ease forwards 1.02s;
        }

        /* ─── Premium Play Button ─── */
        .btn-play {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 16px 38px;
            background: linear-gradient(135deg, var(--gold) 0%, var(--gold-bright) 100%);
            color: #0b0905;
            font-family: 'DM Sans', sans-serif;
            font-size: 14px;
            font-weight: 600;
            letter-spacing: 0.05em;
            text-transform: uppercase;
            border: none;
            border-radius: 100px;
            cursor: pointer;
            text-decoration: none;
            transition: transform 0.3s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.3s, background 0.3s;
            box-shadow: 0 4px 22px rgba(200,168,78,0.25);
            opacity: 0;
            animation: riseIn 0.8s ease forwards 1.12s;
            position: relative;
            overflow: hidden;
        }
        .btn-play::after {
            content: '';
            position: absolute;
            top: -50%; left: -60%;
            width: 30%; height: 200%;
            background: linear-gradient(
                to right,
                rgba(255, 255, 255, 0) 0%,
                rgba(255, 255, 255, 0.32) 50%,
                rgba(255, 255, 255, 0) 100%
            );
            transform: rotate(25deg);
            transition: none;
            opacity: 0;
        }
        .btn-play:hover::after {
            left: 130%;
            opacity: 1;
            transition: all 0.75s ease;
        }
        .btn-play:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 10px 35px rgba(200,168,78,0.38);
        }
        .btn-play:active {
            transform: translateY(-1px);
            box-shadow: 0 3px 14px rgba(200,168,78,0.25);
        }
        .btn-play svg {
            width: 15px; height: 15px;
            fill: currentColor;
            flex-shrink: 0;
            transition: transform 0.3s ease;
        }
        .btn-play:hover svg {
            transform: scale(1.15) rotate(10deg);
        }

        /* ─── Song Actions ─── */
        .song-actions {
            display: grid;
            grid-template-columns: repeat(2, minmax(0, 1fr));
            gap: 12px;
            margin: 28px auto 0;
            opacity: 0;
            animation: riseIn 0.8s ease forwards 1.18s;
        }
        .action-btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            min-height: 46px;
            padding: 12px 16px;
            background: rgba(255, 244, 215, 0.02);
            border: 1px solid rgba(200, 168, 78, 0.14);
            border-radius: 16px;
            color: var(--text-dim);
            font-family: 'DM Sans', sans-serif;
            font-size: 13px;
            font-weight: 500;
            letter-spacing: 0.04em;
            line-height: 1.2;
            text-decoration: none;
            cursor: pointer;
            transition: background 0.25s, border-color 0.25s, color 0.25s, transform 0.25s, box-shadow 0.25s;
        }
        .action-btn:hover,
        .action-btn:focus-visible {
            background: rgba(200, 168, 78, 0.08);
            border-color: rgba(200, 168, 78, 0.38);
            color: var(--gold-bright);
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            outline: none;
        }
        .action-btn.active-btn {
            background: rgba(200, 168, 78, 0.14);
            border-color: rgba(200, 168, 78, 0.5);
            color: var(--gold-bright);
            transform: translateY(0);
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);
        }
        .action-btn svg {
            width: 15px; height: 15px;
            stroke: currentColor;
            fill: none;
            stroke-width: 1.8;
            stroke-linecap: round;
            stroke-linejoin: round;
            flex-shrink: 0;
            transition: transform 0.25s ease;
        }
        .action-btn:hover svg {
            transform: scale(1.1);
        }

        /* ─── Butter Smooth CSS Grid Accordions ─── */
        .panel-container {
            display: grid;
            grid-template-rows: 0fr;
            transition: grid-template-rows 0.45s cubic-bezier(0.16, 1, 0.3, 1);
            overflow: hidden;
        }
        .panel-container.expanded {
            grid-template-rows: 1fr;
        }
        
        .song-panel {
            min-height: 0;
            margin-top: 16px;
            border: 1px solid rgba(200,168,78,0.12);
            border-radius: 20px;
            background: rgba(255, 244, 215, 0.015);
            color: var(--text-dim);
            text-align: left;
            line-height: 1.8;
            transition: border-color 0.3s;
        }
        .panel-content {
            min-height: 0;
            opacity: 0;
            transform: translateY(-8px);
            transition: opacity 0.3s ease, transform 0.3s ease;
            padding: 24px;
        }
        .panel-container.expanded .panel-content {
            opacity: 1;
            transform: translateY(0);
            transition-delay: 0.1s;
        }
        .song-panel h2 {
            font-family: 'Cormorant Garamond', Georgia, serif;
            color: var(--text);
            font-size: 26px;
            font-weight: 600;
            margin-bottom: 16px;
            border-bottom: 1px solid rgba(200,168,78,0.1);
            padding-bottom: 8px;
        }
        
        /* Lyrics layout */
        .lyrics-container {
            display: flex;
            flex-direction: column;
            gap: 16px;
        }
        .lyrics-verse {
            font-family: 'Cormorant Garamond', Georgia, serif;
            font-size: 18px;
            font-style: italic;
            color: var(--text-dim);
            line-height: 1.6;
        }

        /* Credits grid */
        .credits-grid {
            list-style: none;
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px 20px;
        }
        .credits-grid li {
            font-size: 13.5px;
            border-bottom: 1px dashed rgba(200, 168, 78, 0.06);
            padding-bottom: 6px;
        }
        .credits-grid strong {
            color: var(--gold);
            font-weight: 500;
            margin-right: 4px;
        }

        /* ─── Share ─── */
        .share {
            margin-top: 36px;
            opacity: 0;
            animation: riseIn 0.7s ease forwards 1.24s;
        }
        .share-label {
            font-size: 11px;
            letter-spacing: 0.25em;
            text-transform: uppercase;
            color: var(--text-muted);
            margin-bottom: 16px;
            font-weight: 500;
        }
        .share-row {
            display: flex;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
        }
        .share-btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 10px 22px;
            background: rgba(255, 244, 215, 0.02);
            border: 1px solid rgba(200,168,78,0.12);
            border-radius: 100px;
            color: var(--text-dim);
            font-family: 'DM Sans', sans-serif;
            font-size: 13px;
            font-weight: 500;
            cursor: pointer;
            text-decoration: none;
            transition: background 0.2s, border-color 0.2s, color 0.2s, transform 0.2s, box-shadow 0.2s;
        }
        .share-btn:hover {
            background: rgba(200, 168, 78, 0.08);
            border-color: rgba(200, 168, 78, 0.35);
            color: var(--gold-bright);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
        }
        .share-btn svg {
            width: 14px; height: 13px;
            fill: currentColor;
            flex-shrink: 0;
        }

        /* ─── Divider ─── */
        .divider {
            width: 100%; height: 1px;
            background: linear-gradient(90deg, transparent, rgba(200,168,78,0.14), transparent);
            margin: 36px 0;
            opacity: 0;
            animation: riseIn 0.6s ease forwards 1.35s;
        }

        /* ─── Signature ─── */
        .signature {
            font-family: 'Cormorant Garamond', Georgia, serif;
            font-size: 16px;
            font-weight: 300;
            font-style: italic;
            color: var(--text-muted);
            letter-spacing: 0.08em;
            opacity: 0;
            animation: riseIn 0.6s ease forwards 1.44s;
            margin-bottom: 24px;
        }
        .signature strong {
            font-style: normal;
            font-weight: 600;
            color: var(--gold);
        }

        /* ─── Real-time Waveform ─── */
        .waveform {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 3.5px;
            height: 28px;
            opacity: 0;
            animation: riseIn 0.6s ease forwards 1.54s;
        }

        /* ─── Responsive Adjustments ─── */
        @media (max-width: 480px) {
            .card { padding: 42px 24px 38px; }
            .share-row { gap: 10px; }
            .song-actions { grid-template-columns: 1fr; gap: 10px; }
            
            .player-wrapper {
                width: 250px;
                height: 160px;
            }
            .album-jacket {
                width: 130px;
                height: 130px;
                left: 10px;
            }
            .vinyl-record-wrap {
                width: 120px;
                height: 120px;
                left: 60px;
            }
            .tonearm {
                right: 25px;
                top: 5px;
                width: 50px;
                height: 75px;
            }
            .player-wrapper.active .vinyl-record-wrap {
                transform: translateX(45px);
            }
            .player-wrapper:hover .vinyl-record-wrap {
                transform: translateX(60px) scale(1.02);
            }
            .credits-grid {
                grid-template-columns: 1fr;
                gap: 10px;
            }
        }
    </style>
</head>
<body>

<div class="mouse-glow" id="mouseGlow"></div>
<div class="bg"></div>
<div class="grain"></div>
<div class="notes" id="notes"></div>

<div class="container">

    <!-- Cinematic 3D Record Player Centerpiece -->
    <div class="player-container">
        <div class="player-wrapper">
            <div class="album-jacket">
                <div class="jacket-inner">
                    <svg class="jacket-svg" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
                        <circle cx="50" cy="50" r="45" fill="none" stroke="rgba(200,168,78,0.14)" stroke-width="0.8"/>
                        <circle cx="50" cy="50" r="30" fill="none" stroke="rgba(200,168,78,0.18)" stroke-width="0.8"/>
                        <circle cx="50" cy="50" r="15" fill="none" stroke="rgba(200,168,78,0.22)" stroke-width="0.8"/>
                        <line x1="50" y1="5" x2="50" y2="95" stroke="rgba(200,168,78,0.18)" stroke-width="0.8"/>
                        <line x1="5" y1="50" x2="95" y2="50" stroke="rgba(200,168,78,0.18)" stroke-width="0.8"/>
                        <line x1="18.2" y1="18.2" x2="81.8" y2="81.8" stroke="rgba(200,168,78,0.12)" stroke-width="0.8"/>
                        <line x1="18.2" y1="81.8" x2="81.8" y2="18.2" stroke="rgba(200,168,78,0.12)" stroke-width="0.8"/>
                    </svg>
                    <div class="jacket-title">Yo Soy</div>
                    <div class="jacket-artist">MauriSpide</div>
                    <div class="jacket-catalog">MS-2026-A</div>
                </div>
            </div>
            <div class="vinyl-record-wrap">
                <div class="vinyl">
                    <div class="vinyl-label">
                        <div class="label-grooves"></div>
                    </div>
                </div>
            </div>
            <div class="tonearm">
                <div class="tonearm-base"></div>
                <div class="tonearm-arm"></div>
            </div>
        </div>
    </div>

    <!-- main glass card -->
    <div class="card">

        <div class="rule"></div>

        <h1 class="headline">Gracias por escuchar</h1>
        <p class="song-name">
            Yo Soy MauriSpide &nbsp;&middot;&nbsp; Primer Sencillo
            <span class="live-dot-container">
                <span class="live-dot"></span>
                <span class="live-text">ONLINE</span>
            </span>
        </p>

        <p class="body">
            Tu apoyo desde el inicio significa más de lo que las palabras pueden
            expresar. Cada reproducción es un paso más en este sueño musical que
            apenas comienza a tejerse.
        </p>

        <a href="https://youtube.com" class="btn-play" target="_blank" rel="noopener noreferrer">
            <svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg>
            Escuchar de nuevo
        </a>

        <div class="song-actions" aria-label="Opciones de la canción">
            <button class="action-btn" type="button" data-panel="lyricsPanel" aria-controls="lyricsPanel" aria-expanded="false">
                <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M8 4h8l3 3v13H8z"/><path d="M16 4v4h4"/><path d="M11 12h6"/><path d="M11 16h6"/><path d="M11 8h2"/></svg>
                Letra completa
            </button>
            <button class="action-btn" type="button" data-panel="creditsPanel" aria-controls="creditsPanel" aria-expanded="false">
                <svg viewBox="0 0 24 24" aria-hidden="true"><circle cx="12" cy="8" r="4"/><path d="M5 20c1.6-3.1 4-4.6 7-4.6s5.4 1.5 7 4.6"/></svg>
                Créditos
            </button>
        </div>

        <!-- Lyrics Accordion Panel -->
        <div class="panel-container" id="lyricsPanelContainer">
            <section class="song-panel" id="lyricsPanel">
                <div class="panel-content">
                    <h2>Letra completa</h2>
                    <div class="lyrics-container">
                        <p class="lyrics-verse">En la red del destino, un susurro en la piel,<br>caminando en la noche de este gran carrusel.<br>Hilos de oro y ceniza tejiendo la verdad,<br>bajo el cielo estrellado de la gran ciudad.</p>
                        <p class="lyrics-verse">Yo soy el eco, yo soy la voz,<br>MauriSpide cruzando el veloz reloj.<br>No hay gravedad que pueda frenar<br>el latido constante de este cantar.</p>
                        <p class="lyrics-verse">Tejiendo puentes donde antes hubo muros,<br>alumbrando el sendero en los días oscuros.<br>Tu escucha atenta es mi mayor motor,<br>gracias por darle vida a esta canción.</p>
                    </div>
                </div>
            </section>
        </div>

        <!-- Credits Accordion Panel -->
        <div class="panel-container" id="creditsPanelContainer">
            <section class="song-panel" id="creditsPanel">
                <div class="panel-content">
                    <h2>Créditos de la canción</h2>
                    <ul class="credits-grid">
                        <li><strong>Canción:</strong> Yo Soy MauriSpide</li>
                        <li><strong>Artista:</strong> MauriSpide</li>
                        <li><strong>Composición:</strong> MauriSpide</li>
                        <li><strong>Producción:</strong> LAIP.I Music Studio</li>
                        <li><strong>Diseño de Arte:</strong> MauriSpide &amp; Co</li>
                        <li><strong>Distribución:</strong> LAIP.I Music Songs</li>
                        <li><strong>Sencillo:</strong> Primer lanzamiento</li>
                        <li><strong>Agradecimiento:</strong> A ti, por creer en la música independiente.</li>
                    </ul>
                </div>
            </section>
        </div>

        <div class="share">
            <p class="share-label">Comparte la música</p>
            <div class="share-row">
                <button class="share-btn" id="nativeShareBtn" style="display:none" onclick="doNativeShare()">
                    <svg viewBox="0 0 24 24"><path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92s2.92-1.31 2.92-2.92-1.31-2.92-2.92-2.92z"/></svg>
                    Compartir
                </button>
                <a class="share-btn"
                   href="https://wa.me/?text=Escucha+%22Yo+Soy+MauriSpide%22%2C+el+primer+sencillo+de+MauriSpide+%F0%9F%8E%B5"
                   target="_blank" rel="noopener noreferrer">
                    <svg viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
                    WhatsApp
                </a>
            </div>
        </div>

        <div class="divider"></div>

        <p class="signature">— <strong>MauriSpide</strong> &nbsp;&middot;&nbsp; LAIP.I Music Songs</p>

        <!-- Dynamic Real-time Waveform Container -->
        <div class="waveform" id="waveform"></div>

    </div>
</div>

<script>
    /* Floating music notes system */
    const SYMBOLS = ['&#9833;', '&#9834;', '&#9835;', '&#9836;'];
    const notesEl = document.getElementById('notes');
    for (let i = 0; i < 16; i++) {
        const n = document.createElement('span');
        n.className = 'note';
        n.innerHTML = SYMBOLS[i % SYMBOLS.length];
        n.style.cssText = [
            `left: ${(Math.random() * 95).toFixed(1)}%`,
            `--dur: ${(8 + Math.random() * 12).toFixed(1)}s`,
            `--del: ${(Math.random() * 14).toFixed(1)}s`,
            `font-size: ${(14 + Math.random() * 12).toFixed(0)}px`
        ].join(';');
        notesEl.appendChild(n);
    }

    /* Interactive Ambient Cursor Glow */
    const mouseGlow = document.getElementById('mouseGlow');
    const card = document.querySelector('.card');
    
    document.addEventListener('mousemove', (e) => {
        mouseGlow.style.left = `${e.clientX}px`;
        mouseGlow.style.top = `${e.clientY}px`;
        mouseGlow.style.opacity = '1';
    });
    
    card.addEventListener('mousemove', (e) => {
        const rect = card.getBoundingClientRect();
        const x = e.clientX - rect.left;
        const y = e.clientY - rect.top;
        card.style.setProperty('--mouse-x', `${x}px`);
        card.style.setProperty('--mouse-y', `${y}px`);
        
        // Dynamic 3D Card Hover Tilt Effect
        const centerX = rect.width / 2;
        const centerY = rect.height / 2;
        const rotateX = ((y - centerY) / centerY) * -3; // Max tilt: 3 degrees
        const rotateY = ((x - centerX) / centerX) * 3;
        card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
    });

    card.addEventListener('mouseleave', () => {
        card.style.transform = 'perspective(1000px) rotateX(0deg) rotateY(0deg)';
    });

    /* Cinematic Player Slide Out Initialization */
    const playerWrapper = document.querySelector('.player-wrapper');
    setTimeout(() => {
        playerWrapper.classList.add('active');
    }, 600);

    /* Real-time Organic Waveform Animation (requestAnimationFrame) */
    const waveEl = document.getElementById('waveform');
    const BAR_COUNT = 36;
    const bars = [];
    
    for (let i = 0; i < BAR_COUNT; i++) {
        const b = document.createElement('div');
        b.style.width = '3.5px';
        b.style.borderRadius = '3px';
        b.style.backgroundColor = 'var(--gold)';
        b.style.transition = 'background-color 0.3s, opacity 0.3s';
        waveEl.appendChild(b);
        bars.push(b);
    }

    let time = 0;
    let speedMultiplier = 1.0;

    // Increase waveform frequency and amplitude on card hover
    card.addEventListener('mouseenter', () => {
        speedMultiplier = 2.4;
    });
    card.addEventListener('mouseleave', () => {
        speedMultiplier = 1.0;
    });

    function animateWave() {
        time += 0.035 * speedMultiplier;
        bars.forEach((bar, idx) => {
            const wave1 = Math.sin(idx * 0.18 + time) * 8;
            const wave2 = Math.cos(idx * 0.42 - time * 0.8) * 5;
            const wave3 = Math.sin(idx * 0.11 + time * 1.6) * 2;
            
            let height = 5 + Math.abs(wave1 + wave2 + wave3) * speedMultiplier;
            // Clamp heights elegantly
            height = Math.max(4, Math.min(26, height));
            
            bar.style.height = `${height}px`;
            
            // Sync opacity organically
            const opacity = 0.22 + (height / 26) * 0.58;
            bar.style.opacity = opacity;
            
            // Add vibrant glow color for peaking waves
            if (height > 18) {
                bar.style.backgroundColor = 'var(--gold-bright)';
            } else {
                bar.style.backgroundColor = 'var(--gold)';
            }
        });
        requestAnimationFrame(animateWave);
    }
    animateWave();

    /* Native Share API */
    if (navigator.share) {
        document.getElementById('nativeShareBtn').style.display = 'inline-flex';
    }

    function doNativeShare() {
        navigator.share({
            title: 'Yo Soy MauriSpide',
            text: 'Escucha el primer sencillo de MauriSpide',
            url: window.location.href
        }).catch(() => {});
    }

    /* Accordion Panel Drawer Transitions */
    document.querySelectorAll('[data-panel]').forEach((button) => {
        button.addEventListener('click', () => {
            const targetId = button.dataset.panel;
            const targetContainer = document.getElementById(targetId + 'Container');
            const isCurrentlyExpanded = targetContainer.classList.contains('expanded');

            // Collapse all other containers
            document.querySelectorAll('.panel-container').forEach((container) => {
                if (container !== targetContainer) {
                    container.classList.remove('expanded');
                }
            });
            document.querySelectorAll('[data-panel]').forEach((item) => {
                if (item !== button) {
                    item.setAttribute('aria-expanded', 'false');
                    item.classList.remove('active-btn');
                }
            });

            // Toggle selected container
            if (isCurrentlyExpanded) {
                targetContainer.classList.remove('expanded');
                button.setAttribute('aria-expanded', 'false');
                button.classList.remove('active-btn');
            } else {
                targetContainer.classList.add('expanded');
                button.setAttribute('aria-expanded', 'true');
                button.classList.add('active-btn');
                
                // Smooth scroll to view panel beautifully
                setTimeout(() => {
                    targetContainer.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
                }, 180);
            }
        });
    });
</script>

</body>
</html>
