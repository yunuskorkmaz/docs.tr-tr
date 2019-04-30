---
title: Sınıflar ve nesneler C# -Turu C# dil
description: Yeni C#? Bu sınıflar, nesneleri ve devralma bakış okuyun
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: 36def74888f67dfa216cea7c093d80724e452c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706591"
---
# <a name="classes-and-objects"></a>Sınıflar ve nesneler

*Sınıflar* , en temel olan C#'s türleri. Bir sınıf durumu (alanlar) ve işlemleri (yöntemler ve diğer işlev üyeleri) bir araya getiren bir veri yapısı içinde tek bir birimdir. Dinamik olarak oluşturulan için bir sınıf tanımı sağlar *örnekleri* olarak da bilinen, sınıfın *nesneleri*. Destek sınıfları *devralma* ve *çok biçimlilik*, mekanizmaları yapabildiği *türetilmiş sınıflar* genişletmek ve uzmanlaşmış *temel sınıflar*.

Yeni sınıflar, sınıf bildirimi kullanarak oluşturulur. Bir sınıf bildiriminin öznitelikleri ve sınıfı değiştiricileri, sınıf, taban sınıf (belirtilmişse) ve bir sınıf tarafından uygulanan arabirimler adını belirten bir üst bilgisi ile başlar. Başlık sınırlayıcılar arasında yazılan üye bildirimleri listesini içeren sınıf gövdesinin arkasından `{` ve `}`.

Adlı basit bir sınıf bildirimi verilmiştir `Point`:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Sınıfların örneklerini kullanılarak oluşturulur `new` yeni bir örneği için bellek ayırır, işleci örneği başlatmak için bir oluşturucu çağırır ve örneğe bir başvuru döndürür. Aşağıdaki deyimleri, iki nokta nesneleri oluşturmak ve bu nesnelere başvurular iki değişken depolamak:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Nesnenin artık erişilebilir olduğunda otomatik olarak bir nesnenin kapladığı belleği geri kazanılır. Bu, gerekli veya C# nesneler açıkça serbest mümkün olur.

## <a name="members"></a>Üyeler

Statik üye veya örnek üyeleri bir sınıf üyeleridir. Statik üyeleri sınıflarına ait ve örnek üyeleri (sınıfların örneklerini) nesnelere ait.

Aşağıdaki türde üye bir sınıf içeren genel bir bakış sağlar.

* Sabitler
  - Sınıf ile ilişkili olan sabit değerler
* Alanlar
  - Sınıfın değişkenleri
* Yöntemler
  - Sınıfı tarafından gerçekleştirilen eylemler ve hesaplamaları
* Özellikler
  - Okuma ve adlandırılmış sınıfın özelliklerini yazma ile ilişkili eylemler
* Dizin Oluşturucular
  - Dizin oluşturma sınıfına bir dizi gibi örnekleriyle ilişkili eylemler
* Olaylar
  - Sınıfı tarafından oluşturulan bildirimleri
* İşleçler
  - Dönüşümler ve sınıfı tarafından desteklenen ifade işleçleri
* Oluşturucular
  - Sınıfın veya sınıf örneği başlatmak için gerekli eylemleri
* Sonlandırıcılar
  - Sınıf örneğini kalıcı olarak atılmadan önce gerçekleştirilecek eylemler
* Türler
  - Sınıfı tarafından bildirilen iç içe geçmiş türler

## <a name="accessibility"></a>Erişilebilirlik

Bir sınıfın her üyesine erişebilir üyeyi program metni bölümlerine denetleyen bir ilişkili erişilebilirlik sahiptir. Erişilebilirlik altı olası biçimi vardır. Bunlar aşağıda özetlenmiştir.

* `public`
  - Olmayan sınırlı erişim
* `protected`
  - Bu sınıf veya sınıfların sınırlı erişim, bu sınıftan türetilen
* `internal`
  - Geçerli derleme (.exe, .dll, vb.) için sınırlı erişim
* `protected internal`
  - İçeren sınıfı, kapsayan sınıftan türetilmiş sınıflar veya aynı derleme içindeki sınıf sınırlı erişim
* `private`
  - Bu sınıf için sınırlı erişim
