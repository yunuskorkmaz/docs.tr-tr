---
title: İçindeki C# sınıflar ve nesneler- C# dilin turu
description: Yeni C#misiniz? Sınıflar, nesneler ve devralmayla bu genel bakışı okuyun
ms.date: 08/10/2016
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: ff83a3198c6c9fb4c4a438d2486614a211c913ec
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971467"
---
# <a name="classes-and-objects"></a>Sınıflar ve nesneler

*Sınıflar* , türlerin en temel C#larıdır. Bir sınıf, durumu (alanları) ve eylemleri (Yöntemler ve diğer işlev üyelerini) tek bir birimde birleştiren bir veri yapısıdır. Sınıf, *nesne*olarak da bilinen, sınıfının dinamik olarak oluşturulan *örnekleri* için bir tanım sağlar. Sınıflar, *Devralma* ve çok *biçimlilik*desteği, *türetilmiş sınıfların* *temel sınıfları*genişletebileceği ve özelleştirilebilecek mekanizmalar.

Yeni sınıflar sınıf bildirimleri kullanılarak oluşturulur. Sınıf bildirimi, sınıfın özniteliklerini ve değiştiricilerini, sınıfın adını, Taban sınıfını (belirtilmişse) ve sınıf tarafından uygulanan arabirimleri belirten bir üstbilgiyle başlar. Üst bilgi, sınırlayıcılar `{` ve `}`arasında yazılmış üye bildirimlerinin listesinden oluşan sınıf gövdesinden gelir.

Aşağıda adlı `Point`basit bir sınıfın bildirimi verilmiştir:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Sınıf örnekleri, yeni bir örnek için `new` bellek ayıran işleç kullanılarak oluşturulur, örneği başlatmak için bir oluşturucu çağırır ve örneğe bir başvuru döndürür. Aşağıdaki deyimler iki nokta nesnesi oluşturur ve bu nesnelere başvuruları iki değişken halinde depolar:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Nesne artık erişilebilir olmadığında bir nesnenin kapladığı bellek otomatik olarak geri kazanılır. Üzerinde C#nesneleri açıkça serbest bırakmak gerekli değildir veya mümkün değildir.

## <a name="members"></a>Üyeler

Bir sınıfın üyeleri statik üyeler veya örnek üyeleridir. Statik Üyeler sınıflara aittir ve örnek üyeleri nesnelere aittir (sınıf örnekleri).

Aşağıda bir sınıfın içerebileceği üye türlerine ilişkin bir genel bakış sunulmaktadır.

* Sabitler
  - Sınıfla ilişkili sabit değerler
* Alanlar
  - Sınıfın değişkenleri
* Yöntemler
  - Sınıfı tarafından gerçekleştirilebilecek hesaplamalar ve eylemler
* Özellikler
  - Sınıfın adlandırılmış özelliklerini okuma ve yazma ile ilişkili eylemler
* Dizin Oluşturucular
  - Bir dizi gibi sınıfın dizin oluşturma örnekleri ile ilişkili eylemler
* Olaylar
  - Sınıfı tarafından oluşturulabilecek bildirimler
* İşleçler
  - Sınıf tarafından desteklenen dönüşümler ve ifade işleçleri
* Oluşturucular
  - Sınıfın veya sınıfın örneklerinin örneğini başlatmak için gereken eylemler
* Sonlandırıcılar
  - Sınıfın örneklerinden önce gerçekleştirilecek eylemler kalıcı olarak atılır
* Türler
  - Sınıf tarafından tanımlanan iç içe türler

## <a name="accessibility"></a>Erişilebilirlik

Bir sınıfın her üyesinin ilişkili bir erişilebilirliği vardır ve bu, üyeye erişebilen program metni bölgelerini denetler. Olası altı erişilebilirlik biçimi vardır. Bunlar aşağıda özetlenmiştir.

* `public`
  - Erişim sınırlı değil
* `protected`
  - Bu sınıftan türetilmiş bu sınıfla veya sınıflarla sınırlı erişim
* `internal`
  - Geçerli bütünleştirilmiş koda (. exe,. dll, vb.) sınırlı erişim
* `protected internal`
  - İçerilen sınıfla sınırlı erişim, kapsayan sınıftan türetilmiş sınıflar veya aynı derleme içindeki sınıflar
* `private`
  - Bu sınıfla sınırlı erişim
