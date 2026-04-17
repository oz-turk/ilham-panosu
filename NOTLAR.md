# İlham Panosu — Kurulum Notları

## Scheduled Agent

- **Trigger ID:** `trig_01JFNsz9Tg15Dac9dM9KJGq8`
- **Yönetim:** https://claude.ai/code/scheduled/trig_01JFNsz9Tg15Dac9dM9KJGq8
- **Tüm triggerlar:** https://claude.ai/code/scheduled
- **Saat:** Her gün 07:00 İstanbul (UTC 04:00)
- **Repo:** https://github.com/ezatenburak/ilham-panosu

## Agent Prompt'u

```
Günlük ilham bülteni oluştur ve GitHub'a push et.

1. Çalışma dizinini kontrol et (pwd, ls).
2. `kullanilan.md` dosyasını oku — bu listedeki şiir ve kavramları tekrar kullanma.
3. Bugünün tarihini al (YYYY-MM-DD formatı, Türkçe ay örn: 17 Nisan 2026).
4. `ilham-panosu-YYYY-MM-DD.md` oluştur, 6 bölümü doldur.
5. `kullanilan.md` ve `index.md` dosyalarını güncelle.
6. git add / commit / push.

## Bülten Bölümleri

### Günün Şiiri
WebSearch ile "[seçtiğin şairin adı] [seçtiğin şiir başlığı] tam metin" ara. İlk sonuçtan metni kopyala, kaynak URL ekle.
EZBERDEN YAZMA. Kaynak bulunamazsa: "Bugün şiir kaynağı bulunamadı."
Format: Başlık / Yazar / Yıl · şiir metni · tahlil (2-3 cümle) · Kaynak: URL

### Günün 3D Kavramı
Teknik kavram (voronoi, SDF, L-system, NURBS, PBR, ray marching vb.) — Blender/Houdini/Grasshopper bağlamıyla 3-4 cümle. Teknik bilgi kullanılabilir, WebSearch şart değil.

### Mimarlık Makalesi
WebSearch: güncel mimarlık makalesi — ilk gerçek URL + 2 paragraf Türkçe özet.
Bulamazsan: "Bugün kaynak bulunamadı."

### 3D Dünyasından
WebSearch: Blender/Houdini/Rhino güncel haber — ilk gerçek URL + kısa paragraf.
Bulamazsan: "Bugün kaynak bulunamadı."

### Günün Görseli
WikiArt veya müze sitesinde gerçekten var olan eser seç, linki doğrula.
Format: Eser / Sanatçı / Yıl / Teknik · analiz · Link

### Sanat Dünyasından
WebSearch: güncel sanat makalesi — ilk gerçek URL + Türkçe özet.
Bulamazsan: "Bugün kaynak bulunamadı."

## kullanilan.md Güncelleme
Dosyanın sonuna ekle:
- Şiirler: [Yazar — Başlık (YYYY-MM-DD)]
- 3D Kavramlar: [Kavram (YYYY-MM-DD)]

## index.md Güncelleme
`## Sayılar` bölümüne EN ÜSTE ekle:
- [DD Ay YYYY](ilham-panosu-YYYY-MM-DD)

## Git
git add ilham-panosu-YYYY-MM-DD.md kullanilan.md index.md
git commit -m "feat: ilham panosu — YYYY-MM-DD"
git push origin main

## Kurallar
- Tüm içerik Türkçe
- Her WebSearch sorgusunda yalnızca ilk geçerli sonucu kullan
- Kaynak yoksa uydurma
```

## Model
`claude-haiku-4-5-20251001`

## Optimize Günlük Prompt (elle kullanım için)

Claude Code veya claude.ai'da kendin çalıştırmak istersen:

```
Günlük İlham Bülteni — {TARİH}. Türkçe yaz.

1. **Şiir** — Modern Türk şiiri. Başlık / Yazar / Yıl + şiir metni + 2-3 cümle tahlil.
2. **3D Kavram** — Bir teknik modelleme kavramı (voronoi, marching cubes, L-system vb.).
   3-4 cümle açıklama, Blender/Houdini/Grasshopper bağlamıyla.
3. **Mimarlık Makalesi** — Güncel makale + kaynak linki + 2 paragraf özet.
4. **3D Dünya** — Rhino/Grasshopper, Blender veya Houdini'den kısa güncel gelişme.
5. **Görsel** — Bir sanat eseri: ad, sanatçı, yıl, teknik + kısa analiz + WikiArt/müze linki.
6. **Sanat Makalesi** — Modern/çağdaş sanat makalesi + link + özet.
```

## Notlar

- Trigger silinirse https://claude.ai/code/scheduled adresinden yenisi oluşturulabilir.
- Agent push edemezse repo ayarlarını kontrol et; GitHub OAuth bağlantısı
  https://claude.ai/settings/connectors üzerinden yönetilir.
- Yerel repoya çekmek için: `git pull` (ilham-panosu-repo klasöründen)
- Dosyalar `ilham-panosu-YYYY-MM-DD.md` formatında isimlendiriliyor.
