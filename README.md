import React, { useState, useRef, useEffect } from 'react';

export default function RomanticSite() { const [page, setPage] = useState('home'); const [opened, setOpened] = useState(false); const [showCard, setShowCard] = useState(false); const [showModal, setShowModal] = useState(false); const audioRef = useRef(null);

useEffect(() => { // Try to autoplay (browsers often block autoplay with sound). if (audioRef.current) { audioRef.current.volume = 0.6; const play = async () => { try { await audioRef.current.play(); } catch(e) { /* ignore autoplay block */ } }; play(); } }, []);

const openEnvelope = () => { setOpened(true); // card pops out slightly after envelope opens setTimeout(() => setShowCard(true), 700); };
<div className="envelope-front"/IMG_20251117_161748.jpg"/IMG_20251117_161558.jpg">
   ...
</div>
const resetEnvelope = () => { setShowCard(false); setTimeout(() => setOpened(false), 400); };/IMG_20251117_161558.jpg
<main className="max-w-4xl mx-auto mt-8">
<main className="max-w-4xl mx-auto mt-8">
    {/* Page: HOME */}
    {page === 'home' && (
      <section className="bg-white/70 rounded-2xl p-8 shadow-2xl relative overflow-hidden">
        <Sparkles />
        <div className="flex flex-col items-center gap-6">
          <div className="text-center">
            <p className="text-xl">For <span className="font-semibold">Yash</span>, with all my heart.</p>
            <p className="mt-2 text-pink-700">Click the envelope to open your surprise ✧</p>
          </div>

          <div className="relative">
            <div
              onClick={() => opened ? resetEnvelope() : openEnvelope()}
              className={`cursor-pointer w-80 h-48 mx-auto transition-transform duration-700 ${opened ? 'translate-y-2' : ''}`}
            >
              <Envelope opened={opened} />

              {/* Card that pops out */}
              <div className={`absolute left-1/2 -translate-x-1/2 top-8 w-64 transition-all duration-700 ${showCard ? 'translate-y-0 opacity-100 scale-100' : 'translate-y-6 opacity-0 scale-95'}`}>
                <CardVintage show={showCard} />
              </div>
            </div>

            <div className="mt-4 flex justify-center gap-4">
              <button onClick={() => { setPage('letter'); openEnvelope(); }} className="px-4 py-2 rounded-full bg-pink-600 text-white shadow">Open Letter Page</button>
              <button onClick={() => { audioRef.current && audioRef.current.paused ? audioRef.current.play() : audioRef.current.pause(); }} className="px-4 py-2 rounded-full bg-white/80">Play/Pause Music</button>
            </div>
          </div>

          <div className="mt-6 flex items-center gap-4">
            <TeddySVG />
            <div className="text-left">
              <p className="text-sm italic max-w-xl">"I'm sorry Yash — I love you" — a small note with a huge heart. Keep this safe ✧</p>
            </div>
          </div>
        </div>
      </section>
    )}

    {/* Page: LETTER */}
    {page === 'letter' && (
      <section className="bg-white/80 rounded-2xl p-10 shadow-xl relative">
        <Sparkles />
        <h2 className="text-2xl font-semibold mb-4">Your Vintage Letter</h2>
        <div className="flex gap-8">
          <div className="w-1/2">
            <div className="p-6 bg-[url('data:image/svg+xml;utf8,<svg xmlns=\"http://www.w3.org/2000/svg\" width=\"400\" height=\"300\"><rect width=\"100%\" height=\"100%\" fill=\"%23fef3f7\"/><text x=\"20\" y=\"40\" font-size=\"18\" fill=\"%23d6336c\">Vintage Header</text></svg>')] rounded-lg border border-pink-200 shadow-inner">
              <div className="bg-[radial-gradient(ellipse_at_top_left,rgba(255,255,255,0.6),transparent)] p-4 rounded">
                <p style={{fontFamily: 'Georgia, serif'}} className="whitespace-pre-line leading-relaxed">{

My Dearest Yash,\n\nI'm sorry for the moments I hurt you. I think about you every day — your smile, your voice, the way you make ordinary moments feel warm. You mean everything to me.\n\nForever yours,\n— ❤️} </p> </div> </div>

<div className="mt-6">
              <button onClick={() => setShowModal(true)} className="px-5 py-2 rounded-full bg-pink-600 text-white shadow">Will u be mine forever?</button>
            </div>
          </div>

          <div className="w-1/2">
            <h3 className="text-lg font-medium">Letter Details</h3>
            <p className="mt-3 text-sm">This letter has a vintage paper texture, a hand-written feel (using Georgia font), and soft rose-border decorations. Press the button above to show your confession response.</p>

            <div className="mt-6 flex gap-3 flex-wrap">
              <BowSVG />
              <HeartSVG />
              <HeartSVG />
              <BowSVG />
            </div>
          </div>
        </div>
      </section>
    )}

    {/* Page: CONFESSIONS */}
    {page === 'confessions' && (
      <section className="bg-white/80 rounded-2xl p-8 shadow-xl">
        <Sparkles />
        <h2 className="text-2xl font-semibold mb-4">Some Confessions</h2>
        <div className="space-y-4">
          <Confession text={`I miss the little things — the way you laugh at bad jokes, the warmth of your hand, the quiet nights that felt like home. I'm sorry for every time I made you doubt my love. You are my first thought in the morning and my last before sleep.`} />
          <Confession text={`Sometimes I get scared of losing you and say things I don't mean. Please forgive me — my love for you is the truest thing I know.`} />
          <Confession text={`If I could, I'd wrap every day in bows and soft music and make sure you feel loved without question.`} />
        </div>
      </section>
    )}

    {/* Page: GALLERY */}
    {page === 'gallery' && (
      <section className="bg-white/80 rounded-2xl p-6 shadow-xl">
        <h2 className="text-2xl font-semibold mb-4">Cute Gallery</h2>
        <div className="grid grid-cols-3 gap-4">
          <div className="p-4 bg-pink-50 rounded-lg shadow">{TeddySVG()}</div>
          <div className="p-4 bg-pink-50 rounded-lg shadow">{HeartSVG()}</div>
          <div className="p-4 bg-pink-50 rounded-lg shadow">{BowSVG()}</div>
        </div>
      </section>
    )}

    {/* Page: SURPRISES */}
    {page === 'surprises' && (
      <section className="bg-white/80 rounded-2xl p-8 shadow-xl">
        <h2 className="text-2xl font-semibold mb-4">Surprises</h2>
        <ul className="list-disc pl-6 space-y-2">
          <li>A pop-out love card from an envelope with a vintage letter.</li>
          <li>Soft background music (click play if it doesn't autoplay).</li>
          <li>Animated sparkles, hearts and bows.</li>
          <li>"Will u be mine forever?" button that triggers a sweet animation.</li>
        </ul>
      </section>
    )}

  </main>

  <footer className="max-w-4xl mx-auto mt-8 text-center text-sm text-pink-700">
    <p>Made with ❤️ and sparkles — just for Yash.</p>
  </footer>

  <audio src="/music/bgmusic.mp3" autoplay loop></audio"/beabadoobee - Glue Song (Lyrics).mp3">
  <audio ref={audioRef} loop src="/music/cute-melody.mp3" />

  {/* Modal for proposal */}
  {showModal && (
    <div className="fixed inset-0 bg-black/40 flex items-center justify-center z-50">
      <div className="bg-white rounded-2xl p-6 w-96 text-center shadow-2xl">
        <h3 className="text-xl font-bold mb-3">Will you be mine forever?</h3>
        <p className="mb-4">Say yes and let's promise to keep holding each other's hands through everything.</p>
        <div className="flex justify-center gap-4">
          <button onClick={() => { setShowModal(false); setPage('confessions'); }} className="px-4 py-2 rounded-full bg-pink-600 text-white">Yes ♥</button>
          <button onClick={() => setShowModal(false)} className="px-4 py-2 rounded-full bg-white/80">Not yet</button>
        </div>
      </div>
    </div>
  )}

  {/* inline small styles for animations */}
  <style>{`
    @keyframes floaty { 0% { transform: translateY(0);} 50% { transform: translateY(-8px);} 100% { transform: translateY(0);} }
    .floaty { animation: floaty 4s ease-in-out infinite; }
    @keyframes pop { 0% { transform: translateY(18px) scale(0.94); opacity: 0 } 60% { transform: translateY(-6px) scale(1.02); opacity: 1 } 100% { transform: translateY(0) scale(1); opacity: 1 } }
    .popCard { animation: pop 700ms cubic-bezier(.22,.9,.27,1) both; }
  `}</style>
</div>

); }

/* ---------- Small visual components ---------- */
import React, { useState, useRef, useEffect } from 'react';

export default function RomanticSite() { const [page, setPage] = useState('home'); const [opened, setOpened] = useState(false); const [showCard, setShowCard] = useState(false); const [showModal, setShowModal] = useState(false); const audioRef = useRef(null);

useEffect(() => { // Try to autoplay (browsers often block autoplay with sound). if (audioRef.current) { audioRef.current.volume = 0.6; const play = async () => { try { await audioRef.current.play(); } catch(e) { /* ignore autoplay block */ } }; play(); } }, []);

const openEnvelope = () => { setOpened(true); // card pops out slightly after envelope opens setTimeout(() => setShowCard(true), 700); };
<div className="envelope-front"/IMG_20251117_161748.jpg"/IMG_20251117_161558.jpg">
   ...
</div>
const resetEnvelope = () => { setShowCard(false); setTimeout(() => setOpened(false), 400); };/IMG_20251117_161558.jpg
<main className="max-w-4xl mx-auto mt-8">
<main className="max-w-4xl mx-auto mt-8">
    {/* Page: HOME */}
    {page === 'home' && (
      <section className="bg-white/70 rounded-2xl p-8 shadow-2xl relative overflow-hidden">
        <Sparkles />
        <div className="flex flex-col items-center gap-6">
          <div className="text-center">
            <p className="text-xl">For <span className="font-semibold">Yash</span>, with all my heart.</p>
            <p className="mt-2 text-pink-700">Click the envelope to open your surprise ✧</p>
          </div>

          <div className="relative">
            <div
              onClick={() => opened ? resetEnvelope() : openEnvelope()}
              className={`cursor-pointer w-80 h-48 mx-auto transition-transform duration-700 ${opened ? 'translate-y-2' : ''}`}
            >
              <Envelope opened={opened} />

              {/* Card that pops out */}
              <div className={`absolute left-1/2 -translate-x-1/2 top-8 w-64 transition-all duration-700 ${showCard ? 'translate-y-0 opacity-100 scale-100' : 'translate-y-6 opacity-0 scale-95'}`}>
                <CardVintage show={showCard} />
              </div>
            </div>

            <div className="mt-4 flex justify-center gap-4">
              <button onClick={() => { setPage('letter'); openEnvelope(); }} className="px-4 py-2 rounded-full bg-pink-600 text-white shadow">Open Letter Page</button>
              <button onClick={() => { audioRef.current && audioRef.current.paused ? audioRef.current.play() : audioRef.current.pause(); }} className="px-4 py-2 rounded-full bg-white/80">Play/Pause Music</button>
            </div>
          </div>

          <div className="mt-6 flex items-center gap-4">
            <TeddySVG />
            <div className="text-left">
              <p className="text-sm italic max-w-xl">"I'm sorry Yash — I love you" — a small note with a huge heart. Keep this safe ✧</p>
            </div>
          </div>
        </div>
      </section>
    )}

    {/* Page: LETTER */}
    {page === 'letter' && (
      <section className="bg-white/80 rounded-2xl p-10 shadow-xl relative">
        <Sparkles />
        <h2 className="text-2xl font-semibold mb-4">Your Vintage Letter</h2>
        <div className="flex gap-8">
          <div className="w-1/2">
            <div className="p-6 bg-[url('data:image/svg+xml;utf8,<svg xmlns=\"http://www.w3.org/2000/svg\" width=\"400\" height=\"300\"><rect width=\"100%\" height=\"100%\" fill=\"%23fef3f7\"/><text x=\"20\" y=\"40\" font-size=\"18\" fill=\"%23d6336c\">Vintage Header</text></svg>')] rounded-lg border border-pink-200 shadow-inner">
              <div className="bg-[radial-gradient(ellipse_at_top_left,rgba(255,255,255,0.6),transparent)] p-4 rounded">
                <p style={{fontFamily: 'Georgia, serif'}} className="whitespace-pre-line leading-relaxed">{

My Dearest Yash,\n\nI'm sorry for the moments I hurt you. I think about you every day — your smile, your voice, the way you make ordinary moments feel warm. You mean everything to me.\n\nForever yours,\n— ❤️} </p> </div> </div>

<div className="mt-6">
              <button onClick={() => setShowModal(true)} className="px-5 py-2 rounded-full bg-pink-600 text-white shadow">Will u be mine forever?</button>
            </div>
          </div>

          <div className="w-1/2">
            <h3 className="text-lg font-medium">Letter Details</h3>
            <p className="mt-3 text-sm">This letter has a vintage paper texture, a hand-written feel (using Georgia font), and soft rose-border decorations. Press the button above to show your confession response.</p>

            <div className="mt-6 flex gap-3 flex-wrap">
              <BowSVG />
              <HeartSVG />
              <HeartSVG />
              <BowSVG />
            </div>
          </div>
        </div>
      </section>
    )}

    {/* Page: CONFESSIONS */}
    {page === 'confessions' && (
      <section className="bg-white/80 rounded-2xl p-8 shadow-xl">
        <Sparkles />
        <h2 className="text-2xl font-semibold mb-4">Some Confessions</h2>
        <div className="space-y-4">
          <Confession text={`I miss the little things — the way you laugh at bad jokes, the warmth of your hand, the quiet nights that felt like home. I'm sorry for every time I made you doubt my love. You are my first thought in the morning and my last before sleep.`} />
          <Confession text={`Sometimes I get scared of losing you and say things I don't mean. Please forgive me — my love for you is the truest thing I know.`} />
          <Confession text={`If I could, I'd wrap every day in bows and soft music and make sure you feel loved without question.`} />
        </div>
      </section>
    )}

    {/* Page: GALLERY */}
    {page === 'gallery' && (
      <section className="bg-white/80 rounded-2xl p-6 shadow-xl">
        <h2 className="text-2xl font-semibold mb-4">Cute Gallery</h2>
        <div className="grid grid-cols-3 gap-4">
          <div className="p-4 bg-pink-50 rounded-lg shadow">{TeddySVG()}</div>
          <div className="p-4 bg-pink-50 rounded-lg shadow">{HeartSVG()}</div>
          <div className="p-4 bg-pink-50 rounded-lg shadow">{BowSVG()}</div>
        </div>
      </section>
    )}

    {/* Page: SURPRISES */}
    {page === 'surprises' && (
      <section className="bg-white/80 rounded-2xl p-8 shadow-xl">
        <h2 className="text-2xl font-semibold mb-4">Surprises</h2>
        <ul className="list-disc pl-6 space-y-2">
          <li>A pop-out love card from an envelope with a vintage letter.</li>
          <li>Soft background music (click play if it doesn't autoplay).</li>
          <li>Animated sparkles, hearts and bows.</li>
          <li>"Will u be mine forever?" button that triggers a sweet animation.</li>
        </ul>
      </section>
    )}

  </main>

  <footer className="max-w-4xl mx-auto mt-8 text-center text-sm text-pink-700">
    <p>Made with ❤️ and sparkles — just for Yash.</p>
  </footer>

  <audio src="/music/bgmusic.mp3" autoplay loop></audio"/beabadoobee - Glue Song (Lyrics).mp3">
  <audio ref={audioRef} loop src="/music/cute-melody.mp3" />

  {/* Modal for proposal */}
  {showModal && (
    <div className="fixed inset-0 bg-black/40 flex items-center justify-center z-50">
      <div className="bg-white rounded-2xl p-6 w-96 text-center shadow-2xl">
        <h3 className="text-xl font-bold mb-3">Will you be mine forever?</h3>
        <p className="mb-4">Say yes and let's promise to keep holding each other's hands through everything.</p>
        <div className="flex justify-center gap-4">
          <button onClick={() => { setShowModal(false); setPage('confessions'); }} className="px-4 py-2 rounded-full bg-pink-600 text-white">Yes ♥</button>
          <button onClick={() => setShowModal(false)} className="px-4 py-2 rounded-full bg-white/80">Not yet</button>
        </div>
      </div>
    </div>
  )}

  {/* inline small styles for animations */}
  <style>{`
    @keyframes floaty { 0% { transform: translateY(0);} 50% { transform: translateY(-8px);} 100% { transform: translateY(0);} }
    .floaty { animation: floaty 4s ease-in-out infinite; }
    @keyframes pop { 0% { transform: translateY(18px) scale(0.94); opacity: 0 } 60% { transform: translateY(-6px) scale(1.02); opacity: 1 } 100% { transform: translateY(0) scale(1); opacity: 1 } }
    .popCard { animation: pop 700ms cubic-bezier(.22,.9,.27,1) both; }
  `}</style>
</div>

); }

/* ---------- Small visual components ---------- */

function Envelope({ opened=false }){ return ( <div className={mx-auto relative}> <div className={w-80 h-48 rounded-lg bg-pink-100 border border-pink-300 shadow-md relative overflow-hidden transform transition-all duration-700 ${opened ? 'rotate-1' : ''}}> <div className={absolute inset-0 flex items-start justify-center pointer-events-none}> <div className={w-full h-1/3 bg-pink-200 transform origin-top transition-all duration-600 ${opened ? 'translate-y-[-60px] rotate-6' : ''}}></div> </div> <div className="absolute inset-0 flex items-center justify-center"> <div className={w-56 h-32 bg-pink-50 border border-pink-200 rounded shadow-inner ${opened ? 'popCard' : ''}} /> </div> </div> {/* little bow on envelope */} <div className="absolute left-1/2 -translate-x-1/2 top-6"> <BowSVG large /> </div> </div> ); }

function CardVintage({ show=false }){ return ( <div className={bg-[url('data:image/svg+xml;utf8,<svg xmlns=\"http://www.w3.org/2000/svg\" width=\"600\" height=\"480\"><rect rx=\"18\" width=\"100%\" height=\"100%\" fill=\"%23fff5f7\"/></svg>')] border border-pink-200 rounded-lg p-6 shadow-lg ${show ? 'popCard' : ''}}> <div style={{fontFamily: 'Georgia, serif'}}> <h3 className="text-xl font-semibold mb-3">I'm sorry Yash — I love you</h3> <p className="text-sm leading-relaxed whitespace-pre-line">{My Dearest Yash,\n\nI'm sorry for the times I hurt you. I love you more than words can say. Please keep this letter close — it's full of my heart.}</p> <div className="mt-4 flex justify-between items-center"> <div className="text-xs italic">— yours</div> <div className="flex items-center gap-2"> <HeartSVG small /> <BowSVG small /> </div> </div> </div> </div> ); }

function Confession({ text }){ return ( <div className="p-4 bg-pink-50 rounded-lg border border-pink-100 shadow-sm"> <p className="text-sm">{text}</p> </div> ); }

function HeartSVG({ small=false }){ const cls = small ? 'w-6 h-6' : 'w-12 h-12'; return ( <svg className={inline-block ${cls} floaty} viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"> <path d="M12 21s-7-4.35-9-7.2C-1.2 8.7 5 3 7.5 5.2 9 6.7 12 9 12 9s3-2.3 4.5-3.8C19 3 25.2 8.7 21 13.8 19 16.65 12 21 12 21z" fill="#ff6b9a" /> </svg> ); }

function BowSVG({ large=false, small=false }){ const cls = large ? 'w-20 h-8' : small ? 'w-5 h-5' : 'w-10 h-6'; return ( <svg className={${cls} inline-block} viewBox="0 0 64 32" xmlns="http://www.w3.org/2000/svg"> <g fill="#ff92b0"> <ellipse cx="16" cy="16" rx="12" ry="8" /> <ellipse cx="48" cy="16" rx="12" ry="8" /> <rect x="28" y="10" width="8" height="12" rx="2" /> </g> </svg> ); }

function TeddySVG(){ return ( <svg width="120" height="120" viewBox="0 0 120 120" xmlns="http://www.w3.org/2000/svg" className="floaty"> <g> <circle cx="60" cy="40" r="20" fill="#f8c8a0" /> <circle cx="44" cy="30" r="8" fill="#f8c8a0" /> <circle cx="76" cy="30" r="8" fill="#f8c8a0" /> <ellipse cx="60" cy="74" rx="28" ry="26" fill="#f8c8a0" /> <circle cx="52" cy="38" r="3" fill="#222" /> <circle cx="68" cy="38" r="3" fill="#222" /> <path d="M54 48 q6 6 12 0" stroke="#a44" strokeWidth="2" fill="none" strokeLinecap="round" /> <rect x="44" y="86" width="32" height="10" rx="5" fill="#ffd2b3" /> </g> </svg> ); }

function Sparkles(){ return ( <div className="pointer-events-none absolute inset-0 -z-10"> <div className="absolute top-4 left-8 opacity-80 animate-[spin_12s_linear_infinite]">✨</div> <div className="absolute top-20 right-12 opacity-70">✦</div> <div className="absolute bottom-6 left-1/3 opacity-60">✧</div> <div className="absolute bottom-20 right-8 opacity-50">✶</div> </div> ); }
function Envelope({ opened=false }){ return ( <div className={mx-auto relative}> <div className={w-80 h-48 rounded-lg bg-pink-100 border border-pink-300 shadow-md relative overflow-hidden transform transition-all duration-700 ${opened ? 'rotate-1' : ''}}> <div className={absolute inset-0 flex items-start justify-center pointer-events-none}> <div className={w-full h-1/3 bg-pink-200 transform origin-top transition-all duration-600 ${opened ? 'translate-y-[-60px] rotate-6' : ''}}></div> </div> <div className="absolute inset-0 flex items-center justify-center"> <div className={w-56 h-32 bg-pink-50 border border-pink-200 rounded shadow-inner ${opened ? 'popCard' : ''}} /> </div> </div> {/* little bow on envelope */} <div className="absolute left-1/2 -translate-x-1/2 top-6"> <BowSVG large /> </div> </div> ); }

function CardVintage({ show=false }){ return ( <div className={bg-[url('data:image/svg+xml;utf8,<svg xmlns=\"http://www.w3.org/2000/svg\" width=\"600\" height=\"480\"><rect rx=\"18\" width=\"100%\" height=\"100%\" fill=\"%23fff5f7\"/></svg>')] border border-pink-200 rounded-lg p-6 shadow-lg ${show ? 'popCard' : ''}}> <div style={{fontFamily: 'Georgia, serif'}}> <h3 className="text-xl font-semibold mb-3">I'm sorry Yash — I love you</h3> <p className="text-sm leading-relaxed whitespace-pre-line">{My Dearest Yash,\n\nI'm sorry for the times I hurt you. I love you more than words can say. Please keep this letter close — it's full of my heart.}</p> <div className="mt-4 flex justify-between items-center"> <div className="text-xs italic">— yours</div> <div className="flex items-center gap-2"> <HeartSVG small /> <BowSVG small /> </div> </div> </div> </div> ); }

function Confession({ text }){ return ( <div className="p-4 bg-pink-50 rounded-lg border border-pink-100 shadow-sm"> <p className="text-sm">{text}</p> </div> ); }

function HeartSVG({ small=false }){ const cls = small ? 'w-6 h-6' : 'w-12 h-12'; return ( <svg className={inline-block ${cls} floaty} viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"> <path d="M12 21s-7-4.35-9-7.2C-1.2 8.7 5 3 7.5 5.2 9 6.7 12 9 12 9s3-2.3 4.5-3.8C19 3 25.2 8.7 21 13.8 19 16.65 12 21 12 21z" fill="#ff6b9a" /> </svg> ); }

function BowSVG({ large=false, small=false }){ const cls = large ? 'w-20 h-8' : small ? 'w-5 h-5' : 'w-10 h-6'; return ( <svg className={${cls} inline-block} viewBox="0 0 64 32" xmlns="http://www.w3.org/2000/svg"> <g fill="#ff92b0"> <ellipse cx="16" cy="16" rx="12" ry="8" /> <ellipse cx="48" cy="16" rx="12" ry="8" /> <rect x="28" y="10" width="8" height="12" rx="2" /> </g> </svg> ); }

function TeddySVG(){ return ( <svg width="120" height="120" viewBox="0 0 120 120" xmlns="http://www.w3.org/2000/svg" className="floaty"> <g> <circle cx="60" cy="40" r="20" fill="#f8c8a0" /> <circle cx="44" cy="30" r="8" fill="#f8c8a0" /> <circle cx="76" cy="30" r="8" fill="#f8c8a0" /> <ellipse cx="60" cy="74" rx="28" ry="26" fill="#f8c8a0" /> <circle cx="52" cy="38" r="3" fill="#222" /> <circle cx="68" cy="38" r="3" fill="#222" /> <path d="M54 48 q6 6 12 0" stroke="#a44" strokeWidth="2" fill="none" strokeLinecap="round" /> <rect x="44" y="86" width="32" height="10" rx="5" fill="#ffd2b3" /> </g> </svg> ); }

function Sparkles(){ return ( <div className="pointer-events-none absolute inset-0 -z-10"> <div className="absolute top-4 left-8 opacity-80 animate-[spin_12s_linear_infinite]">✨</div> <div className="absolute top-20 right-12 opacity-70">✦</div> <div className="absolute bottom-6 left-1/3 opacity-60">✧</div> <div className="absolute bottom-20 right-8 opacity-50">✶</div> </div> ); }
