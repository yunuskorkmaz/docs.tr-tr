---
title: Machine Learning sözlüğü
description: Makine öğrenimi terimleri içeren sözlük.
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.prod: dotnet-ml
ms.devlang: dotnet
manager: wpickett
ms.openlocfilehash: 332d9e14bea165992f9f00b048286e185269ea79
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "35017302"
---
# <a name="machine-learning-glossary"></a>Machine learning sözlüğü

Aşağıdaki özel Modellerinizi yapı oldukça faydalıdır önemli makine öğrenimi terimleri derlenmesini listesidir.

## <a name="accuracy"></a>Doğruluk

İçinde [sınıflandırma](#classification), doğruluk, doğru olarak sınıflandırılmış öğeleri bölü sınama kümesi öğelerde toplam sayısı numarasıdır. 0 (en az doğru) aralığından 1 (en doğru). Doğruluk modelinizi performansını değerlendirme ölçümlerini biridir. İle birlikte düşünün [duyarlık](#precision), [geri çağırma](#recall), ve [F-score](#f-score).

İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.

## <a name="area-under-the-curve-auc"></a>Eğriyi (AUC) alanında

İçinde [ikili sınıflandırma](#binary-classification), doğru pozitif sonuç oranı (y) çizer eğri alanında hatalı pozitif sonuç oranı (x ekseni) karşı değeri bir değerlendirme ölçümü. 0,5 (en kötü) 1 (iyi) aralıkları. Olarak da bilinen alanı ROC eğrisi, yani, özellik eğri işletim alıcı altında. Daha fazla bilgi için bkz: [karakteristiğini işletim alıcı](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) makale wikipedia'da.

İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.

## <a name="binary-classification"></a>ikili sınıflandırma

A [sınıflandırma](#classification) durumda nerede [etiket](#label) yalnızca bir dışı iki sınıfları. Daha fazla bilgi için bkz: [ikili sınıflandırma](https://en.wikipedia.org/wiki/Binary_classification) makale wikipedia'da.

## <a name="classification"></a>Sınıflandırma

Verileri bir kategori tahmin etmek için kullanıldığında, [denetimli makine öğrenme](#supervised-machine-learning) görev sınıflandırma çağrılır. [İkili sınıflandırma](#binary-classification) yalnızca iki kategorisi (örneğin, bir görüntü resmini 'Kat' veya 'köpek' sınıflandırma) tahmin etmeye için başvuruyor. [Çok sınıflı sınıflandırma](#multiclass-classification) (örneğin, belirli bir köpek bir resim olarak görüntüyü sınıflandırma) birden çok kategori tahmin için başvuruyor.

## <a name="coefficient-of-determination"></a>Katsayısı

İçinde [regresyon](#regression), veri modeli ne kadar iyi uyduğunu gösteren bir değerlendirme ölçümü. 1 aralığı 0'dan. Veri rastgele veya başka türlü 0 anlamına gelir değerini modele sığamıyorsa. Bir değer model verileri tam olarak eşleşen 1 anlamına gelir. Bu genellikle r adlandırılır<sup>2</sup>, R<sup>2</sup>, veya r karesi alınmış.

İlgili ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.

## <a name="feature"></a>Özellik

Ölçülen, olguya genellikle sayısal (double) değeri, ölçülebilir bir özelliği. Birden çok özellik denir bir **özelliği vektör** ve tipik olarak depolanan `double[]`. Özellikleri ölçülen olguya önemli özelliklerini tanımlar. Daha fazla bilgi için bkz: [özelliği](https://en.wikipedia.org/wiki/Feature_(machine_learning)) makale wikipedia'da.

## <a name="feature-engineering"></a>Özellik Mühendisliği

Özellik Mühendisliği işlemidir kümesini tanımlama içeren [özellikleri](#feature) ve başka bir deyişle, özellik vektörlerinin kullanılabilir olguya verilerden üreten yazılım özelliği ayıklama geliştirme. Daha fazla bilgi için bkz: [özellik Mühendisliği](https://en.wikipedia.org/wiki/Feature_engineering) makale wikipedia'da.

## <a name="f-score"></a>F-score

İçinde [sınıflandırma](#classification), dengeleyen bir değerlendirme ölçümü [duyarlık](#precision) ve [geri çağırma](#recall).

İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.

## <a name="hyperparameter"></a>Hyperparameter

Makine öğrenme algoritmasını parametresi. Örnekler karar orman ya da bir gradyan düşüşü algoritması adım boyutunda öğrenmek için ağaçları sayısını içerir. Değerleri *Hyperparameters* eğitim modeli önce ayarlanır ve örneğin, tahmin işlevinde parametre bulma işleminin karar ağacı ya da doğrusal regresyon modeli ağırlıkları karşılaştırma işaret yöneten . Daha fazla bilgi için bkz: [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) wikipedia'da makalesi.

## <a name="label"></a>Etiketle

Makine öğrenimi modeline tahmin öğesi. Örneğin, köpek veya gelecekteki bir stok fiyat türü.

## <a name="log-loss"></a>Günlük kaybı

İçinde [sınıflandırma](#classification), bir değerlendirme ölçümü sınıflandırıcı doğruluğunu belirtir. Daha küçük günlük kaybı, daha doğru bir sınıflandırıcı olmasıdır.

İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.

## <a name="mean-absolute-error-mae"></a>Ortalama mutlak hata (MAE)

İçinde [regresyon](#regression), tüm model hataların ortalaması modeli hata tahmin edilen arasındaki uzaklığı olduğu bir değerlendirme ölçümü [etiket](#label) değeri ve doğru etiket değeri.

İlgili ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.

## <a name="model"></a>Model

Geleneksel olarak, tahmin işlevinde parametreleri. Örneğin, ağırlıkları doğrusal regresyon modeli veya karar ağacında bir bölme noktalarını. ML.NET içinde bir modeli tahmin etmek gerekli tüm bilgileri içerir. [etiket](#label) bir etki alanı nesnesinin (örneğin, görüntü veya metin). Başka bir deyişle, ML.NET modelleri tahmin işlevi için parametre yanı sıra gerekli featurization adımları içerir.

## <a name="multiclass-classification"></a>çok sınıflı sınıflandırma

A [sınıflandırma](#classification) durumda nerede [etiket](#label) üç veya daha fazla sınıf dışında biridir. Daha fazla bilgi için bkz: [çok sınıflı sınıflandırma](https://en.wikipedia.org/wiki/Multiclass_classification) makale wikipedia'da.

## <a name="n-gram"></a>N-gram

Metin verileri için bir özellik ayıklama şeması: N sözcük herhangi bir dizi kapatır içine bir [özelliği](#feature) değeri.

## <a name="numerical-feature-vector"></a>Sayısal özellik vektör

A [özelliği](#feature) yalnızca sayısal değerleri içeren vektör. Bu benzer `double[]`.

## <a name="pipeline"></a>Ardışık Düzen

Tüm işlemlerini bir veri kümesi için bir model sığması gerekli. Bir ardışık düzen veri içeri aktarma, dönüştürme, featurization ve adımları öğrenme oluşur. Bir işlem hattı eğitildi sonra bir modele etkinleştirir.

## <a name="precision"></a>Duyarlık

İçinde [sınıflandırma](#classification), bir sınıf için duyarlık o sınıfın ait toplam sınıfına ait olarak tahmin öğeleri bölü sayısı gibi doğru şekilde tahmin öğelerin sayısıdır.

İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.

## <a name="recall"></a>Geri çağırma

İçinde [sınıflandırma](#classification), bir sınıf için geri çağırma o sınıfın ait toplam gerçekte sınıfına ait öğeleri bölü sayısı gibi doğru şekilde tahmin öğelerin sayısıdır.

İlgili ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.

## <a name="regression"></a>regresyon

A [denetimli makine öğrenme](#supervised-machine-learning) çıkış olduğu gerçek bir değer, örneğin, çift görev. Hisse senedi fiyatları tahmin etmeye örnekler.

## <a name="relative-absolute-error"></a>Göreli mutlak hata

İçinde [regresyon](#regression), tüm mutlak hataların toplamıdır bir değerlendirme ölçümü bölünmüş doğru arasındaki uzaklıkları toplamına [etiket](#label) değerler ve tüm etiket değerlerini düzeltmek ortalamasını.

## <a name="relative-squared-error"></a>Göreli karesi alınmış hata

İçinde [regresyon](#regression), tüm toplamı bir değerlendirme ölçümü doğru arasındaki karesi alınmış uzaklıkları toplamını bölü mutlak hataların karesi alınmış [etiket](#label) değerler ve tüm etiket değerlerini düzeltmek ortalamasını.

## <a name="root-of-mean-squared-error-rmse"></a>Hata (RMSE) kök değerlerin ortalamasının kare

İçinde [regresyon](#regression), hataları kareleri Ortalama kare kökü bir değerlendirme ölçümü.

İlgili ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.

## <a name="supervised-machine-learning"></a>Denetimli makine öğrenme

Machine learning istenen modeli henüz-görünmeyen veri etiketi tahmin sınıfıdır. Sınıflandırma, regresyon ve yapılandırılmış tahmin örnek verilebilir. Daha fazla bilgi için bkz: [denetimli öğrenme](https://en.wikipedia.org/wiki/Supervised_learning) makale wikipedia'da.

## <a name="training"></a>Eğitim

Tanımlama işlemi bir [modeli](#model) verilen eğitim veri kümesi için. Doğrusal bir model için ağırlıkları bulma anlamına gelir. Bir ağaç için tanımlayıcı bölme noktalarını içerir.

## <a name="transform"></a>Dönüştürme

A [ardışık düzen](#pipeline) verileri dönüştüren bileşeni. Sayıda vektör örneğin metinden.

## <a name="unsupervised-machine-learning"></a>Denetimsiz makine öğrenme

Machine learning istenen model verileri gizli (veya görünmeyen) yapısı bulursa sınıfıdır. Örnekler, kümeleme, konu modelleme ve boyut azaltma içerir. Daha fazla bilgi için bkz: [Denetimsiz öğrenme](https://en.wikipedia.org/wiki/Unsupervised_learning) makale wikipedia'da.
