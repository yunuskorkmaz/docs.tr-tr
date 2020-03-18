---
title: ML.NET CLI Komut Başvurusu
description: ML.NET CLI aracındaki otomatik tren komutu için genel bakış, örnekler ve başvuru.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848931"
---
# <a name="the-mlnet-cli-command-reference"></a>cli komut başvurusu ML.NET

Komut, `auto-train` cli aracının ML.NET tarafından sağlanan ana komutdur. Komut, otomatik makine öğrenimi (AutoML) yanı sıra bu modeli çalıştırmak / puan için örnek C# kodu kullanarak iyi bir kaliteli ML.NET modeli oluşturmanıza olanak sağlar. Buna ek olarak, modeli eğitmek için C# kodu, modelin algoritmasını ve ayarlarını araştırmanız için oluşturulur.

> [!NOTE]
> Bu konu, şu anda Önizleme'de olan cli ve ML.NET AutoML'ML.NET anlamına gelir ve malzeme değişebilir.

## <a name="overview"></a>Genel Bakış

Örnek kullanım: 

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

Komut `mlnet auto-train` aşağıdaki varlıkları oluşturur:

- Serileştirilmiş bir model .zip ("en iyi model") kullanıma hazır.
- C# kodu modeli oluşturulan çalıştırmak / puan.
- Bu modeli oluşturmak için kullanılan eğitim kodu ile C# kodu.

İlk iki varlık, modelle ilgili öngörülerde bulunmak için doğrudan son kullanıcı uygulamalarınızda (ASP.NET Core web uygulaması, hizmetler, masaüstü uygulaması ve daha fazlası) kullanılabilir.

Üçüncü varlık, eğitim kodu, oluşturulan modeli eğitmek için CLI tarafından ML.NET API kodunun ne ML.NET kullanıldığını gösterir, böylece modelin belirli algoritmasını ve ayarlarını inceleyebilirsiniz.

## <a name="examples"></a>Örnekler

İkili sınıflandırma sorunu için en basit CLI komutu (AutoML, sağlanan verilerden yapılandırmanın çoğunu çıkartır):

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Bir gerileme sorunu için başka bir basit CLI komutu:

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Bir tren veri kümesi, test veri kümesi ve daha fazla özelleştirme açık bağımsız değişkenleri ile bir ikili sınıflandırma modeli oluşturun ve train:

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Komut seçenekleri

`mlnet auto-train`sağlanan veri kümesine göre birden çok modeli eğitir ve son olarak en iyi modeli seçer, serileştirilmiş .zip dosyası olarak kaydeder artı puanlama ve eğitim için ilgili C# kodu oluşturur.

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

Geçersiz giriş seçenekleri, CLI aracının geçerli girdilerin ve bir hata iletisinin listesini yarayabmasını neden olur.

## <a name="task"></a>Görev

`--task | --mltask | -T`(dize)