* `private protected`
  - Aynı derleme içindeki kapsayan türden türetilmiş kapsayan sınıf veya sınıflarla sınırlı erişim

## <a name="type-parameters"></a>Tür parametreleri

Sınıf tanımı, tür parametre adlarının bir listesini kapsayan açılı ayraçları olan sınıf adını izleyerek bir tür parametreleri kümesi belirtebilir. Daha sonra tür parametreleri sınıfının üyelerini tanımlamak için sınıf bildirimlerinin gövdesinde kullanılabilir. Aşağıdaki örnekte, öğesinin `Pair` `TFirst` tür parametreleri ve `TSecond`:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Tür parametrelerini almak için belirtilen bir sınıf türüne *Genel sınıf türü*denir. Yapı, arabirim ve temsilci türleri de genel olabilir.
Genel sınıf kullanıldığında, tür parametrelerinin her biri için tür bağımsız değişkenlerinin sağlanması gerekir:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Yukarıda olduğu gibi `Pair<int,string>` , tür bağımsız değişkenlerine sahip genel bir tür, oluşturulmuş bir *tür*olarak adlandırılır.

## <a name="base-classes"></a>Temel sınıflar

Sınıf bildirimi, sınıf adı ve tür parametreleri iki nokta ve temel sınıfın adı ile birlikte bir temel sınıf belirtebilir. Temel sınıf belirtiminin atlanması, türden `object`türetmeye benzer. `Point3D` Aşağıdaki örnekte, öğesinin `Point`temel sınıfı ve öğesinin `Point` `object`temel sınıfı:

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Bir sınıf, temel sınıfının üyelerini devralır. Devralma, bir sınıfın örnek ve statik oluşturucular ve temel sınıfın sonlandırıcıları dışında, temel sınıfının tüm üyelerini örtük olarak içerdiği anlamına gelir. Türetilmiş bir sınıf, devralananlara yeni üyeler ekleyebilir, ancak devralınmış bir üyenin tanımını kaldıramaz. Önceki örnekte `Point3D` , `Point3D` `x` `z`ve alanlarını`y` öğesinden`Point`devralır ve her örnek üç alan`y`içerir,, ve. `x`

Bir sınıf türünden, temel sınıf türlerinden herhangi birine örtük bir dönüştürme vardır. Bu nedenle, bir sınıf türünün değişkeni bu sınıfın bir örneğine veya türetilmiş herhangi bir sınıfın örneğine başvurabilir. Örneğin, önceki sınıf bildirimleri verildiğinde, türünde `Point` bir değişken bir `Point` veya a `Point3D`başvurabilir:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Alanlar

*Alan* , bir sınıf ile veya bir sınıf örneğiyle ilişkili bir değişkendir.

Statik değiştiriciyle belirtilen bir alan statik bir alan tanımlar. Statik alan tam olarak bir depolama konumunu tanımlar. Bir sınıfın kaç örneğinin oluşturulduğuna bakılmaksızın, bir statik alanın yalnızca bir kopyası vardır.

Statik değiştirici olmadan belirtilen bir alan bir örnek alanını tanımlar. Bir sınıfın her örneği, bu sınıfın tüm örnek alanlarının ayrı bir kopyasını içerir.

Aşağıdaki örnekte `Color` , sınıfının her örneği `r`, `g`, ve `b` `Black`örnek `Red`alanlarının ayrı bir kopyasına sahiptir ancak `White` ,,,,,,,,,,,,,,,,,,,`Green` ve`Blue` statik alanları:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Önceki örnekte gösterildiği gibi, *salt okuma alanları* bir `readonly` değiştirici ile bildirilebilecek. Bir `readonly` alana atama yalnızca alanın bildiriminin veya aynı sınıftaki bir oluşturucunun parçası olarak gerçekleşebilir.

## <a name="methods"></a>Yöntemler

Bir *Yöntem* , bir nesne veya sınıf tarafından gerçekleştirilebilecek bir hesaplama veya eylem uygulayan bir üyesidir. *Statik yöntemlere* sınıfı aracılığıyla erişilir. *Örnek yöntemlerine* , sınıfının örnekleri aracılığıyla erişilir.

