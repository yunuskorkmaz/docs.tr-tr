---
title: ML.NET CLı ile model eğitimi otomatikleştirin
description: Komut satırından en iyi modeli otomatik olarak eğiteiçin ML.NET CLı aracının nasıl kullanılacağını öğrenin.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: c147464ff59563d336363eed73fc6337bdb12e85
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275853"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>ML.NET CLı ile model eğitimi otomatikleştirin

ML.NET öğrenirken .NET geliştiricileri için ML.NET CLı "verilerinizi keşfetmenizi sunan" ML.NET.

ML.NET API 'sini kendisiyle kullanmak için (ML.NET Düzml CLı olmadan), bir daha (belirli bir görev için makine öğrenimi algoritması uygulaması) ve verilerinize uygulanacak veri dönüştürmeleri (özellik Mühendisliği) kümesini seçmeniz gerekir. En iyi işlem hattı her bir veri kümesi için farklılık gösterir ve tüm seçeneklerden en uygun algoritmayı belirlemek karmaşıklığa ekler. Ayrıca, her algoritmanın ayarlanabilir bir hiper parametre kümesi vardır. Bu nedenle, özellik mühendisliğinin, öğrenme algoritmalarının ve hiper parametrelerin en iyi birleşimlerini bulmaya çalışarak, hafta ve bazen aylık olarak makine öğrenimi modeli iyileştirmesi harcamanıza izin verebilirsiniz.

Bu işlem, ML.NET Otomatikml akıllı altyapısını uygulayan ML.NET CLı ile otomatikleştirilebilir.

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET **CLI** ve ml.net **oto ml**'ye başvurur ve malzemeler değişebilir.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>ML.NET komut satırı arabirimi (CLı) nedir?

Eğitim veri kümenize göre iyi kalitede ML.NET modelleri ve kaynak kodu oluşturmak için ML.NET CLı 'yi herhangi bir komut isteminde (Windows, Mac veya Linux) çalıştırabilirsiniz.

Aşağıdaki şekilde gösterildiği gibi, yüksek kaliteli bir ML.NET modeli (serileştirilmiş model. zip dosyası) ve bu modeli çalıştırmak/skor için örnek C# kodu oluşturmak basittir. Ayrıca, bu model C# oluşturma/eğitme kodu da oluşturulur. böylece, bu oluşturulan "en iyi model" için kullanılan algoritmayı ve ayarları araştırıp yineleyebilirsiniz.

![](media/automate-training-with-cli/cli-high-level-process.png "ml.net CLI içinde çalışan görüntü oto ml altyapısı")

Kendi veri kümelerinizde, sizin tarafınızdan kodlamadan bu varlıkları oluşturabilirsiniz. bu sayede, ML.NET zaten tanıyor olsanız bile üretkenliğinizi de artırır.

Şu anda, ML.NET CLı tarafından desteklenen ML görevleri şunlardır:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Gelecekte: `recommendation`, `ranking`, `anomaly-detection`, `clustering` gibi diğer makine öğrenimi görevleri

Kullanım örneği:

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

*Windows PowerShell*, * MacOS/Linux Bash veya *Windows cmd*' de aynı şekilde çalıştırabilirsiniz. Ancak, tablo otomatik tamamlama (parametre önerileri) *WINDOWS cmd*'de çalışmaz.

## <a name="output-assets-generated"></a>Oluşturulan çıkış varlıkları

CLı `auto-train` komutu çıkış klasöründe aşağıdaki varlıkları oluşturur:

- Bir seri hale getirilmiş model. zip ("en iyi model"), tahminleri çalıştırmak için kullanıma uygun.
- C#Çözüm:
  - C#oluşturulan model (bu modelle Son Kullanıcı uygulamalarınızda tahmine dayalı hale getirmek için) çalıştırılacak/puan veren kod.
  - C#Bu modeli oluşturmak için kullanılan eğitim koduna sahip kod (öğrenme amaçları veya model yeniden eğitimi için).
- Ayrıntılı yapılandırma/işlem hattı da dahil olmak üzere, değerlendirilen birden çok algoritmayana tüm yinelemeler/sweeps bilgileri içeren günlük dosyası.

İlk iki varlık, bu oluşturulmuş ML modeliyle tahminler yapmak için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.

Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğmek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece modelinize yeniden eğitebilir ve CLı ve oto ml tarafından hangi özel eğitimin/algoritma ve hiper parametrelerin seçili olduğunu araştırabilir ve yineleyebilirsiniz içerir.

## <a name="understanding-the-quality-of-the-model"></a>Modelin kalitesini anlama

CLı aracıyla ' en iyi model ' oluşturduğunuzda, hedeflediğiniz ML görevi için uygun olan kalite ölçümlerini (doğruluk ve R-kare) görürsünüz.

Burada, otomatik olarak oluşturulan ' en iyi modellerinizin kalitesini anlayabilmeniz için ML görevine göre gruplanmış olan ölçümler özetlenmektedir.

### <a name="metrics-for-binary-classification-models"></a>Ikili sınıflandırma modelleriyle ilgili ölçümler

Aşağıda, CLı tarafından bulunan en iyi beş modelin ikili sınıflandırma ML görev ölçümleri listesi görüntülenir:

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Doğruluk, sınıflandırma sorunları için popüler bir ölçümdür, ancak aşağıdaki başvurularda açıklanacak şekilde en iyi modeli seçmek için doğruluk her zaman en iyi ölçüm değildir. Ek ölçümler ile modelinizin kalitesini değerlendirmeniz gereken durumlar vardır.

CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [ikili sınıflandırma ölçümleri](resources/metrics.md#metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Çok sınıflı sınıflandırma modelleriyle ilgili ölçümler

Aşağıda, CLı tarafından bulunan en iyi beş model için çok sınıf sınıflandırma ML görev ölçümleri listesi görüntülenir:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [birden çok Lass sınıflandırması Için ölçümler](resources/metrics.md#metrics-for-multi-class-classification).

### <a name="metrics-for-regression-models"></a>Regresyon modelleriyle ilgili ölçümler

Gözlemlenen değerler ve modelin öngörülen değerleri arasındaki farklılıklar küçük ve taraflı değilse, regresyon modeli verileri iyi bir şekilde sığdırır. Gerileme, belirli ölçümler ile değerlendirilebilir.

CLı tarafından bulunan en iyi önde gelen beş kalite modelinin ölçüm bir listesini görürsünüz. Regresyon ML göreviyle ilgili bu durumda:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [gerileme ölçümleri](resources/metrics.md#metrics-for-regression).

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı aracını yüklemek](how-to-guides/install-ml-net-cli.md)
- [Öğretici: ML.NET CLı kullanarak ikili bir sınıflandırıcı otomatik oluşturma](tutorials/mlnet-cli.md)
- [ML.NET CLı komut başvurusu](reference/ml-net-cli-reference.md)
- [ML.NET CLı 'de telemetri](resources/ml-net-cli-telemetry.md)
