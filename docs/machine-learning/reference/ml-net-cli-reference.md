---
title: ML.NET CLı komut başvurusu
description: ML.NET CLı aracında otomatik eğitme komutuna genel bakış, örnekler ve başvuru.
ms.date: 12/18/2019
ms.openlocfilehash: 537f8d361c170378f5fe8cf454320831d7c8cbf2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449705"
---
# <a name="the-mlnet-cli-command-reference"></a>ML.NET CLı komut başvurusu

`auto-train` komutu, ML.NET CLı aracı tarafından sunulan ana komuttur. Komut otomatik makine öğrenimi (Otomatikml) kullanarak iyi bir kalite ML.NET modeli oluşturmanıza ve bu modeli çalıştırmak/skor yapmak için C# örnek kodu oluşturmanızı sağlar. Ayrıca, modelin eğiteme C# kodu, modelin algoritmasını ve ayarlarını araştırmanız için oluşturulur.

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.

## <a name="overview"></a>Genel Bakış

Örnek kullanım:

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` komutu aşağıdaki varlıkları üretir:

- Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.
- C#oluşturulan modeli çalıştırmak/skor kodu.
- C#Bu modeli oluşturmak için kullanılan eğitim koduna sahip kod.

İlk iki varlık, model ile tahmine dayalı hale getirmek için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması ve daha fazlası) doğrudan kullanılabilir.

Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece modelin belirli algoritmasını ve ayarlarını araştırabilirsiniz.

## <a name="examples"></a>Örnekler

İkili sınıflandırma sorunu için en basit CLı komutu (Oto ml, belirtilen verilerden çoğu yapılandırmanın çoğunu):

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Gerileme sorunu için başka bir basit CLı komutu:

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Bir tren veri kümesiyle, test veri kümesiyle ve daha fazla özelleştirme açık bağımsız değişkenlerle bir ikili sınıflandırma modeli oluşturun ve eğitme:

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Komut seçenekleri

`mlnet auto-train`, belirtilen veri kümesine bağlı olarak birden çok model ve son olarak en iyi modeli seçer, bunu serileştirilmiş bir. zip dosyası olarak kaydeder ve Puanlama C# ve eğitim için ilgili kodu oluşturur.

```console
mlnet auto-train

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

Geçersiz giriş seçenekleri, CLı aracının geçerli girişlerin bir listesini ve bir hata iletisini yaymasına neden olur.

## <a name="task"></a>Görev

`--task | --mltask | -T` (dize)

