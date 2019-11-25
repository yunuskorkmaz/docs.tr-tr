---
title: Makine öğrenimi sözlüğü
description: ML.NET ' de özel modellerinizi oluştururken yararlı olan önemli makine öğrenimi terimlerinin bir sözlüğü.
ms.custom: seodec18
ms.topic: reference
ms.date: 07/31/2019
ms.openlocfilehash: bd4f2db701f537d5c87529115a6bd44035432534
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977293"
---
# <a name="machine-learning-glossary-of-important-terms"></a>Önemli terimlerin makine öğrenimi sözlüğü

Aşağıdaki liste, ML.NET ' de özel modellerinizi oluştururken yararlı olan önemli makine öğrenimi koşullarının bir derlenmesi.

## <a name="accuracy"></a>Veritabanınızın

[Sınıflandırmada](#classification)doğruluk, doğru sınıflandırılan öğelerin, test kümesindeki toplam öğe sayısına bölünmesiyle elde edilen sayıdır. 0 (en az doğru) ile 1 (en doğru) arasında değişir. Doğruluk, model performansının değerlendirme ölçümlerinden biridir. [Duyarlık](#precision), [geri çekme](#recall)ve [F puanı](#f-score)ile birlikte göz önünde bulundurun.

## <a name="area-under-the-curve-auc"></a>Eğri altındaki alan (AUC)

[İkili sınıflandırmada](#binary-classification), eğri altındaki alanın değeri olan bir değerlendirme ölçümü, doğru pozitif değer oranını (y ekseni üzerinde) yanlış pozitif sonuçlar oranına (x ekseninde) göre çizer. 0,5 (en kötü) ile 1 (en iyi) arasında aralıklar. Ayrıca, ROC eğrisi, yani alıcı işletim özelliği eğrisi altında alan olarak da bilinir. Daha fazla bilgi için, Vikipde yer alan [alıcı işletim özellikleri](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) makalesine bakın.

## <a name="binary-classification"></a>ikili sınıflandırma

[Etiketin](#label) yalnızca iki sınıftan oluşan bir [Sınıflandırma](#classification) durumu. Daha fazla bilgi için [Machine Learning görevleri](tasks.md) konusunun [ikili sınıflandırma](tasks.md#binary-classification) bölümüne bakın.

## <a name="calibration"></a>Ayarları

Ayar, bir ham puanı ikili ve çoklu sınıf sınıflandırması için bir sınıf üyeliğiyle eşleme işlemidir. Bazı ML.NET traıners `NonCalibrated` sonekine sahiptir. Bu algoritmalar, daha sonra bir sınıf olasılığa eşlenmesi gereken bir ham puan üretir.

## <a name="catalog"></a>Katalog

ML.NET ' de, katalog, ortak bir amaca göre gruplanmış bir uzantı işlevleri koleksiyonudur.

Örneğin, her makine öğrenimi görevi (ikili sınıflandırma, regresyon, derecelendirme vb.), kullanılabilir makine öğrenimi algoritmalarının (traers) bir kataloğuna sahiptir. İkili sınıflandırma esiners için Katalog: <xref:Microsoft.ML.BinaryClassificationCatalog.BinaryClassificationTrainers>.

## <a name="classification"></a>Sınıflandırma

Veriler bir kategoriyi tahmin etmek için kullanıldığında, [denetimli makine öğrenimi](#supervised-machine-learning) görevi sınıflandırma olarak adlandırılır. [İkili sınıflandırma](#binary-classification) yalnızca iki kategoriyi tahmin etmek anlamına gelir (örneğin, bir resmi bir ' Cat ' veya ' köpek ' resmi olarak sınıflandırın). Çoklu [sınıf sınıflandırması](#multiclass-classification) , birden çok kategoriyi tahmin etmek anlamına gelir (örneğin, bir görüntüyü belirli bir köpeğin resmi olarak sınıflandırırken).

## <a name="coefficient-of-determination"></a>Belirleme katsayısı

[Gerileme](#regression)' da, verilerin modele ne kadar iyi uyduğunu gösteren bir değerlendirme ölçümü. 0 ile 1 arasında aralıklar. 0 değeri, verilerin rastgele olması veya başka türlü modele sığamayacak olması anlamına gelir. 1 değeri, modelin verilerle tam olarak eşleştiği anlamına gelir. Bu, genellikle r<sup>2</sup>, r<sup>2</sup>veya r-kare olarak adlandırılır.

## <a name="data"></a>Veri

Veriler, tüm makine öğrenimi uygulamaları için tasarlanmıştır. ML.NET verilerinde <xref:Microsoft.ML.IDataView> nesneler tarafından temsil edilir. Veri görünümü nesneleri:

- sütun ve satırlardan oluşur
- geç değerlendirilir, bu, yalnızca bir işlem tarafından çağrı yapıldığında veri yükler
- her sütunun türünü, biçimini ve uzunluğunu tanımlayan bir şema içerir

## <a name="estimator"></a>Tahmin Aracı

ML.NET içinde <xref:Microsoft.ML.IEstimator%601> arabirimini uygulayan bir sınıf.

Bir tahmin aracı, dönüşümün bir belirtimidir (hem veri hazırlama dönüştürmesi hem de makine öğrenimi modeli eğitim dönüştürmesi). Estimators, bir dizi dönüşümde birlikte zincirlenebilir. Bir tahmin aracı veya tahmini işlem hattının parametreleri <xref:Microsoft.ML.IEstimator`1.Fit*> çağrıldığında öğrenilir. <xref:Microsoft.ML.IEstimator`1.Fit*> sonucu bir [transformatör](#transformer).

## <a name="extension-method"></a>Genişletme yöntemi

Bir sınıfın parçası olan ancak sınıfının dışında tanımlanmış bir .NET yöntemi. Genişletme yönteminin ilk parametresi, Uzantı yönteminin ait olduğu sınıfa yönelik statik bir `this` başvurusudur.

Genişletme yöntemleri, [Tahmini](#estimator)örnekleri oluşturmak için ml.NET içinde yaygın olarak kullanılır.

## <a name="feature"></a>Özellik

Ölçülecek, genellikle sayısal (Double) bir değer olan ölçülebilir bir özellik. Birçok özelliğe **özellik vektörü** denir ve genellikle `double[]`olarak depolanır. Özellikler, ölçülen olgudur 'ın önemli özelliklerini tanımlar. Daha fazla bilgi için Vikipde bulunan [Özellikler](https://en.wikipedia.org/wiki/Feature_(machine_learning)) makalesine bakın.

## <a name="feature-engineering"></a>Özellik Mühendisliği

Özellik Mühendisliği, kullanılabilir olgudur verilerinden, yani Özellik ayıklamadan Özellik vektörleri üreten [bir özellik kümesi tanımlamayı ve yazılım](#feature) geliştirmeyi içerir. Daha fazla bilgi için Vikipde bulunan [özellik Mühendisliği](https://en.wikipedia.org/wiki/Feature_engineering) makalesine bakın.

## <a name="f-score"></a>F puanı

[Sınıflandırmada](#classification) [duyarlık](#precision) ve [geri çekmeyi](#recall)dengeleyen bir değerlendirme ölçümü.

## <a name="hyperparameter"></a>Hiper parametre

Makine öğrenimi algoritmasının parametresi. Örnek olarak, karar verme ormanında veya bir gradyan algoritması algoritmasındaki adım boyutunda öğrenemeyen ağaç sayısını içerir. *Hyperparameters* 'ın değerleri, modeli eğitmek için ayarlanır ve tahmin işlevinin parametrelerini bulma işlemini (örneğin, bir karar ağacındaki karşılaştırma noktaları veya doğrusal regresyon modelindeki ağırlıklar) yönetmek için kullanılır. Daha fazla bilgi için Vikipde bulunan [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) makalesine bakın.

## <a name="label"></a>Etiketle

Machine Learning modeliyle tahmin edilecek öğe. Örneğin, kövil veya gelecekteki bir stok fiyatı.

## <a name="log-loss"></a>Günlük kayıp

[Sınıflandırmada](#classification), sınıflandırıcının doğruluğunu nitelendirir bir değerlendirme ölçümü. Daha küçük günlük kaybı, sınıflandırıcının ne kadar doğru olduğunu.

## <a name="loss-function"></a>Kayıp işlevi

Bir kayıp işlevi, eğitim etiketi değerleri ile modelin yaptığı tahmin arasındaki farktır. Modelin parametreleri, kayıp işlevini en aza indirerek tahmin edilir.

Farklı bir sorun, farklı kayıp işlevleriyle yapılandırılabilir.

## <a name="mean-absolute-error-mae"></a>Ortalama mutlak hata (MAE)

[Gerileme](#regression)' da, model hatasının tahmin edilen [etiket](#label) değeri ile doğru etiket değeri arasındaki mesafe olduğu tüm model hatalarının ortalaması olan bir değerlendirme ölçümü.

## <a name="model"></a>Model

Geleneksel olarak, tahmin işlevinin parametreleri. Örneğin, bir doğrusal regresyon modelindeki ağırlıklar veya bir karar ağacındaki bölünmüş noktaları. ML.NET ' de bir model, bir etki alanı nesnesinin (örneğin, görüntü veya metin) [etiketini](#label) tahmin etmek için gereken tüm bilgileri içerir. Bu, ML.NET modellerinin gerekli adımları ve tahmin işlevinin parametrelerini içermesi anlamına gelir.

## <a name="multiclass-classification"></a>birden çok Lass sınıflandırması

[Etiketin](#label) üç veya daha fazla sınıftan birindeki bir [Sınıflandırma](#classification) durumu. Daha fazla bilgi için [Machine Learning görevleri](tasks.md) konusunun çoklu [sınıf sınıflandırması](tasks.md#multiclass-classification) bölümüne bakın.

## <a name="n-gram"></a>N-gram

Metin verileri için bir özellik ayıklama şeması: herhangi bir N kelime dizisi, bir [özellik](#feature) değerine dönüşür.

## <a name="normalization"></a>Normalleştirme

Normalleştirme, kayan nokta verilerinin 0 ile 1 arasındaki değerlere ölçeklendirilmesi işlemidir. ML.NET ' de kullanılan eğitim algoritmalarının birçoğu, giriş özelliği verilerinin normalleştirilmesini gerektirir. ML.NET, [normalleştirmede](transforms.md#normalization-and-scaling) bir dizi dönüşüm sağlar

## <a name="numerical-feature-vector"></a>Sayısal Özellik vektörü

Yalnızca sayısal değerler içeren bir [özellik](#feature) vektörü. Bu, `double[]`benzerdir.

## <a name="pipeline"></a>Konfigüre

Bir modeli bir veri kümesine sığdırmak için gereken tüm işlemler. İşlem hattı, veri içeri aktarma, dönüştürme, korleştirme ve öğrenme adımlardan oluşur. Bir işlem hattı eğitilirken bir modeli açar.

## <a name="precision"></a>Duyarlık

[Sınıflandırmada](#classification), bir sınıf için duyarlık, sınıfa ait olarak tahmin edilen toplam öğe sayısına bölündüğü için, bu sınıfa ait olarak doğru tahmin edilen öğe sayısıdır.

## <a name="recall"></a>Çekmenin

[Sınıflandırmada](#classification), sınıf için geri çağırma, o sınıfa ait olan öğelerin, gerçekte sınıfa ait olan toplam öğe sayısına bölünmesiyle, doğru şekilde tahmin edilen öğe sayısıdır.

## <a name="regularization"></a>Düzenleme

 Düzenleme penalizes çok karmaşık olması için doğrusal bir model. İki tür düzenleme vardır:

- $L _1 $ düzenleme, önemli özellikler için sıfırlar. Bu düzenleme türünden sonra kaydedilen modelin boyutu daha küçük hale gelebilir.
- $L _2 $ düzenleme, önemli özellikler için ağırlık aralığını en aza indirir. Bu, daha genel bir işlemdir ve aykırı değerleri daha az hassastır.

## <a name="regression"></a>regresyon

Çıktının gerçek bir değer olduğu [denetimli bir makine öğrenimi](#supervised-machine-learning) görevi; Örneğin, Double. Örnek stok fiyatlarını tahmin eder. Daha fazla bilgi için [Machine Learning görevleri](tasks.md) konusunun [gerileme](tasks.md#regression) bölümüne bakın.

## <a name="relative-absolute-error"></a>Göreli mutlak hata

[Gerileme](#regression)' da, tüm mutlak hataların toplamı, doğru [etiket](#label) değerleri ve tüm doğru etiket değerlerinin ortalaması arasındaki uzaklıklara bölünen bir değerlendirme ölçümünün toplamıdır.

## <a name="relative-squared-error"></a>Göreli kare hatası

[Gerileme](#regression)' da, tüm kare dışı mutlak hataların toplamı, doğru [etiket](#label) değerleri ve tüm doğru etiket değerlerinin ortalaması arasındaki kare uzaklıkları toplamı olarak bölünür.

## <a name="root-of-mean-squared-error-rmse"></a>Ortalama kareli hata (rmo) kökü

[Gerileme](#regression)' da, hataların karelerinin ortalamasının kare kökü olan bir değerlendirme ölçümü.

## <a name="scoring"></a>Sonuç

Puanlama, eğitilen bir makine öğrenimi modeline yeni veri uygulama ve tahmin oluşturma işlemidir. Puanlama, ınıras olarak da bilinir. Modelin türüne bağlı olarak, puan ham bir değer, bir olasılık veya kategori olabilir.

## <a name="supervised-machine-learning"></a>Denetimli makine öğrenimi

İstenen modelin, henüz görünmeyen veriler için etiketi tahmin eden makine öğrenimi 'nin bir alt sınıfı. Örnek olarak sınıflandırma, gerileme ve yapılandırılmış tahmin sayılabilir. Daha fazla bilgi için Vikipedi 'teki [denetimli öğrenme](https://en.wikipedia.org/wiki/Supervised_learning) makalesine bakın.

## <a name="training"></a>İtme

Verilen eğitim veri kümesi için bir [modeli](#model) tanımlama işlemi. Doğrusal bir model için bu, ağırlıkları bulma anlamına gelir. Ağaç için bölme noktalarını tanımlamayı içerir.

## <a name="transformer"></a>Dönüştürücü

<xref:Microsoft.ML.ITransformer> arabirimini uygulayan bir ML.NET sınıfı.

Bir transformatör bir <xref:Microsoft.ML.IDataView> diğerine dönüştürür. Bir transformatör, bir [tahmin aracı](#estimator)veya bir tahmin aracı işlem hattı eğitimi tarafından oluşturulur.

## <a name="unsupervised-machine-learning"></a>Denetimli makine öğrenimi

İstenen modelin veride gizli (veya görünmeyen) yapısını bulduğu makine öğrenimi 'nin bir alt sınıfı. Kümeleme, konu modelleme ve boyutlılık azaltmaya örnek olarak verilebilir. Daha fazla bilgi için Vikipedi 'teki denetimsiz [öğrenme](https://en.wikipedia.org/wiki/Unsupervised_learning) makalesine bakın.
