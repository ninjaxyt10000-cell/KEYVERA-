import { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input";

export default function RealEstateSite() { const [search, setSearch] = useState("");

const properties = [ { id: 1, title: "شقة على البحر - البيطاش", price: "1,800,000 جنيه", type: "بيع" }, { id: 2, title: "شقة سوبر لوكس - العجمي", price: "2,200,000 جنيه", type: "بيع" }, { id: 3, title: "استوديو للإيجار - الهانوفيل", price: "7,000 / شهر", type: "إيجار" }, ];

const filtered = properties.filter(p => p.title.includes(search) );

return ( <div className="min-h-screen bg-gray-50 p-6"> {/* Header */} <header className="text-center mb-10"> <h1 className="text-4xl font-bold">KEYVERA</h1> <p className="text-gray-600 mt-2"> وسيطك العقاري في البيطاش والعجمي - الإسكندرية </p> <Button className="mt-4 bg-green-600 text-white"> <a href="https://wa.me/201206369219" target="_blank" rel="noopener noreferrer"> <Button className="mt-4 bg-green-600 text-white"> تواصل واتساب مباشر </Button> </a> </Button> </header>

{/* Search */}
  <div className="max-w-xl mx-auto mb-10">
    <Input
      placeholder="ابحث في البيطاش أو العجمي..."
      value={search}
      onChange={(e) => setSearch(e.target.value)}
    />
  </div>

  {/* Listings */}
  <div className="grid md:grid-cols-3 gap-6">
    {filtered.map((p) => (
      <Card key={p.id} className="rounded-2xl shadow-lg">
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold">{p.title}</h2>
          <p className="text-gray-500 mt-2">{p.type}</p>
          <p className="text-green-600 font-bold mt-2">{p.price}</p>
          <Button className="mt-4 w-full">تفاصيل العقار</Button>
        </CardContent>
      </Card>
    ))}
  </div>

  {/* Footer */}
  <footer className="text-center mt-16 text-gray-500">
    © 2026 KEYVERA - جميع الحقوق محفوظة
  </footer>
</div>

); }