Çözülecek ML sorununu sağlayan tek bir dize. Örneğin, aşağıdaki görevlerden herhangi biri (CLı, sonunda, her zaman oto ml 'de desteklenen tüm görevleri destekleyecektir):

- `regression`-bir sayısal değeri tahmin etmek için ML modelinin kullanılacağını seçin
- `binary-classification`-ML modeli sonucunun iki olası kategorik Boole değeri (0 veya 1) olup olmadığını seçin.
- `multiclass-classification`-ML modeli sonucunda birden çok kategorik olası değer olup olmadığını seçin.

Bu bağımsız değişkende yalnızca bir ML görevi sağlanmalıdır.

## <a name="dataset"></a>Veri kümesi

`--dataset | -d` (dize)

Bu bağımsız değişken, FilePath öğesini aşağıdaki seçeneklerden birine sağlar:

- Y *: tüm veri kümesi dosyası:* Bu seçenek kullanılıyorsa ve Kullanıcı `--test-dataset` ve `--validation-dataset`sağlamadıysanız, modelin doğrulanması için çapraz doğrulama (k-katlama, vb.) veya otomatik veri bölünmüş yaklaşımlar dahili olarak kullanılır. Bu durumda, kullanıcının DataSet FilePath 'i sağlaması yeterlidir.

- *B: eğitim veri kümesi dosyası:* Kullanıcı ayrıca model doğrulaması için (`--test-dataset` kullanarak ve isteğe bağlı `--validation-dataset`) veri kümeleri sağladıysanız `--dataset` bağımsız değişkeni yalnızca "eğitim veri kümesi" olması anlamına gelir. Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümlerini elde etmek için %80-%20 yaklaşımını kullanırken, "eğitim veri kümesi" verilerin %80 ' sini alacak ve "test veri kümesi" verilerin %20 ' sini alacak.

## <a name="test-dataset"></a>Test veri kümesi

`--test-dataset | -t` (dize)

Test veri kümesi dosyasına işaret eden dosya yolu; Örneğin, doğruluk ölçümlerini elde etmek için düzenli doğrulamalar yaparken %80-%20 yaklaşım kullanma.

`--test-dataset`kullanıyorsanız, `--dataset` de gereklidir.

--Validation-DataSet kullanılmadığı müddetçe `--test-dataset` bağımsız değişkeni isteğe bağlıdır. Bu durumda, kullanıcının üç bağımsız değişkenini kullanması gerekir.

## <a name="validation-dataset"></a>Doğrulama veri kümesi

`--validation-dataset | -v` (dize)

Doğrulama veri kümesi dosyasına işaret eden dosya yolu. Doğrulama veri kümesi, her durumda isteğe bağlıdır.

`validation dataset`kullanılıyorsa, davranış şu şekilde olmalıdır:

- `test-dataset` ve `--dataset` bağımsız değişkenleri de gereklidir.

- `validation-dataset` veri kümesi, model seçiminde tahmin hatasını tahmin etmek için kullanılır.

- `test-dataset`, son seçilen modeldeki Genelleştirme hatası değerlendirmesi için kullanılır. İdeal olarak, test kümesinin bir "kasa" içinde tutulması ve yalnızca veri analizinin sonunda getirilmesi gerekir.

Temel olarak, bir `validation dataset` ve `test dataset`kullanılırken, doğrulama aşaması iki parçaya bölünür:

1. İlk bölümde, modellerinize göz atadınız ve doğrulama verilerini kullanarak en iyi şekilde gerçekleştirdiğiniz yaklaşımı seçersiniz (= doğrulama)
2. Ardından seçili yaklaşımın doğruluğunu tahmin edersiniz (= test).

Bu nedenle, verilerin ayrımı 80/10/10 veya 75/15/10 olabilir. Örnek:

- `training-dataset` dosya verilerin %75 ' i olmalıdır.
- `validation-dataset` dosya verilerin %15 ' i olmalıdır.
- `test-dataset` dosya verilerin %10 ' a sahip olmalıdır.

Herhangi bir durumda, bu yüzdeleri Kullanıcı tarafından zaten bölünmüş dosyaları sağlayacak CLı kullanarak kararlanacaktır.

## <a name="label-column-name"></a>Etiket sütun adı

`--label-column-name | -n` (dize)

Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üst bilgisinde ayarlanan sütunun adı kullanılarak belirtilebilir.

Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevleri için kullanılır. *Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.

## <a name="label-column-index"></a>Etiket sütun dizini

`--label-column-index | -i` (int)

Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin dosyasındaki sayısal dizin kullanılarak belirtilebilir (sütun dizini değerleri 1 ' den başlar).

*Note:* Kullanıcı `--label-column-name`de kullanıyorsa, `--label-column-name` kullanılan bir.

Bu bağımsız değişken yalnızca bir *Sınıflandırma sorunu*gıbı denetimli ml görevi için kullanılır. *Kümeleme*gıbı denetimli ml görevleri için kullanılamaz.

## <a name="ignore-columns"></a>Sütunları yoksay

`--ignore-columns | -I` (dize)

Bu bağımsız değişkenle, veri kümesi dosyasında var olan sütunları yoksayabilirsiniz ve bu sayede eğitim işlemleriyle birlikte kullanılmaz.

Yoksaymak istediğiniz sütun adlarını belirtin. Birden çok sütun adını ayırmak için ', ' (boşluk ile virgül) veya ' ' (boşluk) kullanın. Boşluk içeren sütun adları için tırnak işareti kullanabilirsiniz (örneğin, "oturum açmış").

Örnek:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Üst bilgisi vardır

`--has-header | -h` (bool)

Veri kümesi dosyalarının bir üst bilgi satırına sahip olup olmadığını belirtin.
Olası değerler şunlardır:

- `true`
- `false`

Bu bağımsız değişken Kullanıcı tarafından belirtilmemişse, varsayılan değer olarak `true`.

`--label-column-name` bağımsız değişkenini kullanmak için, veri kümesi dosyasında bir üst bilgiye sahip olmanız ve `--has-header` `true` (varsayılan olarak) olarak ayarlamanız gerekir.

## <a name="max-exploration-time"></a>En fazla araştırma süresi

`--max-exploration-time | -x` (dize)

Varsayılan olarak, en fazla araştırma süresi 30 dakikadır.

Bu bağımsız değişken, birden fazla taş ve yapılandırmayı araştırmak için işlem için en uzun süreyi (saniye cinsinden) ayarlar. Belirtilen süre çok kısaysa (2 saniye), tek bir yineleme için yapılandırılan saat kesilebilir. Bu durumda, gerçek süre, tek bir yinelemede tek bir model yapılandırması üretmek için gereken süredir.

Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak farklılık gösterebilir.

## <a name="cache"></a>Önbellek

`--cache | -c` (dize)

Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellek içinde yüklenir.

Küçük ve orta ölçekli veri kümelerinde, önbelleğin kullanılması eğitim performansını önemli ölçüde iyileştirebilir, bu da eğitim süresi önbelleği kullanmadığınız zamandan daha kısa olabilir.

Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellek yetersiz olduğundan olumsuz etkileyebilir. Büyük veri kümesi dosyalarıyla eğitim yaparken ve önbellek kullanmayan ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüdeki veri öbeklerini akışa alabilir.

Aşağıdaki değerleri belirtebilirsiniz:

`on`: eğitim sırasında önbelleğin kullanılmasına zorlar.
`off`: eğitim sırasında önbelleğin kullanılmamaya zorlar.
`auto`:, oto ml buluşsal lerine bağlı olarak, önbellek kullanılır veya değildir. Genellikle, küçük/orta veri kümeleri önbelleği kullanır ve büyük veri kümeleri `auto` seçeneğini kullanırsanız önbelleği kullanmaz.

`--cache` parametresini belirtmezseniz, varsayılan olarak önbellek `auto` yapılandırması kullanılacaktır.

## <a name="name"></a>Adı

`--name | -N` (dize)

Oluşturulan çıkış projesinin veya çözümünün adı. Ad belirtilmemişse, `sample-{mltask}` adı kullanılır.

ML.NET model dosyası (. ZIP dosyası) de aynı adı alır.

## <a name="output-path"></a>Çıkış yolu

`--output-path | -o` (dize)

Oluşturulan çıkışın yerleştirileceği kök konumu/klasörü. Geçerli dizin varsayılandır.

## <a name="verbosity"></a>Ayrıntı Düzeyi

`--verbosity | -V` (dize)

Standart çıkışın ayrıntı düzeyini ayarlar.

İzin verilen değerler şunlardır:

- `q[uiet]`
- `m[inimal]` (varsayılan olarak)
- `diag[nostic]` (günlüğe kaydetme bilgileri düzeyi)

Varsayılan olarak, CLı aracı çalışırken, çalıştığı ve ne kadar süre kaldığını ya da zamanın ne kadar tamamlandığını belirten en düşük geri bildirimleri (en az) göstermelidir.

## <a name="help"></a>Yardım

`-h|--help`

Komut için, her komutun parametresi için bir açıklama içeren yardımı yazdırır.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı aracını yüklemek](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLı 'ye Genel Bakış](../automate-training-with-cli.md)
- [Öğretici: ML.NET CLı kullanarak yaklaşımı çözümleme](../tutorials/sentiment-analysis-cli.md)
- [ML.NET CLı 'de telemetri](../resources/ml-net-cli-telemetry.md)
