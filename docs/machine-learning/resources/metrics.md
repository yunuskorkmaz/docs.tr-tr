---
title: ML.NET ölçümleri
description: Bir ML.NET modelinin performansını değerlendirmek için kullanılan ölçümleri anlayın
ms.date: 04/29/2019
author: natke
ms.openlocfilehash: 362f2f382d050ff9ae246af2dffe3e15d22452eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460735"
---
# <a name="model-evaluation-metrics-in-mlnet"></a>ML.NET içinde model değerlendirmesi ölçümleri

## <a name="metrics-for-binary-classification"></a>Ikili sınıflandırma ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Veritabanınızın** |  [Doğruluk](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) , test veri kümesiyle doğru tahmine göre orandır. Bu değer, toplam giriş örneği sayısına yönelik doğru tahmine yönelik orandır. Yalnızca her sınıfa ait benzer sayıda örnek varsa iyi bir sonuç verir.| **1,00 ' ye yaklaşarak daha iyidir**. Ancak tam olarak 1,00 bir sorunu gösterir (yaygın olarak: etiket/hedef sızıntısı, üzerine sığdırma veya eğitim verileriyle test etme). Test verileri dengesiz olduğunda (örneklerin çoğu sınıflardan birine aitse), veri kümesi çok küçüktür veya 0,00 ya da 1,00 yaklaşımını, doğruluk gerçekten bir sınıflandırıcının verimliliğini yakalamaz ve ek ölçümleri denetlemeniz gerekir. |
| **AUC** |    *eğri altındaki* [aucroc](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) veya alanı: Bu, gerçek pozitif orandan ve yanlış pozitif oranla aynı şekilde oluşturulan eğrinin altındaki alanı ölçmektedir.  |   **1,00 ' ye yaklaşarak daha iyidir**. Modelin kabul edilebilir olması için 0,50 ' den büyük olmalıdır; AUC/0,50 veya daha azını içeren bir model, daha düşüktür. |
| **AUCPR** | *hassas geri çağırma eğrisinin eğrisi altında* [Aucpr](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) veya alanı: sınıflar çok fazla dengeli olduğunda (yüksek oranda eğilmiş veri kümelerinde) tahmin başarısı için yararlı ölçüm. |  **1,00 ' ye yaklaşarak daha iyidir**. 1,00 ' e yakın yüksek puanlar, sınıflandırıcının doğru sonuçları (yüksek duyarlık) döndürdüğünü ve tüm pozitif sonuçların (yüksek geri çağırma) büyük bir kısmını döndürdüğünü gösterir. |
| **F1-Score** | Aynı zamanda *dengeli f puanı veya F ölçü*olarak da bilinen [F1 puanı](https://en.wikipedia.org/wiki/F1_score) . Duyarlık ve geri çağırma 'nin harmonik ortalaması vardır. Duyarlılık ve geri çekme arasında bir denge aramak istediğinizde F1 puanı yararlı olur.| **1,00 ' ye yaklaşarak daha iyidir**.  F1 puanı, 1,00 ve en kötü puanı 0,00 ' de en iyi değere ulaştı. Sınıflandırıcınızı ne kadar kesin olarak söyler. |

İkili sınıflandırma ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Doğruluk, duyarlık, geri çekme veya F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [İkili sınıflandırma ölçümleri sınıfı](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Duyarlık-hatırla ve ROC eğrileri arasındaki Ilişki](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="metrics-for-multi-class-classification"></a>Çok sınıflı sınıflandırmayla ilgili ölçümler

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Mikro doğruluk** |  [Mikro ortalama doğruluk](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) , ortalama ölçümü hesaplamak için tüm sınıfların katkılarını toplar. Doğru tahmin edilen örneklerin kesiri. Mikro ortalama, bir sınıf üyeliğini hesaba almaz. Temel olarak her örnek sınıf çifti, doğruluk ölçüsüne eşit olarak katkıda bulunur. | **1,00 ' ye yaklaşarak daha iyidir**. Çok sınıflı bir sınıflandırma görevinde, bir sınıf dengesizliği olabileceğinden şüphelenirseniz, mikro doğruluk, makro doğruluğu üzerinde tercih edilir (ör. diğer sınıflardan daha fazla bir sınıfa daha fazla örnek olabilir).|
| **Makro doğruluğu** | [Makro-ortalama doğruluk](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) , sınıf düzeyindeki ortalama doğruluk sayısıdır. Her sınıfın doğruluğu hesaplanır ve makro doğruluğu bu accuracies ortalaması olur. Temel olarak her sınıf, doğruluk ölçüsüne eşit olarak katkıda bulunur. Minınlık sınıflarına daha büyük sınıflar olarak eşit ağırlık verilir. Makro-ortalama ölçümü her sınıfa aynı ağırlığı verir, bu sınıftan kaç örnek veri kümesi içeriyor olsun. |  **1,00 ' ye yaklaşarak daha iyidir**.  Ölçüyü her sınıf için bağımsız olarak hesaplar ve ortalama alır (Bu nedenle tüm sınıfları eşit olarak değerlendiriliyor) |
| **Günlük kayıp**| [Logaritmik kayıp](http://wiki.fast.ai/index.php/Log_Loss) , tahmin girişinin 0,00 ile 1,00 arasında bir olasılık değeri olduğu bir sınıflandırma modelinin performansını ölçer. Gerçek etiketten ayrılan tahmini olasılık arttıkça günlük kaybı artar. | **0,00 ' ye yaklaşarak daha iyidir**. Kusursuz bir modelde 0,00 günlük kaybı olur. Machine Learning modellerimizin amacı bu değeri en aza indirmektir.|
| **Günlük kaybını azaltma** | [Logaritmik kayıp azaltma](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) , sınıflandırıcının rastgele bir tahmin üzerinden faydalanması olarak yorumlanabilir.| **-INF ve 1,00 aralıklarında, 1,00 ' in mükemmel tahminlerden ve 0,00 ise ortalama**tahmine göre belirlenir. Örneğin, değer 0,20 eşitse, "doğru bir tahmine ait olasılık %20 tahmininden daha iyidir" olarak yorumlanabilecek.|

Mikro doğruluk genellikle ML tahminlerinin iş gereksinimlerine göre daha iyi hizalanır. Birden çok Lass sınıflandırma görevinin kalitesini seçmek için tek bir ölçüm seçmek istiyorsanız, genellikle mikro doğruluk olmalıdır.

Örnek, bir destek bileti sınıflandırma görevi için: (gelen biletleri ekiplerle eşleştirir)

- Mikro doğruluk--bir gelen bilet doğru ekibe ne sıklıkla sınıflandırıldı?
- Makro doğruluğu--ortalama bir ekip için, takımlarına yönelik gelen bir bilet ne sıklıkta doğru?

Makro doğruluğu bu örnekteki küçük ekipleri fazla ağırlıklardır; yılda 10.000 bileti olan büyük bir ekip kadar, yıl başına yalnızca 10 bilet alan küçük bir takım. Bu durumda mikro doğruluk, "Bilet yönlendirme sürecimi otomatikleştirerek şirket tarafından ne kadar zaman/para tasarrufu yapabilir" iş gereksinimiyle daha iyi bir şekilde ilişkilendirir.

Çok sınıflı sınıflandırma ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Micro-ve makrosu – duyarlık, geri çağırma ve F puanı ortalaması](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Imdengeli veri kümesiyle birden çok Lass sınıflandırması](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="metrics-for-regression"></a>Gerileme ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **R-kare** |  [R-kare (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)veya *belirleme katsayısı* , modelin tahmine dayalı gücünü-inf ile 1,00 arasında bir değer olarak temsil eder. 1,00, mükemmel bir uyum olduğu anlamına gelir ve puanlar negatif olabilir. 0,00 puanı, modelin etiket için beklenen değeri tahmin etmesini anlamına gelir. R2 gerçek test veri değerlerinin tahmin edilen değerlere ne kadar yakın olduğunu ölçer. | **1,00 ' ye yaklaşarak daha iyi kalite**. Ancak, bazen düşük R-kare değerleri (0,50 gibi), senaryolarınız için tamamen normal veya yeterince iyi olabilir ve yüksek R-kare değerleri her zaman iyi ve şüpheli değildir. |
| **Mutlak kayıp** |  [Mutlak kayıp](https://en.wikipedia.org/wiki/Mean_absolute_error) veya *Ortalama mutlak hata (Mae)* , tahminleri gerçek sonuçlar olarak kapatma ölçülerini ölçer. Model hatası, tahmin edilen etiket değeri ve doğru etiket değeri arasındaki mutlak mesafe olan tüm model hatalarının ortasıdır. Bu tahmin hatası, test veri kümesinin her bir kaydı için hesaplanır. Son olarak, tüm kaydedilen mutlak hatalar için Ortalama değer hesaplanır.| **0,00 ' ye yaklaşarak daha iyi kalite.** Ortalama mutlak hatanın ölçülen verilerle aynı ölçeği kullandığını unutmayın (belirli aralığa normalleştirilmez). Mutlak kayıp, kareli kayıp ve RMS-kaybetme yalnızca, benzer bir etiket değeri dağıtımına sahip aynı veri kümesine veya veri kümesine yönelik modeller arasında karşılaştırmalar yapmak için kullanılabilir. |
| **Kare içinde kayıp** |  , *Ortalama kare sapması (MSD)* olarak da adlandırılan [kare Içinde kayıp](https://en.wikipedia.org/wiki/Mean_squared_error) veya *Ortalama kare içi hata (MSE)* , regresyon çizgisini bir test veri değerleri kümesine ne kadar yakın olduğunu söyler. Bu, noktadan uzaklıkları regresyon satırına getirerek (bu uzaklıklar E hatalardır) ve karelerini alıp. Karelerini alıp daha büyük farklılıklara daha fazla ağırlık sağlar. | Her zaman negatif olmayan ve **0,00 ' ye yakın değerler daha iyidir**. Verilerinize bağlı olarak, ortalama kareli hata için çok küçük bir değer almak imkansız olabilir.|
| **RMS-kayıp** |  [RMS-kayıp](https://en.wikipedia.org/wiki/Root-mean-square_deviation) veya *kök ortalama kare hatası (RMI)* ( *kök ortalama kare sapması, RMSD*), bir model tarafından tahmin edilen değerler arasındaki farkın ve modellenen ortamdan alınan değerler arasındaki farkı ölçer. RMS-kayıp, kare Içinde kayıp değerinin kare köküdür ve etiketle aynı birimlere sahiptir, böylece daha büyük farklılıklar daha fazla ağırlığa sahiptir. Kök ortalama kare hatası genellikle deneysel sonuçların doğrulanması için climatology, tahmin ve gerileme analizinde kullanılır. | Her zaman negatif olmayan ve **0,00 ' ye yakın değerler daha iyidir**. RMSD, belirli bir veri kümesi için farklı modellerin tahmin hatalarını, ölçek bağımlı olduğu için veri kümeleri arasında değil, karşılaştırmak için doğruluk ölçüdür.|

Gerileme ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Regresyon analizi: R-kare genişliği 'Ni nasıl yorumlayabilirim ve uygun bir uyum düzeyini değerlendiririm?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Regresyon analizinde R-kare şeklini yorumlama](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [R-kare Içinde tanım](https://www.investopedia.com/terms/r/r-squared.asp)
- [Ortalama kareler hata tanımı](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Ortalama kare Içinde hata ve kök ortalama kare hatası nedir?](https://www.vernier.com/til/1014/)
