---
title: Makine öğrenimi sözlüğü
description: Özel Modellerinizi ML.NET oluştururken, yararlı olan önemli makine öğrenimi terimleri sözlüğü.
ms.custom: seodec18
ms.date: 03/05/2019
ms.openlocfilehash: a3f94f2dedbe620c4d5c2bed2af99471572a91e5
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063677"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Machine learning önemli terimler sözlüğü

Özel Modellerinizi ML.NET oluştururken, yararlı olan önemli makine öğrenimi terimleri derlenmesini listesidir.

> [!NOTE]
> Bu belge, şu anda Önizleme aşamasında olan ML.NET ifade eder. Malzeme değişiklik gösterebilir. Daha fazla bilgi için [ML.NET giriş](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

## <a name="accuracy"></a>Doğruluğu

İçinde [sınıflandırma](#classification), doğruluğunu test Kümedeki öğelerin toplam sayısını bölü doğru sınıflandırılmış öğeleri sayısıdır. 1 (en doğru) 0 (doğru az) arasında değişir. Doğruluk model performansını değerlendirme ölçümlerini biridir. İle birlikte düşünün [duyarlık](#precision), [geri çağırma](#recall), ve [F puanı](#f-score).

## <a name="area-under-the-curve-auc"></a>Eğriyi (AUC) alanında

İçinde [ikili sınıflandırma](#binary-classification), hatalı pozitif sonuç oranına (x ekseni) karşı gerçek pozitif sonuç oranına (y) çizer eğri altındaki alan değer olan bir değerlendirme ölçümü. 0,5 (kötü) 1 (iyi) aralıkları. Olarak da bilinen alanında ROC eğrisi, yani, alıcı özellik eğrisi çizer. Daha fazla bilgi için [karakteristik işletim alıcı](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) wikipedia makalesi.

## <a name="binary-classification"></a>İkili sınıflandırma

A [sınıflandırma](#classification) case nerede [etiket](#label) yalnızca bir tanesi iki sınıfları. Daha fazla bilgi için [ikili sınıflandırma](tasks.md#binary-classification) bölümünü [makine öğrenimi görevlerini](tasks.md) konu.

## <a name="calibration"></a>Ayarlama

Ayarlama ikili ve çok sınıflı sınıflandırma için bir sınıf üyeliğini üzerine bir ham puan eşleme işlemidir. Bazı ML.NET Eğitmenler sahip bir `NonCalibrated` soneki. Bu algoritmalar sınıfı olasılığı eşlenmelidir bir ham puan üretir. 

## <a name="catalog"></a>Katalog 

ML.NET içinde bir katalog uzantı işlevleri, bir ortak amacına göre gruplandırılmış oluşan bir koleksiyondur.

Örneğin, her bir makine öğrenme görev (ikili Sınıflandırma, regresyon, sıralama vb.) kullanılabilir makine öğrenimi algoritmaları (Eğitmenler) oluşan bir katalog sahiptir. İkili sınıflandırma Eğitmenler için katalog: <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>.

## <a name="classification"></a>Sınıflandırma

Bir kategori tahmin etmek için veri kullanıldığında [denetimli makine öğrenimi](#supervised-machine-learning) görevi, sınıflandırma çağrılır. [İkili sınıflandırma](#binary-classification) yalnızca iki kategorisi (örneğin, bir 'cat' veya 'dog' resmi görüntü sınıflandırma) tahmin etmeye ifade eder. [Sınıflı sınıflandırma](#multiclass-classification) birden çok kategori (örneğin, belirli bir köpek resmi görüntü sınıflandırma) tahmin etmeye ifade eder.

## <a name="coefficient-of-determination"></a>Katsayısı

İçinde [regresyon](#regression), veri modeli ne kadar iyi uyduğunu gösteren bir değerlendirme ölçümü. 1 Aralık 0. Değeri 0 anlamına gelir veri rastgele veya başka türlü modele sığamıyorsa. Değeri model verileri tam olarak eşleşen 1 anlamına gelir. Bu genellikle r adlandırılır<sup>2</sup>, R<sup>2</sup>, veya r karesi alınmış.

## <a name="data"></a>Veri

Uygulama öğrenimi herhangi bir makineye merkezi verilerdir. ML.NET içinde veri tarafından temsil edilen <xref:Microsoft.ML.IDataView> nesneleri. Veri nesneleri görüntüle:
- sütun ve satırlardan oluşur
- Gevşek, yani değerlendirilir bir işlem için çağırdığında, yalnızca veri yükleme
- türü, biçimi ve her sütun uzunluğunu tanımlayan bir şema içerir

## <a name="estimator"></a>Tahmin aracı

Bir sınıfta uygulayan ML.NET <xref:Microsoft.ML.IEstimator`1> arabirimi.

Bir tahmin dönüşümünün (veri hazırlama dönüştürme ve machine learning modeli eğitimi dönüştürme) bir özelliğidir. Estimators bir işlem hattı dönüşümlerinin birbirine zincirlenebilir. Bir tahmin veya estimators işlem hattı parametrelerinin öğrenilen olduğunda <xref:Microsoft.ML.IEstimator`1.Fit*> çağrılır. Sonucu <xref:Microsoft.ML.IEstimator`1.Fit*> olduğu bir [Transformer](#transformer).

## <a name="extension-method"></a>Genişletme yöntemi

Bir sınıf bir parçasıdır ancak sınıf dışında tanımlanan bir .NET yöntemi. Genişletme yönteminin ilk parametresi statik bir değer `this` genişletme yöntemini ait olduğu sınıf başvurusu.

Genişletme yöntemleri oluşturulurken sıkça kullanılır ML.NET örneklerini oluşturmak için [estimators](#estimator).

## <a name="feature"></a>Özellik

Ölçülen, genellikle bir sayısal (çift) değer olguya, ölçülebilir bir özelliği. Birden çok özellik olarak ifade edilir bir **özellik vektör** ve tipik olarak depolanan `double[]`. Özellikler, ölçülen olguya önemli özelliklerini tanımlayın. Daha fazla bilgi için [özellik](https://en.wikipedia.org/wiki/Feature_(machine_learning)) wikipedia makalesi.

## <a name="feature-engineering"></a>Özellik mühendisliği

Özellik Mühendisliği olan bir dizi tanımlamayı gerektiriyorsa işlem [özellikleri](#feature) ve başka bir deyişle, kullanılabilir olguya veri özelliği vektörlerinden üreten özelliği ayıklama yazılım geliştirme. Daha fazla bilgi için [özellik Mühendisliği](https://en.wikipedia.org/wiki/Feature_engineering) wikipedia makalesi.

## <a name="f-score"></a>F-puanı

İçinde [sınıflandırma](#classification), dengeleyen bir değerlendirme ölçümü [duyarlık](#precision) ve [geri çağırma](#recall).

## <a name="hyperparameter"></a>Hiper parametre

Bir makine öğrenimi algoritmasının parametresi. Bir karar ormanı ya da bir gradyan düşüşü algoritması adım boyutunu almak için ağaçları sayısı verilebilir. Değerleri *Hiperparametreleri* modeli eğitmek önce ayarlanır ve bir karar ağacı veya bir doğrusal regresyon modeli ağırlıkları karşılaştırma işaret işlevinin parametreleri tahmin, örneğin, bulma işlemini yönetir . Daha fazla bilgi için [hiper parametre](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) wikipedia makalesi.

## <a name="label"></a>Etiketle

Machine learning modeli tahmin öğesi. Örneğin, köpek ve gelecekteki bir hisse senedi fiyatı türü.

## <a name="log-loss"></a>Günlük kaybı

İçinde [sınıflandırma](#classification), bir sınıflandırıcı doğruluğunu belirtir bir değerlendirme ölçümü. Daha küçük günlük kaybı olduğunu daha doğru bir sınıflandırıcıdır.

## <a name="loss-function"></a>Kayıp işlevi

Eğitim etiket değerlerini ve model tarafından yapılan tahmin arasındaki fark kaybı işlevidir. Model parametreleri kaybı işlevi en aza indirerek tahmin edilir.

Farklı eğitmenler farklı kaybı işlevleri ile yapılandırılabilir.

## <a name="mean-absolute-error-mae"></a>Mean Absolute error (MAE)

İçinde [regresyon](#regression), model hatası tahmin edilen arasındaki uzaklığı olduğu tüm model hataları ortalamadır bir değerlendirme ölçümü [etiket](#label) değeri ve doğru etiket değeri.

## <a name="model"></a>Model

Geleneksel olarak, tahmin işlev parametreleri. Örneğin, Ağırlıklar bir doğrusal regresyon modeli veya bir karar ağacında bir bölme noktalarını. ML.NET içinde bir modeli tahmin etmek gerekli tüm bilgileri içerir. [etiket](#label) bir etki alanı nesnenin (örneğin, görüntü veya metin). Başka bir deyişle, ML.NET modelleri tahmin işlevi için parametreleri yanı sıra gerekli özellik kazandırma sayesinde adımları içerir.

## <a name="multiclass-classification"></a>Sınıflı sınıflandırma

A [sınıflandırma](#classification) case nerede [etiket](#label) üç veya daha fazla sınıf dışında biridir. Daha fazla bilgi için [sınıflı sınıflandırma](tasks.md#multiclass-classification) bölümünü [makine öğrenimi görevlerini](tasks.md) konu.

## <a name="n-gram"></a>N-gram

Bir metin veri özelliği ayıklama düzeni: N sözcük herhangi bir dizi kapatır içine bir [özellik](#feature) değeri.

## <a name="numerical-feature-vector"></a>Sayısal özellik vektör

A [özellik](#feature) yalnızca sayısal değerlerini içeren vektör. Bu benzer `double[]`.

## <a name="pipeline"></a>İşlem hattı

Tüm işlemlerin bir veri kümesi modeline uyacak şekilde gerekli. Bir işlem hattı, verileri içeri aktarma, dönüştürme, özellik kazandırma sayesinde ve adımları öğrenme oluşur. Bir işlem hattı eğitildi sonra bir modele kapatır.

## <a name="precision"></a>Duyarlık

İçinde [sınıflandırma](#classification), duyarlık bir sınıf için o sınıfa ait öğeleri sınıfa ait olarak tahmin edilen toplam sayısına göre bölünmüş olarak doğru şekilde tahmin edilen öğeleri sayısıdır.

## <a name="recall"></a>Geri çekme

İçinde [sınıflandırma](#classification), bir sınıf için bir geri çağırma o sınıfa ait gerçekten sınıfına ait öğeleri toplam sayısına göre bölünmüş olarak doğru şekilde tahmin edilen öğeleri sayısıdır.

## <a name="regularization"></a>Düzenleme

 Günlüklerde modelleme işlemi çok karmaşık bir Doğrusal model penalizes. Kurallaştırma iki tür vardır:

- Önemsiz özellikleri için ağırlıkları L_1 $$ Kurallaştırma sıfırlar. Bu tür bir düzenli hale getirme sonra kaydedilmiş modelin boyutundan daha küçük olabilir.
- Önemsiz özellik ağırlık aralığının L_2 $$ Kurallaştırma en aza indirir, bu daha genel bir işlemdir ve aykırı değerleri için daha az duyarlı.

## <a name="regression"></a>Regresyon

A [denetimli makine öğrenimi](#supervised-machine-learning) çıkış olduğu gerçek bir değer, örneğin, iki görev. Hisse senedi fiyatlarını tahmin etme örneklerindendir. Daha fazla bilgi için [regresyon](tasks.md#regression) bölümünü [makine öğrenimi görevlerini](tasks.md) konu.

## <a name="relative-absolute-error"></a>Göreli mutlak hata

İçinde [regresyon](#regression), tüm mutlak hataların toplamı bir değerlendirme ölçümü bölünmüş arasındaki doğru uzaklıkları toplamına göre [etiket](#label) değerleri ve ortalama tüm etiket değerleri düzeltin.

## <a name="relative-squared-error"></a>Göreli karesi alınmış hata

İçinde [regresyon](#regression), tüm toplamı bir değerlendirme ölçümü doğru arasındaki karesi alınmış uzaklıkları toplamına göre bölünmüş mutlak hataların karesi alınmış [etiket](#label) değerleri ve ortalama tüm etiket değerleri düzeltin.

## <a name="root-of-mean-squared-error-rmse"></a>Kök ortalama karesi alınmış hata (RMSE)

İçinde [regresyon](#regression), kareler hataların ortalama kare kökünün bir değerlendirme ölçümü.

## <a name="supervised-machine-learning"></a>Denetimli makine öğrenimi

Machine learning istenen modeli henüz-görünmeyen veri etiketi tahmin eden bir alt sınıfı. Sınıflandırma, regresyon ve yapılandırılmış tahmin verilebilir. Daha fazla bilgi için [denetimli öğrenme](https://en.wikipedia.org/wiki/Supervised_learning) wikipedia makalesi.

## <a name="training"></a>Eğitim

Tanımlama işlemi bir [modeli](#model) belirli bir eğitim veri kümesi için. Bir Doğrusal model için ağırlıkları bulma anlamına gelir. Bir ağaç için bölme noktalarını tanımlayan içerir.

## <a name="transformer"></a>Transformer

Uygulayan bir ML.NET sınıf <xref:Microsoft.ML.ITransformer> arabirimi.

Bir tane dönüştüren <xref:Microsoft.ML.IDataView> diğeriyle birleştirmek. Bir eğitim tarafından oluşturulan bir [estimator](#estimator), veya bir tahmin işlem hattı. 

## <a name="unsupervised-machine-learning"></a>Denetimsiz makine öğrenimi

Bir alt sınıf makine öğrenimi ve istenen modeli gizli (veya görünmeyen) yapısını verileri bulur. Kümeleme, konu modelleme ve boyut düzeyi azaltma verilebilir. Daha fazla bilgi için [Denetimsiz öğrenme](https://en.wikipedia.org/wiki/Unsupervised_learning) wikipedia makalesi.