* `private protected`
  - Aynı bütünleştirilmiş kod içinde kapsayan tür içeren sınıf veya sınıfların sınırlı erişim türetilen

## <a name="type-parameters"></a>Tür parametreleri

Bir sınıf tanımı, sınıf adı türü parametre adları listesini çevreleyen açılı ayraçlar ile izleyerek tür parametrelerinin kümesi belirtebilirsiniz. Tür parametreleri daha sonra sınıf bildirimi gövdesinde sınıf üyelerini tanımlamak için kullanılabilir. Aşağıdaki örnekte, tür parametreleri `Pair` olan `TFirst` ve `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Tür parametreleri gerçekleştirilecek bildirildiği bir sınıf türü olarak adlandırılan bir *genel bir sınıf türü*. Yapı, arabirim ve temsilci türlerinin genel olabilir.
Genel sınıf kullanıldığında, tür bağımsız değişkenleri her tür parametreleri için sağlanmalıdır:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Sağlanan gibi tür bağımsız değişkenleri ile genel tür `Pair<int,string>` yukarıda adlandırılan bir *oluşturulan türü*.

## <a name="base-classes"></a>Temel sınıflar

Sınıf bildiriminin bir temel sınıf, bir iki nokta üst üste ve temel sınıfın adını sınıf adı ve türü parametreleri izleyerek belirtebilirsiniz. Bir temel sınıf belirtimini atlama aynıdır türünden türetme `object`. Aşağıdaki örnekte, temel sınıfını `Point3D` olduğu `Point`ve temel sınıfını `Point` olduğu `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Bir sınıf, taban sınıfı üyelerini devralır. Devralma, bir sınıf dolaylı temel sınıfı, örneği ve statik oluşturucular ve sonlandırıcılar taban sınıfın dışındaki tüm üyeleri içeren anlamına gelir. Türetilmiş bir sınıf devralır bu yeni üyeler ekleyebilirsiniz, ancak devralınan bir üyeyi tanımını kaldırılamaz. Önceki örnekte, `Point3D` devralan `x` ve `y` alanlarını `Point`ve her `Point3D` örneğini içeren üç alan `x`, `y`, ve `z`.

Temel sınıf türlerinden birinin bir sınıf türünden örtük bir dönüştürme yok. Bu nedenle, bir sınıf türünün bir değişkeni, bu sınıfın bir örneğini veya türetilmiş bir sınıf örneği başvuruda bulunabilir. Örneğin, önceki bir sınıf bildirimleri, türünde bir değişken verilen `Point` ya da başvurabilirsiniz bir `Point` veya `Point3D`:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Alanlar

A *alan* bir sınıf veya bir sınıf örneği ile ilişkili bir değişkendir.

Statik değiştirici ile bildirilen bir alana bir statik alanı tanımlar. Statik alan tam olarak bir depolama konumunu tanımlar. Bir sınıfın kaç örneklerin oluşturulduğu ne olursa olsun, yalnızca bir kopyasını statik bir alan yoktur.

Statik değiştirici bildirilen bir alan bir örnek alanıyla tanımlar. Bir sınıfın her örneği, bu sınıfın tüm örnek alanları ayrı bir kopyasını içerir.

Aşağıdaki örnekte, her bir örneği `Color` sınıfına sahip ayrı bir kopyasını `r`, `g`, ve `b` örnek alanları, ancak yalnızca bir kopyası `Black`, `White`, `Red`, `Green`, ve `Blue` statik alanlar:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Önceki örnekte gösterilen şekilde *salt okunur alanları* ile bildirilebilir bir `readonly` değiştiricisi. Atama bir `readonly` alan alanın bildirimin veya aynı sınıftaki bir oluşturucunun parçası olarak yalnızca oluşabilir.

## <a name="methods"></a>Yöntemler

A *yöntemi* hesaplama veya bir nesne veya sınıf tarafından gerçekleştirilen eylem uygulayan bir üyesidir. *Statik yöntemler* sınıfı üzerinden erişilir. *Örnek yöntemleri* sınıfının örneklerini erişilir.

Yöntemleri listesi olabilir *parametreleri*, değerleri veya değişken başvuruları yöntemine geçirilen temsil ve *dönüş türü*, hesaplanan ve yöntem tarafından döndürülen değerin türünü belirtir. Bir yöntemin dönüş türü `void` bir değer döndürmezse.

