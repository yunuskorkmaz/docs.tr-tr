---
title: Makine öğrenimi sözlüğü
description: Özel modellerinizi ML.NET oluştururken yararlı olan önemli makine öğrenimi terimlerinin sözlüğü.
ms.topic: reference
ms.date: 07/31/2019
ms.openlocfilehash: 32ccb6df1cb08db45ebd25a0d1c0ea4396a6c50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398939"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Önemli terimlerin makine öğrenimi sözlüğü

Aşağıdaki liste, ML.NET özel modellerinizi oluştururken yararlı olan önemli makine öğrenimi terimlerinin bir derlemesidir.

## <a name="accuracy"></a>Doğru -luk

[Sınıflandırmada](#classification)doğruluk, test kümesindeki toplam madde sayısına bölünen doğru sınıflanmış maddelerin sayısıdır. 0 (en az doğru) ile 1 (en doğru) arasında değişir. Doğruluk, model performansının değerlendirme ölçümlerinden biridir. [Hassas](#precision), [geri çağırma](#recall)ve [F-skoru](#f-score)ile birlikte düşünün.

## <a name="area-under-the-curve-auc"></a>Eğrinin altındaki alan (AUC)

[İkili sınıflandırmada,](#binary-classification)eğrinin altındaki alanın değeri olan bir değerlendirme ölçüsü, doğru pozitif oranını (y ekseninde) yanlış pozitif oranına (x ekseninde) göre çizer. 0,5 (en kötü) ile 1 (en iyi) arasında değişir. ROC eğrisinin altındaki alan olarak da bilinir, yani alıcı çalışma karakteristik eğrisi. Daha fazla bilgi [için,](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) Wikipedia'daki Alıcı işletim karakteristik makalesine bakın.

## <a name="binary-classification"></a>İkili sınıflandırma

[Etiketin](#label) iki sınıftan yalnızca biri olduğu bir [sınıflandırma](#classification) örneği. Daha fazla bilgi için Makine [öğrenme görevleri](tasks.md) konusunun [İkili sınıflandırma](tasks.md#binary-classification) bölümüne bakın.

## <a name="calibration"></a>Kalibrasyon

Kalibrasyon, ikili ve çok sınıflı sınıflandırma için ham bir puanı sınıf üyeliğine eşleme işlemidir. Bazı ML.NET eğitmenlerinin sonekleri `NonCalibrated` vardır. Bu algoritmalar, daha sonra bir sınıf olasılığı eşlenen gereken bir ham puan üretir.

## <a name="catalog"></a>Katalog

ML.NET olarak, katalog ortak bir amaca göre gruplanmış uzantı işlevleri koleksiyonudur.

Örneğin, her makine öğrenme görevi (ikili sınıflandırma, regresyon, sıralama vb) kullanılabilir makine öğrenme algoritmaları (eğitmenler) bir katalog vardır. İkili sınıflandırma eğitmenleri için <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>katalog: .

## <a name="classification"></a>Sınıflandırma

Veriler bir kategoriyi tahmin etmek için kullanıldığında, [denetlenen makine öğrenimi](#supervised-machine-learning) görevi sınıflandırma olarak adlandırılır. [İkili sınıflandırma](#binary-classification) yalnızca iki kategoriyi tahmin etmek anlamına gelir (örneğin, bir resmi 'kedi' veya 'köpek' resmi olarak sınıflandırmak). [Çok sınıflı sınıflandırma,](#multiclass-classification) birden çok kategoriyi tahmin etmek anlamına gelir (örneğin, bir görüntüyü belirli bir köpek ırkının resmi olarak sınıflandırırken).

## <a name="coefficient-of-determination"></a>Tespit katsayısı

[Regresyonda,](#regression)verilerin bir modele ne kadar iyi uyduğunu gösteren bir değerlendirme ölçüsü. 0 ile 1 arasında değişir. 0 değeri, verilerin rastgele olduğu veya modele başka bir şekilde sığamayacağı anlamına gelir. 1 değeri, modelin verilerle tam olarak eşleştiğini anlamına gelir. Bu genellikle r<sup>2</sup>, R<sup>2</sup>, veya r-kare olarak adlandırılır.

## <a name="data"></a>Veriler

Veriler herhangi bir makine öğrenimi uygulamasının merkezidir. ML.NET veriler nesneler tarafından <xref:Microsoft.ML.IDataView> temsil edilir. Veri görünümü nesneleri:

- sütun ve satırlardan oluşur
- lazily değerlendirilir, yani sadece bir operasyon için çağırır veri yüklemek
- her sütunun türünü, biçimini ve uzunluğunu tanımlayan bir şema içerir

## <a name="estimator"></a>Tahmincisi

<xref:Microsoft.ML.IEstimator%601> Arabirimi uygulayan ML.NET bir sınıf.

Bir tahminci bir dönüşüm (hem veri hazırlama dönüşümü ve makine öğrenimi modeli eğitim dönüşümü) bir belirtimidir. Tahminciler bir dönüşüm ler zincirine zincirlenebilir. Bir tahmincinin veya tahmincilerin ardışık <xref:Microsoft.ML.IEstimator%601.Fit%2A> parametreleri çağrıldığında öğrenilir. Bunun sonucu <xref:Microsoft.ML.IEstimator%601.Fit%2A> bir [Transformatördür.](#transformer)

## <a name="extension-method"></a>Uzatma yöntemi

Sınıfın bir parçası olan ancak sınıfın dışında tanımlanan bir .NET yöntemi. Uzantı yönteminin ilk parametresi, uzantı yönteminin ait olduğu sınıfa statik `this` bir başvurudur.

Uzantı yöntemleri, [tahmincilerin](#estimator)örneklerini oluşturmak için ML.NET yaygın olarak kullanılır.

## <a name="feature"></a>Özellik

Ölçülen fenomenölçülebilir bir özelliği, genellikle bir sayısal (çift) değer. Birden çok özellik **Özellik vektörü** olarak adlandırılır `double[]`ve genellikle . Özellikler ölçülen fenomenin önemli özelliklerini tanımlar. Daha fazla bilgi için Vikipedi'deki [Özellik](https://en.wikipedia.org/wiki/Feature_(machine_learning)) makalesine bakın.

## <a name="feature-engineering"></a>Özellik mühendisliği

Özellik mühendisliği, bir dizi [özelliği](#feature) tanımlamayı ve mevcut fenomen verilerinden, yani özellik çıkarmadan özellik vektörleri üreten yazılımlar geliştirmeyi içeren bir süreçtir. Daha fazla bilgi için Vikipedi'deki [Özellik mühendisliği](https://en.wikipedia.org/wiki/Feature_engineering) makalesine bakın.

## <a name="f-score"></a>F puanı

[Sınıflandırmada,](#classification) [hassasiyeti](#precision) ve geri [çağırmayı](#recall)dengeleyen bir değerlendirme ölçüsü.

## <a name="hyperparameter"></a>Hiperparametre

Makine öğrenme algoritmasının parametresi. Örnekler, karar ormanında öğrenilmesi gereken ağaç sayısını veya degrade libir alçalma algoritmasındaki adım boyutunu içerir. *Hiperparametrelerin* değerleri modeli eğitmeden önce ayarlanır ve tahmin işlevinin parametrelerini bulma işlemini yönetir, örneğin, bir karar ağacındaki karşılaştırma noktaları veya doğrusal bir regresyon modelindeki ağırlıklar. Daha fazla bilgi için Vikipedi'deki [Hiperparametre](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) makalesine bakın.

## <a name="label"></a>Etiketle

Makine öğrenme modeli ile tahmin edilecek eleman. Örneğin, köpek cins veya gelecekteki bir hisse senedi fiyatı.

## <a name="log-loss"></a>Günlük kaybı

[Sınıflandırmada,](#classification)bir sınıflandırıcının doğruluğunu karakterize eden bir değerlendirme ölçüsü. Küçük günlük kaybı, daha doğru bir sınıflandırıcı olduğunu.

## <a name="loss-function"></a>Kayıp fonksiyonu

Kayıp işlevi, eğitim etiketi değerleri ile model tarafından yapılan tahmin arasındaki farktır. Modelin parametreleri kayıp işlevini en aza indirerek tahmin edilir.

Farklı eğitmenler farklı kayıp fonksiyonları ile yapılandırılabilir.

## <a name="mean-absolute-error-mae"></a>Ortalama mutlak hata (MAE)

[Regresyonda,](#regression)model hatasının öngörülen etiket değeri ile doğru [etiket](#label) değeri arasındaki uzaklık olduğu tüm model hatalarının ortalaması olan bir değerlendirme ölçüsüdür.

## <a name="model"></a>Model

Geleneksel olarak, tahmin işlevi için parametreler. Örneğin, doğrusal bir regresyon modelindeki ağırlıklar veya karar ağacındaki bölünmüş noktalar. ML.NET, bir model etki alanı nesnesinin [etiketini](#label) (örneğin, resim veya metin) tahmin etmek için gereken tüm bilgileri içerir. Bu, ML.NET modellerinin gerekli olan featurization adımlarını ve tahmin işlevi için parametreleri içerdiği anlamına gelir.

## <a name="multiclass-classification"></a>Çok sınıflı sınıflandırma

[Etiketin](#label) üç veya daha fazla sınıftan biri olduğu bir [sınıflandırma](#classification) örneği. Daha fazla bilgi için Makine öğrenme [görevleri](tasks.md) konusunun [Çok Sınıflı sınıflandırma](tasks.md#multiclass-classification) bölümüne bakın.

## <a name="n-gram"></a>N-gram

Metin verileri için özellik ayıklama düzeni: Herhangi bir N sözcük dizisi [bir özellik](#feature) değerine dönüşür.

## <a name="normalization"></a>Normalleştirme

Normalleştirme, kayan nokta verilerini 0 ile 1 arasındaki değerlere ölçekleme işlemidir. ML.NET kullanılan eğitim algoritmalarının çoğu, giriş özelliği verilerinin normalleştirilmesini gerektirir. ML.NET [normalleştirme için](transforms.md#normalization-and-scaling) bir dizi dönüşüm sağlar

## <a name="numerical-feature-vector"></a>Sayısal özellik vektörü

Yalnızca sayısal değerlerden oluşan bir [özellik](#feature) vektörü. Bu benzer `double[]`.

## <a name="pipeline"></a>İşlem hattı

Bir modeli veri kümesine sığdırmak için gereken tüm işlemler. Bir ardışık veri alma, dönüştürme, featurization ve öğrenme adımlarından oluşur. Bir boru hattı eğitildikten sonra, bir modele dönüşür.

## <a name="precision"></a>Duyarlık

[Sınıflandırmada,](#classification)bir sınıfın kesinliği, sınıfa ait olduğu tahmin edilen toplam madde sayısına bölünerek o sınıfa ait olarak doğru olarak tahmin edilen öğe sayısıdır.

## <a name="recall"></a>Geri Çağırma

[Sınıflandırmada,](#classification)bir sınıfın geri çağırması, sınıfa ait toplam madde sayısına bölünerek o sınıfa ait olarak doğru olarak tahmin edilen öğelerin sayısıdır.

## <a name="regularization"></a>Düzenlileştirme

 Düzenlileştirme, doğrusal bir modeli çok karmaşık olduğu için cezalandırır. İki tür düzenlileştirme vardır:

- $L_1$ normalleştirme önemsiz özellikler için ağırlıkları sıfırlar. Kaydedilen modelin boyutu, bu tür bir düzenlilleştirmeden sonra küçülebilir.
- $L_2$ düzenlileştirme önemsiz özellikler için ağırlık aralığını en aza indirir. Bu daha genel bir süreçtir ve aykırılara karşı daha az duyarlıdır.

## <a name="regression"></a>Regresyon

Çıktının gerçek bir değer olduğu [denetlenen bir makine öğrenimi](#supervised-machine-learning) görevi, örneğin, iki katı. Buna örnek olarak hisse senedi fiyatlarını tahmin etmek verilebilir. Daha fazla bilgi için Makine öğrenme [görevleri](tasks.md) konusunun [Regresyon](tasks.md#regression) bölümüne bakın.

## <a name="relative-absolute-error"></a>Göreli mutlak hata

[Regresyonda,](#regression)doğru etiket değerleri ile tüm doğru [etiket](#label) değerlerinin ortalaması arasındaki mesafelerin toplamına bölünen tüm mutlak hataların toplamı olan bir değerlendirme ölçüsüdür.

## <a name="relative-squared-error"></a>Göreli kareli hata

[Regresyonda,](#regression)doğru etiket değerleri ile tüm doğru [etiket](#label) değerlerinin ortalaması arasındaki kareli mesafelerin toplamına bölünen tüm karemutlak hataların toplamı olan bir değerlendirme ölçüsüdür.

## <a name="root-of-mean-squared-error-rmse"></a>Ortalama kare hatanın kökü (RMSE)

[Regresyon,](#regression)hataların kareleri ortalamasının kare kökü olan bir değerlendirme ölçüsüdür.

## <a name="scoring"></a>Puanlama

Puanlama, eğitimli bir makine öğrenme modeline yeni veriler uygulama ve öngörüler oluşturma işlemidir. Puanlama da inferencing olarak bilinir. Modeltürüne bağlı olarak, puan ham bir değer, bir olasılık veya bir kategori olabilir.

## <a name="supervised-machine-learning"></a>Denetimli makine öğrenimi

İstenilen bir modelin henüz görünmeyen veriler için etiketi öngördüğü bir alt makine öğrenimi sınıfı. Örnekler sınıflandırma, regresyon ve yapılandırılmış tahmin içerir. Daha fazla bilgi için Vikipedi'deki [Denetimli öğrenme](https://en.wikipedia.org/wiki/Supervised_learning) makalesine bakın.

## <a name="training"></a>Eğitim

Belirli bir eğitim veri kümesi için bir [model](#model) tanımlama işlemi. Doğrusal bir model için bu ağırlıkları bulmak anlamına gelir. Bir ağaç için, bölünmüş noktaları tanımlama içerir.

## <a name="transformer"></a>Trafo

<xref:Microsoft.ML.ITransformer> Arabirimi uygulayan ML.NET sınıfı.

Bir transformatör <xref:Microsoft.ML.IDataView> birini diğerine dönüştürür. Bir transformatör, bir [tahmincinin](#estimator)veya bir tahminci boru hattının eğitilmesiyle oluşturulur.

## <a name="unsupervised-machine-learning"></a>Denetimsiz makine öğrenimi

İstenilen bir modelin verilerde gizli (veya gizli) yapıyı bulduğu makine öğrenimi alt sınıfı. Örnekler kümeleme, konu modelleme ve boyutlandırma içerir. Daha fazla bilgi için Vikipedi'deki [Denetimsiz öğrenme](https://en.wikipedia.org/wiki/Unsupervised_learning) makalesine bakın.
