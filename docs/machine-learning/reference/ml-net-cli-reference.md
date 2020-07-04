---
title: ML.NET CLı komut başvurusu
description: ML.NET CLı aracında otomatik eğitme komutuna genel bakış, örnekler ve başvuru.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 4c6cb1346c16f6162077d3414140d693de9e0d8c
ms.sourcegitcommit: 182c7b6c079ebcc0e1898dfd9e921b9ef472ea2c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85946947"
---
# <a name="the-mlnet-cli-command-reference"></a>ML.NET CLı komut başvurusu

`classification`, `regression` Ve komutları, `recommendation` ml.net CLI aracı tarafından sunulan ana komutlardır. Bu komutlar otomatik makine öğrenimi (Otomatikml) kullanarak sınıflandırma, regresyon ve öneri modelleri için iyi kaliteli ML.NET modelleri oluşturmanızı ve bu modeli çalıştırmak/skor yapmak için örnek C# kodunu oluşturmanızı sağlar. Ayrıca, modeli eğitmek için C# kodu, modelin algoritmasını ve ayarlarını araştırmanız için oluşturulur.

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET CLı ve ML.NET oto ml 'ye başvurur ve malzemeler değişebilir.

## <a name="overview"></a>Genel Bakış

Örnek kullanım: 

```console
mlnet regression --dataset "cars.csv" --label-col price
```

`mlnet`Ml görev komutları ( `classification` , `regression` , ve `recommendation` ) aşağıdaki varlıkları oluşturur:

- Seri hale getirilmiş bir model. zip ("en iyi model") kullanıma hazırlanıyor.
- Oluşturulan modeli çalıştırmak/öğrenmek için C# kodu.
- Bu modeli oluşturmak için kullanılan eğitim koduna sahip C# kodu.

İlk iki varlık, model ile tahmine dayalı hale getirmek için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması ve daha fazlası) doğrudan kullanılabilir.

Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece modelin belirli algoritmasını ve ayarlarını araştırabilirsiniz.

## <a name="examples"></a>Örnekler