Yöntemler, yönteme geçirilen değerleri veya değişken başvurularını temsil eden bir *parametre*listesine ve hesaplanan ve yöntem tarafından döndürülen değer türünü belirten bir *dönüş türüne*sahip olabilir. Bir yöntemin dönüş türü `void` bir değer döndürmezse.

Türler gibi yöntemler de bir tür parametreleri kümesine sahip olabilir, bu da yöntem çağrıldığında tür bağımsız değişkenlerinin belirtilmesi gerekir. Türlerin aksine, tür bağımsız değişkenleri genellikle yöntem çağrısının bağımsız değişkenlerinden çıkarsanamıyor ve açıkça verilmemelidir.

Yöntemin *imzası* , yöntemin bildirildiği sınıfta benzersiz olmalıdır. Bir yöntemin imzası yöntemin adından, tür parametrelerinin sayısına ve parametrelerinin sayısına, değiştiricilerine ve türlerine sahiptir. Bir yöntemin imzası, dönüş türünü içermez.

### <a name="parameters"></a>Parametreler

Parametreler, değerlere veya değişken başvurularını yöntemlere geçirmek için kullanılır. Bir yöntemin parametreleri, yöntemi çağrıldığında belirtilen *bağımsız değişkenlerden* gerçek değerlerini alır. Dört tür parametre vardır: değer parametreleri, başvuru parametreleri, çıkış parametreleri ve parametre dizileri.

Giriş bağımsız değişkenlerini geçirmek için bir *değer parametresi* kullanılır. Değer parametresi, parametresi için geçirilen bağımsız değişkenden ilk değerini alan yerel bir değişkene karşılık gelir. Değer parametresindeki değişiklikler, parametresi için geçirilen bağımsız değişkeni etkilemez.

Değer parametreleri, ilgili bağımsız değişkenlerin atlanabilmesi için varsayılan bir değer belirtilerek isteğe bağlı olabilir.

*Başvuru parametresi* , bağımsız değişkenleri başvuruya göre geçirmek için kullanılır. Başvuru parametresi için geçirilen bağımsız değişken, kesin bir değere sahip bir değişken olmalıdır ve yöntemin yürütülmesi sırasında başvuru parametresi, bağımsız değişken değişkeniyle aynı depolama konumunu temsil eder. Bir başvuru parametresi `ref` değiştiriciyle birlikte bildirilmiştir. Aşağıdaki örnek `ref` parametrelerin kullanımını gösterir.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

Bir *output parametresi* , bağımsız değişkenleri başvuruya göre geçirmek için kullanılır. Bir başvuru parametresine benzer, ancak çağıran tarafından belirtilen bağımsız değişkene açıkça bir değer atamanız gerekmez. Bir çıkış parametresi `out` değiştiriciyle birlikte bildirilmiştir. Aşağıdaki örnek, 7 ' de `out` C# tanıtılan sözdizimi kullanılarak parametrelerin kullanımını gösterir.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

Bir *parametre dizisi* , bir metoda değişken sayıda bağımsız değişken geçirilmesine izin verir. Bir parametre dizisi `params` değiştiriciyle birlikte bildirilmiştir. Bir yöntemin yalnızca son parametresi bir parametre dizisi olabilir ve bir parametre dizisinin türü tek boyutlu bir dizi türü olmalıdır. <xref:System.Console?displayProperty=nameWithType> Sınıfının Write ve WriteLine yöntemleri, parametre dizisi kullanımının iyi örnekleridir. Bunlar aşağıdaki gibi bildirilmiştir.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Bir parametre dizisi kullanan bir yöntem içinde, parametre dizisi tam olarak bir dizi türünün normal parametresine benzer şekilde davranır. Ancak, bir parametre dizisi olan bir yöntem çağrısında, parametre dizisi türünün tek bir bağımsız değişkenini veya parametre dizisinin öğe türünün herhangi bir sayıda bağımsız değişkenini geçirmek mümkündür. İkinci durumda, bir dizi örneği otomatik olarak oluşturulur ve verilen bağımsız değişkenlerle başlatılır. Bu örnek

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

, aşağıdaki yazma ile eşdeğerdir.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Yöntem gövdesi ve yerel değişkenler

Yöntemin gövdesi, yöntemi çağrıldığında yürütülecek deyimleri belirtir.