Türleri gibi yöntemleri de bir dizi yöntem çağrıldığında tür bağımsız değişkenleri belirtilmiş olmalıdır, tür parametreleri olabilir. Türleri, farklı tür bağımsız değişkeni genellikle bir yöntem çağrısının bağımsız değişkenlerden çıkarılan ve açıkça verilmemiş.

*İmza* yöntemi yöntemi bildirilmiş sınıfında benzersiz olması gerekir. Yöntemin imzası yöntem, tür parametreleri ve sayısı, değiştiriciler ve parametrelerinin türleri sayısı adını oluşur. Yöntemin imzası dönüş türü içermez.

### <a name="parameters"></a>Parametreler

Parametre değerleri veya değişken başvuruları yöntemlere geçirmek için kullanılır. Bir yöntem parametreleri, gerçek değerleri alma *bağımsız değişkenleri* yöntemi çağrıldığında belirtilir. Dört tür parametrelerinin vardır: parametreler, başvuru parametreleri, çıktı parametreleri ve parametre dizileri değeri.

A *değer parametresi* giriş bağımsız değişkenleri geçirmek için kullanılır. Bir değer parametresini karşılık gelen bir yerel değişkene parametresi için geçirilen bağımsız ilk değerini alır. Parametresi için geçirilen bağımsız değişken bir değer parametresini değişiklikler etkilemez.

Böylece karşılık gelen bağımsız değişken atlanırsa, varsayılan bir değer belirterek değeri parametreleri, isteğe bağlı olabilir.

A *parametre başvurusunu* başvuruya göre bağımsız değişkenleri geçirme kullanılır. Bir başvuru parametresi için geçirilen bağımsız değişken kesin bir değere sahip bir değişken olmalıdır ve yöntemin yürütülmesi sırasında aynı depolama konumu olarak bir bağımsız değişken başvuru parametresi temsil eder. Bir başvuru parametresi ile bildirilen `ref` değiştiricisi. Aşağıdaki örnek kullanımını gösterir `ref` parametreleri.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

Bir *çıkış parametresi* başvuruya göre bağımsız değişkenleri geçirme kullanılır. Değeri açıkça çağıran tarafından sağlanan bağımsız değişkene atayın gerektirmeyen dışında her bir başvuru parametresi için de benzer. Çıkış parametresi ile bildirilen `out` değiştiricisi. Aşağıdaki örnek kullanımını gösterir `out` sürümünde söz dizimini kullanarak parametreleri C# 7.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

A *parametre dizisi* bir yönteme iletilecek bağımsız değişken bir sayı verir. Bir parametre dizisi ile bildirilen `params` değiştiricisi. Bir yöntem yalnızca son parametresi bir parametre dizisi olabilir ve bir parametre dizisi türünde tek boyutlu dizi türü olmalıdır. Yazma ve WriteLine yöntemlerini <xref:System.Console?displayProperty=nameWithType> sınıfı iyi parametre dizisi kullanımı örnekleri verilmiştir. Bunlar aşağıdaki gibi bildirilir.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Parametre dizisi, bir parametre dizisi kullanan bir yöntem içinde bir dizi türünde tam olarak normal bir parametre gibi davranır. Ancak, bir parametre dizisi olan bir yöntem çağrısını içinde parametresi dizi türünde tek bir bağımsız değişken veya herhangi bir sayıda öğe türü parametre dizisi bağımsız değişkenleri geçirmek mümkündür. İkinci durumda, bir dizi örneği otomatik olarak oluşturulur ve belirtilen bağımsız değişkenler ile başlatıldı. Bu örnek

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

Aşağıdaki yazmaya eşdeğerdir.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Yöntem gövdesini ve yerel değişkenler

Bir yöntemin gövdesi yöntemi çağrıldığında çalıştırılacak deyimleri belirtir.