Bir sınıflandırma sorunu için en basit CLı komutu (Oto ml 'nin, belirtilen verilerden çoğu yapılandırmanın çoğunu):

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

Gerileme sorunu için başka bir basit CLı komutu:

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

Bir eğitim veri kümesi, test veri kümesi ve daha fazla özelleştirme açık bağımsız değişkenlerle bir sınıflandırma modeli oluşturun ve eğitme:

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a>Komut seçenekleri

`mlnet`Ml görev komutları ( `classification` , `regression` ve), `recommendation` belirtilen VERI kümesi ve ml.net CLI seçeneklerine göre birden çok modeli eğitme. Bu komutlar Ayrıca en iyi modeli seçer, modeli serileştirilmiş bir. zip dosyası olarak kaydeder ve Puanlama ve eğitim için ilgili C# kodu oluşturur.

### <a name="classification-options"></a>Sınıflandırma seçenekleri

Çalışan `mlnet classification` bir sınıflandırma modelini eğitecektir. ML modelinin verileri 2 veya daha fazla sınıfa (ör. yaklaşım Analizi) sınıflandırmasına istiyorsanız bu komutu seçin.

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a>Regresyon seçenekleri

Çalıştırmak `mlnet regression` , regresyon modeli eğitecektir. Bir ML modelinin sayısal bir değer (örn. fiyat tahmini) tahmin etmek istiyorsanız bu komutu seçin.

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a>Öneri seçenekleri

Çalışan `mlnet recommendation` bir öneri modeli eğitecektir.  Bir ML modelinin derecelendirmelere göre kullanıcılara (örn. ürün önerisi) öğe önermesini istiyorsanız bu komutu seçin.

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

Geçersiz giriş seçenekleri, CLı aracının geçerli girişlerin bir listesini ve bir hata iletisini yaymasına neden olur.

## <a name="dataset"></a>Veri kümesi

`--dataset | -d`dizisinde

Bu bağımsız değişken, FilePath öğesini aşağıdaki seçeneklerden birine sağlar:

- Y *: tüm veri kümesi dosyası:* Bu seçenek kullanılıyorsa ve Kullanıcı ve sağlamadıysanız `--test-dataset` `--validation-dataset` çapraz doğrulama (k-katlama, vb.) veya otomatik veri bölme yaklaşımları, modeli doğrulamak için dahili olarak kullanılır. Bu durumda, kullanıcının DataSet FilePath 'i sağlaması yeterlidir.

- *B: eğitim veri kümesi dosyası:* Kullanıcı ayrıca model doğrulaması için ( `--test-dataset` ve isteğe bağlı olarak) veri kümeleri sağladıysanız `--validation-dataset` , `--dataset` bağımsız değişken yalnızca "eğitim veri kümesi" olması anlamına gelir. Örneğin, modelin kalitesini doğrulamak ve doğruluk ölçümlerini elde etmek için %80-%20 yaklaşımını kullanırken, "eğitim veri kümesi" verilerin %80 ' sini alacak ve "test veri kümesi" verilerin %20 ' sini alacak.

## <a name="test-dataset"></a>Test veri kümesi

`--test-dataset | -t`dizisinde

Test veri kümesi dosyasına işaret eden dosya yolu; Örneğin, doğruluk ölçümlerini elde etmek için düzenli doğrulamalar yaparken %80-%20 yaklaşım kullanma.

Kullanılıyorsa `--test-dataset` , `--dataset` de gereklidir.

`--test-dataset`--Validation-DataSet kullanılmadığı müddetçe bağımsız değişken isteğe bağlıdır. Bu durumda, kullanıcının üç bağımsız değişkenini kullanması gerekir.

## <a name="validation-dataset"></a>Doğrulama veri kümesi

`--validation-dataset | -v`dizisinde

Doğrulama veri kümesi dosyasına işaret eden dosya yolu. Doğrulama veri kümesi, her durumda isteğe bağlıdır.

Bir kullanıyorsanız `validation dataset` , davranış şu şekilde olmalıdır:

- `test-dataset`Ve `--dataset` bağımsız değişkenleri de gereklidir.

- `validation-dataset`Veri kümesi, model seçimine yönelik tahmin hatasını tahmin etmek için kullanılır.

- , `test-dataset` Seçili son modeldeki Genelleştirme hatası değerlendirmesi için kullanılır. İdeal olarak, test kümesinin bir "kasa" içinde tutulması ve yalnızca veri analizinin sonunda getirilmesi gerekir.

Temel olarak, bir `validation dataset` artı kullandığınızda `test dataset` , doğrulama aşaması iki parçaya ayrılır:

1. İlk bölümde, modellerinize göz atadınız ve doğrulama verilerini kullanarak en iyi şekilde gerçekleştirdiğiniz yaklaşımı seçersiniz (= doğrulama)
2. Ardından seçili yaklaşımın doğruluğunu tahmin edersiniz (= test).

Bu nedenle, verilerin ayrımı 80/10/10 veya 75/15/10 olabilir. Örneğin:

- `training-dataset`Dosya, verilerin %75 ' i olmalıdır.
- `validation-dataset`Dosya, verilerin %15 ' i olmalıdır.
- `test-dataset`Dosya, verilerin %10 ' a sahip olmalıdır.

Herhangi bir durumda, bu yüzdeleri Kullanıcı tarafından zaten bölünmüş dosyaları sağlayacak CLı kullanarak kararlanacaktır.

## <a name="label-column"></a>Etiket sütunu

`--label-col`(int veya String)

Bu bağımsız değişkenle, belirli bir amaç/hedef sütunu (tahmin etmek istediğiniz değişken) veri kümesinin üstbilgisinde veya sütunun veri kümesinin dosyasındaki sayısal dizininde bulunan sütunun adı kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).

Bu bağımsız değişken, *Sınıflandırma* ve *gerileme* sorunları için kullanılır.

## <a name="item-column"></a>Öğe sütunu

`--item-col`(int veya String)

Öğe sütunu, kullanıcıların hızaldığı öğelerin listesini içerir (öğeler kullanıcılara önerilir). Bu sütun, veri kümesinin üstbilgisinde sütun adı kümesi veya veri kümesinin dosyasında sütunun sayısal dizini kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).

Bu bağımsız değişken yalnızca *öneri* görevi için kullanılır.

## <a name="rating-column"></a>Derecelendirme sütunu

`--rating-col`(int veya String)

Derecelendirme sütunu kullanıcılara göre öğelere verilen derecelendirmelerin listesini içerir. Bu sütun, veri kümesinin üstbilgisinde sütun adı kümesi veya veri kümesinin dosyasında sütunun sayısal dizini kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).

Bu bağımsız değişken yalnızca *öneri* görevi için kullanılır.

## <a name="user-column"></a>Kullanıcı sütunu

`--user-col`(int veya String)

