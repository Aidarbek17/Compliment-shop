# Compliment-shop 
import { useState } from "react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { motion } from "framer-motion";

const compliments = [
  "Ты сегодня сияешь!",
  "Ты делаешь этот мир лучше!",
  "У тебя потрясающая энергия!",
  "Ты вдохновляешь!",
  "Ты суперзвезда в своём деле!"
];

export default function ComplimentShop() {
  const [selected, setSelected] = useState("");
  const [recipient, setRecipient] = useState("");

  const getCompliment = () => {
    const random = compliments[Math.floor(Math.random() * compliments.length)];
    setSelected(random);
  };

  return (
    <div className="min-h-screen bg-gradient-to-b from-pink-100 to-white p-6 flex flex-col items-center">
      <motion.h1 initial={{ opacity: 0, y: -20 }} animate={{ opacity: 1, y: 0 }} className="text-4xl font-bold mb-4">
        Магазин Виртуальных Комплиментов
      </motion.h1>

      <Card className="w-full max-w-md mb-6">
        <CardContent className="p-4 flex flex-col gap-4">
          <Input
            placeholder="Кому отправить? (ник или email)"
            value={recipient}
            onChange={(e) => setRecipient(e.target.value)}
          />
          <Button onClick={getCompliment}>Купить комплимент — 0.99$</Button>
          {selected && (
            <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="text-center mt-4 text-xl">
              ✨ {selected}
            </motion.div>
          )}
        </CardContent>
      </Card>
    </div>
  );
}