Yöntem gövdesi, yöntemi çağrısına özgü değişkenleri bildirebilir. Bu tür değişkenlere *yerel değişkenler*denir. Yerel bir değişken bildirimi bir tür adı, değişken adı ve muhtemelen bir başlangıç değeri belirtir. Aşağıdaki örnek, başlangıç değeri sıfır olan `i` yerel bir değişken ve ilk değeri olmayan bir yerel değişken `j` bildirir.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C#değeri alınabilmesi için önce bir yerel değişkenin *kesinlikle atanmasını* gerektirir. Örneğin, önceki `i` bildiriminde bir başlangıç değeri yoksa, derleyici programın sonraki `i` kullanımları için bir hata bildirir çünkü `i` bu, programda bu noktalarda kesinlikle atanmamalıdır.

Bir yöntem, çağrı `return` yapana denetim döndürmek için deyimlerini kullanabilir. `void` Döndürülen`return` bir yöntemde deyimler bir ifade belirtemez. Void olmayan bir yöntemde `return` deyim dönüş değerini hesaplayan bir ifade içermelidir.

### <a name="static-and-instance-methods"></a>Statik ve örnek yöntemleri

Statik değiştirici ile belirtilen bir yöntem *statik bir yöntemdir*. Statik bir yöntem belirli bir örnek üzerinde çalışmaz ve yalnızca statik üyelere doğrudan erişebilir.

Statik değiştirici olmadan belirtilen bir yöntem bir *örnek yöntemidir*. Örnek yöntemi, belirli bir örnek üzerinde çalışır ve hem statik hem de örnek üyelerine erişebilir. Örnek yönteminin çağrıldığı örnek, olarak `this`açıkça erişilebilir. Statik bir yöntemde başvurmak `this` için bir hatadır.

Aşağıdaki `Entity` sınıfta hem statik hem de örnek üyeleri vardır.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Her `Entity` örnek bir seri numarası içerir (ve burada görünmeyen bazı diğer bilgileri kabul etmez). `Entity` Oluşturucu (bir örnek yöntemi gibi) yeni örneği bir sonraki kullanılabilir seri numarasıyla başlatır. Oluşturucu bir örnek üyesi olduğundan, hem `serialNo` örnek alanına `nextSerialNo` hem de statik alana erişim izni verilir.

`GetNextSerialNo` Ve `serialNo` statik yöntemler statikalanaerişebilir,ancakörnekalanınadoğrudanerişmesiiçinbirhataolabilir.`nextSerialNo` `SetNextSerialNo`

Aşağıdaki örnek, Entity sınıfının kullanımını gösterir.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Sınıfının örneklerinde `GetSerialNo` örnek `SetNextSerialNo` yöntemi `GetNextSerialNo` çağrıldığında, ve statik yöntemlerin sınıfında çağrılabileceğini unutmayın.

### <a name="virtual-override-and-abstract-methods"></a>Sanal, geçersiz kılma ve soyut yöntemler

Bir örnek yöntemi bildirimi bir `virtual` değiştirici içerdiğinde, yöntemi bir *sanal yöntem*olarak kabul edilir. Bir sanal değiştirici yoksa, yöntem *sanal olmayan bir yöntem*olarak kabul edilir.

Bir sanal yöntem çağrıldığında, çağrının gerçekleştiği örneğin *çalışma zamanı türü* , çağrılacak gerçek Yöntem uygulamasını belirler. Sanal olmayan bir yöntem çağrısında, örneğin *derleme zamanı türü* belirleme faktörü olur.

Bir sanal yöntem, türetilmiş bir sınıfta *geçersiz kılınabilir* . Bir örnek yöntemi bildirimi bir geçersiz kılma değiştiricisi içerdiğinde, yöntemi aynı imzaya sahip devralınmış bir sanal yöntemi geçersiz kılar. Sanal bir yöntem bildiriminde yeni bir yöntem tanıtıldığı halde, bir geçersiz kılma yöntemi bildirimi, bu yöntemin yeni bir uygulamasını sağlayarak, var olan bir devralınmış sanal yöntemi uzmanlık eder.

*Soyut bir yöntem* , uygulama içermeyen bir sanal yöntemdir. Soyut bir yöntem soyut değiştiriciyle birlikte bildirilmiştir ve yalnızca soyut olarak da tanımlanmış bir sınıfta izin verilir. Soyut olmayan her türetilmiş sınıfta bir soyut yöntem geçersiz kılınmalıdır.