Kullanıcı sütunu, öğelere derecelendirme veren kullanıcıların listesini içerir. Bu sütun, veri kümesinin üstbilgisinde sütun adı kümesi veya veri kümesinin dosyasında sütunun sayısal dizini kullanılarak belirtilebilir (sütun dizini değerleri 0 ' dan başlar).

Bu bağımsız değişken yalnızca *öneri* görevi için kullanılır.

## <a name="ignore-columns"></a>Sütunları yoksay

`--ignore-columns`dizisinde

Bu bağımsız değişkenle, veri kümesi dosyasında var olan sütunları yoksayabilirsiniz ve bu sayede eğitim işlemleriyle birlikte kullanılmaz.

Yoksaymak istediğiniz sütun adlarını belirtin. Birden çok sütun adını ayırmak için ', ' (boşluk ile virgül) veya ' ' (boşluk) kullanın. Boşluk içeren sütun adları için tırnak işareti kullanabilirsiniz (örneğin, "oturum açmış").

Örnek:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Üst bilgisi vardır

`--has-header`bool

Veri kümesi dosyalarının bir üst bilgi satırına sahip olup olmadığını belirtin.
Olası değerler şunlardır:

- `true`
- `false`

Bu bağımsız değişken Kullanıcı tarafından belirtilmemişse, ML.NET CLı bu özelliği algılamaya çalışır.

## <a name="train-time"></a>Eğitim süresi

`--train-time`dizisinde

Varsayılan olarak, en fazla araştırma/tren süresi 30 dakikadır.

Bu bağımsız değişken, birden fazla taş ve yapılandırmayı araştırmak için işlem için en uzun süreyi (saniye cinsinden) ayarlar. Belirtilen süre çok kısaysa (2 saniye), tek bir yineleme için yapılandırılan saat kesilebilir. Bu durumda, gerçek süre, tek bir yinelemede tek bir model yapılandırması üretmek için gereken süredir.

Yinelemeler için gereken süre, veri kümesinin boyutuna bağlı olarak farklılık gösterebilir.

## <a name="cache"></a>Önbellek

`--cache`dizisinde

Önbelleğe alma kullanırsanız, tüm eğitim veri kümesi bellek içinde yüklenir.

Küçük ve orta ölçekli veri kümelerinde, önbelleğin kullanılması eğitim performansını önemli ölçüde iyileştirebilir, bu da eğitim süresi önbelleği kullanmadığınız zamandan daha kısa olabilir.

Ancak, büyük veri kümeleri için bellekteki tüm verilerin yüklenmesi, bellek yetersiz olduğundan olumsuz etkileyebilir. Büyük veri kümesi dosyalarıyla eğitim yaparken ve önbellek kullanmayan ML.NET, eğitim sırasında daha fazla veri yüklemesi gerektiğinde sürücüdeki veri öbeklerini akışa alabilir.

Aşağıdaki değerleri belirtebilirsiniz:

`on`: Eğitim sırasında önbelleğin kullanılmasına zorlar.
`off`: Eğitim sırasında önbelleğin kullanılmasına izin vermez.
`auto`: Bu, oto ml buluşsal türüne bağlı olarak, önbellek kullanılır veya değildir. Genellikle, küçük/orta veri kümeleri önbelleği kullanır ve büyük veri kümeleri seçeneği kullanırsanız önbelleği kullanmaz `auto` .

`--cache`Parametresini belirtmezseniz, `auto` Varsayılan olarak önbellek yapılandırması kullanılacaktır.

## <a name="name"></a>Adı

`--name`dizisinde

Oluşturulan çıkış projesinin veya çözümünün adı. Ad belirtilmemişse, ad `sample-{mltask}` kullanılır.

ML.NET model dosyası (. ZIP dosyası) de aynı adı alır.

## <a name="output-path"></a>Çıkış yolu

`--output | -o`dizisinde

Oluşturulan çıkışın yerleştirileceği kök konumu/klasörü. Geçerli dizin varsayılandır.

## <a name="verbosity"></a>Ayrıntı Düzeyi

`--verbosity | -v`dizisinde

Standart çıkışın ayrıntı düzeyini ayarlar.

İzin verilen değerler şunlardır:

- `q[uiet]`
- `m[inimal]`(varsayılan olarak)
- `diag[nostic]`(günlük bilgisi düzeyi)

Varsayılan olarak, CLı aracı çalışırken en az geri bildirim ( `minimal` ), çalışıp çalışmadığını ve ne kadar süre kaldığını veya sürenin% ne kadar tamamlandığını gösterir.

## <a name="help"></a>Yardım

`-h |--help`

Komut için, her komutun parametresi için bir açıklama içeren yardımı yazdırır.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı aracını yüklemek](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLı 'ye Genel Bakış](../automate-training-with-cli.md)
- [Öğretici: ML.NET CLı kullanarak yaklaşımı çözümleme](../tutorials/sentiment-analysis-cli.md)
- [ML.NET CLı 'de telemetri](../resources/ml-net-cli-telemetry.md)
