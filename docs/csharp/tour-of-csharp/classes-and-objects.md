---
title: Sınıflar ve nesneler C# ' ta - C# dili turu
description: C# yeni misiniz? Bu sınıf, nesneler ve devralma genel bakış
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: 1e89d8b89e5f4f74d637a1e3674fb3959a231a49
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298298"
---
# <a name="classes-and-objects"></a>Sınıflar ve nesneler

*Sınıfları* olan en temel C# ' ın türü. Bir sınıf durumu (alanları) ve eylemleri (yöntemleri ve diğer işlevi üyeleri) birleştiren bir veri yapısı içinde tek bir birimdir. Dinamik olarak oluşturulan için bir sınıf tanımı sağlar *örnekleri* olarak da bilinen sınıfının *nesneleri*. Destek sınıfları *devralma* ve *çok biçimlilik*, mekanizmaları yapabildiği *türetilmiş sınıfları* genişletmek ve özelleştirmek *temel sınıflar*.

Yeni sınıflar sınıf bildirimleri kullanılarak oluşturulur. Sınıf bildirimi öznitelikleri ve sınıfın değiştiricileri, sınıfı, temel sınıfı (belirtilmişse) ve sınıf tarafından uygulanan arabirimler adını belirten bir başlık başlar. Üstbilgi arasında sınırlayıcıları yazılmış üye bildirimleri listesini oluşan sınıf gövdesi arkasından `{` ve `}`.

Aşağıdaki adlı basit bir sınıf bildirimidir `Point`:

[!code-csharp[PointClass](../../../samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Sınıfların örneklerini kullanarak oluşturulur `new` bellek için yeni bir örnek ayırır, işleci örneği başlatmak için bir oluşturucu çağırır ve örneğine başvuru döndürür. Aşağıdaki deyimleri iki nokta nesneleri oluşturmak ve bu nesnelere başvurular iki değişken depolamak:

[!code-csharp[PointExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Nesne artık erişilebilir olduğunda bir nesnenin kapladığı bellek otomatik olarak geri. Ne gerekli ya da açıkça C# nesneleri serbest bırakma mümkün değil.

## <a name="members"></a>Üyeler

Statik üyeler veya örnek üyelerin bir sınıf üyeleridir. Statik üyeler sınıflarına ait ve örnek üyelerin (sınıfların örneklerini) nesnelere ait.

Bir sınıf içerebilir üyeleri tür genel bir bakış sağlar.

* Sabitler
    - Sınıfıyla ilişkili sabit değerler
* Alanlar
    - Sınıfının değişkenleri
* Yöntemler
    - Hesaplamalar ve sınıf tarafından gerçekleştirilen eylemler
* Özellikler
    - Okuma ve yazma sınıfının adlandırılmış özellikleri ile ilişkili eylemler
* Dizin Oluşturucular
    - Dizin oluşturma sınıfın örnekleri, bir dizi gibi ilişkili eylemler
* Olaylar
    - Sınıfı tarafından oluşturulan bildirimleri
* İşleçler
    - Dönüşümler ve sınıf tarafından desteklenen ifade işleçleri
* Oluşturucular
    - Sınıf veya sınıf örneği başlatmak için gerekli eylemleri
* Sonlandırıcılar
    - Sınıfın örnekleri, kalıcı olarak atılmadan önce gerçekleştirilecek eylemler
* Türler
    - Sınıfı tarafından bildirilen iç içe geçmiş türler

## <a name="accessibility"></a>Erişilebilirlik

Her bir sınıf üyesi üye erişebilen program metin bölümlerinin denetimleri bir ilişkili erişilebilirlik sahiptir. Erişilebilirlik beş olası form vardır. Bunlar, aşağıda özetlenmiştir.

* `public`
    - Değil sınırlı erişim
* `protected`
    - Bu sınıf veya sınıfların sınırlı erişim bu sınıfından türetilen
* `internal`
    - Geçerli derlemeye (.exe, .dll, vb.) sınırlı erişim
* `protected internal`
    - İçeren sınıf veya sınıfların sınırlı erişim içeren sınıfından türetilen
* `private`
    - Bu sınıf için sınırlı erişim
* `private protected`
    - Aynı bütünleştirilmiş kod içinde içeren türde içeren sınıf veya sınıfların sınırlı erişim türetilmiş

## <a name="type-parameters"></a>Tür parametreleri

Bir sınıf tanımı sınıf adı köşeli ayraç tür parametre adları listesini kapsayan izleyerek türü parametreleri kümesini belirtebilir. Tür parametreleri ardından sınıf bildirimleri gövdesinde sınıfı üyeleri tanımlamak için kullanılır. Aşağıdaki örnekte, tür parametrelerini `Pair` olan `TFirst` ve `TSecond`:

[!code-csharp[Pair](../../../samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Tür parametreleri almak için bildirilen bir sınıf türü olarak adlandırılan bir *genel bir sınıf türü*. Yapı, arabirim ve temsilci türleri genel olabilir.
Genel sınıfı kullanıldığında, tür bağımsız değişkenleri her tür parametreleri için sağlanmalıdır:

[!code-csharp[PairExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Tür bağımsız değişkenleri gibi sağlanan ile genel tür `Pair<int,string>` yukarıdaki adlı bir *oluşturulan türü*.

## <a name="base-classes"></a>Temel sınıflar

Sınıf bildirimi bir taban sınıf sınıf adını ve türünü parametrelerle bir iki nokta üst üste ve temel sınıfın adını izleyerek belirtebilir. Bir temel sınıf belirtimi atlama aynıdır türünden türetme `object`. Aşağıdaki örnekte, temel sınıfını `Point3D` olan `Point`ve temel sınıfını `Point` olan `object`:

[!code-csharp[Point3DClass](../../../samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Bir sınıf devralınabilir. taban sınıfı üyeleri devralır. Devralma bir sınıf dolaylı olarak temel sınıfı olan örneği ve statik oluşturucular ve sonlandırıcılar taban sınıfın dışında tüm üyelerini içerir anlamına gelir. Türetilmiş bir sınıf yeni üyeler devralır olanlar ekleyebilirsiniz, ancak bir devralınan üye tanımının kaldıramazsınız. Önceki örnekte, `Point3D` devralır `x` ve `y` alanlarını `Point`ve her `Point3D` örneği üç alanları içeren `x`, `y`, ve `z`.

Örtük bir dönüştürme bir sınıf türünden temel sınıf türlerinden birine bulunmaktadır. Bu nedenle, bir sınıf türünde bir değişken bu sınıfının bir örneği veya türetilmiş bir sınıf örneği başvuruda bulunabilir. Örneğin, önceki sınıf bildirimleri türünde bir değişken verilen `Point` ya da başvurabilirsiniz bir `Point` veya `Point3D`:

[!code-csharp[Point3DExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Alanlar

A *alan* bir sınıf veya sınıfının bir örneği ile ilişkili bir değişkendir.

Statik değiştirici ile bildirilen alan statik bir alana tanımlar. Statik bir alana tam olarak bir depolama konumu tanımlar. Kaç tane bir sınıf örneğinin oluşturulduğu olsun, statik bir alana yalnızca hiç bir kopyası yoktur.

Statik değiştirici bildirilen alan bir örnek alanı tanımlar. Sınıfın her örneği bu sınıfın tüm örneği alanları ayrı bir kopyasını içerir.

Aşağıdaki örnekte, her örneği `Color` sınıfına sahip ayrı bir kopyasını `r`, `g`, ve `b` örneği alanları, ancak yalnızca bir kopyası yok `Black`, `White`, `Red`, `Green`, ve `Blue` statik alanları:

[!code-csharp[ColorClass](../../../samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Önceki örnekte gösterildiği gibi *salt okunur alanları* ile bildirilen bir `readonly` değiştiricisi. Atamaya bir `readonly` alan parçası olarak alanın bildirimi veya aynı sınıfta oluşturucuda yalnızca oluşabilir.

## <a name="methods"></a>Yöntemler

A *yöntemi* bir hesaplama ya da nesne veya sınıf tarafından gerçekleştirilen eylem uygulayan bir üyesidir. *Statik yöntemler* sınıfı aracılığıyla erişilir. *Örnek yöntemleri* sınıfın bir örneği erişilir.

Yöntemleri listesini olabilir *parametreleri*, değerleri veya yönteme geçirilen değişken başvuruları temsil ve *dönüş türü*, hesaplanan ve yöntem tarafından döndürülen değerin türü belirtir. Bir yöntemin dönüş türü `void` bir değer döndürmezse.

Türleri gibi yöntemleri yöntemi çağrıldığında tür bağımsız değişkeni belirtilen gerekir türü parametreleri kümesini de olabilir. Türleri, farklı tür bağımsız değişkeni bir yöntem çağrısı bağımsız değişkenlerden genellikle çıkarsanabileceği ve açıkça verilmemiş.

*İmza* yöntemi yöntemi bildirilmiş sınıfında benzersiz olması gerekir. Bir yöntemin imzası tür parametreleri ve sayısı, değiştiricileri ve türleri parametrelerinin sayısı yöntemin adını oluşur. İmza bir yöntemin dönüş türü içermez.

### <a name="parameters"></a>Parametreler

Parametre değerleri veya değişken başvuruları yöntemlere geçirmek için kullanılır. Bir yöntemin parametrelerini gerçek değerlerine alma *bağımsız değişkenleri* yöntemi çağrıldığında belirtilir. Parametreleri dört tür vardır: değer parametreleri, başvuru parametreleri, çıktı parametreleri ve parametre dizileri.

A *değer parametresi* giriş bağımsız değişkenleri geçirme kullanılır. Bir değer parametresini karşılık gelen bir yerel değişkene parametresi için geçirilen bağımsız değişken başlangıç değerini alır. Bir değer parametresini değişiklikler parametresi için geçirilen bağımsız değişken etkilemez. 

Böylece karşılık gelen bağımsız değişkenleri atlanabilir varsayılan bir değer belirterek değer parametreleri isteğe bağlı olabilir.

A *parametresi başvuru* başvuruya göre bağımsız değişkenleri geçirme kullanılır. Bir başvuru parametresi için geçirilen bağımsız değişken kesin bir değere sahip bir değişken olmalıdır ve yönteminin yürütülmesi sırasında başvuru parametre bağımsız değişken olarak aynı depolama konumunu temsil eder. Bir başvuru parametresi ile bildirilmiş `ref` değiştiricisi. Aşağıdaki örnek kullanımı gösterilmiştir `ref` parametreleri.

[!code-csharp[swapExample](../../../samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

Bir *çıkış parametresi* başvuruya göre bağımsız değişkenleri geçirme kullanılır. Bir değer açıkça çağıran tarafından sağlanan bağımsız değişkenine atayın gerektirmez, bir başvuru parametre benzerdir. Çıktı parametresi ile bildirilmiş `out` değiştiricisi. Aşağıdaki örnek kullanımı gösterilmiştir `out` C# 7'de sunulan sözdizimini kullanarak parametreleri.

[!code-csharp[OutExample](../../../samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

A *parametre dizisi* bir yönteme iletilecek bağımsız değişken sayısı izin verir. Bir parametre dizisi ile bildirilmiş `params` değiştiricisi. Yalnızca son parametresi bir yöntemi, bir parametre dizisi olabilir ve bir parametre dizisi türü bir tek boyutlu dizi türü olmalıdır. Yazma ve WriteLine yöntemlerinin <xref:System.Console?displayProperty=nameWithType> sınıfı parametre dizisi kullanımının iyi örnekler verilmiştir. Bunlar aşağıdaki gibi bildirilir.

[!code-csharp[ConsoleExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Bir parametre dizisi kullanan bir yöntem içinde parametre dizisine bir dizi türünün tam olarak normal bir parametre gibi davranır. Ancak, bir parametre dizisi olan bir yöntem çağrısını içinde tek bir bağımsız değişken parametre dizisi türü veya herhangi bir sayıda parametre dizi öğesi türü bağımsız değişkenleri geçirmek mümkündür. İkinci durumda, bir dizi örneği otomatik olarak oluşturulur ve belirtilen bağımsız değişkenlerle başlatıldı. Bu örnek

[!code-csharp[StringFormat](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

Aşağıdaki yazmaya eşdeğerdir.

[!code-csharp[StringFormat2](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Yöntem gövdesi ve yerel değişkenler

Bir yöntemin gövde yöntemi çağrıldığında çalıştırılacak deyimleri belirtir.

Yöntem gövdesi yöntemin çağrılması için belirli değişkenleri bildirebilirsiniz. Bu tür değişkenler adlandırılır *yerel değişkenler*. Yerel bir değişken bildirimi bir tür adı, bir değişken adı ve büyük olasılıkla bir başlangıç değeri belirtir. Aşağıdaki örnek, yerel bir değişken bildirir `i` sıfır ve yerel bir değişken başlangıç değeri ile `j` hiçbir başlangıç değeri.

[!code-csharp[Squares](../../../samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# olması için yerel bir değişken gerektirir *kesinlikle atanan* değeri elde edilebilir önce. Örneğin, varsa önceki bildirimi `i` başlangıç değeri içermeyen, derleyici sonraki kullanımlar için bir hata raporlar `i` çünkü `i` kesinlikle noktalarda program atanmamış.

Bir yöntemi kullanabilirsiniz `return` çağırıcısına denetim döndürülecek deyimleri. Döndüren bir yöntem `void`, `return` deyimleri bir ifade belirtemezsiniz. Olmayan-void, döndüren bir yöntem `return` deyimleri dönüş değeri hesaplar bir ifade içermelidir.

### <a name="static-and-instance-methods"></a>Statik ve örnek yöntemleri

Statik değiştirici ile bildirilmiş bir yöntemi olan bir *statik yöntemi*. Bir statik yöntem belirli bir örneğinde çalışmaz ve statik üyeler yalnızca doğrudan erişebilirsiniz.

Statik değiştirici olmayan bir yöntem olarak bildirilen bir *örnek yöntemi*. Örnek yöntemi belirli bir örneğinde çalışır ve her iki statik erişmek ve üyeleri örneği. Bir örnek yönteminin çağrıldığı örnek olarak açıkça erişilebilir `this`. Başvurmak için bir hata olduğunu `this` bir statik yöntem.

Aşağıdaki `Entity` sınıfı statik sahiptir ve üyeleri örneği.

[!code-csharp[Entity](../../../samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Her `Entity` örneği bir seri numarası (ve burada gösterilmiyor büyük olasılıkla bazı diğer bilgileri içerir). `Entity` (Bu örnek yöntemi gibi) Oluşturucu sonraki kullanılabilir seri numarasına sahip yeni örneğini başlatır. Örnek üyesine Oluşturucusu olduğu için her ikisi de erişim izni `serialNo` örnek alan ve `nextSerialNo` statik alan.

`GetNextSerialNo` Ve `SetNextSerialNo` statik yöntemler erişebilir `nextSerialNo` statik alan, ancak bunları için bir hata doğrudan erişimi olacaktır `serialNo` örnek alanı.

Aşağıdaki örnekte, varlık sınıfı kullanımını göstermektedir.

[!code-csharp[EntityExample](../../../samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Unutmayın `SetNextSerialNo` ve `GetNextSerialNo` statik yöntemler, sınıf üzerinde çağrılır, ancak `GetSerialNo` sınıfın bir örneği üzerinde örnek yöntemi çağrılır.

### <a name="virtual-override-and-abstract-methods"></a>Sanal, geçersiz kılma ve soyut yöntemler

Ne zaman bir örnek yöntemi bildirimi içeren bir `virtual` değiştiricisi, yöntem olarak kabul edilir bir *sanal yöntemi*. Hiçbir sanal değiştiricisi bulunduğunda yöntemi olarak kabul edilir bir *sanal olmayan yöntemi*.

Sanal bir yöntem çağrıldığında, *çalışma zamanı tür* bu çağrısını aldığı örneği yer çağırmak için gerçek uygulama yönteminin belirler. Sanal olmayan yöntemi çağrısı *derleme zamanı tür* belirleyici faktör örneğidir.

Sanal bir yöntem olabilir *geçersiz kılınmış* türetilmiş bir sınıf içinde. Bir örneği yöntemi bildiriminde bir geçersiz kılma değiştiricisi içerdiğinde yöntemi aynı imzayla devralınan bir sanal yöntemi geçersiz kılar. Bir sanal yöntem bildirimi iki yöntem sunar ancak bu yöntem, yeni bir uygulama sağlayarak bir geçersiz kılma yöntemi bildirimi varolan bir devralınan sanal yöntemi uzmanlaşmış.

Bir *soyut yöntemi* hiçbir uygulaması sanal bir yöntemdir. Soyut bir yöntem soyut değiştiricisi ile bildirilir ve soyut bildirilmiş bir sınıfta izin verilir. Her Özet olmayan türetilen sınıfta soyut bir yöntem geçersiz kılınmalıdır.

Aşağıdaki örnek, bir Özet sınıf bildirir `Expression`, bir ifade ağaç düğümünü temsil eder ve üç türetilmiş sınıfları `Constant`, `VariableReference`, ve `Operation`, ifade ağaç düğümleri sabitleri, değişken için uygulama başvuruları ve aritmetik işlemler. (Bu ifade ağaç türleriyle karıştırılmamalıdır ancak, benzer).

[!code-csharp[ExpressionClass](../../../samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Önceki dört sınıflar, aritmetik ifadeler modellemek için kullanılabilir. Örneğin, bu sınıfları, ifade kullanarak `x + 3` gibi temsil edilebilir.

[!code-csharp[ExpressionExample](../../../samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

`Evaluate` Yöntemi bir `Expression` örneği verilen ifade değerlendirmek ve üretmek için çağrıldığında bir `double` değeri. Yöntem alır bir `Dictionary` (olarak girişleri anahtarları) değişken adları ve değerleri (olarak girişlerinin değerleri) içeren değişken. Çünkü `Evaluate` soyut bir yöntem, türetilen soyut olmayan sınıflar `Expression` geçersiz kılmanız gerekir `Evaluate`.

A `Constant`'s uyarlamasını `Evaluate` yalnızca depolanmış sabiti döndürür. A `VariableReference`adı değişken adı sözlükteki uygulama arar ve sonuç değeri döndürür. Bir `Operation`'s uygulama önce sol ve sağ işlenen değerlendirir (özyinelemeli çağırma tarafından kendi `Evaluate` yöntemleri) ve verilen aritmetik işlemi gerçekleştirir.

Aşağıdaki program kullanan `Expression` ifade değerlendirmek için sınıflar `x * (y + 2)` farklı değerler için `x` ve `y`.

[!code-csharp[ExpressionUsage](../../../samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Yöntemi aşırı yüklemesi

Yöntem *aşırı* benzersiz imzaları sahip oldukları sürece aynı ada sahip aynı sınıfta birden çok yöntem verir. Aşırı yüklenmiş yöntemin bir çağrısını derlerken, derleme kullanır *aşırı yükleme çözümü* çağırmak için belirli yöntemi belirlemek için. Aşırı yükleme çözünürlüğü en iyi bağımsız değişkenlerle veya tek en iyi eşleşme bulunamazsa, bir hata raporları bir yöntem bulur. Aşağıdaki örnek aşırı yükleme çözünürlüğü yürürlükte gösterir. Her çağırma için yorum `UsageExample` yöntemi gösterilir hangi yöntemi gerçekte çağrılır.

[!code-csharp[OverloadUsage](../../../samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Örnekte gösterildiği gibi belirli bir yöntem her zaman açıkça tam parametre türleri değişkenleri atama ve/veya açıkça tür bağımsız değişkenleri sağladığını seçilebilir.

## <a name="other-function-members"></a>Diğer işlevi üyeleri

Yürütülebilir kod içeren üyeleri topluca olarak bilinen *işlev üyeleri* bir sınıf. Önceki bölümde işlevi üyeleri birincil tür yöntemleri açıklar. Bu bölümde C# tarafından desteklenen işlevi üyelerinin diğer türleri açıklanmaktadır: Oluşturucular, özellikleri, dizin oluşturucular, olaylar, işleçler ve sonlandırıcılar.

Aşağıdaki liste adlı genel bir sınıf gösterir<T>, growable nesnelerin listesini uygular. Sınıfı en yaygın tür işlevi üye bazı örnekleri içerir.

[!code-csharp[ListClass](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Oluşturucular

C# örneği ve statik oluşturucular destekler. Bir *örnek oluşturucusu* sınıfının bir örneği başlatmak için gerekli eylemleri uygulayan bir üyesidir. A *statik Oluşturucusu* ilk yüklendiğinde bir sınıf başlatmak için gerekli eylemleri uygulayan bir üyesidir.

Dönüş türü ve içeren sınıf aynı ada sahip bir yöntemi gibi bir oluşturucu bildirildi. Statik değiştirici Oluşturucu bildirimi içeriyorsa, statik Oluşturucu bildirir. Aksi takdirde, örnek oluşturucu bildirir.

Örnek oluşturucuları aşırı yüklenebilir ve isteğe bağlı parametreler olabilir. Örneğin, `List<T>` sınıfı parametresiz ve tutacak bir biriyle iki örnek oluşturucuları bildiren bir `int` parametresi. Örnek oluşturucuları kullanarak çağrılır `new` işleci. Aşağıdaki deyimleri iki tahsis `List<string>` oluşturucusunun kullanma örnekleri `List` sınıfı ile ve isteğe bağlı bağımsız değişkeni olmadan.

[!code-csharp[ListExample1](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Diğer üyeleri aksine örnek oluşturucuları devralınmaz ve bir sınıf dışında bu gerçekte bildirilen örnek oluşturucusu sınıfında yok. Hiçbir örnek oluşturucu için bir sınıf sağlanırsa, sonra boş bir parametre olmadan otomatik olarak sağlanır.

### <a name="properties"></a>Özellikler

*Özellikler* alanlarının doğal bir uzantıdır. Her ikisi de ilişkili türlerini üyeleriyle adlandırılır ve alanlar ve Özellikler erişmek için söz dizimi aynıdır. Ancak, alanları özellikleri depolama konumları belirtmek değil. Bunun yerine, özelliklere sahip *erişimciler* değerlerine okunabilir veya yazılabilir zaman yürütülecek deyimleri belirtin.

Bildirim alma erişimcisi ve/veya sınırlayıcıları yazılmış bir set erişimcisi ile biten dışında bir özelliği bir alan gibi bildirildiği `{` ve `}` noktalı virgül bitiş yerine. Bir get erişimcisine ve bir set erişimcisine sahip bir özellik olan bir *okuma-yazma özelliği*, yalnızca bir get erişimcisine sahip bir özellik olan bir *salt okunur özelliği*, ve yalnızca bir set erişimcisine sahip bir özellik bir *salt yazılır özellik*.

Get erişimcisi özellik türü dönüş değeri parametresiz bir yöntemle karşılık gelir. Bir özelliği bir ifadede başvurulduğunda dışında bir atama hedef olarak özelliğinin get erişimcisine özelliğin değerini hesaplamak için çağrılır.

Bir set erişimcisi değeri ve dönüş türü adlı için tek bir parametre için bir yöntem karşılık gelir. Ne zaman bir özellik başvurulan atama hedefi veya işleneni olarak ++ veya--, yeni değer sağlayan bir bağımsız değişken set erişimcisine çağrılır.

`List<T>` Sınıfı salt okunur ve okuma-yazma, sırasıyla sayısı ve kapasite, iki özelliği bildirir. Bu özelliklerin kullanımı bir örnek verilmiştir.

[!code-csharp[ListExample2](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Alanları ve yöntemleri benzer, C# örnek özelliklerini ve statik özellikleri destekler. Statik özellikler statik değiştirici ile bildirilir ve örnek özelliklerini olmadan bildirilir.

Bir özelliğin accessor(s) sanal olabilir. Ne zaman bir özellik bildirimi içeren bir `virtual`, `abstract`, veya `override` değiştiricisi, özellik accessor(s) için geçerlidir.

### <a name="indexers"></a>Dizin Oluşturucular

Bir *dizin oluşturucu* bir dizi aynı şekilde dizine nesneler sağlayan bir üyesidir. Üyenin adını bu arasında sınırlayıcıları yazılmış bir parametre listesine ve ardından olması dışında bir dizin oluşturucu özelliği gibi bildirilmiş `[` ve `]`. Parametreleri dizin oluşturucu accessor(s) içinde kullanılabilir. Benzer özellikleri için dizin oluşturucular okuma-yazma, salt okunur ve yalnızca yazma olabilir ve bir dizinleyici accessor(s) sanal olabilir.

`List` Sınıf gereken tek bir okuma-yazma dizin oluşturucu bildiren bir `int` parametresi. Dizin Oluşturucu, dizine mümkün kılar `List` ile örnekleri `int` değerleri. Örneğin:

[!code-csharp[ListExample3](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Dizin Oluşturucular, sayı veya kendi parametre türlerini farklı sürece bir sınıfın birden çok dizin oluşturucu bildirebilir anlamı aşırı yüklenmiş.

### <a name="events"></a>Olaylar

Bir *olay* bir sınıf veya nesne bildirimleri sağlamak üzere etkinleştirir bir üyesidir. Bir olay türü bir temsilci türü olmalıdır ve bir event anahtar sözcüğü bildirimi içerir ancak bu gibi bir alan bildirildi.

(Olay Özet olmayan ve erişimciler bildirmiyor sağlanan) bir olay üye bildiren bir sınıf içinde olay yalnızca bir temsilci türü bir alan gibi davranır. Alan olaya eklenmiş olan olay işleyicileri temsil eden bir temsilci başvuru depolar. Olay işleyicileri mevcut olup olmadığını alandır `null`.

`List<T>` Sınıfı bildirir adlı tek bir olay üyeye `Changed`, belirten yeni bir öğeyi listeye eklendi. Değiştirilen olay tarafından tetiklenir `OnChanged` hangi ilk olay olup olmadığını denetler, sanal bir yöntem `null` (hiçbir işleyicileri mevcut olduğu anlamına gelir). Bir olayı tetiklenmeden tanımlanmaları olayı tarafından temsil edilen temsilci çağırmak için tam olarak eşittir; Bu nedenle, olaylar oluşturma için hiçbir özel dil yapıları vardır.

İstemcileri tepki olayları *olay işleyicileri*. Olay işleyicileri kullanarak bağlı `+=` işleci ve kaldırılan kullanarak `-=` işleci. Aşağıdaki örnekte bir olay işleyicisi ekler `Changed` olayı bir `List<string>`.

[!code-csharp[EventExample](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Bir olayın temel alınan depolama biriminin denetimi istenen burada Gelişmiş senaryolar için bir olay bildirimi açıkça sağlayabilir `add` ve `remove` biraz benzer erişimciler `set` bir özellik erişimcisi.

### <a name="operators"></a>İşleçler

Bir *işleci* bir sınıfın bir örneği için belirli ifade işleci uygulama anlamı tanımlayan bir üyesidir. Üç tür işleçleri tanımlanabilir: birli işleç, ikili işleçler ve dönüştürme işleçleri. Tüm işleçleri olarak bildirilmelidir `public` ve `static`.

`List<T>` Sınıfı bildirir iki işleç `operator ==` ve `operator !=`ve bu nedenle bu işleç geçerli ifadeler için yeni anlamı verir `List` örnekleri. Özellikle, işleçler iki eşitliği tanımlama `List<T>` örnekleri kendi eşittir yöntemlerini kullanarak içerdiği nesnelerin her biri karşılaştırma olarak. Aşağıdaki örnek kullanır `==` iki Karşılaştırılacak işleci `List<int>` örnekleri.

[!code-csharp[OperatorExample](../../../samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

İlk `Console.WriteLine` çıkarır `True` listelerini aynı değerleri aynı sırayla nesnelerle aynı sayıda içerdiğinden. Vardı `List<T>` tanımlanmamış `operator ==`, ilk `Console.WriteLine` çıkış `False` çünkü `a` ve `b` başvuru farklı `List<int>` örnekleri.

### <a name="finalizers"></a>Sonlandırıcılar

A *sonlandırıcıyı* sınıfının bir örneği sonlandırmaya gerekli eylemleri uygulayan bir üyesidir. Sonlandırıcılar parametrelere sahip olamaz, erişilebilirlik değiştiricileri sahip olamaz ve açıkça çağrılamaz. Bir örneği için sonlandırıcıyı çöp toplama sırasında otomatik olarak çağrılır.

Çöp toplayıcı nesneler toplamak ve sonlandırıcılar çalıştırmak karar verme, geniş enlem izin verilir. Özellikle, sonlandırıcıyı çağrılarını zamanlama belirleyici değil ve sonlandırıcılar hiçbir iş parçacığı üzerinde yürütülen. Sınıfları, bunlar ve diğer nedenler için yalnızca başka bir çözüm uygun olduğunda sonlandırıcılar uygulamanız gerekir.

`using` Deyimi nesne yok etme daha iyi bir yaklaşım sağlar.

>[!div class="step-by-step"]
[Önceki](statements.md)
[sonraki](structs.md)
