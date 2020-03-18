---
title: ML.NET ölçümleri
description: ML.NET bir modelin performansını değerlendirmek için kullanılan ölçümleri anlama
ms.date: 12/17/2019
ms.openlocfilehash: 8e823fd8cc344c1b8e0ecd709b527137368cbfa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399219"
---
# <a name="evaluate-your-mlnet-model-with-metrics"></a>ML.NET modelinizi ölçümlerle değerlendirin

ML.NET bir modeli değerlendirmek için kullanılan ölçümleri anlayın.

Değerlendirme ölçümleri, bir modelin gerçekleştirdiği makine öğrenimi görevinin türüne özgür.

Örneğin, sınıflandırma görevi için model, tahmin edilen bir kategorinin gerçek kategoriyle ne kadar iyi eşleştiğini ölçerek değerlendirilir. Kümeleme için değerlendirme, kümelenmiş öğelerin birbirine ne kadar yakın olduğuna ve kümeler arasında ne kadar ayrım olduğuna bağlıdır.

## <a name="evaluation-metrics-for-binary-classification"></a>İkili Sınıflandırma için değerlendirme ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Doğru -luk** |  [Doğruluk,](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification) bir test veri kümesi ile doğru tahminlerin oranıdır. Doğru tahmin sayısının toplam giriş örneği sayısına oranıdır. Her sınıfa ait benzer sayıda örnek varsa iyi çalışır.| **1.00'a ne kadar yakınsa o kadar iyi.** Ama tam olarak 1.00 bir sorunu gösterir (genellikle: etiket / hedef sızıntısı, aşırı uydurma, ya da eğitim verileri ile test). Test verileri dengesizse (örneklerin çoğu sınıflardan birine aitolduğunda), veri kümesi küçükse veya puanlar 0,00 veya 1,00'a yaklaşırsa, doğruluk bir sınıflandırıcının etkinliğini gerçekten yakalamaz ve ek ölçümleri denetlemeniz gerekir. |
| **Auc** |    [aucROC](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) veya *Alan eğrisi altında* gerçek pozitif oranı vs yanlış pozitif oranı süpürme tarafından oluşturulan eğri altında alan ölçer.  |   **1.00'a ne kadar yakınsa o kadar iyi.** Bir modelin kabul edilebilir olması için 0,50'den büyük olması gerekir. 0,50 veya daha az AUC ile bir model değersizdir. |
| **AUCPR** | [aucPR](https://www.coursera.org/lecture/ml-classification/precision-recall-curve-rENu8) veya *Alan Hassas Geri Çağırma eğrisi eğrisi altında*: Sınıflar dengesiz olduğunda tahmin başarısının yararlı ölçüsü (yüksek oranda çarpık veri kümeleri). |  **1.00'a ne kadar yakınsa o kadar iyi.** 1,00'a yakın yüksek puanlar, sınıflandırıcının doğru sonuçları (yüksek hassasiyet) döndürderken ve tüm olumlu sonuçların çoğunluğunu (yüksek geri çağırma) geri döndürdiğini gösterir. |
| **F1 puanı** | [F1 skoru](https://en.wikipedia.org/wiki/F1_score) dengeli *F-skoru veya F-ölçümü*olarak da bilinir. Bu hassasiyet ve hatırlama nın harmonik ortalamasıdır. Hassasve Geri Çağırma arasında bir denge aramak istediğinizde F1 Puanı yararlıdır.| **1.00'a ne kadar yakınsa o kadar iyi.**  F1 skoru en iyi değeri ne kadar 1.00, en kötü puanı ise 0.00'dır. Sınıflandırıcınızın ne kadar hassas olduğunu söyler. |

İkili sınıflandırma ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Doğruluk, Hassasiyet, Geri Çağırma veya F1?](https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9)
- [İkili Sınıflandırma Ölçümleri sınıfı](xref:Microsoft.ML.Data.BinaryClassificationMetrics)
- [Hassas Geri Çağırma ve ROC Eğrileri Arasındaki İlişki](http://pages.cs.wisc.edu/~jdavis/davisgoadrichcamera2.pdf)

## <a name="evaluation-metrics-for-multi-class-classification"></a>Çok Sınıflı Sınıflandırma için değerlendirme ölçümleri

| Ölçümler   |      Açıklama      |  Aramak |
|-----------|-----------------------|-----------|
| **Mikro Doğruluk** |  [Mikro ortalama Doğruluk,](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MicroAccuracy) ortalama ölçütünün hesaplanması için tüm sınıfların katkılarını toplar. Doğru tahmin edilen örneklerin bir kısmıdır. Mikro ortalama sınıf üyeliğini hesaba katmaz. Temel olarak, her örnek sınıf çifti doğruluk ölçümüeşit katkıda bulunur. | **1.00'a ne kadar yakınsa o kadar iyi.** Çok sınıflı bir sınıflandırma görevinde, sınıf dengesizliği olabileceğinden şüpheleniyorsanız makro doğruluk yerine mikro doğruluk tercih edilir (örn. bir sınıfa diğer sınıflara göre çok daha fazla örnek olabilir).|
| **Makro-Doğruluk** | [Makro-ortalama Doğruluk](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.MacroAccuracy) sınıf düzeyinde ortalama doğruluk. Her sınıf için doğruluk hesaplanır ve makro doğruluğu bu doğrulukların ortalamasıdır. Temel olarak, her sınıf doğruluk ölçümüne eşit olarak katkıda bulunur. Azınlık sınıfları daha büyük sınıflar olarak eşit ağırlık verilir. Makro ortalama metrik, veri kümesinin içerdiği bu sınıftan kaç örnek içerse de, her sınıfa aynı ağırlığı verir. |  **1.00'a ne kadar yakınsa o kadar iyi.**  Her sınıf için ölçümü bağımsız olarak hesaplar ve sonra ortalamayı alır (dolayısıyla tüm sınıfları eşit olarak ele alır) |
| **Günlük kaybı**| [Logaritmik kayıp,](http://wiki.fast.ai/index.php/Log_Loss) tahmin girdisinin 0,00 ile 1,00 arasında bir olasılık değeri olduğu bir sınıflandırma modelinin performansını ölçer. Öngörülen olasılık gerçek etiketten farklılaştınkça günlük kaybı artar. | **0.00'a ne kadar yakınsa o kadar iyi.** Mükemmel bir model 0.00 bir günlük kaybı olurdu. Makine öğrenme modellerimizin amacı bu değeri en aza indirmektir.|
| **Günlük Kaybı Azaltma** | [Logaritmik kayıp azaltma](xref:Microsoft.ML.Data.MulticlassClassificationMetrics.LogLossReduction) rasgele bir tahmin üzerinde sınıflandırıcı avantajı olarak yorumlanabilir.| **1.00'ın mükemmel öngörüler olduğu ve 0.00'ın ortalama tahminleri gösterdiği -inf ve 1.00 aralıkları.** Örneğin, değer 0,20'ye eşitse, "doğru tahmin olasılığı rasgele tahminden %20 daha iyidir" olarak yorumlanabilir.|

Mikro-doğruluk genellikle daha iyi ML tahminlerin iş ihtiyaçları ile uyumludur. Çok sınıflı bir sınıflandırma görevinin kalitesini seçmek için tek bir metrik seçmek istiyorsanız, genellikle mikro doğruluk olmalıdır.

Örnek, bir destek bileti sınıflandırma görevi için: (destek ekiplerine gelen biletleri haritala)

- Mikro doğruluk -- gelen bilet ne sıklıkta doğru takıma sınıflandırılır?
- Makro doğruluk -- ortalama bir takım için, gelen bilet takımiçin ne sıklıkta doğrudur?

Makro-doğruluk kilolu küçük takımlar bu örnekte; yılda sadece 10 bilet alan küçük bir takım, yılda 10k biletli büyük bir takım kadar önemlidir. Bu durumda mikro-doğruluk daha iyi iş ihtiyacı ile ilişkilidir, "ne kadar zaman / para şirket benim bilet yönlendirme süreci otomatikleştirerek kaydedebilirsiniz".

Çok sınıflı sınıflandırma ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Hassas, Geri Çağırma ve F-Skorunun Mikro ve Makro ortalaması](https://rushdishams.blogspot.com/2011/08/micro-and-macro-average-of-precision.html)
- [Dengesiz Dataset ile Çok Sınıflı Sınıflandırma](https://towardsdatascience.com/machine-learning-multiclass-classification-with-imbalanced-data-set-29f6a177c1a)

## <a name="evaluation-metrics-for-regression-and-recommendation"></a>Regresyon ve Öneri için değerlendirme ölçümleri

Hem gerileme hem de öneri görevleri bir sayıyı tahmin eder. Regresyon durumunda, sayı giriş özelliklerinden etkilenen herhangi bir çıkış özelliği olabilir. Tavsiye için, sayı genellikle bir derecelendirme değeri (örneğin 1 ile 5 arasında) veya evet/hayır önerisidir (sırasıyla 1 ve 0 ile temsil edilir).

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
| **R-Kare** |  [R-kare (R2)](https://en.wikipedia.org/wiki/Coefficient_of_determination)veya *belirleme katsayısı* -inf ve 1.00 arasındaki bir değer olarak modelin tahmin gücünü temsil eder. 1.00 mükemmel bir uyum olduğu anlamına gelir ve skorları negatif olabilir, böylece uyum keyfi olarak kötü olabilir. 0,00 puan, modelin etiket için beklenen değeri tahmin ettiğini anlamına gelir. R2, gerçek test veri değerlerinin öngörülen değerlere ne kadar yakın olduğunu ölçer. | **1.00'a ne kadar yakınsa, o kadar kaliteli.** Ancak, bazen düşük R-kare değerleri (0,50 gibi) tamamen normal veya senaryo nuz için yeterince iyi olabilir ve yüksek R kare değerleri her zaman iyi değildir ve şüpheli olabilir. |
| **Mutlak kayıp** |  [Mutlak kayıp](https://en.wikipedia.org/wiki/Mean_absolute_error) veya *Ortalama mutlak hata (MAE),* tahminlerin gerçek sonuçlara ne kadar yakın olduğunu ölçer. Model hatasının, öngörülen etiket değeri ile doğru etiket değeri arasındaki mutlak uzaklık olduğu tüm model hatalarının ortalamasıdır. Bu tahmin hatası, test veri kümesinin her kaydı için hesaplanır. Son olarak, kaydedilen tüm mutlak hatalar için ortalama değer hesaplanır.| **0.00'a ne kadar yakınsa, o kadar kaliteli.** Ortalama mutlak hata, ölçülen verilerle aynı ölçeği kullanır (belirli aralıkta normalleştirilmez). Mutlak kayıp, Kare-kayıp ve RMS kaybı yalnızca aynı veri kümesinin modelleri veya benzer etiket değeri dağılımına sahip veri kümesi için modeller arasında karşılaştırma yapmak için kullanılabilir. |
| **Kare-kayıp** |  [Kare-kayıp](https://en.wikipedia.org/wiki/Mean_squared_error) veya *Ortalama Karehata (MSE)* olarak da adlandırılan *Ortalama Kare sapma (MSD)*, bir regresyon çizgisinin bir dizi test veri değerikümesine ne kadar yakın olduğunu, noktalardan gerileme çizgisine (bu mesafeler E hatalarıdır) ve bunları squaring olarak gösterir. Squaring daha büyük farklılıklara daha fazla ağırlık verir. | Her zaman negatif değildir ve **0.00'a yakın değerler daha iyidir.** Verilerinize bağlı olarak, ortalama kare hata için çok küçük bir değer elde etmek imkansız olabilir.|
| **RMS kaybı** |  [RMS kaybı](https://en.wikipedia.org/wiki/Root-mean-square_deviation) veya *Kök Ortalama Karehatası (RMSE)* *(Kök Ortalama Kare Sapması olarak*da adlandırılır), bir model tarafından öngörülen değerler ile modellenen ortamdan gözlenen değerler arasındaki farkı ölçer. RMS-loss Kare-kayıp kare kökü ve etiket olarak aynı birimler, mutlak kaybı olsa da daha büyük farklılıklara daha fazla ağırlık veren benzer vardır. Kök ortalama kare hatası genellikle deneysel sonuçları doğrulamak için klimatoloji, tahmin ve regresyon analizinde kullanılır. | Her zaman negatif değildir ve **0.00'a yakın değerler daha iyidir.** RMSD, ölçek bağımlı olduğu için veri kümeleri arasında değil, belirli bir veri kümesi için farklı modellerin tahmin hatalarını karşılaştırmak için bir doğruluk ölçüsüdür.|

Regresyon ölçümleri hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:

- [Regresyon Analizi: R-karesini nasıl yorumluyorum ve Fit İyiliğini Nasıl Değerlendiririm?](https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit)
- [Regresyon Analizinde R-kare nasıl yorumlanır?](https://statisticsbyjim.com/regression/interpret-r-squared-regression)
- [R-Kare tanımı](https://www.investopedia.com/terms/r/r-squared.asp)
- [Ortalama Karehata Tanımı](https://www.statisticshowto.datasciencecentral.com/mean-squared-error/)
- [Ortalama Kare hata ve Kök Ortalama Kare hata nedir?](https://www.vernier.com/til/1014/)

## <a name="evaluation-metrics-for-clustering"></a>Kümeleme için değerlendirme ölçümleri

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
|**Ortalama Mesafe**|Veri noktaları ile atanan kümenin merkezi arasındaki uzaklık ortalaması. Ortalama uzaklık, veri noktalarının küme santrikoitlerine olan yakınlığının bir ölçüsüdür. Kümenin ne kadar 'sıkı' olduğunun bir ölçüsüdür.|**0'a** yakın değerler daha iyidir. Ortalama uzaklık sıfıra ne kadar yakınsa, veriler o kadar kümelenir. Ancak, küme sayısı artırılırsa bu ölçümün azalacağını ve aşırı durumda (her bir veri noktasının kendi kümesi olduğu durumlarda) sıfıra eşit olacağını unutmayın.
|**Davies Bouldin Endeksi**|Küme içindeki uzaklıkların küme arasındaki uzaklıklara ortalama oranı. Küme ne kadar sıkı ve kümeler ne kadar uzaksa, bu değer o kadar düşüktür.|**0'a** yakın değerler daha iyidir. Birbirinden daha uzak ve daha az dağılmış kümeler daha iyi bir skor elde eder.|
|**Normalleştirilmiş Karşılıklı Bilgiler**|Kümeleme modelini eğitmek için kullanılan eğitim verileri de zemin gerçeği etiketleri (yani denetimli kümeleme) ile birlikte geldiğinde kullanılabilir. Normalleştirilmiş Karşılıklı Bilgiler ölçümü, benzer veri noktalarının aynı kümeye atanıp atanmadığını ve birbirinden farklı veri noktalarının farklı kümelere atanıp atanmadığını ölçer. Normalleştirilmiş karşılıklı bilgi 0 ile 1 arasında bir değerdir|**1'e** yakın değerler daha iyidir|

## <a name="evaluation-metrics-for-ranking"></a>Sıralama için değerlendirme ölçümleri

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
|**İndirimli Kümülatif Kazançlar**|İndirimli kümülatif kazanç (DCG) sıralama kalitesinin bir ölçüsüdür. İki varsayımdan türetilmiştir. Bir: Son derece alakalı öğeler sıralama sırasına göre daha yüksek görünürken daha yararlıdır. İki: Kullanışlılık, alaka düzeyini, alaka düzeyi ne kadar yüksekse, bir öğeyi o kadar kullanışlı izler. İndirimli kümülatif kazanç, sıralama sırasında belirli bir pozisyon için hesaplanır. İlgi pozisyonuna kadar sıralama dizininin logaritma tarafından bölünmüş alaka derecelendirmesini özetler. $\sum_{i=0}^{p} \frac {rel_i} {\log_{e}{i+1}}}$ Alaka düzeyi derecelendirmeleri, zemin gerçeği etiketleri olarak sıralama eğitim algoritmasına sağlanır. Sıralama tablosundaki her pozisyon için bir DCG değeri sağlanır, bu nedenle İndirimli Kümülatif **Kazançlar**adı verilir. |**Daha yüksek değerler daha iyidir**|
|**Normalleştirilmiş İndirimli Kümülatif Kazançlar**|DCG'nin normalleştirilmesi, ölçümün farklı uzunluklarda sıralama listeleri yle karşılaştırılmasına olanak tanır|**1'e yakın değerler daha iyidir**|

## <a name="evaluation-metrics-for-anomaly-detection"></a>Anomali Tespiti için değerlendirme ölçümleri

| Ölçüm   |      Açıklama      |  Aramak |
|----------|-----------------------|-----------|
|**ROC Eğrisi Altındaki Alan**|Alıcı işleci eğrisialtındaki alan, modelin anormal ve olağan veri noktalarını ne kadar iyi ayırdığını ölçer.|**1'e yakın değerler daha iyidir.** Yalnızca 0,5'ten büyük değerler modelin etkinliğini gösterir. 0,5 veya altındaki değerler, modelin girişleri anormal ve olağan kategorilere rasgele ayırmaktan daha iyi olmadığını gösterir|
|**Yanlış Pozitif Sayımda Algılama Oranı**|Yanlış pozitif sayımda algılama oranı, doğru tanımlanmış anomali sayısının, her yanlış pozitif tarafından indekslenen bir test kümesindeki toplam anomali sayısına oranıdır. Diğer bir tarihte, her yanlış pozitif öğe için yanlış pozitif sayımda algılama oranı için bir değer vardır.|**1'e yakın değerler daha iyidir.** Yanlış pozitif ler yoksa, bu değer 1|
