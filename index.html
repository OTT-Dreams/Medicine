import React, { useMemo, useState } from "react";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select";
import { Badge } from "@/components/ui/badge";
import { AlertTriangle, Activity, Stethoscope, Search, ShieldAlert, CircleHelp } from "lucide-react";
import { motion } from "framer-motion";

// ---------------- SAFETY FIRST ----------------
// এই ডেমোটি কেবল শিক্ষা/তথ্যগত উদ্দেশ্যে।
// এটি কোনও রোগনির্ণয় বা চিকিৎসার বিকল্প নয়। ডোজ/ঔষধ শুরু করার আগে লাইসেন্সপ্রাপ্ত আয়ুর্বেদিক চিকিৎসকের (BAMS) পরামর্শ নিন।

const RED_FLAGS: { pattern: RegExp; message: string }[] = [
  { pattern: /(বুকের ব্যথা|চেস্ট পেইন|চাপ|শ্বাসকষ্ট|শ্বাস নিতে অসুবিধা)/i, message: "বুকের ব্যথা বা শ্বাসকষ্ট — তাৎক্ষণিক জরুরি চিকিৎসা নিন (112/108)।" },
  { pattern: /(অচেতন|বেহুঁশ|বিভ্রান্তি|হ্যালুসিনেশন)/i, message: "অচেতনতা/বিভ্রান্তি — জরুরি চিকিৎসা দরকার।" },
  { pattern: /(রক্তপাত|ব্লিডিং|রক্ত উঠছে|রক্তমিশ্রিত পায়খানা)/i, message: "অতিরিক্ত রক্তপাত/রক্তমিশ্রিত পায়খানা — জরুরি সেবা নিন।" },
  { pattern: /(গর্ভবতী|প্রেগন্যান্সি|গর্ভাবস্থা)/i, message: "গর্ভাবস্থায় ওষুধ নেয়ার আগে অবশ্যই ডাক্তার দেখান।" },
  { pattern: /(শিশু|বাচ্চা|নবজাতক|৫ বছরের কম)/i, message: "৫ বছরের কম শিশুর ক্ষেত্রে নিজে থেকে ওষুধ না নিয়ে শিশু-চিকিৎসকের কাছে যান।" },
  { pattern: /(অত্যধিক জ্বর|১০২|১০৩|১০৪|উচ্চ জ্বর)/i, message: "উচ্চ জ্বরের সাথে খিঁচুনি/বিভ্রান্তি হলে জরুরি সেবা নিন।" },
  { pattern: /(তীব্র ডিহাইড্রেশন|মূর্ছা|খুব দুর্বল|চোখ বসে যাওয়া|প্রস্রাব কম)/i, message: "ডিহাইড্রেশনের লক্ষণ — স্যালাইন/চিকিৎসা জরুরি।" },
];

// খুব সাধারণ কীওয়ার্ড-টু-সাজেশন রুলস (ডেমো ডাটা)
const RULES: Record<string, { tags: string[]; options: string[]; caution?: string }> = {
  "সর্দি": {
    tags: ["কাশি", "নাক বন্ধ", "গলা ব্যথা"],
    options: ["তুলসী-অদা-লেবু চা", "সিতোপলাদি চূর্ণ", "তালিসাদি চূর্ণ", "স্টিম ইনহেলেশন (নুনজল)", "গিলয়/গুডুচি ক্বাথ"],
  },
  "কাশি": {
    tags: ["শুষ্ক কাশি", "বুকে কফ"],
    options: ["যষ্টিমধু (মুলেঠি) গলা সোহাতে", "সিতোপলাদি চূর্ণ", "পিপ্পলি চূর্ণ", "মধু-লেবু গরম জল"],
  },
  "জ্বর": {
    tags: ["শীত শীত", "শরীর ব্যথা"],
    options: ["গুডুচি/তিন্তালি ক্বাথ", "তুলসী-পানীয়", "আদা-তুলসী ক্বাথ", "বিশ্রাম ও জলপান"],
    caution: "উচ্চ জ্বর/৩ দিন স্থায়ী হলে ডাক্তার দেখান।",
  },
  "অ্যাসিডিটি": {
    tags: ["গ্যাস", "ঝাল খেলে বাড়ে", "বুক জ্বালা"],
    options: ["অভিপত্তিকার চূর্ণ", "ধনিয়া-জিরা-সৌফ সিদ্ধ জল", "নারকেলের জল", "দধিমস্ত (পাতলা দই)"],
  },
  "পেট খারাপ": {
    tags: ["ডায়রিয়া", "ঢিলা পায়খানা"],
    options: ["কুটজারিষ্ঠ", "বিল্বাদি চূর্ণ", "ভাতের মাড়/ORS", "দই-ভাত (সহ্য হলে)"],
    caution: "রক্তমিশ্রিত পায়খানা/ডিহাইড্রেশন হলে জরুরি সেবা।",
  },
  "জয়েন্ট ব্যথা": {
    tags: ["হাঁটু", "কোমর", "সকালের জড়তা"],
    options: ["শালাক্ষা/বোসওয়েলিয়া", "অশ্বগন্ধা", "নির্গুণ্ডি তেল মালিশ", "হালকা ব্যায়াম ও উষ্ণ সেঁক"],
  },
  "ত্বকে র‍্যাশ": {
    tags: ["চুলকানি", "লালচে দাগ"],
    options: ["নিম পাতার স্নান", "খাদিরারিষ্ঠ", "ত্রিফলা/মানজিষ্ঠা", "শরীর ঠাণ্ডা রাখা"],
    caution: "ফোস্কা/শ্বাসকষ্ট/মুখ ফুলে গেলে অ্যালার্জি জরুরি।",
  },
  "ঘুমের সমস্যা": {
    tags: ["উদ্বেগ", "স্ট্রেস"],
    options: ["ব্রাহ্মী/জটামানসি", "অশ্বগন্ধা", "গরম দুধে জয়ফল", "স্ক্রিন-ফ্রি রুটিন"],
  },
};

