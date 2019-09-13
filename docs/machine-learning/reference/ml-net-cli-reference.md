---
title: ML.NET CLı aracında otomatik eğitme komutu
description: ML.NET CLı aracında otomatik eğitme komutuna genel bakış, örnekler ve başvuru.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929195"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>ML.NET CLı içindeki ' Auto-eğitme ' komutu

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.

`auto-train` Komut, ml.net CLI aracı tarafından sunulan ana komuttur. Komutu iyi bir Quality ML.NET modeli (serileştirilmiş model. zip dosyası) ve bu modeli çalıştırmak/skor için örnek C# kodu oluşturmanızı sağlar. Ayrıca, bu model C# oluşturma/eğitme kodu, oluşturulan "en iyi model" için hangi algoritmaların ve hangi ayarların kullandığını araştırmak için de oluşturulur.

Kendi veri kümelerinizde, sizin tarafınızdan kodlamadan bu varlıkları oluşturabilirsiniz. bu sayede, ML.NET zaten tanıyor olsanız bile üretkenliğinizi de artırır.

Şu anda, ML.NET CLı tarafından desteklenen ML görevleri şunlardır:

- `binary-classification`
- `multiclass-classification`
- `regression`

- Yayımlanacak Gibi diğer makine öğrenimi görevleri
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Komut isteminde kullanım örneği:

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` Komut aşağıdaki varlıkları oluşturur:

- Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.
- C#oluşturulan model (bu modelle Son Kullanıcı uygulamalarınızda tahmine dayalı hale getirmek Için) çalıştırılacak/puan veren kod.
- C#Bu modeli oluşturmak için kullanılan eğitim koduna sahip kod (öğrenme amaçları).

İlk iki varlık, bu oluşturulmuş ML modeliyle tahminler yapmak için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.

Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. bu sayede, CLı ve ML.NET oto altyapısı tarafından hangi özel oran/algoritma ve Hyper-parametrelerinin seçili olduğunu araştırabilirsiniz.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>' Auto-eğitme ' komutu otomatik ml altyapısını kullanır

CLı, aşağıdaki diyagramda gösterildiği gibi en iyi kalite modellerini bulmak için ML.NET oto ml altyapısını (NuGet paketi) kullanır:

![görüntü](./media/ml-net-automl-working-diagram.png "Ml.net CLI içinde çalışan oto ml altyapısı")

' Auto-tren-komutuyla ML.NET CLı aracını çalıştırırken, farklı algoritmalara ve yapılandırma birleşimlerine sahip çok sayıda yineleme gerçekleştirmeye çalışan aracı görürsünüz.

## <a name="reference-for-auto-train-command"></a>' Auto-eğitme ' komutu başvurusu

## <a name="examples"></a>Örnekler

İkili sınıflandırma sorunu için en basit CLı komutu (Oto ml 'nin, bu yapılandırmanın çoğunu belirtilen verilerden çıkarması gerekir):

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Gerileme sorunu için başka bir basit CLı komutu:

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Bir tren veri kümesiyle, test veri kümesiyle ve daha fazla özelleştirme açık bağımsız değişkenlerle bir ikili sınıflandırma modeli oluşturun ve eğitme:

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Ad

`mlnet auto-train`-Belirtilen veri kümesine bağlı olarak birden çok model (' n ' yineleme) yapın ve son olarak en iyi modeli seçer, onu serileştirilmiş bir. zip dosyası olarak kaydeder ve ayrıca C# Puanlama ve eğitim için ilgili kodu oluşturur.

## <a name="synopsis"></a>Özeti

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

Geçersiz giriş seçenekleri, CLı aracının geçerli girişlerin bir listesini ve bu durumda söz konusu bağımsız değişken 'in eksik olduğunu açıklayan bir hata iletisini yaymasına neden olur.

## <a name="options"></a>Seçenekler

 ----------------------------------------------------------

`--task | --mltask | -T`dizisinde

Çözülecek ML sorununu sağlayan tek bir dize. Örneğin, aşağıdaki görevlerden herhangi biri (CLı, sonunda, her zaman oto ml 'de desteklenen tüm görevleri destekleyecektir):

- `regression`-Bir sayısal değeri tahmin etmek için ML modelinin kullanılacağını seçin
- `binary-classification`-ML modelinde sonucun iki olası kategorik Boole değeri (0 veya 1) olup olmadığını seçin.
- `multiclass-classification`-ML modeli sonucunun birden çok kategorik olası değeri olup olmadığını seçin.

Gelecekte `recommendations` `ranking` , `clustering` gibi ek ml görevleri ve senaryoları yayınlar ve desteklenecektir.

 Bu bağımsız değişkende yalnızca bir ML görevi sağlanmalıdır.

 ----------------------------------------------------------

`--dataset | -d`dizisinde

Bu bağımsız değişken, FilePath öğesini aşağıdaki seçeneklerden birine sağlar:

- *A Tüm veri kümesi dosyası:* Bu seçenek kullanılıyorsa ve Kullanıcı ve `--test-dataset` `--validation-dataset`sağlamadıysanız çapraz doğrulama (k-katlama, vb.) veya otomatik veri bölme yaklaşımları, modeli doğrulamak için dahili olarak kullanılır. Bu durumda, kullanıcının DataSet FilePath 'i sağlaması yeterlidir.

- *KENARI Eğitim veri kümesi dosyası:* Kullanıcı ayrıca model doğrulaması için ( `--test-dataset` ve isteğe bağlı olarak `--validation-dataset`) veri kümeleri sağladıysanız, `--dataset` bağımsız değişken yalnızca "eğitim veri kümesi" olması anlamına gelir. Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümlerini elde etmek için% 80-% 20 yaklaşımını kullanırken, "eğitim veri kümesi" verilerin% 80 ' sini alacak ve "test veri kümesi" verilerin% 20 ' sini alacak.

----------------------------------------------------------

`--test-dataset | -t`dizisinde

Test veri kümesi dosyasına işaret eden dosya yolu; Örneğin, doğruluk ölçümlerini elde etmek için düzenli doğrulamalar yaparken% 80-% 20 yaklaşım kullanma.

`--test-dataset` Kullanılıyorsa`--dataset` , de gereklidir.

--Validation-DataSet kullanılmadığı müddetçe bağımsızdeğişkenisteğebağlıdır.`--test-dataset` Bu durumda, kullanıcının üç bağımsız değişkenini kullanması gerekir.

----------------------------------------------------------

`--validation-dataset | -v`dizisinde

Doğrulama veri kümesi dosyasına işaret eden dosya yolu. Doğrulama veri kümesi, her durumda isteğe bağlıdır.

Bir `validation dataset`kullanıyorsanız, davranış şu şekilde olmalıdır:

- `test-dataset` Ve`--dataset` bağımsız değişkenleri de gereklidir.

- Veri `validation-dataset` kümesi, model seçimine yönelik tahmin hatasını tahmin etmek için kullanılır.

- , `test-dataset` Seçili son modeldeki Genelleştirme hatası değerlendirmesi için kullanılır. İdeal olarak, test kümesinin bir "kasa" içinde tutulması ve yalnızca veri analizinin sonunda getirilmesi gerekir.

Temel olarak, bir `validation dataset` `test dataset`artı kullandığınızda, doğrulama aşaması iki parçaya ayrılır:

1. İlk bölümde, modellerinize göz atadınız ve doğrulama verilerini kullanarak en iyi şekilde gerçekleştirdiğiniz yaklaşımı seçersiniz (= doğrulama)
2. Ardından seçili yaklaşımın doğruluğunu tahmin edersiniz (= test).

Bu nedenle, verilerin ayrımı 80/10/10 veya 75/15/10 olabilir. Örneğin:

- `training-dataset`Dosya, verilerin% 75 ' i olmalıdır.
- `validation-dataset`Dosya, verilerin% 15 ' i olmalıdır.
- `test-dataset`Dosya, verilerin% 10 ' a sahip olmalıdır.

Herhangi bir durumda, bu yüzdeleri Kullanıcı tarafından zaten bölünmüş dosyaları sağlayacak CLı kullanarak kararlanacaktır.

----------------------------------------------------------

`--label-column-name | -n`dizisinde

Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üst bilgisinde ayarlanan sütunun adı kullanılarak belirtilebilir.

Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevleri için kullanılır. *Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.

----------------------------------------------------------

`--label-column-index | -i`'tir

Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin dosyasındaki sayısal dizin kullanılarak belirtilebilir (sütun dizini değerleri 1 ' den başlar).

*Not:* Kullanıcı da kullanıyorsa `--label-column-name` `--label-column-name` , kullanılmakta olan olur.

Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevi için kullanılır. *Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.

----------------------------------------------------------

`--ignore-columns | -I`dizisinde

Bu bağımsız değişkenle, veri kümesi dosyasında var olan sütunları yoksayabilirsiniz ve bu sayede eğitim işlemleriyle birlikte kullanılmaz.

Yoksaymak istediğiniz sütun adlarını belirtin. Birden çok sütun adını ayırmak için ', ' (boşluk ile virgül) veya ' ' (boşluk) kullanın. Boşluk içeren sütun adları için tırnak işareti kullanabilirsiniz (örneğin, "oturum açmış").

Örnek:

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h`bool

