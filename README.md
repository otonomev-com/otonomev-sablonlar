# OtonomEv şablonları

[OtonomEv](https://otonomev.com/otomasyonlar/)'deki otomasyonların Home Assistant dosyaları. Her otomasyon
sitede kendi sayfasında anlatılır; oradaki "Home Assistant'ıma aktar" düğmesi buradaki şablonu açar.

| Klasör | İçinde ne var? |
| --- | --- |
| `blueprints/automation/otonomev/` | Şablonlar (blueprint). Home Assistant'a içe aktarılır; sen yalnızca cihazlarını seçersin. |
| `otomasyonlar/` | Aynı otomasyonların düz YAML hâli. Kendi varlık kimliklerini yazıp otomasyon düzenleyicisine yapıştırırsın. |
| `denetim/`, `.github/workflows/` | Otomatik denetim (aşağıda). Home Assistant'ına kurman gerekmez. |

Kurallar:

- Her otomasyon yayımlanmadan önce bir Home Assistant'ta kurulup denenir. Dosyanın başında en az hangi
  Home Assistant sürümünü istediği yazar (`min_version`).
- Yayımlanmış bir şablonun girdi adları değişmez; büyük bir değişiklik yeni bir şablon olur. Böylece şablonu
  önceden içe aktaranların otomasyonu bozulmaz.
- Dosyalardaki varlık kimlikleri (ör. `light.koridor`) örnektir; kendi evindekilerle değiştirmen gerekir.

## Denetim

Her değişiklikte ve haftada bir GitHub Actions iki denetim çalıştırır (`.github/workflows/denetim.yml`):

- YAML biçim denetimi (yamllint).
- Home Assistant yapılandırma denetimi: her şablon `denetim/configuration.yaml`'daki örnek girdilerle kurulur, düz
  otomasyonlar eklenir ve Home Assistant'ın kararlı ve beta sürümüyle denetlenir.

Haftalık denetim bozulursa depoda bir sorun (issue) açılır. Böylece yeni bir Home Assistant sürümü bir şablonu
bozarsa erkenden fark edilir. İş akışı anahtar kullanmaz ve salt okunur çalışır; yalnızca haftalık denetimin sorun
açma izni vardır.

## Lisans

MIT. Ayrıntı: [LICENSE](LICENSE).
