---
title: ML.NET CLI ile model eğitimini otomatikleştirin
description: Komut satırından en iyi modeli otomatik olarak eğitmek için ML.NET CLI aracını nasıl kullanacağımı keşfedin.
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185889"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>ML.NET CLI ile model eğitimini otomatikleştirin

cli ML.NET .NET geliştiricileri için model oluşturma otomatikleştirir.

ML.NET API'yi tek başına kullanmak için (automl CLI ML.NET olmadan) bir eğitmen (belirli bir görev için makine öğrenimi algoritması uygulaması) ve verilerinize uygulamak için veri dönüşümleri kümesini (özellik mühendisliği) seçmeniz gerekir. En uygun ardışık düzen hattı her veri kümesi için değişir ve tüm seçeneklerden en uygun algoritmaseçerek karmaşıklığı ekler. Dahası, her algoritmanın ayarlanacak bir dizi hiperparametresi vardır. Bu nedenle, özellik mühendisliği, öğrenme algoritmaları ve hiperparametrelerin en iyi kombinasyonlarını bulmaya çalışarak makine öğrenimi modeli optimizasyonu üzerinde haftalar ve bazen aylar geçirebilirsiniz.

CLI ML.NET otomatik makine öğrenimi (AutoML) kullanarak bu işlemi basitleştirir.

> [!NOTE]
> Bu konu, şu anda Önizleme'de olan **cli** ve ML.NET **AutoML**ML.NET anlamına gelir ve malzeme değişebilir.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>komut satırı arabirimi (CLI) ML.NET nedir?

CLI ML.NET bir [.NET Core aracıdır.](../core/tools/global-tools.md) Yüklendikten sonra, bir makine öğrenme görevi ve bir eğitim veri seti vermek ve bir ML.NET modeli yanı sıra uygulamanızda modeli kullanmak için çalıştırmak için C# kodu oluşturur.

Aşağıdaki şekilde gösterildiği gibi, yüksek kaliteli bir ML.NET modeli (serileştirilmiş model .zip dosyası) artı örnek C# kodu çalıştırmak / bu modeli puan oluşturmak kolaydır. Buna ek olarak, bu modeli oluşturmak/eğitmek için C# kodu da oluşturulur, böylece "en iyi model" için kullanılan algoritma ve ayarları araştırabilir ve yineleyebilirsiniz.

![Görüntü](media/automate-training-with-cli/cli-high-level-process.png "CLI ML.NET içinde çalışan AutoML motoru")

Bu varlıkları kendi veri kümelerinizden kendi kodlamadan oluşturabilirsiniz, bu nedenle ML.NET bildiğiniz halde üretkenliğinizi de artırır.

Şu anda, CLI ML.NET tarafından desteklenen ML Görevleri şunlardır:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Gelecek: gibi diğer makine `recommendation` `ranking`öğrenme `anomaly-detection`görevleri , , ,`clustering`

Kullanım örneği:

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

*Windows PowerShell*, *macOS/Linux bash veya *Windows CMD'de*aynı şekilde çalıştırabilirsiniz. Ancak, tabular otomatik tamamlama (parametre önerileri) *Windows CMD*üzerinde çalışmaz.

## <a name="output-assets-generated"></a>Üretilen çıktı varlıkları

CLI `auto-train` komutu çıktı klasöründe aşağıdaki varlıkları oluşturur:

- Serileştirilmiş bir model .zip ("en iyi model") tahminleri çalıştırmak için kullanıma hazır.
- C# çözeltisi:
  - C# kodu ( bu model ile son kullanıcı uygulamalarında öngörüler yapmak için) oluşturulan modeli çalıştırmak / puan.
  - Bu modeli oluşturmak için kullanılan eğitim kodu ile C# kodu (öğrenme amaçlı veya model yeniden eğitim için).
- Ayrıntılı yapılandırma/ardışık hatlar da dahil olmak üzere, değerlendirilen birden çok algoritma arasında tüm yinelemelerin/taramaların bilgilerini içeren günlük dosyası.

İlk iki varlık, oluşturulan ML modeliyle öngörülerde bulunmak için son kullanıcı uygulamalarınızda (ASP.NET Core web uygulaması, hizmetler, masaüstü uygulaması, vb.) doğrudan kullanılabilir.

Üçüncü varlık, eğitim kodu, oluşturulan modeli eğitmek için CLI tarafından ne ML.NET API kodunun kullanıldığını gösterir, böylece modelinizi yeniden eğitebilir ve cli ve AutoML tarafından kapakların altında belirli eğitmen/algoritma ve hiperparametrelerin seçildiğini araştırabilir ve yineleyebilirsiniz.

## <a name="understanding-the-quality-of-the-model"></a>Modelin kalitesini anlama

CLI aracıyla bir 'en iyi model' oluşturduğunuzda, hedeflediğiniz ML görevi için uygun olarak kalite ölçümleri (doğruluk ve R-Squared gibi) görürsünüz.

Burada bu ölçümler ML görev tarafından gruplandırılır, böylece otomatik olarak oluşturulan 'en iyi model'in kalitesini anlayabilirsiniz.

### <a name="metrics-for-binary-classification-models"></a>İkili Sınıflandırma modelleri için ölçümler

Aşağıdaki cli tarafından bulunan ilk beş model için ikili sınıflandırma ML görev ölçümleri listesini görüntüler:

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Doğruluk sınıflandırma sorunları için popüler bir metriktir, ancak doğruluk her zaman aşağıdaki başvurularda açıklandığı gibi en iyi modeli seçmek için en iyi metrik değildir. Ek ölçümlerle modelinizin kalitesini değerlendirmeniz gereken durumlar vardır.

CLI tarafından çıktı edilen ölçümleri keşfetmek ve anlamak [için ikili sınıflandırma için Değerlendirme ölçümlerine](resources/metrics.md#evaluation-metrics-for-binary-classification)bakın.

### <a name="metrics-for-multi-class-classification-models"></a>Çok Sınıflı Sınıflandırma modelleri için ölçümler

CLI tarafından bulunan ilk beş model için çok sınıflı sınıflandırma ML görev ölçümleri listesini aşağıda görüntüler:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

CLI tarafından çıktı edilen ölçümleri keşfetmek ve anlamak [için, çok sınıflı sınıflandırma için Değerlendirme ölçümlerine](resources/metrics.md#evaluation-metrics-for-multi-class-classification)bakın.

### <a name="metrics-for-regression-and-recommendation-models"></a>Regresyon ve Öneri modelleri için ölçümler

Gözlenen değerler ile modelin öngörülen değerleri arasındaki farklar küçük ve tarafsızsa, bir regresyon modeli verilere iyi uyar. Regresyon belirli ölçümlerle değerlendirilebilir.

CLI tarafından bulunan en iyi beş kaliteli model için benzer bir ölçüm listesi görürsünüz. Bu özel durumda bir regresyon ML görev ile ilgili:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

CLI tarafından çıktı edilen ölçümleri keşfetmek ve anlamak [için, regresyon için Değerlendirme ölçümlerine](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLI aracı nasıl yüklenir?](how-to-guides/install-ml-net-cli.md)
- [Öğretici: CLI ML.NET kullanarak duyguları analiz edin](tutorials/sentiment-analysis-cli.md)
- [ML.NET CLI komut başvurusu](reference/ml-net-cli-reference.md)
- [ML.NET CLI'de telemetri](resources/ml-net-cli-telemetry.md)