Veri kümesi dosyalarının bir üst bilgi satırına sahip olup olmadığını belirtin.
Olası değerler şunlardır:

- `true`
- `false`

Bu bağımsız değişken Kullanıcı tarafından `true` belirtilmemişse, varsayılan olarak değeri.

`--label-column-name` Bağımsız değişkenini kullanmak için, veri kümesi dosyasında bir üst bilgiye sahip olmanız ve `--has-header` (varsayılan olarak) olarak `true` ayarlamanız gerekir.

----------------------------------------------------------

`--max-exploration-time | -x`dizisinde

Varsayılan olarak, en fazla araştırma süresi 30 dakikadır.

Bu bağımsız değişken, birden fazla taş ve yapılandırmayı araştırmak için işlem için en uzun süreyi (saniye cinsinden) ayarlar. Belirtilen süre çok kısaysa (2 saniye), tek bir yineleme için yapılandırılan saat kesilebilir. Bu durumda, gerçek süre, tek bir yinelemede tek bir model yapılandırması üretmek için gereken süredir.

Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak farklılık gösterebilir.

----------------------------------------------------------

`--cache | -c`dizisinde

Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellek içinde yüklenir.

Küçük ve orta ölçekli veri kümelerinde, önbelleğin kullanılması eğitim performansını önemli ölçüde iyileştirebilir, bu da eğitim süresi önbelleği kullanmadığınız zamandan daha kısa olabilir.

Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellek yetersiz olduğundan olumsuz etkileyebilir. Büyük veri kümesi dosyalarıyla eğitim yaparken ve önbellek kullanmayan ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüdeki veri öbeklerini akışa alabilir.