Bir yöntem gövdesi yöntemi çağırmayı için özel değişkenleri bildirebilirsiniz. Bu tür değişkenleri olarak adlandırılmasının *yerel değişkenler*. Yerel bir değişken bildirimi bir tür adı, bir değişken adı ve büyük olasılıkla bir başlangıç değeri belirtir. Aşağıdaki örnek, yerel bir değişken bildirir `i` bir başlangıç değeri sıfır ve yerel bir değişken ile `j` ile başlangıç değeri yok.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# olarak yerel bir değişken gerektirir *kesinlikle atanan* önce değeri elde edilebilir. Örneğin, önceki bildirimi `i` bir başlangıç değeri içermesi gerekmez, derleyici bir hata sonraki kullanımlar için rapor `i` çünkü `i` kesinlikle noktalarda program atanır değil.

Bir yöntemi kullanabilirsiniz `return` denetimi onu arayan döndürülecek deyimleri. Döndüren bir yöntem içinde `void`, `return` deyimleri, bir ifade belirtemez. Void olmayan, döndüren bir yöntem içinde `return` deyimleri, dönüş değeri hesaplar bir ifade içermelidir.

### <a name="static-and-instance-methods"></a>Statik ve örnek yöntemleri

Statik bir değiştiriciyle bildirildi bir yöntem bir *statik yöntem*. Statik bir yöntemi, belirli bir örneği üzerinde çalışmaz ve statik üyeler yalnızca doğrudan erişebilir.

Statik değiştirici olmayan bir yöntem olarak bildirilen bir *örnek yöntemi*. Bir örnek yöntemi belirli bir örneği üzerinde çalışır ve hem statik erişebilir ve örnek üyeler. Bir örnek yöntemi çağrıldığı örnek olarak açıkça erişilebilir `this`. Başvurmak için bir hata olduğunu `this` statik yöntemde.

Aşağıdaki `Entity` sınıfında statik ve örnek üyeleri.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Her `Entity` örneği seri numarası (ve burada gösterilmez büyük olasılıkla bazı diğer bilgileri içerir). `Entity` (Olan bir örnek yöntemi gibi) bir oluşturucu sonraki kullanılabilir seri numarasına sahip yeni örneğini başlatır. Oluşturucu bir örnek üyesi olduğundan, her ikisi de erişmesine izin verilen `serialNo` örnek alan ve `nextSerialNo` statik alan.

`GetNextSerialNo` Ve `SetNextSerialNo` statik yöntemler erişebilir `nextSerialNo` statik alan, ancak bir hata için bunları doğrudan erişimini olacak `serialNo` örnek alanı.

Aşağıdaki örnek, varlık sınıfının kullanımı gösterilmektedir.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Unutmayın `SetNextSerialNo` ve `GetNextSerialNo` statik yöntemler, sınıf üzerinde çağrılır, ancak `GetSerialNo` sınıf örnekleri üzerinde örnek yöntemi çağrılır.

### <a name="virtual-override-and-abstract-methods"></a>Soyut metotlar sanal ve geçersiz kılma

Ne zaman bir örnek yöntemi bildirimi içeren bir `virtual` değiştiricisi, yöntem olarak kabul edilir bir *sanal yöntem*. Hiçbir sanal değiştirici mevcut olduğunda, yöntemin olduğu söylenir bir *yöntemi sanal olmayan*.

Sanal bir yöntem çağrıldığında *çalışma zamanı tür* bu çağırma aldığı örneğini yerde çağrılacak gerçek yöntem uygulaması belirler. Bir sanal olmayan bir yöntem çağrısı *derleme zamanı tür* belirleyici faktör örneğidir.

Sanal bir yöntem olabilir *geçersiz kılınan* türetilen bir sınıfta. Bir örnek yöntem bildiriminde geçersiz kılma değiştiricisini içerdiğinde, yöntemin aynı imzaya sahip devralınan sanal yöntemi geçersiz kılar. Bir geçersiz kılma yöntemi bildirimini sanal yöntem bildiriminde bir yöntem sunar ancak bu yöntem yeni bir uygulamasını sağlayarak mevcut devralınan sanal yöntemi uzmanlaşmış.

Bir *yöntemi soyut* uygulama içermeyen sanal bir yöntemdir. Soyut bir yöntemi soyut değiştiriciyle bildirildi ve yalnızca soyut bildirildiği bir sınıf içinde izin verilir. Her bir soyut olmayan türetilmiş sınıf içinde soyut bir yöntemi geçersiz kılınmalıdır.