Ml sorunu çözmek için sağlayan tek bir dize. Örneğin, aşağıdaki görevlerden herhangi biri (CLI sonunda AutoML'de desteklenen tüm görevleri destekler):

- `regression`- ML Modeli'nin sayısal bir değeri tahmin etmek için kullanIlip kullanılmeyeceğini seçin
- `binary-classification`- ML Model sonucunun iki olası kategorik boolean değeri (0 veya 1) olup olmadığını seçin.
- `multiclass-classification`- ML Model sonucunun birden çok kategorik olası değeri olup olmadığını seçin.

Bu bağımsız değişkende yalnızca bir ML görevi sağlanmalıdır.

## <a name="dataset"></a>Veri kümesi

`--dataset | -d`(dize)

Bu bağımsız değişken, aşağıdaki seçeneklerden birine dosya yolunu sağlar:

- *C: Tüm veri kümesi dosyası:* Bu seçeneği kullanarak ve kullanıcı `--test-dataset` sağmıyorsa `--validation-dataset`ve sonra çapraz doğrulama (k-fold, vb) veya otomatik veri bölme yaklaşımları modeli doğrulamak için dahili olarak kullanılacaktır. Bu durumda, kullanıcının yalnızca veri kümesi dosya yolunu sağlaması gerekir.

- *B: Eğitim veri seti dosyası:* Kullanıcı ayrıca model doğrulama (kullanarak `--test-dataset` ve isteğe bağlı `--validation-dataset`olarak) `--dataset` için veri kümeleri sağlıyorsa, bağımsız değişken yalnızca "eğitim veri kümesine" sahip olmak anlamına gelir. Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümleri elde etmek için %80 - %20'lik bir yaklaşım kullanırken, "eğitim veri kümesi" verilerin %80'ine ve "test veri kümesi" verilerin %20'sine sahip olacaktır.

## <a name="test-dataset"></a>Test veri kümesi

`--test-dataset | -t`(dize)

Doğruluk ölçümleri elde etmek için düzenli doğrulama yaparken örneğin %80 - %20'lik bir yaklaşım kullanırken, test veri kümesi dosyasını gösteren dosya yolu.

Kullanıyorsanız, `--test-dataset` `--dataset` o zaman da gereklidir.

--doğrulama-veri kümesi kullanılmadığı sürece `--test-dataset` bağımsız değişken isteğe bağlıdır. Bu durumda, kullanıcı üç bağımsız değişkeni kullanmalıdır.

## <a name="validation-dataset"></a>Doğrulama veri kümesi

`--validation-dataset | -v`(dize)

Doğrulama veri kümesi dosyasını gösteren dosya yolu. Doğrulama veri kümesi her durumda isteğe bağlıdır.

Bir `validation dataset`kullanıyorsanız, davranış olmalıdır:

- Ve `test-dataset` `--dataset` bağımsız değişkenler de gereklidir.

- Veri `validation-dataset` kümesi, model seçimi için tahmin hatasını tahmin etmek için kullanılır.

- Son `test-dataset` seçilen modelin genelleme hatasının değerlendirilmesi için kullanılır. İdeal olarak, test seti bir "kasada" tutulmalı ve yalnızca veri analizinin sonunda çıkarılmalıdır.

Temel olarak, `validation dataset` bir `test dataset`artı kullanırken , doğrulama aşaması iki bölüme ayrılır:

1. İlk bölümde, sadece modelleribakmak ve doğrulama verileri (= doğrulama) kullanarak en iyi performans yaklaşım seçin
2. Daha sonra seçili yaklaşımın (=test) doğruluğunu tahmin emzebilirsiniz.

Bu nedenle, veri ayırma 80/10/10 veya 75/15/10 olabilir. Örnek:

- `training-dataset`dosya verilerin% 75 olmalıdır.
- `validation-dataset`dosya verilerin% 15 olmalıdır.
- `test-dataset`dosya verilerin% 10 olmalıdır.

Her durumda, bu yüzdeler zaten bölünmüş dosyaları sağlayacak CLI kullanarak kullanıcı tarafından karar verilecektir.

## <a name="label-column-name"></a>Etiket sütun adı

`--label-column-name | -n`(dize)

Bu bağımsız değişkenle, belirli bir hedef/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üstbilgisinde sütunun ad kümesi kullanılarak belirtilebilir.

Bu bağımsız değişken yalnızca *sınıflandırma sorunu*gibi denetlenen ML görevleri için kullanılır. *Kümeleme*gibi denetimsiz ML Görevleri için kullanılamaz.

## <a name="label-column-index"></a>Etiket sütun dizini

`--label-column-index | -i`(int)

Bu bağımsız değişkenle, belirli bir hedef/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin dosyasındaki sütunun sayısal dizini kullanılarak belirtilebilir (Sütun dizin değerleri 1'den başlar).

*Not:* Kullanıcı da `--label-column-name`kullanıyorsa, `--label-column-name` kullanılan biridir.

Bu bağımsız değişken yalnızca bir sınıflandırma *sorunu*gibi denetlenen ML görevi için kullanılır. *Kümeleme*gibi denetimsiz ML Görevleri için kullanılamaz.

## <a name="ignore-columns"></a>Sütunları yoksay

`--ignore-columns | -I`(dize)

Bu bağımsız değişkenle, veri kümesi dosyasındaki varolan sütunları, eğitim işlemleri tarafından yüklenmedikleri ve kullanılmaması için yok sayabilirsiniz.

Yoksaymak istediğiniz sütun adlarını belirtin. Birden çok sütun adını ayırmak için ',' (boşlukla virgül) veya ' ' (boşluk) kullanın. Beyaz boşluk içeren sütun adları için tırnak işaretleri kullanabilirsiniz (örn. "oturum açmış").

Örnek:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Üstbilgi var

`--has-header | -h`(bool)

Veri kümesi dosyasının üstbilgi satırı olup olmadığını belirtin.
Olası değerler şunlardır:

- `true`
- `false`

Varsayılan değer, `true` bu bağımsız değişkenin kullanıcı tarafından belirtilmemiş olmasıdır.

Bağımsız değişkeni `--label-column-name` kullanmak için, veri kümesi dosyasında bir üstbilgi nin olması ve `--has-header` `true` (varsayılan olarak) ayarlanabilmesi gerekir.

## <a name="max-exploration-time"></a>Maksimum arama süresi

`--max-exploration-time | -x`(dize)

Varsayılan olarak, maksimum arama süresi 30 dakikadır.

Bu bağımsız değişken, işlemin birden çok eğitmeni ve yapılandırmayı keşfetmesi için en fazla zamanı (saniye cinsinden) ayarlar. Sağlanan süre tek bir yineleme için çok kısaysa (örneğin 2 saniye) yapılandırılan süre aşılabilir. Bu durumda, gerçek zaman tek bir yinelemede bir model yapılandırması üretmek için gerekli zamandır.

Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak değişebilir.

## <a name="cache"></a>Önbellek

`--cache | -c`(dize)

Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellekte yüklenir.

Küçük ve orta veri kümeleri için önbellek kullanmak eğitim performansını önemli ölçüde artırabilir, bu da eğitim süresinin önbelleği kullanmadığınız zamankinden daha kısa olabileceği anlamına gelir.

Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellekten çıkabileceğiniz için olumsuz etki gösterebilir. Büyük veri kümesi dosyalarıyla eğitim alırken ve önbellek kullanmazken, ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüden veri yığınları akışı olacaktır.

Aşağıdaki değerleri belirtebilirsiniz:

`on`: Eğitim de kullanılacak önbelleği zorlar.
`off`: Eğitim de kullanılmaması için önbelleği zorlar.
`auto`: AutoML sezgisel bağlı olarak, önbellek kullanılacak veya kullanılmaz. Genellikle, küçük/orta veri kümeleri önbellek kullanır ve `auto` seçimi kullanırsanız büyük veri kümeleri önbellek kullanmaz.

Parametreyi `--cache` belirtmezseniz, önbellek `auto` yapılandırması varsayılan olarak kullanılır.

## <a name="name"></a>Adı

`--name | -N`(dize)

Oluşturulan çıktı projesinin veya çözümün adı. Ad belirtilmemişse, `sample-{mltask}` ad kullanılır.

ML.NET modeli dosyası (. ZIP dosyası) de aynı adı alırsınız.

## <a name="output-path"></a>Çıkış yolu

`--output-path | -o`(dize)

Oluşturulan çıktıyı yerleştirmek için kök konumu/klasörü. Geçerli dizin varsayılandır.

## <a name="verbosity"></a>Ayrıntı Düzeyi

`--verbosity | -V`(dize)

Standart çıktının ayrıntılı düzeyini ayarlar.

İzin verilen değerler şunlardır:

- `q[uiet]`
- `m[inimal]`(varsayılan olarak)
- `diag[nostic]`(günlük bilgi düzeyi)

Varsayılan olarak, CLI aracı çalışırken, çalıştığını ve mümkünse ne kadar zaman kaldığını veya %ne kadar Zaman'ın tamamlandığını belirtmek gibi bazı minimum geri bildirimleri (minimal) göstermelidir.

## <a name="help"></a>Yardım

`-h|--help`

Her komutun parametresi için bir açıklama içeren komut için yardım yazdırır.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLI aracı nasıl yüklenir?](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLI'ye Genel Bakış](../automate-training-with-cli.md)
- [Öğretici: CLI ML.NET kullanarak duyguları analiz edin](../tutorials/sentiment-analysis-cli.md)
- [ML.NET CLI'de telemetri](../resources/ml-net-cli-telemetry.md)