Aşağıdaki değerleri belirtebilirsiniz:

`on`: Eğitim sırasında önbelleğin kullanılmasına zorlar.
`off`: Eğitim sırasında önbelleğin kullanılmamaya zorlar.
`auto`: Oto ml buluşsal türüne bağlı olarak, önbellek kullanılır veya değildir. Genellikle, küçük/orta veri kümeleri önbelleği kullanır ve büyük veri kümeleri `auto` seçeneği kullanırsanız önbelleği kullanmaz.

`--cache` Parametresini belirtmezseniz, varsayılan olarak önbellek `auto` yapılandırması kullanılacaktır.

----------------------------------------------------------

`--name | -N`dizisinde

Oluşturulan çıkış projesinin veya çözümünün adı. Ad belirtilmemişse, ad `sample-{mltask}` kullanılır.

ML.NET model dosyası (. ZIP dosyası) de aynı adı alır.

----------------------------------------------------------

`--output-path | -o`dizisinde

Oluşturulan çıkışın yerleştirileceği kök konumu/klasörü. Geçerli dizin varsayılandır.

----------------------------------------------------------

`--verbosity | -V`dizisinde

Standart çıkışın ayrıntı düzeyini ayarlar.

İzin verilen değerler şunlardır:

- `q[uiet]`
- `m[inimal]`(varsayılan olarak)
- `diag[nostic]`(günlük bilgisi düzeyi)

Varsayılan olarak, CLı aracı çalışırken, çalıştığı ve ne kadar süre kaldığını ya da zamanın ne kadar tamamlandığını belirten en düşük geri bildirimleri (en az) göstermelidir.

----------------------------------------------------------

`-h|--help`

Komut için, her komutun parametresi için bir açıklama içeren yardımı yazdırır.

----------------------------------------------------------

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı aracını yüklemek](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLı ile model eğitimi otomatikleştirin](../automate-training-with-cli.md)
- [Öğretici: ML.NET CLı kullanarak ikili bir sınıflandırıcı otomatik oluşturma](../tutorials/mlnet-cli.md)
- [ML.NET CLı 'de telemetri](../resources/ml-net-cli-telemetry.md)