Aşağıdaki örnek, bir ifade ağaç düğümünü temsil `Expression`eden bir soyut sınıfı ve sabitler, değişken için ifade ağacı düğümleri uygulayan `Constant`üç `VariableReference`türetilmiş sınıfı `Operation`,, ve ve ' ı tanımlar. başvurular ve aritmetik işlemler. (Bu şuna benzerdir, ancak ifade ağacı türleriyle karıştırılmamalıdır).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Önceki dört sınıf aritmetik ifadeleri modellemek için kullanılabilir. Örneğin, bu sınıfların örneklerini kullanarak, ifadesi `x + 3` aşağıdaki gibi gösterilebilir.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

`double` Bir `Evaluate` Örneğinyöntemi,verilenifadeyideğerlendirmekvebirdeğerüretmekiçinçağrılır.`Expression` Yöntemi, değişken adlarını `Dictionary` (girdilerin anahtarları olarak) ve değerlerini (girişlerin değerleri olarak) içeren bir bağımsız değişken alır. Soyut `Evaluate` bir yöntem olduğundan, öğesinden `Expression` türetilen soyut olmayan sınıflar geçersiz kılınmalıdır `Evaluate`.

' Nin uygulanması, `Evaluate` yalnızca saklı sabiti döndürür. `Constant` A `VariableReference`uygulamasının, sözlükte değişken adını arar ve elde edilen değeri döndürür. Bir `Operation`uygulama ilk olarak sol ve sağ işlenenleri değerlendirir ( `Evaluate` yöntemlerini özyinelemeli olarak çağırarak) ve ardından verilen aritmetik işlemi gerçekleştirir.

Aşağıdaki program, `Expression` `x` ve `x * (y + 2)` farklı`y`değerleri için ifadeyi değerlendirmek için sınıflarını kullanır.

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Yöntem aşırı yüklemesi

Yöntem *aşırı yüklemesi* , aynı sınıftaki birden çok metodun benzersiz imzalara sahip oldukları sürece aynı ada sahip olmasını sağlar. Aşırı yüklenmiş bir yöntemin çağrılması derlenirken, derleyici çağrılacak özel yöntemi belirlemekte *aşırı yükleme çözümü* kullanır. Aşırı yükleme çözümlemesi, bağımsız değişkenlerle en iyi eşleşen bir yöntemi bulur veya tek bir en iyi eşleşme bulunamazsa hata bildiriyor. Aşağıdaki örnekte, etkin olan aşırı yükleme çözümü gösterilmektedir. `UsageExample` Yöntemi içindeki her çağrının yorumu aslında hangi yöntemin çağrılacağını gösterir.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Örnekte gösterildiği gibi belirli bir yöntem her zaman bağımsız değişkenleri tam parametre türlerine açıkça atayarak ve/veya açıkça tür bağımsız değişkenleri sunarak seçilebilir.

## <a name="other-function-members"></a>Diğer işlev üyeleri

Yürütülebilir kod içeren Üyeler topluca bir sınıfın *işlev üyeleri* olarak bilinir. Yukarıdaki bölümde, işlev üyelerinin birincil türü olan yöntemler açıklanmıştır. Bu bölümde, tarafından C#desteklenen diğer işlev üyesi türleri açıklanmaktadır: oluşturucular, özellikler, Dizin oluşturucular, olaylar, işleçler ve sonlandırıcılar.

Aşağıda, bir nesne growable listesini uygulayan `MyList<T>`adlı bir genel sınıf gösterilmektedir. Sınıfı, en yaygın işlev üyesi türlerine birkaç örnek içerir.

> [!NOTE]
> Bu örnek, .net `MyList` standardı <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>ile aynı olmayan bir sınıf oluşturur. Bu, bu tur için gereken kavramları gösterir, ancak bu sınıfın yerini almaz.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Oluşturucular

C#hem örnek hem de statik oluşturucuları destekler. *Örnek Oluşturucu* , bir sınıfın örneğini başlatmak için gereken eylemleri uygulayan bir üyedir. *Statik Oluşturucu* , ilk yüklendiği zaman bir sınıfın kendisini başlatmak için gereken eylemleri uygulayan bir üyesidir.

Bir Oluşturucu, dönüş türü olmayan bir yöntem ve kapsayan sınıfla aynı adı ile birlikte bildirilmiştir. Bir Oluşturucu bildirimi statik değiştirici içeriyorsa, statik bir Oluşturucu bildirir. Aksi takdirde, bir örnek Oluşturucu bildirir.

