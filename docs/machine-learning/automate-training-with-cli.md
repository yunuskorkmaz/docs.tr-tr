---
title: Model eğitiminin ML.NET CLI ile otomatikleştirme
description: ML.NET CLI aracı otomatik olarak komut satırından en iyi modeli eğitmek için nasıl kullanılacağını keşfedin.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: 33383582140d9df4290a0bbf30659301af837d1d
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066264"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Model eğitiminin ML.NET CLI ile otomatikleştirme

ML.NET CLI "ML.NET .NET geliştiricileri için ML.NET öğrenme, ıot'yi herkesin kullanımına sunan".

ML.NET API kendisi tarafından (ML.NET AutoML CLI) kullanmak için verilere uygulanacak bir eğitmen (uygulaması belirli bir görev için makine öğrenimi algoritması) ve veri Dönüşümleri (özellik Mühendisliği) kümesini seçmeniz gerekir. En iyi işlem hattı her veri kümesi için farklılık gösterir ve tüm seçenekler arasından en iyi algoritmayı seçerek karmaşıklığa ekler. Dahası, her bir algoritmanın ayarlanmasına hiperparametreleri kümesi vardır. Bu nedenle, özellik Mühendisliği, öğrenme algoritmaları ve hiperparametreleri en iyi kombinasyonu bulunmaya çalışılırken modeli iyileştirme öğrenme makinede haftalar ve bazen ay ayırabilirsiniz.

ML.NET AutoML akıllı altyapısı uygulayan ML.NET CLI ile bu işlem otomatikleştirilebilir. 

> [!NOTE]
> Bu konu için ML.NET başvuruyor **CLI** ve ML.NET **AutoML**, şu anda Önizleme aşamasındadır ve malzeme değişikliğe tabi olabilir. 

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>ML.NET komut satırı arabirimi (CLI) nedir?

ML.NET CLI herhangi komut kaliteli ML.NET modelleri ve eğitim veri kümenize dayalı kaynak kodu oluşturmak için istemi (Windows, Mac veya Linux) çalıştırabilirsiniz.

Aşağıdaki çizimde gösterildiği gibi yüksek kaliteli ML.NET modeli (serileştirilmiş modeli .zip dosyası) örnek oluşturmak daha kolaydır C# Çalıştır/puanı bu modeli için kod. Ayrıca, C# /bu modeli eğitme oluşturmak için kod da oluşturulur, araştırma ve algoritmasına yinelemek ve ayarları için kullanılan oluşturulan "en iyi modeli". 

![Görüntü](media/automate-training-with-cli/cli-high-level-process.png "AutoML altyapısı ML.NET CLI içinde çalışma")

ML.NET bildiğiniz olsa bile, ayrıca üretkenliğinizi artıran şekilde kendiniz, kodlama olmadan, bu varlıkları kendi veri kümeleri oluşturabilirsiniz.

Şu anda, ML ML.NET CLI tarafından desteklenen görevler şunlardır:

- `binary-classification`
- `multiclass-classification` 
- `regression`
- Gelecekteki: görevler gibi diğer makine öğrenimi `recommendation`, `ranking`, `anomaly-detection`, `clustering`

Kullanım örneği:

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![görüntü](media/automate-training-with-cli/cli-model-generation.gif)

Aynı şekilde üzerinde çalıştırabilirsiniz *Windows PowerShell*, * macOS/Linux bash veya *Windows CMD*. Ancak, tablosal otomatik tamamlama (parametre önerileri) üzerinde çalışmaz *Windows CMD*.

## <a name="output-assets-generated"></a>Oluşturulan çıktı varlıkları

CLI'yı `auto-train` komut çıktı klasöründe şu varlıkları oluşturur:

- Serileştirilmiş modeli .zip ("en iyi modeli") Öngörüler çalıştırmak için kullanıma hazır. 
- C#Çözümle:
    - C#kod, Çalıştır/puan modeli (Bu modeli ile son kullanıcı uygulamalarınızda Öngörüler oluşturmak için) oluşturulur.
    - C#Eğitim kodla (amacıyla veya modeli yeniden eğitme öğrenme için) Bu modeli oluşturmak için kullanılan kod.
- Kendi ayrıntılı yapılandırma/işlem hattı dahil olmak üzere tüm yinelemeleri/süpürmeleri birden fazla bir algoritmalar arasında bilgi günlük dosyası değerlendirilir.

İlk iki varlıklar ile oluşturulan, ML model doğrudan, son kullanıcı uygulamaları (ASP.NET Core web uygulaması, hizmetleri, masaüstü uygulaması, vb.) tahminlerde bulunmak üzere kullanılabilir.

Üçüncü bir varlık, eğitim kod gösterir, hangi ML.NET API kodu CLI tarafından oluşturulan modeli eğitmek için kullanılan, modelinizi yeniden eğitme ve araştırabilir ve yineleme yapmak için hangi belirli trainer/algoritması ve hiperparametreleri AutoML ve CLI seçilmedi Perde. 

## <a name="understanding-the-quality-of-the-model"></a>Model kalitesini anlama

CLI aracını kullanarak 'en iyi modeli' oluştururken, hedeflediğiniz ML görev için uygun Kalite Ölçümleri (doğruluk gibi ve R karesi alınmış) bakın.

Burada bu ölçümleri otomatik olarak oluşturulan 'en iyi modelinizin kalitesini ' anlayabilmeniz ML görevine göre gruplandırılmış özetler.

### <a name="metrics-for-binary-classification-models"></a>İkili sınıflandırma modelleri için ölçümleri

 CLI tarafından bulunan ilk beş modelleri için ikili sınıflandırma ML görev ölçümleri listesi görüntüler: 

![görüntü](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Doğruluk her zaman aşağıdaki başvuruları içinde anlatıldığı gibi en iyi modeli seçmek için en iyi ölçüm değildir ancak doğruluk sınıflandırma sorunlar için popüler bir unsurdur. Ek ölçümler ile modelinizin kalitesini değerlendirmek için gerek duyduğunuz durumlar vardır.

Keşfedin ve CLI tarafından çıkarılan ölçümleri anlamak için bkz: [ikili sınıflandırma için ölçümleri](resources/metrics.md#metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Çok sınıflı sınıflandırma modelleri için ölçümleri

 CLI tarafından bulunan ilk beş modellerine yönelik çok sınıflı sınıflandırma ML görev ölçümleri listesi görüntüler: 

![görüntü](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Keşfedin ve CLI tarafından çıkarılan ölçümleri anlamak için bkz: [sınıflı sınıflandırma için ölçümleri](resources/metrics.md#metrics-for-multi-class-classification).

### <a name="metrics-for-regression-models"></a>Regresyon modelleri için ölçümleri

Küçük ve popülasyon modelin tahmin edilen değerler gözlenen değerler arasındaki farkları da, verileri bir regresyon modeli uyar. Regresyon, belirli ölçümleri ile değerlendirilebilir.

CLI tarafından bulunan en iyi en çok beş kalite modellerine yönelik ölçümleri, benzer bir listesini görürsünüz. Bu durumda, ML görev için bir regresyon ilgili:

![görüntü](media/automate-training-with-cli/cli-regression-metrics.png)

Keşfedin ve CLI tarafından çıkarılan ölçümleri anlamak için bkz: [regresyon ölçümlerini](resources/metrics.md#metrics-for-regression).

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLI Aracı'nı yükleme](how-to-guides/install-ml-net-cli.md)
- [Öğretici: ML.NET CLI kullanarak bir ikili dosya sınıflandırıcı otomatik oluştur](tutorials/mlnet-cli.md)
- [ML.NET CLI komut başvurusu](reference/ml-net-cli-reference.md)
- [ML.NET CLI'de telemetri](resources/ml-net-cli-telemetry.md)
