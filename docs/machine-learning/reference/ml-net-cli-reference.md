---
title: ML.NET CLI aracında otomatik train komutu
description: Genel bakış, örnekler ve ML.NET CLI aracında otomatik train komut başvurusu.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 28eb56eb018e3d1cc76f300ee78c298af77c9b91
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557936"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>ML.NET CLI 'train otomatik' komutu

> [!NOTE]
> ML.NET CLI ve ML.NET AutoML şu anda önizlemede olan bu konuda ifade eder ve malzeme değişiklik gösterebilir.

`auto-train` Komuttur ML.NET CLI aracı tarafından sağlanan ana komutu. Komut kaliteli ML.NET modeli (serileştirilmiş modeli .zip dosyası) örnek oluşturmanızı sağlar C# Çalıştır/puanı bu modeli için kod. Ayrıca, C# /bu modeli eğitme oluşturmak için kod da oluşturulur hangi algoritması ve ayarları için kullanılıyor "en iyi modeli" oluşturulan araştırmak için.

ML.NET bildiğiniz olsa bile, ayrıca üretkenliğinizi artıran şekilde kendiniz, kodlama olmadan, bu varlıkları kendi veri kümeleri oluşturabilirsiniz.

Şu anda, ML ML.NET CLI tarafından desteklenen görevler şunlardır:

- `binary-classification`
- `multiclass-classification`
- `regression`

- Gelecekteki: Diğer makine öğrenimi görevlerini, aşağıdaki gibi
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Komut isteminde kullanım örneği:

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` Komutu şu varlıkları oluşturur:

- Serileştirilmiş modeli .zip ("en iyi modeli") kullanıma hazır.
- C#kod, Çalıştır/puan modeli (Bu modeli ile son kullanıcı uygulamalarınızda Öngörüler oluşturmak için) oluşturulur.
- C#Bu model (öğrenme amacıyla) oluşturmak için kullanılan eğitim kod ile kod.

İlk iki varlıklar ile oluşturulan, ML model doğrudan, son kullanıcı uygulamaları (ASP.NET Core web uygulaması, hizmetleri, masaüstü uygulaması, vb.) tahminlerde bulunmak üzere kullanılabilir.

Üçüncü bir varlık, eğitim kod hangi ML.NET API kodu CLI tarafından hangi belirli trainer/algoritması araştırabilir ve parametrelerini hyper CLI ve ML.NET AutoML altyapısı tarafından seçilen oluşturulan modeli eğitmek için kullanılan gösterir.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>'Otomatik train' komut AutoML altyapısı kullanır.

CLI ML.NET AutoML altyapısı (NuGet paketi) en iyi kalite modelleri için akıllı bir şekilde aramak için aşağıdaki diyagramda gösterildiği gibi kullanır:

![Görüntü](./media/ml-net-automl-working-diagram.png "AutoML altyapısı ML.NET CLI içinde çalışma")

ML.NET CLI aracı ile çalışırken ' otomatik-train-komutu, birçok yineleme farklı algoritmalar ve yapılandırması bileşimleri ile çalışırken aracı görürsünüz.

## <a name="reference-for-auto-train-command"></a>'Otomatik train' komutu için başvuru

## <a name="examples"></a>Örnekler

(AutoML sağlanan veri yapılandırmasından çoğunu çıkarsamak gerekir) basit CLI komutunu ikili sınıflandırma sorunu için:

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Başka bir basit CLI komutunu regresyon problemi için:

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Oluşturma ve eğitme veri kümesi, test veri kümesini ve daha fazla özelleştirme açık bağımsız bir ikili sınıflandırma modeli eğitme:

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Ad

`mlnet auto-train` -Birden çok modeli eğitir ('n' yinelemeler) sağlanan bir veri kümesini temel alan ve son olarak en iyi modeli oluşturur ve bir seri hale getirilmiş bir .zip dosyası olarak ilgili kaydeder seçer C# Puanlama ve eğitim için kod.

## <a name="synopsis"></a>Synopsis

```console
> mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

Geçersiz giriş seçenekleri, geçerli girişler ve bu durumda, hangi arg eksik açıklayan bir hata iletisi listesini yaymak CLI aracını neden olmaz.

## <a name="options"></a>Seçenekler

 ----------------------------------------------------------

`--task | --mltask | -T` (dize)

ML sorunu çözmek için sağlama, tek bir dize. Örneğin, (içinde AutoML desteklenen tüm görevler CLI sonunda destekleyecek) aşağıdaki görevlerden herhangi birini:

- `regression` -Seçin ML Model sayısal bir değeri tahmin etmek için kullanılır
- `binary-classification` -ML Model sonucu olası iki kategorik Boole değeri (0 veya 1) olup olmadığını seçin.
- `multiclass-classification` -ML Model sonucu birden çok kategorik olası değerler olup olmadığını seçin.