Örnek oluşturucular aşırı yüklenebilir ve isteğe bağlı parametrelere sahip olabilir. Örneğin, `MyList<T>` sınıfı tek bir isteğe bağlı `int` parametre ile bir örnek Oluşturucu bildirir. Örnek oluşturucular `new` işleci kullanılarak çağrılır. Aşağıdaki deyimler, ve isteğe `MyList<string>` bağlı bağımsız değişken olmadan `MyList` sınıfının oluşturucusunu kullanarak iki örnek ayırır.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Diğer üyelerin aksine, örnek oluşturucular devralınmaz ve bir sınıfın sınıfta tanımlananlardan farklı örnek oluşturucuları yoktur. Bir sınıf için örnek Oluşturucu sağlanmazsa, parametresi olmayan boş bir değer otomatik olarak sağlanır.

### <a name="properties"></a>Özellikler

*Özellikler* , alanlar için doğal bir uzantıdır. Her ikisi de ilişkili türlerin bulunduğu isimlerdir ve alanlara ve özelliklere erişim için sözdizimi aynıdır. Ancak, alanların aksine, Özellikler depolama konumlarını göstermiyor. Bunun yerine, özellikler, değerleri okunmak veya yazıldığında yürütülecek deyimleri belirten *erişimcileri* vardır.

Bir özellik, bildirim bir get erişimcisi ve/veya sınırlayıcılar `{` arasında yazılmış bir set erişimcisi ile sona erdiğinde ve `}` noktalı virgül ile sona ermek yerine bir alan gibi tanımlanır. Hem get erişimcisine hem de bir set erişimcisine sahip olan bir özellik *okuma-yazma özelliğidir*, yalnızca bir get erişimcisine sahip olan bir özellik *salt okunurdur*ve yalnızca bir set erişimcisi olan bir özellik yalnızca bir salt *yazılır özelliktir*.

Get erişimcisi, özellik türünün dönüş değeri olan parametresiz bir yönteme karşılık gelir. Atama hedefi haricinde, bir ifadede bir özelliğe başvurulduğunda, özelliğin değerini hesaplamak için özelliğin get erişimcisi çağrılır.

Bir set erişimcisi, value adlı tek parametreli ve dönüş türü olmayan bir yönteme karşılık gelir. Bir atamaya bir atama hedefi olarak veya + + veya--, işleneni olarak başvurulduğunda, yeni değer sağlayan bir bağımsız değişkenle çağrılır.

Sınıfı iki özellik bildirir `Capacity`ve sırasıyla salt okunurdur ve okuma-yazma olur. `Count` `MyList<T>` Aşağıda bu özelliklerin kullanılmasına bir örnek verilmiştir:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Alanlar ve yöntemlere benzer şekilde hem C# örnek özelliklerini hem de statik özellikleri destekler. Statik özellikler statik değiştirici ile tanımlanır ve örnek özellikleri bu olmadan tanımlanır.

Bir özelliğin erişimcisi sanal olabilir. Bir özellik bildirimi `virtual`, `abstract`, veya `override` değiştiricisini içerdiğinde, özelliğin erişimcilerle geçerli olur.

### <a name="indexers"></a>Dizin Oluşturucular

*Dizin Oluşturucu* , nesnelerin diziyle aynı şekilde dizinlenmesini sağlayan bir üyedir. Bir Dizin Oluşturucu, üyenin `this` adının ardından sınırlayıcılar `[` ve `]`arasında yazılmış bir parametre listesi gelmesi dışında bir özellik gibi bildirilmiştir. Parametreler, dizin oluşturucunun erişimcisinde kullanılabilir. Özelliklere benzer şekilde, Dizin oluşturucular okunabilir-yazılır, salt okunurdur ve salt yazılır olabilir ve bir dizin oluşturucunun erişimcisi sanal olabilir.

Sınıfı `MyList<T>` , bir `int` parametresi alan tek bir okuma-yazma Dizin Oluşturucu bildirir. Dizin Oluşturucu, `MyList<T>` `int` örneklerin değerleriyle dizin oluşturmanızı mümkün kılar. Örneğin:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Dizin oluşturucular aşırı yüklenebilir, yani parametrelerinin sayısı veya türleri farklı olduğu sürece bir sınıfın birden çok dizin kümesini bildirebileceği anlamına gelir.

