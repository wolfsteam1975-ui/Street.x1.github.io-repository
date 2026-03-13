# Street.x1.github.io-repository
import { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button";

const products = [ { id: 1, name: "Street.X1 Minimal T‑Shirt", price: 39, img: "https://via.placeholder.com/500" }, { id: 2, name: "Street.X1 Oversized T‑Shirt", price: 49, img: "https://via.placeholder.com/500" }, { id: 3, name: "Street.X1 Football Jersey", price: 59, img: "https://via.placeholder.com/500" }, { id: 4, name: "Street.X1 Premium Jersey", price: 69, img: "https://via.placeholder.com/500" } ];

export default function StreetX1Store() { const [cart, setCart] = useState([]);

const addToCart = (product) => { setCart([...cart, product]); };

const total = cart.reduce((sum, item) => sum + item.price, 0);

return ( <div className="min-h-screen bg-black text-white"> <header className="flex justify-between items-center px-8 py-6 border-b border-zinc-800"> <h1 className="text-2xl font-semibold tracking-[0.3em]">Street.X1</h1> <div className="text-sm">Cart ({cart.length})</div> </header>

<section className="text-center py-28 px-6 max-w-4xl mx-auto">
    <h2 className="text-5xl font-semibold mb-6">Minimal Luxury Streetwear</h2>
    <p className="text-zinc-400 mb-10">
      Premium T‑shirts and jerseys designed for a clean, modern street style.
    </p>
    <Button className="rounded-2xl px-8">Shop Collection</Button>
  </section>

  <section className="px-10 pb-28 grid md:grid-cols-4 gap-8">
    {products.map((p) => (
      <Card key={p.id} className="bg-zinc-900 rounded-2xl border border-zinc-800">
        <CardContent className="p-5">
          <img src={p.img} className="rounded-xl mb-4" />
          <h3 className="text-lg font-medium">{p.name}</h3>
          <p className="text-zinc-400 mb-4">${p.price}</p>

          <select className="w-full mb-3 p-2 rounded-lg text-black">
            <option>Select Size</option>
            <option>S</option>
            <option>M</option>
            <option>L</option>
            <option>XL</option>
          </select>

          <Button
            onClick={() => addToCart(p)}
            className="w-full rounded-xl"
          >
            Add to Cart
          </Button>
        </CardContent>
      </Card>
    ))}
  </section>

  <section className="px-10 pb-28 max-w-lg">
    <h2 className="text-3xl font-semibold mb-6">Checkout</h2>
    <p className="text-zinc-400 mb-4">Total: ${total}</p>
    <Button className="rounded-xl w-full">
      Pay Now (Razorpay Integration)
    </Button>
  </section>

  <section className="px-10 pb-28 max-w-xl">
    <h2 className="text-3xl font-semibold mb-6">Contact</h2>
    <form className="flex flex-col gap-4">
      <input className="p-3 rounded-xl text-black" placeholder="Your Name" />
      <input className="p-3 rounded-xl text-black" placeholder="Email" />
      <textarea className="p-3 rounded-xl text-black" placeholder="Message" />
      <Button className="rounded-xl">Send Message</Button>
    </form>
  </section>

  <footer className="text-center py-10 border-t border-zinc-800 text-zinc-500">
    © 2026 Street.X1 — Minimal Luxury Brand
  </footer>
</div>

); }