Aşağıdaki örnek, bir soyut sınıfı bildirir `Expression`, bir ifade ağacı düğümünü temsil eder ve üç türetilmiş sınıfları `Constant`, `VariableReference`, ve `Operation`, sabitler, değişken için ifade ağaç düğümleri uygulayın başvurular ve aritmetik işlemler. (Bu ifade ağacı türleriyle karıştırılmamalıdır ancak, benzer).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Önceki dört sınıfları, aritmetik ifadeler modellemek için kullanılabilir. Örneğin, ifade bu sınıfların örnekleri kullanarak `x + 3` şu şekilde temsil edilebilir.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

`Evaluate` Yöntemi bir `Expression` örneği belirtilen ifadeyi değerlendirir ve üretmek için çağrıldığında bir `double` değeri. Yöntem alır bir `Dictionary` (anahtar olarak girişlerinin) değişken adları ve değerleri (olarak girdilerinin değerlerini) içeren bir bağımsız değişken. Çünkü `Evaluate` soyut bir yöntem, türetilen soyut olmayan sınıflar `Expression` kılmalı `Evaluate`.

A `Constant`'s uygulaması `Evaluate` yalnızca saklı sabiti döndürür. A `VariableReference`kullanıcının sözlük değişken adında uygulama arar ve elde edilen değeri döndürür. Bir `Operation`ait uygulama ilk sol ve sağ işlenen değerlendirilir (yinelemeli olarak çağırarak kendi `Evaluate` yöntemleri) ve ardından belirli bir aritmetik işlemi gerçekleştirir.

Aşağıdaki program kullanan `Expression` ifadeyi değerlendiren şeyde sınıfları `x * (y + 2)` farklı değerler için `x` ve `y`.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Yöntemi aşırı yüklemesi

Yöntemi *aşırı yükleme* aynı sınıfta benzersiz imzaları sahip oldukları sürece aynı ada sahip birden çok yöntem izin verir. Aşırı yüklenmiş yöntem çağrısından derlerken, derleyicinin kullandığı *aşırı yükleme çözümlemesi* çağrılacak belirli yöntemi belirlemek için. En iyi eşleşen bağımsız değişkenler veya tek en iyi eşleşme bulunamazsa, bir hata raporları bir yöntemi aşırı yükleme çözünürlüğü bulur. Aşağıdaki örnek, aşırı yükleme çözünürlüğü geçerli gösterir. Her bir çağrıda yorum `UsageExample` yöntemi gösterir hangi yöntemi gerçekten çağrılır.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Örnekte gösterildiği gibi belirli bir yöntem her zaman tam parametre türleri bağımsız değişkenleri açıkça atama ve/veya tür bağımsız değişkenleri açıkça sağlama tarafından seçilebilir.

## <a name="other-function-members"></a>Diğer işlev üyeleri

Yürütülebilir kod içeren bir üye olarak bilinir topluca *işlev üyeleri* bir sınıf. Birincil işlev üyeleri türü olan yöntemler, önceki bölümde açıklanmaktadır. Bu bölümde bir işlev üyeleri tarafından desteklenen tür açıklanmaktadır C#: Oluşturucular, özellikleri, Dizinleyicileri, olayları, işleçler ve sonlandırıcılar.

Adlı bir genel sınıf aşağıdaki gösterir `MyList<T>`, growable nesnelerin listesini uygular. Sınıf işlev üyeleri en yaygın tür çeşitli örneklerini içerir.

> [!NOTE]
> Bu örnekte bir `MyList` .NET standard ile aynı değil, sınıf <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Bu turda gerekli kavramları göstermek, ancak o sınıf için yerine geçmez.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Oluşturucular

C# örneği hem de statik oluşturucular destekler. Bir *örnek oluşturucusu* uygulayan bir sınıf örneği başlatmak için gerekli eylemleri bir üyesidir. A *statik Oluşturucu* ilk yüklendiğinde bir sınıf başlatmak için gerekli eylemleri uygulayan bir üyesidir.

Bir oluşturucu dönüş türü ve kapsayan sınıfı aynı ada sahip bir yöntemi gibi bildirilir. Statik değiştirici Oluşturucu bildirimi içeriyorsa, bir statik Oluşturucu bildirir. Aksi takdirde, bir örnek oluşturucusu bildirir.