### <a name="events"></a>Olaylar

Bir *olay* , bir sınıf veya nesnenin bildirimler sağlamasını sağlayan bir üyedir. Bir olay, bildirim bir event anahtar sözcüğü içermesi ve türün bir temsilci türü olması dışında, bir alan gibi bildirilmiştir.

Olay üyesini bildiren bir sınıf içinde, olay bir temsilci türünün alanı gibi davranır (olay soyut değildir ve erişimcileri bildirmez). Bu alan, olaya eklenmiş olan olay işleyicilerini temsil eden bir temsilciye bir başvuru depolar. Hiçbir olay işleyicisi yoksa, alanı olur `null`.

Sınıfı, adlı `Changed`tek bir olay üyesini bildirir ve bu, listeye yeni bir öğe eklendiğini gösterir. `MyList<T>` Değiştirilen olay `OnChanged` sanal yöntemi tarafından tetiklenir ve bu, önce `null` olayın (hiçbir işleyicinin mevcut olmadığı anlamına gelir) olup olmadığını denetler. Bir olayı oluşturma kavramı, olayın gösterdiği temsilciyi çağırmak için tam olarak eşdeğerdir. bu nedenle, olayları yükseltmek için özel dil yapıları yoktur.

İstemciler *olay işleyicileri*aracılığıyla olaylara tepki verir. Olay işleyicileri `+=` işleci kullanılarak eklenir ve `-=` işleci kullanılarak kaldırılır. Aşağıdaki örnek, olayına bir `Changed` `MyList<string>`olay işleyicisi ekler.

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Bir olayın temeldeki depolamanın denetiminin istendiği Gelişmiş senaryolarda, bir olay bildirimi açıkça bir özelliğin `add` `set` erişenine benzer bir şekilde sağlayabilir ve `remove` erişimciler sağlar.

### <a name="operators"></a>İşleçler

*İşleci* , bir sınıfın örneklerine belirli bir ifade işlecini uygulamanın anlamını tanımlayan bir üyesidir. Üç tür işleç tanımlanabilir: Birli İşleçler, ikili işleçler ve dönüştürme işleçleri. Tüm işleçler ve `public` `static`olarak bildirilmelidir.

Sınıfı iki `MyList` işleç `operator ==` bildirirvebunedenlebuişleçleriörneklereuygulayandeyimlereyenianlamıverir.`operator !=` `MyList<T>` Özellikle, işleçler, içerilen nesnelerin her birini `MyList<T>` , eşittir yöntemlerini kullanarak karşılaştıran iki örnek için eşitlik tanımlar. Aşağıdaki örnek, iki `==` `MyList<int>` örneği karşılaştırmak için işlecini kullanır.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

Bu iki `Console.WriteLine` liste `True` aynı sırada aynı değerleri taşıyan aynı sayıda nesne içerdiğinden ilk çıktılar. `MyList<T>` Tanımlı değil,`Console.WriteLine` ilkiçıktıyı`False` içeriyor ve`b` farklı örneklere`MyList<int>` başvuracaktır. `a` `operator ==`

### <a name="finalizers"></a>Sonlandırıcılar

*Sonlandırıcı* , bir sınıfın örneğini tamamlamak için gereken eylemleri uygulayan bir üyesidir. Sonlandırıcılar parametrelere sahip olamaz, erişilebilirlik değiştiricilerine sahip olamaz ve açıkça çağrılamaz. Örnek için Sonlandırıcı çöp toplama sırasında otomatik olarak çağrılır.

Çöp toplayıcısına, nesnelerin toplanması ve Sonlandırıcıların ne zaman toplanacağına karar verirken geniş bir enlem vardır. Özellikle, Sonlandırıcı etkinleştirmeleri zamanlaması belirleyici değildir ve herhangi bir iş parçacığında sonlandırıcılar çalıştırılabilir. Bu ve diğer nedenlerden dolayı sınıfların yalnızca başka hiçbir çözüm uygulanabilir olmadığında sonlandırıcılar uygulaması gerekir.

İfade `using` , nesne yok etme için daha iyi bir yaklaşım sağlar.

> [!div class="step-by-step"]
> [Önceki](statements.md)İleri
> [](structs.md)
