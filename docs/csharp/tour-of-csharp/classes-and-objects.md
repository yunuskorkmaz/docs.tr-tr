---
title: İçindeki C# sınıflar ve nesneler- C# dilin turu
description: Yeni C#misiniz? Sınıflar, nesneler ve devralmayla bu genel bakışı okuyun
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: be8e760b19b7ca5305918ecfdbf9ad797d7e76b2
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105628"
---
# <a name="classes-and-objects"></a>Sınıflar ve nesneler

*Sınıflar* , türlerin en temel C#larıdır. Bir sınıf, durumu (alanları) ve eylemleri (Yöntemler ve diğer işlev üyelerini) tek bir birimde birleştiren bir veri yapısıdır. Sınıf, *nesne*olarak da bilinen, sınıfının dinamik olarak oluşturulan *örnekleri* için bir tanım sağlar. Sınıflar, *Devralma* ve çok *biçimlilik*desteği, *türetilmiş sınıfların* *temel sınıfları*genişletebileceği ve özelleştirilebilecek mekanizmalar.

Yeni sınıflar sınıf bildirimleri kullanılarak oluşturulur. Sınıf bildirimi, sınıfın özniteliklerini ve değiştiricilerini, sınıfın adını, Taban sınıfını (belirtilmişse) ve sınıf tarafından uygulanan arabirimleri belirten bir üstbilgiyle başlar. Üst bilgi, `{` ve `}`sınırlayıcılarının yazıldığı üye bildirimlerinin bir listesinden oluşan sınıf gövdesinden gelir.

Aşağıda `Point`adlı basit bir sınıfın bildirimi verilmiştir:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Sınıf örnekleri, yeni bir örnek için bellek ayıran `new` işleci kullanılarak oluşturulur, örneği başlatmak için bir oluşturucu çağırır ve örneğe bir başvuru döndürür. Aşağıdaki deyimler iki nokta nesnesi oluşturur ve bu nesnelere başvuruları iki değişken halinde depolar:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Nesne artık erişilebilir olmadığında bir nesnenin kapladığı bellek otomatik olarak geri kazanılır. Üzerinde C#nesneleri açıkça serbest bırakmak gerekli değildir veya mümkün değildir.

## <a name="members"></a>Üyeler

Bir sınıfın üyeleri statik üyeler veya örnek üyeleridir. Statik Üyeler sınıflara aittir ve örnek üyeleri nesnelere aittir (sınıf örnekleri).

Aşağıda bir sınıfın içerebileceği üye türlerine ilişkin bir genel bakış sunulmaktadır.

- {1&gt;Sabitler&lt;1}
  - Sınıfla ilişkili sabit değerler
- Alanlar
  - Sınıfın değişkenleri
- Yöntemler
  - Sınıfı tarafından gerçekleştirilebilecek hesaplamalar ve eylemler
- Özellikler
  - Sınıfın adlandırılmış özelliklerini okuma ve yazma ile ilişkili eylemler
- Dizin Oluşturucular
  - Bir dizi gibi sınıfın dizin oluşturma örnekleri ile ilişkili eylemler
- Olaylar
  - Sınıfı tarafından oluşturulabilecek bildirimler
- İşleçler
  - Sınıf tarafından desteklenen dönüşümler ve ifade işleçleri
- Oluşturucular
  - Sınıfın veya sınıfın örneklerinin örneğini başlatmak için gereken eylemler
- Sonlandırıcılar
  - Sınıfın örneklerinden önce gerçekleştirilecek eylemler kalıcı olarak atılır
- Türler
  - Sınıf tarafından tanımlanan iç içe türler

## <a name="accessibility"></a>Erişilebilirlik

Bir sınıfın her üyesinin ilişkili bir erişilebilirliği vardır ve bu, üyeye erişebilen program metni bölgelerini denetler. Olası altı erişilebilirlik biçimi vardır. Bunlar aşağıda özetlenmiştir.

- `public`
  - Erişim sınırlı değil
- `protected`
  - Bu sınıftan türetilmiş bu sınıfla veya sınıflarla sınırlı erişim
- `internal`
  - Geçerli bütünleştirilmiş koda (. exe,. dll, vb.) sınırlı erişim
- `protected internal`
  - İçerilen sınıfla sınırlı erişim, kapsayan sınıftan türetilmiş sınıflar veya aynı derleme içindeki sınıflar