Örnek oluşturucuları aşırı yüklenebilir ve isteğe bağlı parametreler olabilir. Örneğin, `MyList<T>` sınıfı bildirir, bir parametre ve süren iki örnek oluşturucuları bir `int` parametresi. Örnek oluşturucuları kullanarak çağrılır `new` işleci. Aşağıdaki deyimleri iki ayırma `MyList<string>` Oluşturucusu kullanarak örneği `MyList` sınıfı ile ve isteğe bağlı bağımsız değişken olmadan.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Diğer üyeleri farklı olarak örnek oluşturucuları olmayan devralınır ve sınıfı, bu gerçekte bildirilen dışında hiçbir örnek oluşturucuları bir sınıfa sahip. Hiçbir örnek oluşturucusu için bir sınıf sağlanırsa, sonra boş bir parametre olmadan otomatik olarak sağlanır.

### <a name="properties"></a>Özellikler

*Özellikleri* alanları doğal bir uzantısıdır. Her ikisi de ilişkili türlerini üyeleriyle adlı ve alanlar ve Özellikler erişmek için sözdizimi aynıdır. Ancak, alanlar özellikleri depolama konumları belirtmek değil. Bunun yerine, özelliklere sahip *erişimcileri* değerlerine okunabilir veya yazılabilir bırakıldığında yürütülecek deyimler belirtin.

Bildirimi bir alma erişimcisi ve/veya sınırlayıcılar arasında yazılan ayarlama erişimcisine biten dışında bir özellik gibi bir alan, bildirilmiş `{` ve `}` noktalı bitiş yerine. Hem bir alma erişimcisi hem de ayarlama erişimcisine sahip olduğu bir özelliği bir *okuma-yazma özelliği*, yalnızca bir alma erişimcisi bir özelliği bir *salt okunur özelliği*, ve yalnızca bir set erişimcisine sahip bir özelliği bir *salt yazılır özelliği*.

Bir alma erişimcisi, dönüş değeri, özellik türü olan bir parametresiz yöntemin karşılık gelir. Bir özellik bir ifadede başvurulduğunda dışında bir atama hedefi olarak özelliğin get erişimcisine özelliğin değerini hesaplamak için çağrılır.

Ayarlama erişimcisine değeri ve dönüş türü olarak adlandırılan tek bir parametre ile bir yönteme karşılık gelir. Ne zaman bir özelliği başvuru atama hedefi veya işleneni olarak ++ veya--, set erişimcisine yeni değer sağlayan bağımsız değişkenlerle çağrılır.

`MyList<T>` Sınıfı bildirir iki özellik `Count` ve `Capacity`, olan salt okunur ve okuma-yazma, sırasıyla. Bu özelliklerin kullanımı bir örnek verilmiştir:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Benzer şekilde, alanlar ve yöntemler, C# örnek özelliklerini hem statik özelliklerini destekler. Statik özellikler statik değiştiricisi ile bildirilir ve örnek özelliklerini olmadan bildirilir.

Bir özelliğin accessor(s) sanal olabilir. Ne zaman bir özellik bildirimi içeren bir `virtual`, `abstract`, veya `override` değiştiricisi, özellik accessor(s) için geçerlidir.

### <a name="indexers"></a>Dizin Oluşturucular

Bir *dizin oluşturucu* nesneleri dizisi olarak aynı şekilde dizinlenmesini sağlar bir üyesidir. Üyenin adını bu sınırlayıcılar arasında yazılmış bir parametre listesi ardından olması dışında dizin oluşturucu bir özellik gibi bildirilir `[` ve `]`. Parametreler, dizin oluşturucunun accessor(s) içinde kullanılabilir. Benzer şekilde, özellikler, dizin oluşturucular okuma-yazma, salt okunur ve salt yazılır olabilir ve bir dizin oluşturucu accessor(s) sanal olabilir.

`MyList<T>` Sınıfı bildirir gereken tek bir okuma-yazma dizin oluşturucu bir `int` parametresi. Dizin oluşturucunun, dizin mümkün kılar `MyList<T>` ile örnekler `int` değerleri. Örneğin:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Dizin Oluşturucular, sayı veya kendi parametre türleri farklı olduğu sürece bir sınıfın birden çok dizin oluşturucu bildirebilirsiniz anlamına gelen aşırı yüklenebilir.

