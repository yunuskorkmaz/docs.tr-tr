---
title: ML.NET ölçümleri
description: Bir ML.NET modelinin performansını değerlendirmek için kullanılan ölçümleri anlayın
ms.date: 12/17/2019
ms.openlocfilehash: 046e0a3feea2da702dfef5ca9ce4f498fce5fb26
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804828"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>Ölçümler ile ML.NET modelinizi değerlendirin

Bir ML.NET modelini değerlendirmek için kullanılan ölçümleri anlayın.

Değerlendirme ölçümleri, bir modelin gerçekleştirdiği makine öğrenimi görevinin türüne özeldir.

Örneğin, sınıflandırma görevinde, tahmini bir kategorinin gerçek kategoriyle ne kadar iyi eşleştiğini ölçerek model değerlendirilir. Ve kümeleme için, değerlendirme kümelenmiş öğelerin birbirlerine ne kadar yakın olduğunu ve kümeler arasında ne kadar ayrım olduğunu temel alır.

## <a name="evaluation-metrics-for-binary-classification"></a>Ikili sınıflandırma için değerlendirme ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Veritabanınızın** |  [Doğruluk](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) , test veri kümesiyle doğru tahmine göre orandır. Bu değer, toplam giriş örneği sayısına yönelik doğru tahmine yönelik orandır. Her sınıfa ait benzer sayıda örnek varsa iyi sonuç verir.| **1,00 ' ye yaklaşarak daha iyidir**. Ancak tam olarak 1,00 bir sorunu gösterir (yaygın olarak: etiket/hedef sızıntısı, üzerine sığdırma veya eğitim verileriyle test etme). Test verileri dengesiz olduğunda (örneklerin çoğunun sınıfların birine ait olduğu), veri kümesi küçük ya da 0,00 veya 1,00 ' de, doğruluk gerçekten bir sınıflandırıcının verimliliğini yakalamaz ve ek ölçümleri denetlemeniz gerekir. |
| **AUC** |    *eğri altındaki* [aucroc](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) veya alanı, gerçek pozitif oranı ve yanlış pozitif oranı ile oluşturulan eğrinin altındaki alanı ölçer.  |   **1,00 ' ye yaklaşarak daha iyidir**. Modelin kabul edilebilir olması için 0,50 ' den büyük olmalıdır. AUC/0,50 veya daha azını içeren bir model, daha düşüktür. |
| **AUCPR** | *bir duyarlık geri çağırma eğrisinin eğrisi altındaki*Aucpr veya alanı: sınıflar imletilmiş (yüksek oranda eğilmiş veri kümeleri) olduğunda, tahmin başarısı için kullanışlı ölçüm. |  **1,00 ' ye yaklaşarak daha iyidir**. 1,00 ' e yakın yüksek puanlar, sınıflandırıcının doğru sonuçları (yüksek duyarlık) döndürdüğünü ve tüm pozitif sonuçların (yüksek geri çağırma) büyük bir kısmını döndürdüğünü gösterir. |
| **F1-Score** | Aynı zamanda *dengeli f puanı veya F ölçü*olarak da bilinen [F1 puanı](https://en.wikipedia.org/wiki/F1_score) . Duyarlık ve geri çağırma 'nin harmonik ortalaması vardır. Duyarlılık ve geri çekme arasında bir denge aramak istediğinizde F1 puanı yararlı olur.| **1,00 ' ye yaklaşarak daha iyidir**.  F1 puanı, 1,00 ve en kötü puanı 0,00 ' de en iyi değere ulaştı. Sınıflandırıcınızı ne kadar kesin olarak söyler. |

İkili sınıflandırma ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Doğruluk, duyarlık, geri çağırma veya F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [İkili sınıflandırma ölçümleri sınıfı](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Duyarlık-hatırla ve ROC eğrileri arasındaki Ilişki](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Çok sınıf sınıflandırması için değerlendirme ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Mikro doğruluk** |  [Mikro ortalama doğruluk](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) , ortalama ölçümü hesaplamak için tüm sınıfların katkılarını toplar. Doğru tahmin edilen örneklerin kesiri. Mikro ortalama, bir sınıf üyeliğini hesaba almaz. Temel olarak her örnek sınıf çifti, doğruluk ölçüsüne eşit olarak katkıda bulunur. | **1,00 ' ye yaklaşarak daha iyidir**. Çok sınıflı bir sınıflandırma görevinde, bir sınıf dengesizliği olabileceğinden şüphelenirseniz, mikro doğruluk, makro doğruluğu üzerinde tercih edilir (ör. diğer sınıflardan daha fazla bir sınıfa daha fazla örnek olabilir).|
| **Makro doğruluğu** | [Makro-ortalama doğruluk](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) , sınıf düzeyindeki ortalama doğruluk sayısıdır. Her sınıfın doğruluğu hesaplanır ve makro doğruluğu bu accuracies ortalaması olur. Temel olarak her sınıf, doğruluk ölçüsüne eşit olarak katkıda bulunur. Minınlık sınıflarına daha büyük sınıflar olarak eşit ağırlık verilir. Makro-ortalama ölçümü her sınıfa aynı ağırlığı verir, bu sınıftan kaç örnek veri kümesi içeriyor olsun. |  **1,00 ' ye yaklaşarak daha iyidir**.  Ölçüyü her sınıf için bağımsız olarak hesaplar ve ortalama alır (Bu nedenle tüm sınıfları eşit olarak değerlendiriliyor) |
| **Günlük kayıp**| Logaritmik kayıp, tahmin girişinin 0,00 ile 1,00 arasında bir olasılık değeri olduğu bir sınıflandırma modelinin performansını ölçer. Gerçek etiketten ayrılan tahmini olasılık arttıkça günlük kaybı artar. | **0,00 ' ye yaklaşarak daha iyidir**. Kusursuz bir modelde 0,00 günlük kaybı olur. Machine Learning modellerimizin amacı bu değeri en aza indirmektir.|
| **Günlük kaybını azaltma** | [Logaritmik kayıp azaltma](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) , sınıflandırıcının rastgele bir tahmin üzerinden faydalanması olarak yorumlanabilir.| **-INF ve 1,00 aralıklarında, 1,00 ' in mükemmel tahminlerden ve 0,00 ise ortalama**tahmine göre belirlenir. Örneğin, değer 0,20 eşitse, "doğru bir tahmine ait olasılık %20 tahmininden daha iyidir" olarak yorumlanabilecek.|

Mikro doğruluk genellikle ML tahminlerinin iş gereksinimlerine göre daha iyi hizalanır. Birden çok Lass sınıflandırma görevinin kalitesini seçmek için tek bir ölçüm seçmek istiyorsanız, genellikle mikro doğruluk olmalıdır.

Örnek, bir destek bileti sınıflandırma görevi için: (gelen biletleri ekiplerle eşleştirir)

- Mikro doğruluk--bir gelen bilet doğru ekibe ne sıklıkla sınıflandırıldı?
- Makro doğruluğu--ortalama bir ekip için, takımlarına yönelik gelen bir bilet ne sıklıkta doğru?

Makro doğruluğu bu örnekteki küçük ekipleri fazla ağırlıklardır; ayda 10.000 bileti olan büyük bir ekip kadar, yılda yalnızca 10 bilet alan küçük bir ekip. Bu durumda mikro doğruluk, "Bilet yönlendirme sürecimi otomatikleştirerek şirket tarafından ne kadar zaman/para tasarrufu yapabilir" iş gereksinimiyle daha iyi bir şekilde ilişkilendirir.

Çok sınıflı sınıflandırma ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Micro-ve Macro-Precision, geri çek ve F puanı ortalaması](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Imdengeli veri kümesiyle birden çok Lass sınıflandırması](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Gerileme ve öneri için değerlendirme ölçümleri

Gerileme ve öneri görevlerinin her ikisi de bir sayı tahmin eder. Gerileme durumunda, sayı, giriş özellikleri tarafından etkilenen herhangi bir çıkış özelliği olabilir. Öneri için, sayı genellikle bir derecelendirme değeridir (örneğin 1 ile 5 arasında) veya bir Evet/Hayır önerisi (sırasıyla 1 ve 0 ile temsil edilir).

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
| **R-kare** |  [R-kare (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)veya *belirleme katsayısı* , modelin tahmine dayalı gücünü-inf ile 1,00 arasında bir değer olarak temsil eder. 1,00, mükemmel bir uyum olduğu anlamına gelir ve puanlar negatif olabilir. 0,00 puanı, modelin etiket için beklenen değeri tahmin etmesini anlamına gelir. R2 gerçek test veri değerlerinin tahmin edilen değerlere ne kadar yakın olduğunu ölçer. | **1,00 ' ye yaklaşarak daha iyi kalite**. Ancak, bazen düşük R-kare değerleri (0,50 gibi), senaryolarınız için tamamen normal veya yeterince iyi olabilir ve yüksek R-kare değerleri her zaman iyi ve şüpheli değildir. |
| **Mutlak kayıp** |  [Mutlak kayıp](https://en.wikipedia.org/wiki/Mean_absolute_error) veya *Ortalama mutlak hata (Mae)* , tahminleri gerçek sonuçlar olarak kapatma ölçülerini ölçer. Model hatası, tahmin edilen etiket değeri ve doğru etiket değeri arasındaki mutlak mesafe olan tüm model hatalarının ortasıdır. Bu tahmin hatası, test veri kümesinin her bir kaydı için hesaplanır. Son olarak, tüm kaydedilen mutlak hatalar için Ortalama değer hesaplanır.| **0,00 ' ye yaklaşarak daha iyi kalite.** Ortalama mutlak hata, ölçülen verilerle aynı ölçeği kullanır (belirli aralığa normalleştirilmez). Mutlak kayıp, kareli kayıp ve RMS-kaybetme yalnızca, benzer bir etiket değeri dağıtımına sahip aynı veri kümesine veya veri kümesine yönelik modeller arasında karşılaştırmalar yapmak için kullanılabilir. |
| **Kare içinde kayıp** |  [Kareler-kayıp](https://en.wikipedia.org/wiki/Mean_squared_error) veya *Ortalama kare hatası (MSE)*, *Ortalama kare sapması (MSD)* olarak da bilinir, noktadan uzaklıkları regresyon satırına getirerek bir regresyon çizgisini bir dizi test veri değeri için nasıl kapatırsınız (bu uzaklıklar E hatalardır) ve karelerini alıp onları belirler. Karelerini alıp daha büyük farklılıklara daha fazla ağırlık sağlar. | Her zaman negatif olmayan ve **0,00 ' ye yakın değerler daha iyidir**. Verilerinize bağlı olarak, ortalama kareli hata için çok küçük bir değer almak imkansız olabilir.|
| **RMS-kayıp** |  [RMS-kayıp](https://en.wikipedia.org/wiki/Root-mean-square_deviation) veya *kök ortalama kare hatası (Rmde)* ( *kök ortalama kare sapması, RMSD*), bir model tarafından tahmin edilen değerler arasındaki farkı ve modellenen ortamdan gözlemlenen değerleri ölçer. RMS-kayıp, kare Içinde kayıp değerinin kare köküdür ve etiketle aynı birimlere sahiptir, böylece daha büyük farklılıklar daha fazla ağırlığa sahiptir. Kök ortalama kare hatası genellikle deneysel sonuçların doğrulanması için climatology, tahmin ve gerileme analizinde kullanılır. | Her zaman negatif olmayan ve **0,00 ' ye yakın değerler daha iyidir**. RMSD, belirli bir veri kümesi için farklı modellerin tahmin hatalarını, ölçek bağımlı olduğu için veri kümeleri arasında değil, karşılaştırmak için doğruluk ölçüdür.|

Gerileme ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Regresyon analizi: R-kare genişliği 'Ni nasıl yorumlayabilirim ve uygun bir uyum düzeyini değerlendiririm?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Regresyon analizinde R-kare şeklini yorumlama](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [R-kare Içinde tanım](https://www.investopedia.com/terms/r/r-squared.asp)
- [Ortalama kareler hata tanımı](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Ortalama kare Içinde hata ve kök ortalama kare hatası nedir?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Kümeleme için değerlendirme ölçümleri

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
|**Ortalama uzaklık**|Veri noktaları ve atanan kümesinin merkezi arasındaki mesafe ortalaması. Ortalama mesafe, centroıd 'leri Kümelendirmek için veri noktalarının yakınlık ölçüsüdür. Kümenin ' sıkı ' olduğu bir ölçüdür.|**0** ' a yakın değerler daha iyidir. Ortalama uzaklığın ne kadar yakın olması, verilerin daha fazla kümelenmiş olması. Bu durumda, küme sayısı arttıkça bu ölçümün azalyacağını ve çok büyük (her farklı veri noktasının kendi kümesi olduğu) sıfıra eşit olacağını unutmayın.
|**Davvıes Bouldın dizini**|Küme içi uzaklıklarda, küme uzaklıklarında ortalama oran. Kümenin daha sıkı olması ve kümelerin daha da farklı olması, bu değerin ne kadar küçük olması gerekir.|**0** ' a yakın değerler daha iyidir. Daha fazla ve daha az dağınık kümeler daha iyi bir puana neden olur.|
|**Normalleştirilmiş karşılıklı bilgiler**|Kümeleme modelini eğitme sırasında kullanılan eğitim verileri de taban gerçeği etiketleri (yani denetimli kümeleme) ile birlikte olduğunda kullanılabilir. Normalleştirilmiş karşılıklı bilgi ölçümü, benzer veri noktalarının aynı kümeye atanıp atanmadığını ve farklı kümelere farklı veri noktaları atandığını ölçer. Normalleştirilmiş karşılıklı bilgi, 0 ile 1 arasında bir değerdir|**1** ' e yakın değerler daha iyidir|

## <a name="evaluation-metrics-for-ranking"></a>Sıralama için değerlendirme ölçümleri

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
|**İndirimli kümülatif kazanç**|İndirimli kümülatif kazanç (DCG), bir derecelendirme kalitesi ölçüsüdür. İki varsayımda türetilir. Tek: son derece ilgili öğeler, derecelendirme düzeninde daha yüksek görünzaman daha yararlıdır. İki: kullanışlılığı, ilginin ne kadar yüksek olduğunu, daha fazla yararlı bir öğe olduğunu izler. İndirimli toplu kazanç, derecelendirme düzeninde belirli bir konum için hesaplanır. Derecelendirme konumunun, ilgilendiğiniz konuma kadar logaritmasını elde eden ilgiyi bir şekilde toplar. $ \ Sum_ {i = 0} ^ {p} \frac {rel_i} {\ log_ {e} {i + 1}}} kullanılarak hesaplanır. bir derecelendirme eğitim algoritmasına taban Derecelendirme tablosundaki her konum için bir DCG değeri sağlanır; bu nedenle, Indirimli kümülatif **kazanç**adı. |**Daha yüksek değerler daha iyidir**|
|**Normalleştirilmiş Indirimli birikmeli kazançlar**|DCG normalleştirilmesi, ölçümün farklı uzunluklardan oluşan derecelendirme listeleri için karşılaştırılmasını sağlar|**1 ' e yakın değerler daha iyidir**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Anomali algılama için değerlendirme ölçümleri

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
|**ROC eğrisi altındaki alan**|Alıcı işleci eğrisinin altındaki alan, modelin anormal ve olağan veri noktalarını ne kadar iyi ayırdığına ilişkin ölçüm ölçer.|**1 ' e yakın değerler daha iyidir**. Yalnızca 0,5 ' den büyük değerler modelin verimliliğini gösterir. 0,5 veya altındaki değerler, modelin, anormal ve normal kategorilere göre rastgele bir şekilde giriş ayırmasından daha iyi olmadığını gösterir|
|**Algılama oranı yanlış pozitif sayı**|Hatalı pozitif sayı olan algılama oranı, her bir yanlış pozitif tarafından dizin oluşturulan bir test kümesindeki toplam anomali sayısına doğru şekilde tanımlanan anomali sayısının oranıdır. Diğer bir deyişle, her bir yanlış pozitif öğe için yanlış pozitif sayı değerinde algılama oranı için bir değer vardır.|**1 ' e yakın değerler daha iyidir**. Yanlış pozitif sonuç yoksa, bu değer 1 ' dir|
