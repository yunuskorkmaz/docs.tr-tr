---
title: ML.NET ölçümleri
description: ML.NET model performansını değerlendirmek için kullanılan ölçüleri anlama
ms.date: 04/29/2019
author: natke
ms.openlocfilehash: 45176902a195906e7b5cffd24fc9da839406ad9d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410523"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>Modeli değerlendirme ML.NET ölçümlerde

## <a name="metrics-for-binary-classification"></a>İkili sınıflandırma için ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Doğruluğu** |  [Doğruluk](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) olan bir sınama veri kümesi ile doğru tahminler oranı. Giriş örneklerin toplam sayısı için doğru tahminler sayısının oranıdır. Yalnızca iyi çalışır olması durumunda her sınıfa ait örnek benzer sayısı.| **1,00, daha iyi yakın**. Ancak 1,00 tam olarak bir sorunu gösterir (genellikle: Etiket/hedef sızıntısı, aşırı sığdırma veya eğitim verileri ile test). Test verilerini olduğunda (burada örneklerin çoğu sınıflardan birine ait) dengesiz, veri kümesi çok küçük veya doğruluğu, gerçekten sınıflandırıcı verimliliğini yakalamaz ve ek ölçümler denetlemek gereken puanları 0,00 veya 1,00, yaklaşan. |
| **AUC** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) veya *eğri alanında*: Bu, gerçek pozitif sonuç oranına hatalı pozitif sonuç oranı karşılaştırması Süpürme tarafından oluşturulan eğri alanında ölçme.  |   **1,00, daha iyi yakın**. Kabul edilebilir bir model için 0,50 büyük olmalıdır; bir model AUC 0,50 veya daha az ile işe yaramaz. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) veya *eğrinin duyarlık geri çekme eğrinin alanında*: Sınıfları çok imbalanced (yüksek oranda dengesiz veri kümeleri) olduğunda tahmin başarısını yararlı ölçüsü. |  **1,00, daha iyi yakın**. Yüksek puan yakın sınıflandırıcı (Yüksek duyarlılık) doğru sonuçlar döndüren yanı sıra, tüm pozitif sonuçlar (yüksek geri çağırma) çoğunu döndüren 1.00 göster. |
| **F1 puanı** | [F1 puanı](https://en.wikipedia.org/wiki/F1_score) olarak da bilinen *puanı F veya F ölçümü dengeli*. Bu geri çağırma ve duyarlık harmonik olur. F1 puanı, duyarlık ve geri çağırma arasında bir denge arama istediğinizde yararlıdır.| **1,00, daha iyi yakın**.  F1 puanı 1.00 ve en kötü puanı 0,00 en iyi değerini ulaşır. Bu durum, sınıflandırıcınızı nasıl hassas olduğunu bildirir. |

İkili sınıflandırma ilgili diğer ayrıntılar için aşağıdaki makalelere ölçümleri okuyun:

- [Doğruluk, kesinlik, geri çağırma veya F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [İkili sınıflandırma ölçümleri sınıfı](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Duyarlık geri çekme ve ROC eğrileri arasındaki ilişki](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="metrics-for-multi-class-classification"></a>Çok sınıflı sınıflandırma için ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Mikro doğruluğu** |  [Micro-ortalama kesinlik](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) ortalama ölçüsünü hesaplamak için tüm sınıflar Katkıların toplar. Doğru şekilde tahmin edilen örnekler bir bölümüdür. Micro-ortalama sınıfı üyelik dikkate almaz. Temel olarak, her örnek sınıfı çifti eşit doğruluğu ölçüme katkıda bulunur. | **1,00, daha iyi yakın**. Sınıf dengesizliği (yani olabilir şüpheleniyorsanız bir çok sınıflı sınıflandırma görevde micro doğruluğu makrosu doğruluğu tercih edilir "bir sınıfı diğer sınıfların çok daha fazla örnek olabilir).|
| **Doğruluk makrosu** | [Makro ortalama kesinlik](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) sınıf düzeyinde ortalama kesinlik olduğunu. Her sınıf için doğruluğu hesaplanır ve makrosu doğruluğu bu doğruluk ortalamasıdır. Temel olarak, her sınıf eşit doğruluğu ölçüme katkıda bulunur. Azınlık sınıfları daha büyük bir sınıf olarak eşit ağırlık verilir. Makro ortalama ölçüm ağırlık olanlardan kaç tane bağımsız olarak veri kümesi sınıfı içeriyor. her sınıf sağlar. |  **1,00, daha iyi yakın**.  Ölçüm bağımsız olarak her sınıf için hesaplar ve ardından (Bu nedenle tüm sınıflar eşit olarak değerlendirmek) ortalamasını alır. |
| **Günlük kaybı**| [Logaritmik kaybı](http://wiki.fast.ai/index.php/Log_Loss) tahmin giriş 0,00 1,00 arasındaki bir olasılık değeri olduğu bir sınıflandırma modeli performansını ölçer. Tahmin olasılık gerçek etiketten kareninkinden günlük kaybı artar. | **0,00, daha iyi yakın**. Mükemmel bir model 0,00 kaybı oturum açması gerekir. Bu değer en aza indirmek için makine öğrenimi modellerinin amacı olan.|
| **Günlük kaybı azaltma** | [Logaritmik kaybı azaltma](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) rasgele tahmin sınıflandırıcı avantajı olarak yorumlanabilir.| **Aralıkları -INF ve burada 1,00 mükemmel Öngörüler ve 0,00 gösterir ortalama Öngörüler 1,00**. Değer 0,20 eşitse "doğru bir tahmin olasılığını %20 rasgele tahmin daha iyi olduğu gibi" Örneğin, bu yorumlanabilir|

Mikro doğruluğu genellikle daha iyi iş gereksinimlerine göre ML Öngörüler hizalanır. Bir çok sınıflı sınıflandırma görevi kalitesini seçmeye yönelik tek bir ölçüm seçmek istiyorsanız, bu genellikle mikro doğruluğu olmalıdır.

Örneğin, bir destek bileti sınıflandırma görevi: (takımları desteklemek için gelen biletleri eşlenir)

- Micro-doğruluğu--ne sıklıkta gelen bir bilet doğru ekibe sınıflandırılmış?
- Makro doğruluk--ortalama bir takımda, ne sıklıkta gelen bir bilet ekip için doğru mu?

Bu örnekte küçük ekipler makrosu doğruluğu overweights; yıl 10 k büyük bir takımla biletleri kadar yıl başına yalnızca 10 biletleri alır, küçük bir takımda sayar. Mikro doğruluğu bu durumda daha iyi iş gereksinimlerini, "ne kadar zaman/para kaydetme şirket bilet yönlendirme işlemi otomatik hale getirerek olabilir" ile ilişkilendirir.

Çok sınıflı sınıflandırma ilgili diğer ayrıntılar için aşağıdaki makalelere ölçümleri okuyun:

- [Micro - ve makro-ortalama duyarlık geri çekme ve F puanı](http://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Imbalanced kümesiyle sınıflı sınıflandırma](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="metrics-for-regression"></a>Regresyon için ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **R karesi alınmış** |  [R karesi alınmış (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination), veya *katsayısı* - INF ve 1,00 arasında bir değer olarak Tahmine dayalı model gücünü temsil eder. 1,00 mükemmel bir uyum yoktur ve puanları negatif olabilir. Bu nedenle uygun rasgele kötü olabilir anlamına gelir. 0,00 anlamına gelir. bir puan modeli etiket için beklenen değer tahmin etme. R2 ne kadar yakın gerçek test veri değerler için tahmin edilen değerler: ölçer. | **1,00, daha iyi kalite yakın**. Ancak, bazen düşük R karesi alınmış değerleri (örneğin, 0,50) tamamen normal veya senaryonuz için yeterince iyi olabilir ve yüksek R karesi alınmış değer her zaman iyi değildir ve şüpheli. |
| **Mutlak kaybı** |  [Mutlak kaybı](https://en.wikipedia.org/wiki/Mean_absolute_error) veya *ortalama mutlak hata (MAE)* tahminler elde etmek için gerçek sonuçların ne kadar yakın olan ölçer. Bu model hataları model hatası tahmin edilen etiket değeri ile doğru etiket değeri arasındaki mutlak uzaklık olduğu ortalamasıdır. Bu tahmin hata, test veri kümesinin her bir kayıt için hesaplanır. Son olarak, ortalama değer için kaydedilen tüm mutlak hataların hesaplanır.| **0,00, daha iyi kalite yakın.** Ortalama mutlak hata ölçülen veri aynı ölçeğini kullandığına dikkat edin (belirli bir aralık için normale döndürülemez). Mutlak kaybı Squared kaybı ve RMS kaybı yalnızca aynı veri kümesi veya veri kümesi ile benzer bir etiket değeri dağıtım modelleri arasında karşılaştırma yapmak için kullanılabilir. |
| **Kare kaybı** |  [Squared kaybı](https://en.wikipedia.org/wiki/Mean_squared_error) veya *ortalama karesi alınmış hata (MSE)* ayrıca adlı *Ortalama kare sapma (MSD'yi)* , regresyon satır test veri değerlerini bir dizi için ne kadar yakın olduğunu bildirir. Bunu noktaları uzaklıkta (Bu uzaklığa E hatalardır) regresyon satırına almak ve bunları karesini yapar. Daha fazla ağırlık karesini büyük farklılıklar sağlar. | Her zaman negatif olmayan, ve **0,00 yakın değerler daha iyidir**. Verilerinizi bağlı olarak, ortalama karesi alınmış hata için çok küçük bir değer almak mümkün olabilir.|
| **RMS kaybı** |  [RMS kaybı](https://en.wikipedia.org/wiki/Root-mean-square_deviation) veya *kök ortalama karesi alınmış hata (RMSE)* (olarak da adlandırılan *kök Ortalama kare sapma, RMSD*), bir model tarafından tahmin edilen değerler ve değerlerin birbirinden gerçekten ölçer Model alınmıştır ortamından gözlemledik. RMS kaybı Squared kaybı kare kökünü ve aynı birim etiketi için mutlak kaybı benzer olarak daha fazla ağırlık vermek daha büyük farklılıklar da vardır. Kök Ortalama kare hata, Deneysel sonuçları doğrulamak için climatology, tahmin ve gerileme analizini yaygın olarak kullanılır. | Her zaman negatif olmayan, ve **0,00 yakın değerler daha iyidir**. RMSD ölçek bağımlı olduğu gibi belirli bir veri kümesi ve veri kümeleri arasında değil, farklı modelleri, tahmin hataları Karşılaştırılacak doğruluk ölçüsüdür.|

Regresyon ölçümleri hakkında daha ayrıntılı bilgi için bu makaleleri okuyun:

- [Gerileme analizini: Nasıl R karesi alınmış yorumlar ve uygun olan özelliği değerlendirmek?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [R kare gerilemesi analizi yorumlama](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [R karesi alınmış tanımı](https://www.investopedia.com/terms/r/r-squared.asp)
- [Ortalama karesi alınmış hata tanımı](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Ortalama karesi alınmış hata ve kök ortalama karesi alınmış hata nedir?](https://www.vernier.com/til/1014/)