### <a name="events"></a>Olaylar

Bir *olay* bir sınıf veya nesne bildirimleri sağlamak için sağlayan bir üyesidir. Bir olay gibi bir alan bildirimi bir event anahtar sözcüğü içerir ve türü bir temsilci türü olmalıdır bildirilir.

(Olay soyut değil ve erişimcileri bildirmiyor sağlanan) bir olay üyesi bildiren bir sınıf içinde olay yalnızca bir temsilci türüne bir alan gibi davranır. Olaya eklenmiş olan olay işleyicilerini temsil eden bir temsilci bir başvuru alan depolar. Hiçbir olay işleyicileri varsa alandır `null`.

`MyList<T>` Sınıfı olarak adlandırılan tek bir olay üyesi bildirir `Changed`, yeni bir öğe listesine eklendiğini gösterir. Değiştirilen olay tarafından gerçekleştirilen `OnChanged` hangi ilk olay olup olmadığını denetler, sanal bir yöntem `null` (hiçbir işleyicileri bulunduğunu anlamına gelir). Olay bildirmek, kavram olay tarafından temsil edilen temsilci çağırmak için tam olarak eşittir; Bu nedenle, olayları oluşturma için hiçbir özel dil yapıları vardır.

İstemciler react ile olayları *olay işleyicileri*. Olay işleyicileri kullanılarak eklenen `+=` işleci ve kaldırılan kullanarak `-=` işleci. Aşağıdaki örnek bir olay işleyicisi ekler `Changed` olayı bir `MyList<string>`.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Denetim bir olay temel alınan depolamanın istenen burada Gelişmiş senaryolar için bir olay bildirimi açıkça sağlayabilir `add` ve `remove` biraz benzerdir erişimcileri `set` özellik erişimcisi.

### <a name="operators"></a>İşleçler

Bir *işleci* belirli ifade işleci bir sınıfın bir örneği için uygulama ne anlama geldiğini tanımlayan bir üyesidir. Üç tür işleç tanımlanabilir: Birli işleçler, ikili işleçler ve dönüştürme işleçleri. Tüm işleçler olarak bildirilmelidir `public` ve `static`.

`MyList<T>` Sınıfı bildirir iki işleç `operator ==` ve `operator !=`ve bu nedenle bu işleçleri için geçerli ifadeler için yeni anlamı verir `MyList` örnekleri. Özellikle, iki eşitlik işleçleri tanımlama `MyList<T>` örnekleri her biri kendi eşittir yöntemlerini kullanarak kapsanan nesneleri karşılaştırma olarak. Aşağıdaki örnekte `==` karşılaştırmak için işleci `MyList<int>` örnekleri.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

İlk `Console.WriteLine` çıkarır `True` listelerini nesneleri aynı sırada aynı değerlerle aynı sayıda içerdiğinden. Vardı `MyList<T>` tanımlanmamış `operator ==`, ilk `Console.WriteLine` çıkış `False` çünkü `a` ve `b` başvuru farklı `MyList<int>` örnekleri.

### <a name="finalizers"></a>Sonlandırıcılar

A *Sonlandırıcı* uygulayan bir sınıfın örneği sonlandırmaya gereken eylemler bir üyesidir. Sonlandırıcı parametrelere sahip olamaz, Erişilebilirlik değiştiricilere sahip olamaz ve açıkça çağrılamaz. Bir örneği için Sonlandırıcı çöp toplama sırasında otomatik olarak çağrılır.

Çöp toplayıcı nesnelerin toplamak ve sonlandırıcılar çalıştırmak ne zaman karar içinde geniş enlem izin verilir. Özellikle, sonlandırıcı çağrılarını zamanlamasını belirleyici değildir ve sonlandırıcılar herhangi bir iş parçacığı üzerinde çalıştırılabilir. Diğer çözüm uygun olduğunda bunlar ve diğer nedenleriyle sınıfları sonlandırıcılar uygulamalıdır.

`using` Deyim nesnesi yok etme için daha iyi bir yaklaşım sağlar.

> [!div class="step-by-step"]
> [Önceki](statements.md)
> [İleri](structs.md)