const CATEGORY_HINTS = Object.keys(RULES);

function analyze(text: string) {
  const found: { key: string; rule: (typeof RULES)[string] }[] = [];
  const lower = text.toLowerCase();
  for (const key of Object.keys(RULES)) {
    if (lower.includes(key.toLowerCase())) {
      found.push({ key, rule: RULES[key] });
    }
  }
  // If nothing matched, try fuzzy keyword search
  if (found.length === 0) {
    const guesses: { key: string; rule: (typeof RULES)[string]; hits: number }[] = [];
    for (const key of Object.keys(RULES)) {
      let hits = 0;
      for (const t of RULES[key].tags) {
        if (lower.includes(t.toLowerCase())) hits++;
      }
      if (hits > 0) guesses.push({ key, rule: RULES[key], hits });
    }
    guesses.sort((a, b) => b.hits - a.hits);
    if (guesses.length) found.push({ key: guesses[0].key, rule: guesses[0].rule });
  }
  // red flag detection
  const flags = RED_FLAGS.filter((rf) => rf.pattern.test(text));
  return { found, flags };
}

export default function AyurSymptomChecker() {
  const [symptoms, setSymptoms] = useState("");
  const [bodySystem, setBodySystem] = useState<string>("");
  const [history, setHistory] = useState<string[]>([]);

  const { found, flags } = useMemo(() => analyze(symptoms), [symptoms]);

  const addExample = (t: string) => setSymptoms((s) => (s ? s + "\n" + t : t));

  return (
    <div className="min-h-screen bg-gradient-to-b from-rose-50 to-stone-50 p-4 md:p-10">
      <motion.div initial={{ opacity: 0, y: 8 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.4 }}>
        <div className="max-w-4xl mx-auto space-y-6">
          <div className="flex items-center justify-between">
            <h1 className="text-2xl md:text-4xl font-bold tracking-tight">🪷 আয়ুর্বেদিক উপসর্গ-সাজেশন (ডেমো)</h1>
            <Badge className="text-xs md:text-sm" variant="secondary">ডেমো • তথ্যগত</Badge>
          </div>

          <Card className="shadow-lg rounded-2xl">
            <CardHeader className="pb-2">
              <CardTitle className="flex items-center gap-2 text-xl"><Search className="h-5 w-5"/> আপনার উপসর্গ লিখুন</CardTitle>
            </CardHeader>
            <CardContent className="space-y-4">
              <Textarea
                placeholder="উদাহরণ: গত ২ দিন ধরে কাশি ও সর্দি, রাতে বেড়ে যায়।"
                value={symptoms}
                onChange={(e) => setSymptoms(e.target.value)}
                className="min-h-[120px]"
              />

              <div className="grid grid-cols-1 md:grid-cols-3 gap-3">
                <div>
                  <label className="text-sm text-stone-600">বডি সিস্টেম (ঐচ্ছিক)</label>
                  <Select onValueChange={setBodySystem} value={bodySystem}>
                    <SelectTrigger>
                      <SelectValue placeholder="একটি বেছে নিন" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="resp">শ্বাসতন্ত্র</SelectItem>
                      <SelectItem value="gi">পরিপাক তন্ত্র</SelectItem>
                      <SelectItem value="msk">হাড়-সন্ধি</SelectItem>
                      <SelectItem value="skin">ত্বক</SelectItem>
                      <SelectItem value="neuro">স্নায়ু/ঘুম</SelectItem>
                    </SelectContent>
                  </Select>
                </div>

                <div className="md:col-span-2 flex flex-wrap gap-2 items-center">
                  <span className="text-sm text-stone-600">দ্রুত উদাহরণ:</span>
                  {[
                    "কাশি, নাক বন্ধ, গলা ব্যথা",
                    "বুক জ্বালা, অ্যাসিডিটি, গ্যাস",
                    "ঢিলা পায়খানা, পেট ব্যথা",
                    "জয়েন্টে ব্যথা, হাঁটতে কষ্ট",
                    "ত্বকে র‍্যাশ ও চুলকানি",
                    "উদ্বেগ, রাতে ঘুম হয় না",
                  ].map((ex) => (
                    <Button key={ex} size="sm" variant="outline" onClick={() => addExample(ex)} className="rounded-full">
                      {ex}
                    </Button>
                  ))}
                </div>
              </div>

              {flags.length > 0 && (
                <Card className="border-red-300 bg-red-50">
                  <CardHeader className="pb-1">
                    <CardTitle className="text-red-700 flex items-center gap-2 text-base"><ShieldAlert className="h-5 w-5"/> জরুরি সতর্কতা</CardTitle>
                  </CardHeader>
                  <CardContent className="space-y-1 text-sm text-red-800">
                    {flags.map((f, i) => (
                      <div key={i}>• {f.message}</div>
                    ))}
                    <div>এই অবস্থায় নিজে থেকে ওষুধ না নিয়ে নিকটস্থ হাসপাতালে যান।</div>
                  </CardContent>
                </Card>
              )}

              <div className="space-y-3">
                <h3 className="font-semibold flex items-center gap-2"><Stethoscope className="h-4 w-4"/> সম্ভাব্য ক্যাটেগরি</h3>
                <div className="flex flex-wrap gap-2">
                  {CATEGORY_HINTS.map((c) => (
                    <Badge key={c} variant={found.some(f => f.key === c) ? "default" : "secondary"}>{c}</Badge>
                  ))}
                </div>

                <h3 className="font-semibold flex items-center gap-2 mt-4"><Activity className="h-4 w-4"/> সাজেস্টেড আয়ুর্বেদিক অপশন (ডোজ নয়)</h3>
                {found.length === 0 ? (
                  <div className="text-sm text-stone-600 flex items-center gap-2"><CircleHelp className="h-4 w-4"/> মিল পাওয়া যায়নি। স্পষ্ট করে উপসর্গ লিখুন বা উপর থেকে একটি উদাহরণ বেছে নিন।</div>
                ) : (
                  <div className="grid grid-cols-1 md:grid-cols-2 gap-3">
                    {found.map(({ key, rule }) => (
                      <Card key={key} className="rounded-xl">
                        <CardHeader className="pb-2">
                          <CardTitle className="text-base">{key}</CardTitle>
                        </CardHeader>
                        <CardContent className="space-y-2 text-sm">
                          <div className="flex flex-wrap gap-1">{rule.tags.map((t) => (<Badge key={t} variant="outline">{t}</Badge>))}</div>
                          <ul className="list-disc ml-5">
                            {rule.options.map((opt) => (<li key={opt}>{opt}</li>))}
                          </ul>
                          {rule.caution && <div className="text-amber-700 text-xs">সতর্কতা: {rule.caution}</div>}
                          <div className="text-xs text-stone-500">নোট: এগুলি সাধারণত আলোচিত আয়ুর্বেদিক বিকল্প। ডোজ/প্রয়োগের আগে BAMS চিকিৎসকের পরামর্শ নিন।</div>
                        </CardContent>
                      </Card>
                    ))}
                  </div>
                )}
              </div>

              <div className="flex items-center justify-between pt-2">
                <Button onClick={() => setHistory((h) => [symptoms, ...h].slice(0, 10))} disabled={!symptoms}>
                  ফলাফল সেভ করুন
                </Button>
                <Button variant="ghost" onClick={() => { setSymptoms(""); setBodySystem(""); }}>রিসেট</Button>
              </div>
            </CardContent>
          </Card>

          {history.length > 0 && (
            <Card className="rounded-2xl">
              <CardHeader className="pb-2">
                <CardTitle className="text-lg flex items-center gap-2"><AlertTriangle className="h-5 w-5"/> সাম্প্রতিক সার্চ</CardTitle>
              </CardHeader>
              <CardContent className="space-y-2">
                {history.map((h, i) => (
                  <div key={i} className="text-sm text-stone-700 border-b last:border-none py-2">{h}</div>
                ))}
              </CardContent>
            </Card>
          )}

          <Card className="border-amber-300 bg-amber-50 rounded-2xl">
            <CardContent className="text-sm text-amber-900 p-4">
              ⚠️ <span className="font-semibold">ডিসক্লেইমার:</span> এই টুলটি স্বাস্থ্য-শিক্ষা উদ্দেশ্যে। এটি কোনও চিকিৎসা পরামর্শ বা রোগ নির্ণয় নয়। জরুরি অবস্থায় 112/108 এ ফোন করুন এবং নিকটস্থ হাসপাতাল/চিকিৎসকের সাথে যোগাযোগ করুন।
            </CardContent>
          </Card>
        </div>
      </motion.div>
    </div>
  );
}
                