- `private`
  - Bu sınıfla sınırlı erişim
- `private protected`
  - Aynı derleme içindeki kapsayan türden türetilmiş kapsayan sınıf veya sınıflarla sınırlı erişim

## <a name="type-parameters"></a>Tür parametreleri

Sınıf tanımı, tür parametre adlarının bir listesini kapsayan açılı ayraçları olan sınıf adını izleyerek bir tür parametreleri kümesi belirtebilir. Daha sonra tür parametreleri sınıfının üyelerini tanımlamak için sınıf bildirimlerinin gövdesinde kullanılabilir. Aşağıdaki örnekte, `Pair` türü parametreleri `TFirst` ve `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Tür parametrelerini almak için belirtilen bir sınıf türüne *Genel sınıf türü*denir. Yapı, arabirim ve temsilci türleri de genel olabilir.
Genel sınıf kullanıldığında, tür parametrelerinin her biri için tür bağımsız değişkenlerinin sağlanması gerekir:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Yukarıda `Pair<int,string>` gibi sunulan tür bağımsız değişkenlerine sahip genel bir tür, *oluşturulmuş bir tür*olarak adlandırılır.

## <a name="base-classes"></a>Temel sınıflar

Sınıf bildirimi, sınıf adı ve tür parametreleri iki nokta ve temel sınıfın adı ile birlikte bir temel sınıf belirtebilir. Temel sınıf belirtiminin atlanması `object`türünden türeterek aynıdır. Aşağıdaki örnekte, `Point3D` temel sınıfı `Point`ve `Point` taban sınıfı `object`:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Bir sınıf, temel sınıfının üyelerini devralır. Devralma, bir sınıfın örnek ve statik oluşturucular ve temel sınıfın sonlandırıcıları dışında, temel sınıfının tüm üyelerini örtük olarak içerdiği anlamına gelir. Türetilmiş bir sınıf, devralananlara yeni üyeler ekleyebilir, ancak devralınmış bir üyenin tanımını kaldıramaz. Önceki örnekte, `Point3D` `x` ve `y` alanları `Point`devralır ve her `Point3D` örnek, `x`, `y`ve `z`üç alan içerir.

Bir sınıf türünden, temel sınıf türlerinden herhangi birine örtük bir dönüştürme vardır. Bu nedenle, bir sınıf türünün değişkeni bu sınıfın bir örneğine veya türetilmiş herhangi bir sınıfın örneğine başvurabilir. Örneğin, önceki sınıf bildirimleri verildiğinde `Point` türünde bir değişken `Point` veya `Point3D`başvurabilir:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Alanlar

*Alan* , bir sınıf ile veya bir sınıf örneğiyle ilişkili bir değişkendir.

Statik değiştiriciyle belirtilen bir alan statik bir alan tanımlar. Statik alan tam olarak bir depolama konumunu tanımlar. Bir sınıfın kaç örneğinin oluşturulduğuna bakılmaksızın, bir statik alanın yalnızca bir kopyası vardır.

Statik değiştirici olmadan belirtilen bir alan bir örnek alanını tanımlar. Bir sınıfın her örneği, bu sınıfın tüm örnek alanlarının ayrı bir kopyasını içerir.

Aşağıdaki örnekte, `Color` sınıfının her örneği `r`, `g`ve `b` örneği alanlarının ayrı bir kopyasına sahiptir ancak `Black`, `White`, `Red`, `Green`ve `Blue` statik alanlarının yalnızca bir kopyası vardır:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Önceki örnekte gösterildiği gibi, *salt okuma alanları* `readonly` değiştiricisi ile bildirilebilecek. Bir `readonly` alana atama yalnızca alanın bildiriminin veya aynı sınıftaki bir oluşturucunun parçası olarak gerçekleşebilir.

## <a name="methods"></a>Yöntemler

Bir *Yöntem* , bir nesne veya sınıf tarafından gerçekleştirilebilecek bir hesaplama veya eylem uygulayan bir üyesidir. *Statik yöntemlere* sınıfı aracılığıyla erişilir. *Örnek yöntemlerine* , sınıfının örnekleri aracılığıyla erişilir.

Yöntemler, yönteme geçirilen değerleri veya değişken başvurularını temsil eden bir *parametre*listesine ve hesaplanan ve yöntem tarafından döndürülen değer türünü belirten bir *dönüş türüne*sahip olabilir. Bir yöntemin dönüş türü bir değer döndürmezse `void`.

Türler gibi yöntemler de bir tür parametreleri kümesine sahip olabilir, bu da yöntem çağrıldığında tür bağımsız değişkenlerinin belirtilmesi gerekir. Türlerin aksine, tür bağımsız değişkenleri genellikle yöntem çağrısının bağımsız değişkenlerinden çıkarsanamıyor ve açıkça verilmemelidir.

Yöntemin *imzası* , yöntemin bildirildiği sınıfta benzersiz olmalıdır. Bir yöntemin imzası yöntemin adından, tür parametrelerinin sayısına ve parametrelerinin sayısına, değiştiricilerine ve türlerine sahiptir. Bir yöntemin imzası, dönüş türünü içermez.

### <a name="parameters"></a>Parametreler

Parametreler, değerlere veya değişken başvurularını yöntemlere geçirmek için kullanılır. Bir yöntemin parametreleri, yöntemi çağrıldığında belirtilen *bağımsız değişkenlerden* gerçek değerlerini alır. Dört tür parametre vardır: değer parametreleri, başvuru parametreleri, çıkış parametreleri ve parametre dizileri.

Giriş bağımsız değişkenlerini geçirmek için bir *değer parametresi* kullanılır. Değer parametresi, parametresi için geçirilen bağımsız değişkenden ilk değerini alan yerel bir değişkene karşılık gelir. Değer parametresindeki değişiklikler, parametresi için geçirilen bağımsız değişkeni etkilemez.

Değer parametreleri, ilgili bağımsız değişkenlerin atlanabilmesi için varsayılan bir değer belirtilerek isteğe bağlı olabilir.

*Başvuru parametresi* , bağımsız değişkenleri başvuruya göre geçirmek için kullanılır. Başvuru parametresi için geçirilen bağımsız değişken, kesin bir değere sahip bir değişken olmalıdır ve yöntemin yürütülmesi sırasında başvuru parametresi, bağımsız değişken değişkeniyle aynı depolama konumunu temsil eder. Bir başvuru parametresi `ref` değiştiricisiyle birlikte bildirilmiştir. Aşağıdaki örnek `ref` parametrelerinin kullanımını gösterir.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

Bir *output parametresi* , bağımsız değişkenleri başvuruya göre geçirmek için kullanılır. Bir başvuru parametresine benzer, ancak çağıran tarafından belirtilen bağımsız değişkene açıkça bir değer atamanız gerekmez. Bir çıkış parametresi `out` değiştiricisiyle birlikte bildirilmiştir. Aşağıdaki örnek, 7 ' de C# tanıtılan sözdizimi kullanılarak `out` parametrelerinin kullanımını gösterir.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

Bir *parametre dizisi* , bir metoda değişken sayıda bağımsız değişken geçirilmesine izin verir. Bir parametre dizisi `params` değiştiricisiyle birlikte bildirilmiştir. Bir yöntemin yalnızca son parametresi bir parametre dizisi olabilir ve bir parametre dizisinin türü tek boyutlu bir dizi türü olmalıdır. <xref:System.Console?displayProperty=nameWithType> sınıfının Write ve WriteLine yöntemleri, parametre dizisi kullanımının iyi örnekleridir. Bunlar aşağıdaki gibi bildirilmiştir.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Bir parametre dizisi kullanan bir yöntem içinde, parametre dizisi tam olarak bir dizi türünün normal parametresine benzer şekilde davranır. Ancak, bir parametre dizisi olan bir yöntem çağrısında, parametre dizisi türünün tek bir bağımsız değişkenini veya parametre dizisinin öğe türünün herhangi bir sayıda bağımsız değişkenini geçirmek mümkündür. İkinci durumda, bir dizi örneği otomatik olarak oluşturulur ve verilen bağımsız değişkenlerle başlatılır. Bu örnek

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

, aşağıdaki yazma ile eşdeğerdir.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Yöntem gövdesi ve yerel değişkenler

Yöntemin gövdesi, yöntemi çağrıldığında yürütülecek deyimleri belirtir.

Yöntem gövdesi, yöntemi çağrısına özgü değişkenleri bildirebilir. Bu tür değişkenlere *yerel değişkenler*denir. Yerel bir değişken bildirimi bir tür adı, değişken adı ve muhtemelen bir başlangıç değeri belirtir. Aşağıdaki örnek, başlangıç değeri sıfır olan `i` yerel bir değişken ve ilk değeri olmayan `j` bir yerel değişken bildirir.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C#değeri alınabilmesi için önce bir yerel değişkenin *kesinlikle atanmasını* gerektirir. Örneğin, önceki `i` bildirimi bir başlangıç değeri içermiyorsa, `i`, programda bu noktalarda kesinlikle atanamadığı için, derleyici `i` sonraki kullanımları için bir hata raporlayabilir.

Bir yöntem, `return` deyimlerini kullanarak çağıranına denetim döndürebilir. `void`döndüren bir yöntemde `return` deyimler bir ifade belirtemez. Void olmayan `return` deyimlerini döndüren bir yöntemde, dönüş değerini hesaplayan bir ifade içermelidir.

### <a name="static-and-instance-methods"></a>Statik ve örnek yöntemleri

Statik değiştirici ile belirtilen bir yöntem *statik bir yöntemdir*. Statik bir yöntem belirli bir örnek üzerinde çalışmaz ve yalnızca statik üyelere doğrudan erişebilir.

Statik değiştirici olmadan belirtilen bir yöntem bir *örnek yöntemidir*. Örnek yöntemi, belirli bir örnek üzerinde çalışır ve hem statik hem de örnek üyelerine erişebilir. Örnek yönteminin çağrıldığı örnek, `this`olarak açıkça erişilebilir. Statik bir yöntemde `this` başvurmak hatadır.

Aşağıdaki `Entity` sınıfı hem statik hem de örnek üyelere sahiptir.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Her bir `Entity` örneği bir seri numarası içerir (ve burada görünmeyen bazı diğer bilgileri kabul etmez). `Entity` Oluşturucusu (bir örnek yöntemi gibi) yeni örneği bir sonraki kullanılabilir seri numarası ile başlatır. Oluşturucu bir örnek üyesi olduğundan, hem `serialNo` örnek alanına hem de `nextSerialNo` statik alanına erişim izni verilir.

`GetNextSerialNo` ve `SetNextSerialNo` statik yöntemleri `nextSerialNo` statik alana erişebilir, ancak `serialNo` örnek alanına doğrudan erişmesi için bir hata olabilir.

Aşağıdaki örnek, Entity sınıfının kullanımını gösterir.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Sınıf üzerinde `GetSerialNo` örnek yöntemi çağrıldığında, `SetNextSerialNo` ve `GetNextSerialNo` statik yöntemlerinin sınıfında çağırılacağını unutmayın.

### <a name="virtual-override-and-abstract-methods"></a>Sanal, geçersiz kılma ve soyut yöntemler

Bir örnek yöntemi bildirimi `virtual` değiştirici içerdiğinde, yöntem *sanal bir yöntem*olarak kabul edilir. Bir sanal değiştirici yoksa, yöntem *sanal olmayan bir yöntem*olarak kabul edilir.

Bir sanal yöntem çağrıldığında, çağrının gerçekleştiği örneğin *çalışma zamanı türü* , çağrılacak gerçek Yöntem uygulamasını belirler. Sanal olmayan bir yöntem çağrısında, örneğin *derleme zamanı türü* belirleme faktörü olur.

Bir sanal yöntem, türetilmiş bir sınıfta *geçersiz kılınabilir* . Bir örnek yöntemi bildirimi bir geçersiz kılma değiştiricisi içerdiğinde, yöntemi aynı imzaya sahip devralınmış bir sanal yöntemi geçersiz kılar. Sanal bir yöntem bildiriminde yeni bir yöntem tanıtıldığı halde, bir geçersiz kılma yöntemi bildirimi, bu yöntemin yeni bir uygulamasını sağlayarak, var olan bir devralınmış sanal yöntemi uzmanlık eder.

*Soyut bir yöntem* , uygulama içermeyen bir sanal yöntemdir. Soyut bir yöntem soyut değiştiriciyle birlikte bildirilmiştir ve yalnızca soyut olarak da tanımlanmış bir sınıfta izin verilir. Soyut olmayan her türetilmiş sınıfta bir soyut yöntem geçersiz kılınmalıdır.

Aşağıdaki örnek, bir soyut sınıfı, bir ifade ağaç düğümünü temsil eden `Expression`, üç türetilmiş sınıf, `Constant`, `VariableReference`ve `Operation`sabitler, değişken başvuruları ve aritmetik işlemler için ifade ağacı düğümleri uygulayan bildirir. (Bu şuna benzerdir, ancak ifade ağacı türleriyle karıştırılmamalıdır).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Önceki dört sınıf aritmetik ifadeleri modellemek için kullanılabilir. Örneğin, bu sınıfların örneklerini kullanarak ifade `x + 3` aşağıdaki gibi gösterilebilir.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

Bir `Expression` örneğinin `Evaluate` Yöntemi verilen ifadeyi değerlendirmek ve bir `double` değeri üretmek için çağrılır. Yöntemi, değişken adlarını (girdilerin anahtarları olarak) ve değerlerini (girdilerin değerleri olarak) içeren `Dictionary` bir bağımsız değişken alır. `Evaluate` soyut bir yöntem olduğundan, `Expression` türetilmiş soyut olmayan sınıfların `Evaluate`geçersiz kılması gerekir.

`Constant``Evaluate` uygulanması yalnızca depolanan sabiti döndürür. `VariableReference`uygulama, sözlükte değişken adını arar ve elde edilen değeri döndürür. `Operation`uygulamasının ilk önce sol ve sağ işlenenleri değerlendirir (`Evaluate` yöntemlerini yinelemeli olarak çağırarak) ve ardından verilen aritmetik işlemi gerçekleştirir.

Aşağıdaki program, `x` ve `y`farklı değerleri için ifade `x * (y + 2)` değerlendirmek üzere `Expression` sınıflarını kullanır.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Yöntem aşırı yüklemesi

Yöntem *aşırı yüklemesi* , aynı sınıftaki birden çok metodun benzersiz imzalara sahip oldukları sürece aynı ada sahip olmasını sağlar. Aşırı yüklenmiş bir yöntemin çağrılması derlenirken, derleyici çağrılacak özel yöntemi belirlemekte *aşırı yükleme çözümü* kullanır. Aşırı yükleme çözümlemesi, bağımsız değişkenlerle en iyi eşleşen bir yöntemi bulur veya tek bir en iyi eşleşme bulunamazsa hata bildiriyor. Aşağıdaki örnekte, etkin olan aşırı yükleme çözümü gösterilmektedir. `UsageExample` yöntemi içindeki her çağrının yorumu, hangi yöntemin gerçekten çağrılacağını gösterir.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Örnekte gösterildiği gibi belirli bir yöntem her zaman bağımsız değişkenleri tam parametre türlerine açıkça atayarak ve/veya açıkça tür bağımsız değişkenleri sunarak seçilebilir.

## <a name="other-function-members"></a>Diğer işlev üyeleri

Yürütülebilir kod içeren Üyeler topluca bir sınıfın *işlev üyeleri* olarak bilinir. Yukarıdaki bölümde, işlev üyelerinin birincil türü olan yöntemler açıklanmıştır. Bu bölümde, tarafından C#desteklenen diğer işlev üyesi türleri açıklanmaktadır: oluşturucular, özellikler, Dizin oluşturucular, olaylar, işleçler ve sonlandırıcılar.

Aşağıda, growable bir nesne listesi uygulayan `MyList<T>`adlı bir genel sınıf gösterilmektedir. Sınıfı, en yaygın işlev üyesi türlerine birkaç örnek içerir.

> [!NOTE]
> Bu örnekte, .NET Standard <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>ile aynı olmayan bir `MyList` sınıfı oluşturulur. Bu, bu tur için gereken kavramları gösterir, ancak bu sınıfın yerini almaz.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Oluşturucular

C#hem örnek hem de statik oluşturucuları destekler. *Örnek Oluşturucu* , bir sınıfın örneğini başlatmak için gereken eylemleri uygulayan bir üyedir. *Statik Oluşturucu* , ilk yüklendiği zaman bir sınıfın kendisini başlatmak için gereken eylemleri uygulayan bir üyesidir.

Bir Oluşturucu, dönüş türü olmayan bir yöntem ve kapsayan sınıfla aynı adı ile birlikte bildirilmiştir. Bir Oluşturucu bildirimi statik değiştirici içeriyorsa, statik bir Oluşturucu bildirir. Aksi takdirde, bir örnek Oluşturucu bildirir.

Örnek oluşturucular aşırı yüklenebilir ve isteğe bağlı parametrelere sahip olabilir. Örneğin `MyList<T>` sınıfı, tek bir isteğe bağlı `int` parametresine sahip bir örnek Oluşturucu bildirir. Örnek oluşturucular `new` işleci kullanılarak çağrılır. Aşağıdaki deyimler, ve isteğe bağlı bağımsız değişken olmadan `MyList` sınıfının yapıcısını kullanarak iki `MyList<string>` örneği ayırır.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Diğer üyelerin aksine, örnek oluşturucular devralınmaz ve bir sınıfın sınıfta tanımlananlardan farklı örnek oluşturucuları yoktur. Bir sınıf için örnek Oluşturucu sağlanmazsa, parametresi olmayan boş bir değer otomatik olarak sağlanır.

### <a name="properties"></a>Özellikler

*Özellikler* , alanlar için doğal bir uzantıdır. Her ikisi de ilişkili türlerin bulunduğu isimlerdir ve alanlara ve özelliklere erişim için sözdizimi aynıdır. Ancak, alanların aksine, Özellikler depolama konumlarını göstermiyor. Bunun yerine, özellikler, değerleri okunmak veya yazıldığında yürütülecek deyimleri belirten *erişimcileri* vardır.

Bir özellik, bir alan gibi, bildirim bir get erişimcisi ve/veya sınırlayıcılar arasında yazılmış bir set erişimcisi ve/veya virgülle sona ermek yerine `}` `{` Hem get erişimcisine hem de bir set erişimcisine sahip olan bir özellik *okuma-yazma özelliğidir*, yalnızca bir get erişimcisine sahip olan bir özellik *salt okunurdur*ve yalnızca bir set erişimcisi olan bir özellik yalnızca bir salt *yazılır özelliktir*.

Get erişimcisi, özellik türünün dönüş değeri olan parametresiz bir yönteme karşılık gelir. Atama hedefi haricinde, bir ifadede bir özelliğe başvurulduğunda, özelliğin değerini hesaplamak için özelliğin get erişimcisi çağrılır.

Bir set erişimcisi, value adlı tek parametreli ve dönüş türü olmayan bir yönteme karşılık gelir. Bir atamaya bir atama hedefi olarak veya + + veya--, işleneni olarak başvurulduğunda, yeni değer sağlayan bir bağımsız değişkenle çağrılır.

`MyList<T>` sınıfı, sırasıyla salt okuma ve okuma-yazma olan iki özellik `Count` ve `Capacity`bildirir. Aşağıda bu özelliklerin kullanılmasına bir örnek verilmiştir:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Alanlar ve yöntemlere benzer şekilde hem C# örnek özelliklerini hem de statik özellikleri destekler. Statik özellikler statik değiştirici ile tanımlanır ve örnek özellikleri bu olmadan tanımlanır.

Bir özelliğin erişimcisi sanal olabilir. Bir özellik bildirimi `virtual`, `abstract`veya `override` değiştiricisini içerdiğinde, özelliğin erişimcilerle geçerli olur.

### <a name="indexers"></a>Dizin Oluşturucular

*Dizin Oluşturucu* , nesnelerin diziyle aynı şekilde dizinlenmesini sağlayan bir üyedir. Bir Dizin Oluşturucu, üye adının `this` ve ardından sınırlayıcı `[` ve `]`arasında yazılmış bir parametre listesi olması dışında bir özellik gibi bildirilmiştir. Parametreler, dizin oluşturucunun erişimcisinde kullanılabilir. Özelliklere benzer şekilde, Dizin oluşturucular okunabilir-yazılır, salt okunurdur ve salt yazılır olabilir ve bir dizin oluşturucunun erişimcisi sanal olabilir.

`MyList<T>` sınıfı, bir `int` parametresi alan tek bir okuma-yazma Dizin oluşturucuyu bildirir. Dizin Oluşturucu, `MyList<T>` örneklerinin `int` değerlerle dizinini oluşturmanızı mümkün kılar. Örneğin:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Dizin oluşturucular aşırı yüklenebilir, yani parametrelerinin sayısı veya türleri farklı olduğu sürece bir sınıfın birden çok dizin kümesini bildirebileceği anlamına gelir.

### <a name="events"></a>Olaylar

Bir *olay* , bir sınıf veya nesnenin bildirimler sağlamasını sağlayan bir üyedir. Bir olay, bildirim bir event anahtar sözcüğü içermesi ve türün bir temsilci türü olması dışında, bir alan gibi bildirilmiştir.

Olay üyesini bildiren bir sınıf içinde, olay bir temsilci türünün alanı gibi davranır (olay soyut değildir ve erişimcileri bildirmez). Bu alan, olaya eklenmiş olan olay işleyicilerini temsil eden bir temsilciye bir başvuru depolar. Hiçbir olay işleyicisi yoksa, alan `null`.

`MyList<T>` sınıfı, `Changed`adlı tek bir olay üyesini bildirir ve bu, listeye yeni bir öğe eklendiğini gösterir. Değiştirilen olay `OnChanged` sanal yöntemi tarafından tetiklenir ve bu, önce olayın `null` olup olmadığını denetler (hiçbir işleyici yok anlamına gelir). Bir olayı oluşturma kavramı, olayın gösterdiği temsilciyi çağırmak için tam olarak eşdeğerdir. bu nedenle, olayları yükseltmek için özel dil yapıları yoktur.

İstemciler *olay işleyicileri*aracılığıyla olaylara tepki verir. Olay işleyicileri `+=` işleci kullanılarak iliştirilir ve `-=` işleci kullanılarak kaldırılır. Aşağıdaki örnek, bir `MyList<string>``Changed` olayına bir olay işleyicisi ekler.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Bir olayın temeldeki depolamanın denetiminin istendiği Gelişmiş senaryolarda, bir olay bildirimi açıkça bir özelliğin `set` erişimcisine benzer olan `add` ve `remove` erişimcileri sağlayabilir.

### <a name="operators"></a>İşleçler

*İşleci* , bir sınıfın örneklerine belirli bir ifade işlecini uygulamanın anlamını tanımlayan bir üyesidir. Üç tür işleç tanımlanabilir: Birli İşleçler, ikili işleçler ve dönüştürme işleçleri. Tüm işleçler `public` ve `static`olarak bildirilmelidir.

`MyList<T>` sınıfı iki işleç bildirir `operator ==` ve `operator !=`ve bu işleçleri `MyList` örneklerine uygulayan deyimlere yeni anlam verir. Özel olarak, işleçler iki `MyList<T>` örneğinin eşitliğini tanımlar ve bu nesnelerin her birini eşittir yöntemlerini kullanarak karşılaştırır. Aşağıdaki örnek, iki `MyList<int>` örneğini karşılaştırmak için `==` işlecini kullanır.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

İki liste aynı sırada aynı değerlerle aynı sayıda nesne içerdiğinden, ilk `Console.WriteLine` `True` çıkışı oluşur. `operator ==`tanımlanmayan `MyList<T>`, `a` ve `b` farklı `MyList<int>` örneklerine başvurduğundan ilk `Console.WriteLine` çıkış `False` sahip olur.

### <a name="finalizers"></a>Sonlandırıcılar

*Sonlandırıcı* , bir sınıfın örneğini tamamlamak için gereken eylemleri uygulayan bir üyesidir. Sonlandırıcılar parametrelere sahip olamaz, erişilebilirlik değiştiricilerine sahip olamaz ve açıkça çağrılamaz. Örnek için Sonlandırıcı çöp toplama sırasında otomatik olarak çağrılır.

Çöp toplayıcısına, nesnelerin toplanması ve Sonlandırıcıların ne zaman toplanacağına karar verirken geniş bir enlem vardır. Özellikle, Sonlandırıcı etkinleştirmeleri zamanlaması belirleyici değildir ve herhangi bir iş parçacığında sonlandırıcılar çalıştırılabilir. Bu ve diğer nedenlerden dolayı sınıfların yalnızca başka hiçbir çözüm uygulanabilir olmadığında sonlandırıcılar uygulaması gerekir.

`using` ifade, nesne yok etme için daha iyi bir yaklaşım sağlar.

> [!div class="step-by-step"]
> [Önceki](statements.md)
> [İleri](structs.md)
