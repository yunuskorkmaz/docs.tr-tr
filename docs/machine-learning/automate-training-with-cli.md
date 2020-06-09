---
title: ML.NET CLı ile model eğitimi otomatikleştirin
description: Komut satırından en iyi modeli otomatik olarak eğiteiçin ML.NET CLı aracının nasıl kullanılacağını öğrenin.
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: d7c6102c2257be1daa613fde0edabce83d04b414
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589674"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>ML.NET CLı ile model eğitimi otomatikleştirin

ML.NET CLı, .NET geliştiricileri için model oluşturmayı otomatikleştirir.

ML.NET API 'sini kendisiyle kullanmak için (ML.NET Düzml CLı olmadan), bir daha (belirli bir görev için makine öğrenimi algoritması uygulaması) ve verilerinize uygulanacak veri dönüştürmeleri (özellik Mühendisliği) kümesini seçmeniz gerekir. En iyi işlem hattı her bir veri kümesi için farklılık gösterir ve tüm seçeneklerden en uygun algoritmayı belirlemek karmaşıklığa ekler. Ayrıca, her algoritmanın ayarlanabilir bir hiper parametre kümesi vardır. Bu nedenle, özellik mühendisliğinin, öğrenme algoritmalarının ve hiper parametrelerin en iyi birleşimlerini bulmaya çalışarak, hafta ve bazen aylık olarak makine öğrenimi modeli iyileştirmesi harcamanıza izin verebilirsiniz.

ML.NET CLı, otomatik makine öğrenimi (Otomatikml) kullanarak bu işlemi basitleştirir.

> [!NOTE]
> Bu konu, şu anda önizleme aşamasında olan ML.NET **CLI** ve ml.net **oto ml**'ye başvurur ve malzemeler değişebilir.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>ML.NET komut satırı arabirimi (CLı) nedir?

ML.NET CLı, bir [.NET Core aracıdır](../core/tools/global-tools.md). Yüklendikten sonra, bir makine öğrenimi görevi ve eğitim veri kümesi verirsiniz ve bir ML.NET modeli, ayrıca uygulamanızdaki modeli kullanmak için çalıştırılacak C# kodu oluşturur.

Aşağıdaki şekilde gösterildiği gibi, bu modeli çalıştırmak/skor için yüksek kaliteli bir ML.NET modeli (serileştirilmiş model. zip dosyası) ve örnek C# kodu oluşturmak kolaydır. Ayrıca, bu modeli oluşturmak/eğitebilmek için C# kodu da oluşturulur. böylece, bu oluşturulan "en iyi model" için kullanılan algoritmayı ve ayarları araştırıp yineleyebilirsiniz.

![image](media/automate-training-with-cli/cli-high-level-process.png "ML.NET CLı içinde çalışan oto ml altyapısı")

Kendi veri kümelerinizde, sizin tarafınızdan kodlamadan bu varlıkları oluşturabilirsiniz. bu sayede, ML.NET zaten tanıyor olsanız bile üretkenliğinizi de artırır.

Şu anda, ML.NET CLı tarafından desteklenen ML görevleri şunlardır:

- Sınıflandırma (ikili ve çok sınıf)
- regresyon
- Önerilen
- Gelecekte: görüntü sınıflandırması, derecelendirme, anomali algılama, kümeleme gibi diğer makine öğrenimi görevleri

Kullanım örneği (sınıflandırma senaryosu):

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![image](media/automate-training-with-cli/mlnet-classification-powershell.gif)

*Windows PowerShell*, *MacOS/Linux Bash*veya *Windows cmd*' de aynı şekilde çalıştırabilirsiniz. Ancak, tablo otomatik tamamlama (parametre önerileri) *WINDOWS cmd*'de çalışmaz.

## <a name="output-assets-generated"></a>Oluşturulan çıkış varlıkları

CLı 'deki ML görev komutları, çıkış klasöründe aşağıdaki varlıkları oluşturur:

- Bir seri hale getirilmiş model. zip ("en iyi model"), tahminleri çalıştırmak için kullanıma uygun.
- İle C# çözümü:
  - Oluşturulan modeli çalıştırmak/öğrenmek için C# kodu (bu modelle Son Kullanıcı uygulamalarınızda tahminleri yapmak için).
  - Bu modeli oluşturmak için kullanılan eğitim koduna sahip C# kodu (öğrenme amaçları veya model yeniden eğitimi için).
- Ayrıntılı yapılandırma/işlem hattı da dahil olmak üzere, değerlendirilen birden çok algoritmayana tüm yinelemeler/sweeps bilgileri içeren günlük dosyası.

İlk iki varlık, bu oluşturulmuş ML modeliyle tahminler yapmak için Son Kullanıcı uygulamalarınızda (ASP.NET Core Web uygulaması, hizmetler, masaüstü uygulaması vb.) doğrudan kullanılabilir.

Eğitim kodu olan üçüncü varlık, CLı tarafından oluşturulan modeli eğitemek için hangi ML.NET API kodunun kullanıldığını gösterir. böylece, modelinize yeniden eğitebilir ve tüm özel bir oran/algoritma ve hiper parametrelerin, kapsamaların altındaki CLı ve oto ml tarafından seçili olduğunu araştırın ve yineleyebilirsiniz.

## <a name="understanding-the-quality-of-the-model"></a>Modelin kalitesini anlama

CLı aracıyla ' en iyi model ' oluşturduğunuzda, hedeflediğiniz ML görevi için uygun olan kalite ölçümlerini (doğruluk ve R-kare gibi) görürsünüz.

Burada, otomatik olarak oluşturulan ' en iyi modellerinizin kalitesini anlayabilmeniz için bu ölçümler ML görevine göre gruplandırılır.

### <a name="metrics-for-classification-models"></a>Sınıflandırma modelleriyle ilgili ölçümler

Aşağıda, CLı tarafından bulunan ilk beş modelin sınıflandırma ölçümleri listesi görüntülenir:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 Doğruluk, sınıflandırma sorunları için popüler bir ölçümdür, ancak doğruluk, aşağıdaki başvurularda açıklanacak şekilde en iyi modeli seçmek için her zaman en iyi ölçüm değildir. Ek ölçümler ile modelinizin kalitesini değerlendirmeniz gereken durumlar vardır.

CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [Sınıflandırma Için değerlendirme ölçümleri](resources/metrics.md#evaluation-metrics-for-multi-class-classification).

### <a name="metrics-for-regression-and-recommendation-models"></a>Gerileme ve öneri modelleriyle ilgili ölçümler

Gözlemlenen değerler ve modelin öngörülen değerleri arasındaki farklılıklar küçük ve taraflı değilse, regresyon modeli verileri iyi bir şekilde sığdırır. Gerileme, belirli ölçümler ile değerlendirilebilir.

CLı tarafından bulunan en iyi önde gelen beş kalite modeli için aynı ölçüm listesini görürsünüz. Regresyon ML göreviyle ilgili bu durumda:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

CLı tarafından çıktı olan ölçümleri araştırmak ve anlamak için bkz. [gerileme Için değerlendirme ölçümleri](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).

## <a name="see-also"></a>Ayrıca bkz.

- [ML.NET CLı aracını yüklemek](how-to-guides/install-ml-net-cli.md)
- [Öğretici: ML.NET CLı kullanarak yaklaşımı çözümleme](tutorials/sentiment-analysis-cli.md)
- [ML.NET CLı komut başvurusu](reference/ml-net-cli-reference.md)
- [ML.NET CLı 'de telemetri](resources/ml-net-cli-telemetry.md)