Gelecekte ek ML görevler ve senaryolar gibi serbest `recommendations`, `clustering` ve `ranking` desteklenecektir.

 Bu bağımsız değişken yalnızca bir ML görev sağlanmalıdır.

 ----------------------------------------------------------

`--dataset | -d` (dize)

Bu bağımsız değişken, aşağıdaki seçeneklerden birini yolu sağlar:

- *Y: Tüm veri kümesi dosyası:* Bu seçenek ve kullanıcı kullanarak değil sağlıyorsa `--test-dataset` ve `--validation-dataset`, çapraz doğrulama (k Katlama, vb.) veya otomatik veri yaklaşımları bölme dahili olarak model doğrulamak için kullanılır. Bu durumda, kullanıcı yalnızca veri kümesi dosya yolunu sağlamanız gerekir.

- *B: Eğitim veri kümesi dosyası:* Kullanıcı veri kümeleri de model doğrulama için sağlayıp sağlamadığını (kullanarak `--test-dataset` ve isteğe bağlı olarak `--validation-dataset`), ardından `--dataset` bağımsız değişken anlamına gelir "eğitim veri kümesi" yalnızca sağlamak. Örneğin, model kalitesini doğrulamak ve doğruluk ölçümleri elde etmek için bir % 80-%20 yaklaşımı kullanarak, verilerin %80 "eğitim veri kümesi" olacaktır ve verilerin %20 "test veri" gerekir.

----------------------------------------------------------

`--test-dataset | -t` (dize)

Test veri kümesi dosyası, % 80-%20 yaklaşım doğruluğu ölçümleri elde etmek için normal doğrulamaları yaparken kullanırken örneğin işaret eden dosya yolu.

Kullanıyorsanız `--test-dataset`, ardından `--dataset` de gereklidir.

`--test-dataset` Bağımsız değişken isteğe bağlı sürece doğrulama veri kümesi kullanılır. Bu durumda, kullanıcı üç bağımsız değişken kullanmanız gerekir.

----------------------------------------------------------

`--validation-dataset | -v` (dize)

Doğrulama dataset dosyasına işaret eden dosya yolu. Doğrulama veri kümesi, her durumda, isteğe bağlı.

Kullanılıyorsa bir `validation dataset`, davranışı olmalıdır:

- `test-dataset` Ve `--dataset` bağımsız değişkenleri gereklidir de.

- `validation-dataset` Veri kümesi, model seçimi için tahmin hata tahmin etmek için kullanılır.

- `test-dataset` Modeli seçilen son Genelleştirme hata değerlendirmesi için kullanılır. İdeal olarak, test kümesi "kasada" tutulması gereken ve veri analizi yalnızca sonunda getirilmesi.

Temelde, kullanırken bir `validation dataset` artı `test dataset`, doğrulama aşamasını iki bölüme ayrılır:

1. İlk bölüm, yalnızca, model bakın ve en iyi performansa sahip (doğrulama =) doğrulama verileri kullanarak bir yaklaşım seçin
2. Ardından (test =) seçili yaklaşım doğruluğunu tahmin edin.

Bu nedenle, veri ayrımı 80/10/10 veya 75/15/10 olabilir. Örneğin:

- `training-dataset` Dosya, verilerin %75 olması gerekir.
- `validation-dataset` Dosya, verilerin %15 olması gerekir.
- `test-dataset` Dosya, verilerin %10 olması gerekir.

Herhangi bir durumda, söz konusu yüzdeleri dosyaya zaten bölme sağlayacak CLI kullanarak kullanıcı tarafından belirlenir.

----------------------------------------------------------

`--label-column-name | -n` (dize)

Bu bağımsız değişken kümesinin üstbilgisinde ayarlanan sütunun adını kullanarak belirli bir amaç/hedef sütun (tahmin etmek istediğiniz değişken) belirtilebilir.

Bu bağımsız değişken gibi yalnızca denetimli ML görevler için kullanılan bir *sınıflandırma problemi*. Bu gibi Denetimsiz ML görevler için kullanılamaz *Kümeleme*.

----------------------------------------------------------

`--label-column-index | -i` (int)

Bu bağımsız değişken kümesinin dosyasında (sütun dizini değerleri 1'den başlar) sütunun sayısal dizin kullanarak belirli bir amaç/hedef sütun (tahmin etmek istediğiniz değişken) belirtilebilir.

*Not:* Kullanıcı ayrıca kullanıyorsa `--label-column-name`, `--label-column-name` olduğu kullanılan bir.

Bu bağımsız değişken gibi yalnızca denetimli ML görev için kullanılan bir *sınıflandırma problemi*. Bu gibi Denetimsiz ML görevler için kullanılamaz *Kümeleme*.

----------------------------------------------------------

`--ignore-columns | -I` (dize)

Bu değişkeni, bu nedenle bunlar değil yüklendi ve eğitim işlemler tarafından kullanılan veri kümesi dosyası mevcut sütunlardaki yoksayabilirsiniz.

Yok saymak için istediğiniz sütun adlarını belirtin. Kullanım ',' (boşluk ile ayrılmış) veya ' ' (birden çok sütun adını ayırmak için alanı). Tırnak işaretleri (örn: "oturum açmış") boşluk içeren sütun adları için kullanabilirsiniz.

Örnek:

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h` (Boole)

Veri kümesi dosyaları bir üst bilgi satırı varsa belirtin.
Olası değerler şunlardır:
- `true`
- `false`

Varsayılan değerdir `true` kullanıcı tarafından bu bağımsız değişken belirtilmezse.

Kullanmak için `--label-column-name` bağımsız değişkeni, bir üst bilgi veri kümesi dosyasında olması gerekir ve `--has-header` kümesine `true` (varsayılan olarak olmayan).

----------------------------------------------------------

`--max-exploration-time | -x` (dize)

Varsayılan olarak, en fazla araştırma süre 10 saniyedir.

Bu bağımsız değişken birden çok eğitmenler ve yapılandırmalarını keşfetmek işlemi için en uzun süreyi (saniye cinsinden) ayarlar. Belirtilen saat (örneğin, 2 saniye) tek bir yineleme için çok kısa ise, yapılandırılan süre aşılmış olabilir. Bu durumda, gerçek bir model yapılandırmasında tek bir yineleme oluşturmak için gereken zamanı zamandır.

Yinelemeler için gereken zaman, veri kümesinin boyutuna bağlı olarak değişebilir.

----------------------------------------------------------

`--cache | -c` (dize)

Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellekteki yüklü olacaktır.

Küçük ve orta ölçekli veri kümeleri için önbellek kullanarak eğitim süresini önbellek zaman kullanmayın daha kısa olabilir yani eğitim performansını önemli ölçüde artırabilir.

Bellek yetersiz aldığından ancak, büyük veri kümeleri için bellekteki tüm verileri yüklenirken olumsuz yönde etkileyebilir. Ne zaman eğitim sırasında daha fazla veri yüklemek gerektiğinde eğitim büyük veri dosyalarını ve önbellek, ML.NET sürücüsünden veri öbekleri akış.

Aşağıdaki değerleri belirtebilirsiniz:

`on`: Eğitim yapılırken kullanılacak önbellek zorlar.
`off`: Eğitimindeki kullanılamaz önbellek zorlar.
`auto`: Önbellek veya AutoML buluşsal bağlı olarak kullanılır. Genellikle, küçük/Orta veri kümeleri önbelleğini kullanır ve büyük veri kümeleri, önbellek kullanmayacağınız, kullanırsanız `auto` seçim.

Belirtmezseniz `--cache` parametresi, ardından da önbelleğe `auto` yapılandırma varsayılan olarak kullanılır.

----------------------------------------------------------

`--name | -N` (dize)

Oluşturulan çıktı proje veya çözüm adı. Hiçbir ad belirtilmediği takdirde, ad `sample-{mltask}` kullanılır.

ML.NET model dosyası (. ZIP dosyası), aynı adı da alırsınız.

----------------------------------------------------------

`--output-path | -o` (dize)

Kök konumu/oluşturulan çıktı yerleştirileceği klasör. Geçerli dizin varsayılandır.

----------------------------------------------------------

`--verbosity | -V` (dize)

Standart çıkış ayrıntı düzeyini ayarlar.

İzin verilen değerler şunlardır:

- `q[uiet]`
- `m[inimal]`  (varsayılan)
- `diag[nostic]` (günlük bilgi düzeyi)

Varsayılan olarak CLI aracı en az birkaç geri bildirim (minimum) çalışırken, çalışıyor ve eğer mümkünse ne kadar süre sol hangi % sürede tamamlandı mı bahseden gibi göstermelidir.

----------------------------------------------------------

`-h|--help`

Komut için Yardım her komutun parametresi için bir açıklama ile yazdırır.

----------------------------------------------------------

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLI Aracı'nı yükleme](../how-to-guides/install-ml-net-cli.md)
- [Model eğitiminin ML.NET CLI ile otomatikleştirme](../automate-training-with-cli.md)
- [Öğretici: ML.NET CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur](../tutorials/mlnet-cli.md)
- [ML.NET CLI'de telemetri](../resources/ml-net-cli-telemetry.md)
