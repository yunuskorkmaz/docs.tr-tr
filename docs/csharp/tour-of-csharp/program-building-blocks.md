---
title: C# programlarının yapı taşları "
description: C# üyeleri, ifadeler ve deyimler hakkında bilgi edinin. Türler yazdığınız üyeleri içerir. Bu Üyeler deyimlerden ve ifadelerden oluşturulur.
ms.date: 08/06/2020
ms.openlocfilehash: 3bdc6a4da6ae76148c7d1d5cb8ccb65d91fda61a
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358823"
---
# <a name="program-building-blocks"></a>Program yapı taşları

Önceki makalede açıklanan türler, bu derleme blokları kullanılarak oluşturulmuştur: [***Üyeler***](../programming-guide/classes-and-structs/members.md), [ ***ifadeler***ve ***deyimler***](../programming-guide/statements-expressions-operators/index.md).

## <a name="members"></a>Üyeler

A üyeleri `class` ***statik Üyeler*** veya ***örnek üyeleridir***. Statik Üyeler sınıflara aittir ve örnek üyeleri nesnelere aittir (sınıf örnekleri).

Aşağıdaki liste, bir sınıfın içerebileceği üye türlerine genel bir bakış sağlar.

- **Sabitler**: sınıfla ilişkili sabit değerler
- **Alanlar**: sınıfıyla ilişkili değişkenler
- **Yöntemler**: sınıfı tarafından gerçekleştirilebilecek eylemler
- **Özellikler**: sınıfının adlandırılmış özelliklerini okuma ve yazma ile ilişkili eylemler
- **Dizin oluşturucular**: bir dizi gibi sınıfın dizin oluşturma örnekleri ile ilişkili eylemler
- **Olaylar**: sınıfı tarafından oluşturulabilecek bildirimler
- **İşleçler**: sınıf tarafından desteklenen dönüşümler ve ifade işleçleri
- **Oluşturucular**: sınıf veya sınıf örneklerinin başlatılması için gereken eylemler
- **Sonlandırıcılar**: sınıf örneklerinin kalıcı olarak atılmadan önce gerçekleştirilen eylemler
- **Türler**: sınıf tarafından belirtilen iç içe türler

## <a name="accessibility"></a>Erişilebilirlik

Bir sınıfın her üyesinin ilişkili bir erişilebilirliği vardır ve bu, üyeye erişebilen program metni bölgelerini denetler. Olası altı erişilebilirlik biçimi vardır. Erişim değiştiriciler aşağıda özetlenmiştir.

- `public`: Erişim sınırlı değil.
- `private`: Erişim bu sınıfla sınırlıdır.
- `protected`: Erişim bu sınıftan türetilmiş bu sınıf veya sınıflarla sınırlıdır.
- `internal`: Erişim geçerli derleme (veya) ile sınırlıdır `.exe` `.dll` .
- `protected internal`: Erişim bu sınıfla, bu sınıftan türetilmiş sınıflarla veya aynı derleme içindeki sınıflardan sınırlıdır.
- `private protected`: Erişim bu sınıf veya aynı derleme içindeki bu türden türetilmiş sınıflarla sınırlıdır.

## <a name="fields"></a>Alanlar

*Alan* , bir sınıf ile veya bir sınıf örneğiyle ilişkili bir değişkendir.

Statik değiştiriciyle belirtilen bir alan statik bir alan tanımlar. Statik alan tam olarak bir depolama konumunu tanımlar. Bir sınıfın kaç örneğinin oluşturulduğuna bakılmaksızın, bir statik alanın yalnızca bir kopyası vardır.

Statik değiştirici olmadan belirtilen bir alan bir örnek alanını tanımlar. Bir sınıfın her örneği, bu sınıfın tüm örnek alanlarının ayrı bir kopyasını içerir.

Aşağıdaki örnekte, sınıfının her örneği `Color` ,, ve örnek alanlarının ayrı bir kopyasına sahiptir `r` `g` `b` , ancak,,, `Black` `White` `Red` `Green` ve `Blue` statik alanlarının yalnızca bir kopyası vardır:

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ColorClassDefinition":::

Önceki örnekte gösterildiği gibi, *salt okuma alanları* bir değiştirici ile bildirilebilecek `readonly` . Salt okunurdur bir alana atama, yalnızca alanın bildiriminin bir parçası olarak veya aynı sınıftaki bir Oluşturucu halinde gerçekleşebilir.

## <a name="methods"></a>Yöntemler

Bir *Yöntem* , bir nesne veya sınıf tarafından gerçekleştirilebilecek bir hesaplama veya eylem uygulayan bir üyesidir. *Statik yöntemlere* sınıfı aracılığıyla erişilir. *Örnek yöntemlerine* , sınıfının örnekleri aracılığıyla erişilir.

Metotlarda, metoda geçirilen değerleri veya değişken başvurularını temsil eden bir *parametre*listesi bulunabilir. Yöntemler, hesaplanan ve yöntemi tarafından döndürülen değerin türünü belirten bir *dönüş türüne*sahiptir. Bir yöntemin dönüş türü `void` bir değer döndürmezse.

Türler gibi yöntemler de bir tür parametreleri kümesine sahip olabilir, bu da yöntem çağrıldığında tür bağımsız değişkenlerinin belirtilmesi gerekir. Türlerin aksine, tür bağımsız değişkenleri genellikle yöntem çağrısının bağımsız değişkenlerinden çıkarsanamıyor ve açıkça verilmemelidir.

Yöntemin *imzası* , yöntemin bildirildiği sınıfta benzersiz olmalıdır. Bir yöntemin imzası yöntemin adından, tür parametrelerinin sayısına ve parametrelerinin sayısına, değiştiricilerine ve türlerine sahiptir. Bir yöntemin imzası, dönüş türünü içermez.

Bir yöntem gövdesi tek bir ifadesiyse, aşağıdaki örnekte gösterildiği gibi, yöntem bir Compact ifadesi biçimi kullanılarak tanımlanabilir:

```csharp
public override ToString() => "This is an object";
```

### <a name="parameters"></a>Parametreler

Parametreler, değerlere veya değişken başvurularını yöntemlere geçirmek için kullanılır. Bir yöntemin parametreleri, yöntemi çağrıldığında belirtilen *bağımsız değişkenlerden* gerçek değerlerini alır. Dört tür parametre vardır: değer parametreleri, başvuru parametreleri, çıkış parametreleri ve parametre dizileri.

Giriş bağımsız değişkenlerini geçirmek için bir *değer parametresi* kullanılır. Değer parametresi, parametresi için geçirilen bağımsız değişkenden ilk değerini alan yerel bir değişkene karşılık gelir. Değer parametresindeki değişiklikler, parametresi için geçirilen bağımsız değişkeni etkilemez.

Değer parametreleri, ilgili bağımsız değişkenlerin atlanabilmesi için varsayılan bir değer belirtilerek isteğe bağlı olabilir.

*Başvuru parametresi* , bağımsız değişkenleri başvuruya göre geçirmek için kullanılır. Başvuru parametresi için geçirilen bağımsız değişken, kesin bir değere sahip bir değişken olmalıdır. Yöntemin yürütülmesi sırasında başvuru parametresi, bağımsız değişken değişkeniyle aynı depolama konumunu temsil eder. Bir başvuru parametresi değiştiriciyle birlikte bildirilmiştir `ref` . Aşağıdaki örnek parametrelerin kullanımını gösterir `ref` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RefExample":::

Bir *output parametresi* , bağımsız değişkenleri başvuruya göre geçirmek için kullanılır. Bir başvuru parametresine benzer, ancak çağıran tarafından belirtilen bağımsız değişkene açıkça bir değer atamanız gerekmez. Bir çıkış parametresi değiştiriciyle birlikte bildirilmiştir `out` . Aşağıdaki örnek, `out` C# 7 ' de tanıtılan sözdizimi kullanılarak parametrelerin kullanımını gösterir.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="OutExample":::

Bir *parametre dizisi* , bir metoda değişken sayıda bağımsız değişken geçirilmesine izin verir. Bir parametre dizisi değiştiriciyle birlikte bildirilmiştir `params` . Bir yöntemin yalnızca son parametresi bir parametre dizisi olabilir ve bir parametre dizisinin türü tek boyutlu bir dizi türü olmalıdır. `Write`Sınıfının ve `WriteLine` yöntemleri, <xref:System.Console?displayProperty=nameWithType> parametre dizisi kullanımının iyi örnekleridir. Bunlar aşağıdaki şekilde bildirilmiştir.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ConsoleExtract":::

Bir parametre dizisi kullanan bir yöntem içinde, parametre dizisi tam olarak bir dizi türünün normal parametresine benzer şekilde davranır. Ancak, bir parametre dizisi olan bir yöntem çağrısında, parametre dizisi türünün tek bir bağımsız değişkenini veya parametre dizisinin öğe türünün herhangi bir sayıda bağımsız değişkenini geçirmek mümkündür. İkinci durumda, bir dizi örneği otomatik olarak oluşturulur ve verilen bağımsız değişkenlerle başlatılır. Bu örnek

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseParamsArgs":::

, aşağıdaki yazma ile eşdeğerdir.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CompilerParams":::

### <a name="method-body-and-local-variables"></a>Yöntem gövdesi ve yerel değişkenler

Yöntemin gövdesi, yöntemi çağrıldığında yürütülecek deyimleri belirtir.

Yöntem gövdesi, yöntemi çağrısına özgü değişkenleri bildirebilir. Bu tür değişkenlere *yerel değişkenler*denir. Yerel bir değişken bildirimi bir tür adı, değişken adı ve muhtemelen bir başlangıç değeri belirtir. Aşağıdaki örnek, başlangıç değeri sıfır olan yerel bir değişken `i` ve ilk değeri olmayan bir yerel değişken bildirir `j` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="SquaresClass":::

C# değeri alınabilmesi için önce bir yerel değişkenin *kesinlikle atanmasını* gerektirir. Örneğin, önceki bildirimi `i` bir başlangıç değeri içermiyorsa, `i` `i` programda bu noktalarda kesin olarak atanmadığı için derleyici daha sonraki kullanımları için bir hata bildirir.

Bir yöntem `return` , çağrı yapana denetim döndürmek için deyimlerini kullanabilir. Döndürülen bir yöntemde `void` `return` deyimler bir ifade belirtemez. Void olmayan bir yöntemde `return` deyim dönüş değerini hesaplayan bir ifade içermelidir.

### <a name="static-and-instance-methods"></a>Statik ve örnek yöntemleri

Değiştirici ile belirtilen bir yöntem `static` *statik bir yöntemdir*. Statik bir yöntem, belirli bir örnek üzerinde çalışmaz ve yalnızca statik üyelere doğrudan erişebilir.

Değiştirici olmadan bildirildiği bir yöntem `static` bir *örnek yöntemidir*. Örnek yöntemi, belirli bir örnek üzerinde çalışır ve hem statik hem de örnek üyelerine erişebilir. Örnek yönteminin çağrıldığı örnek, olarak açıkça erişilebilir `this` . Statik bir yöntemde başvurmak için bir hatadır `this` .

Aşağıdaki `Entity` sınıfta hem statik hem de örnek üyeleri vardır.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="EntityClass":::

Her `Entity` örnek bir seri numarası içerir (ve burada görünmeyen bazı diğer bilgileri kabul edilir). `Entity`Oluşturucu (bir örnek yöntemi gibi) yeni örneği bir sonraki kullanılabilir seri numarasıyla başlatır. Oluşturucu bir örnek üyesi olduğundan, hem `_serialNo` örnek alanına hem de statik alana erişme izni vardır `s_nextSerialNo` .

`GetNextSerialNo`Ve `SetNextSerialNo` statik yöntemler `s_nextSerialNo` statik alana erişebilir, ancak örnek alanına doğrudan erişmesi için bir hata olabilir `_serialNo` .

Aşağıdaki örnek sınıfının kullanımını gösterir `Entity` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingEntity":::

`SetNextSerialNo`Ve `GetNextSerialNo` statik yöntemler sınıfında çağrılır, ancak `GetSerialNo` örnek yöntemi sınıfının örneklerinde çağrılır.

### <a name="virtual-override-and-abstract-methods"></a>Sanal, geçersiz kılma ve soyut yöntemler

Bir örnek yöntemi bildirimi bir değiştirici içerdiğinde `virtual` , yöntemi bir *sanal yöntem*olarak kabul edilir. Bir sanal değiştirici yoksa, yöntem *sanal olmayan bir yöntem*olarak kabul edilir.

Bir sanal yöntem çağrıldığında, çağrının gerçekleştiği örneğin *çalışma zamanı türü* , çağrılacak gerçek Yöntem uygulamasını belirler. Sanal olmayan bir yöntem çağrısında, örneğin *derleme zamanı türü* belirleme faktörü olur.

Bir sanal yöntem, türetilmiş bir sınıfta *geçersiz kılınabilir* . Bir örnek yöntemi bildirimi bir geçersiz kılma değiştiricisi içerdiğinde, yöntemi aynı imzaya sahip devralınmış bir sanal yöntemi geçersiz kılar. Bir sanal yöntem bildirimi yeni bir yöntem sunar. Bir geçersiz kılma yöntemi bildirimi, bu yöntemin yeni bir uygulamasını sağlayarak, var olan bir devralınmış sanal yöntemi uzmanlık eder.

*Soyut bir yöntem* , uygulama içermeyen bir sanal yöntemdir. Soyut bir yöntem `abstract` değiştiriciyle tanımlanmış ve yalnızca bir soyut sınıfta izin verilir. Soyut olmayan her türetilmiş sınıfta bir soyut yöntem geçersiz kılınmalıdır.

Aşağıdaki örnek, `Expression` bir ifade ağaç düğümünü temsil eden bir soyut sınıfı ve `Constant` `VariableReference` `Operation` sabitler, değişken başvuruları ve aritmetik işlemler için ifade ağacı düğümleri uygulayan üç türetilmiş sınıfı,, ve ' ı tanımlar. (Bu örnek, ifade ağacı türleriyle ilgili değildir ancak ile benzerdir).

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="WorkingWithExpressions":::

Önceki dört sınıf aritmetik ifadeleri modellemek için kullanılabilir. Örneğin, bu sınıfların örneklerini kullanarak, ifadesi `x + 3` aşağıdaki gibi gösterilebilir.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseExpressions":::

`Evaluate`Bir örneğin yöntemi, `Expression` verilen ifadeyi değerlendirmek ve bir değer üretmek için çağrılır `double` . Yöntemi, `Dictionary` değişken adlarını (girdilerin anahtarları olarak) ve değerlerini (girişlerin değerleri olarak) içeren bir bağımsız değişken alır. `Evaluate`Soyut bir yöntem olduğundan, öğesinden türetilen soyut olmayan sınıflar `Expression` geçersiz kılınmalıdır `Evaluate` .

' `Constant` Nin uygulanması, `Evaluate` yalnızca saklı sabiti döndürür. A `VariableReference` uygulamasının, sözlükte değişken adını arar ve elde edilen değeri döndürür. Bir `Operation` uygulama ilk olarak sol ve sağ işlenenleri değerlendirir (yöntemlerini özyinelemeli olarak çağırarak `Evaluate` ) ve ardından verilen aritmetik işlemi gerçekleştirir.

Aşağıdaki program, `Expression` `x * (y + 2)` ve farklı değerleri için ifadeyi değerlendirmek için sınıflarını kullanır `x` `y` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingExpressions":::

### <a name="method-overloading"></a>Yöntem aşırı yüklemesi

Yöntem *aşırı yüklemesi* , aynı sınıftaki birden çok metodun benzersiz imzalara sahip oldukları sürece aynı ada sahip olmasını sağlar. Aşırı yüklenmiş bir yöntemin çağrılması derlenirken, derleyici çağrılacak özel yöntemi belirlemekte *aşırı yükleme çözümü* kullanır. Aşırı yükleme çözümlemesi, bağımsız değişkenlerle en iyi eşleşen bir yöntemi bulur. Tek bir en iyi eşleşme bulunamazsa bir hata bildirilir. Aşağıdaki örnekte, etkin olan aşırı yükleme çözümü gösterilmektedir. Yöntemi içindeki her çağrının yorumu `UsageExample` hangi yöntemin çağrılacağını gösterir.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="Overloading":::

Örnekte gösterildiği gibi belirli bir yöntem her zaman bağımsız değişkenleri tam parametre türlerine ve tür bağımsız değişkenlerine açıkça atayarak seçilebilir.

## <a name="other-function-members"></a>Diğer işlev üyeleri

Yürütülebilir kod içeren Üyeler topluca bir sınıfın *işlev üyeleri* olarak bilinir. Yukarıdaki bölümde, işlev üyelerinin birincil türleri olan yöntemler açıklanmıştır. Bu bölümde C# tarafından desteklenen diğer işlev üyesi türleri açıklanmaktadır: oluşturucular, özellikler, Dizin oluşturucular, olaylar, işleçler ve sonlandırıcılar.

Aşağıdaki örnek `MyList<T>` , bir nesne growable listesini uygulayan adlı bir genel sınıfı gösterir. Sınıfı, en yaygın işlev üyesi türlerine birkaç örnek içerir.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListExample":::

### <a name="constructors"></a>Oluşturucular

C# hem örnek hem de statik oluşturucuları destekler. *Örnek Oluşturucu* , bir sınıfın örneğini başlatmak için gereken eylemleri uygulayan bir üyedir. *Statik Oluşturucu* , ilk yüklendiği zaman bir sınıfın kendisini başlatmak için gereken eylemleri uygulayan bir üyesidir.

Bir Oluşturucu, dönüş türü olmayan bir yöntem ve kapsayan sınıfla aynı adı ile birlikte bildirilmiştir. Bir Oluşturucu bildiriminde bir değiştirici varsa `static` , bir statik oluşturucu bildirir. Aksi takdirde, bir örnek Oluşturucu bildirir.

Örnek oluşturucular aşırı yüklenebilir ve isteğe bağlı parametrelere sahip olabilir. Örneğin, `MyList<T>` sınıfı tek bir isteğe bağlı parametre ile bir örnek Oluşturucu bildirir `int` . Örnek oluşturucular işleci kullanılarak çağrılır `new` . Aşağıdaki deyimler, `MyList<string>` `MyList` ve isteğe bağlı bağımsız değişken olmadan sınıfının oluşturucusunu kullanarak iki örnek ayırır.

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CreateLists":::

Diğer üyelerin aksine, örnek oluşturucular devralınmaz. Bir sınıf, sınıfta gerçekten tanımlanmış olan oluşturuculardan başka örnek oluşturuculara sahip değildir. Bir sınıf için örnek Oluşturucu sağlanmazsa, parametresi olmayan boş bir değer otomatik olarak sağlanır.

### <a name="properties"></a>Özellikler

*Özellikler* , alanlar için doğal bir uzantıdır. Her ikisi de ilişkili türlerin bulunduğu isimlerdir ve alanlara ve özelliklere erişim için sözdizimi aynıdır. Ancak, alanların aksine, Özellikler depolama konumlarını göstermiyor. Bunun yerine, özellikler, değerleri okunmak veya yazıldığında yürütülen deyimleri belirten *erişimcileri* vardır.

Bir özellik, bildirim bir get erişimcisi ile sona erene veya sınırlayıcılar arasında yazılmış bir set erişimcisi ya da bir `{` noktalı virgülle bitmesi dışında, bir alan gibi tanımlanır `}` . Hem get erişimcisine hem de bir set erişimcisine sahip olan bir özellik *okuma-yazma özelliğidir*, yalnızca bir get erişimcisine sahip olan bir özellik *salt okunurdur*ve yalnızca bir set erişimcisi olan bir özellik yalnızca bir salt *yazılır özelliktir*.

Get erişimcisi, özellik türünün dönüş değeri olan parametresiz bir yönteme karşılık gelir. Bir set erişimcisi, value adlı tek parametreli ve dönüş türü olmayan bir yönteme karşılık gelir. Get erişimcisi özelliğin değerini hesaplar. Set erişimcisi, özelliği için yeni bir değer sağlar. Özellik bir atamanın hedefi ya da veya işleneni, `++` `--` set erişimcisi çağrılır. Özelliğin başvurduğu diğer durumlarda, get erişimcisi çağrılır.

`MyList<T>`Sınıfı iki özellik bildirir `Count` ve `Capacity` sırasıyla salt okunurdur ve okuma-yazma olur. Aşağıdaki kod, bu özelliklerin kullanım örneğidir:

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="AccessProperties":::

Alanlar ve yöntemlere benzer şekilde C# hem örnek özelliklerini hem de statik özellikleri destekler. Statik özellikler statik değiştirici ile tanımlanır ve örnek özellikleri bu olmadan tanımlanır.

Bir özelliğin erişimcisi sanal olabilir. Bir özellik bildirimi `virtual` ,, `abstract` veya değiştiricisini içerdiğinde, `override` özelliğin erişimcilerle geçerli olur.

### <a name="indexers"></a>Dizin Oluşturucular

*Dizin Oluşturucu* , nesnelerin diziyle aynı şekilde dizinlenmesini sağlayan bir üyedir. Bir Dizin Oluşturucu, üyenin adının `this` ardından sınırlayıcılar ve arasında yazılmış bir parametre listesi gelmesi dışında bir özellik gibi bildirilmiştir `[` `]` . Parametreler, dizin oluşturucunun erişimcisinde kullanılabilir. Özelliklere benzer şekilde, Dizin oluşturucular okunabilir-yazılır, salt okunurdur ve salt yazılır olabilir ve bir dizin oluşturucunun erişimcisi sanal olabilir.

`MyList<T>`Sınıfı, bir parametresi alan tek bir okuma-yazma Dizin Oluşturucu bildirir `int` . Dizin Oluşturucu, örneklerin değerleriyle dizin oluşturmanızı mümkün kılar `MyList<T>` `int` . Örneğin:

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAccess":::

Dizin oluşturucular aşırı yüklenebilir. Bir sınıf, parametrelerinin sayısı veya türleri farklı olduğu sürece birden çok Dizin Oluşturucu bildirebilir.

### <a name="events"></a>Ekinlikler

Bir *olay* , bir sınıf veya nesnenin bildirimler sağlamasını sağlayan bir üyedir. Bildirimin bir `event` anahtar sözcük içermesi ve türün bir temsilci türü olması dışında bir olay, bir alan gibi bildirilmiştir.

Olay üyesini bildiren bir sınıf içinde, olay bir temsilci türünün alanı gibi davranır (olay soyut değildir ve erişimcileri bildirmez). Bu alan, olaya eklenmiş olan olay işleyicilerini temsil eden bir temsilciye bir başvuru depolar. Hiçbir olay işleyicisi yoksa, alanı olur `null` .

`MyList<T>`Sınıfı, adlı tek bir olay üyesini bildirir `Changed` ve bu, listeye yeni bir öğe eklendiğini gösterir. Değiştirilen olay `OnChanged` sanal yöntemi tarafından tetiklenir ve bu, önce olayın `null` (hiçbir işleyicinin mevcut olmadığı anlamına gelir) olup olmadığını denetler. Bir olayı oluşturma kavramı, olay tarafından temsil edilen temsilciyi çağırmaya tam olarak eşdeğerdir. Olayları yükseltmek için özel dil yapıları yoktur.

İstemciler *olay işleyicileri*aracılığıyla olaylara tepki verir. Olay işleyicileri işleci kullanılarak eklenir `+=` ve işleci kullanılarak kaldırılır `-=` . Aşağıdaki örnek, olayına bir olay işleyicisi ekler `Changed` `MyList<string>` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RespondToEvents":::

Bir olayın temeldeki depolamanın denetiminin istendiği Gelişmiş senaryolarda, bir olay bildirimi açıkça sağlayabilir `add` ve `remove` Bu da `set` bir özelliğin erişimcisine benzer.

### <a name="operators"></a>İşleçler

*İşleci* , bir sınıfın örneklerine belirli bir ifade işlecini uygulamanın anlamını tanımlayan bir üyesidir. Üç tür işleç tanımlanabilir: Birli İşleçler, ikili işleçler ve dönüştürme işleçleri. Tüm işleçler ve olarak bildirilmelidir `public` `static` .

`MyList<T>`Sınıfı iki işleç bildirir `operator ==` ve `operator !=` . Bu geçersiz kılınan operatörler, bu işleçleri örneklere uygulayan deyimlere yeni anlam verir `MyList` . Özellikle, işleçler, `MyList<T>` içerilen nesnelerin her birini yöntemlerini kullanarak karşılaştıran iki örneğin eşitliğini tanımlar `Equals` . Aşağıdaki örnek, `==` iki örneği karşılaştırmak için işlecini kullanır `MyList<int>` .

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAddition":::

Bu `Console.WriteLine` `True` iki liste aynı sırada aynı değerleri taşıyan aynı sayıda nesne içerdiğinden ilk çıktılar. `MyList<T>`Tanımlı değil `operator ==` , ilki `Console.WriteLine` çıktıyı içeriyor `False` `a` ve `b` farklı örneklere başvuracaktır `MyList<int>` .

### <a name="finalizers"></a>Sonlandırıcılar

*Sonlandırıcı* , bir sınıfın örneğini tamamlamak için gereken eylemleri uygulayan bir üyesidir. Genellikle, yönetilmeyen kaynakları serbest bırakmak için sonlandırıcının olması gerekir. Sonlandırıcılar parametrelere sahip olamaz, erişilebilirlik değiştiricilerine sahip olamaz ve açıkça çağrılamaz. Örnek için Sonlandırıcı çöp toplama sırasında otomatik olarak çağrılır. Daha fazla ayrıntı için [sonlandırıcılar](../programming-guide/classes-and-structs/destructors.md)hakkındaki makaleye bakın.

Çöp toplayıcısına, nesnelerin toplanması ve Sonlandırıcıların ne zaman toplanacağına karar verirken geniş bir enlem vardır. Özellikle, Sonlandırıcı çağırma zamanlaması belirleyici değildir ve herhangi bir iş parçacığında sonlandırıcılar çalıştırılabilir. Bu ve diğer nedenlerden dolayı sınıfların yalnızca başka hiçbir çözüm uygulanabilir olmadığında sonlandırıcılar uygulaması gerekir.

`using`İfade, nesne yok etme için daha iyi bir yaklaşım sağlar.

## <a name="expressions"></a>İfadeler

*İfadeler* , *işlenenler* ve *işleçlerden*oluşturulur. Bir ifadenin işleçleri, işlenenlerin hangi işlemleri uygulanacağını gösterir. İşleç örnekleri,, `+` , `-` `*` ve içerir `/` `new` . İşlenenlerin örnekleri, sabit değerleri, alanları, yerel değişkenleri ve ifadeleri içerir.

Bir ifade birden çok işleç içerdiğinde işleçlerin *önceliği*, her bir işlecin değerlendirilme sırasını denetler. Örneğin, `x + y * z` `x + (y * z)` `*` işleç işleçten daha yüksek önceliğe sahip olduğu için ifade değerlendirilir `+` .

Aynı önceliğe sahip iki işleç arasında bir işlenen gerçekleştiğinde, işleçlerin *ilişkilendirilebilirliği* , işlemlerin gerçekleştirileceği sırayı denetler:

* Atama ve null birleşim işleçleri hariç olmak üzere tüm ikili işleçler *sola ilişkilendirilebilir*, yani işlemler soldan sağa yapılır. Örneğin, `x + y + z` olarak değerlendirilir `(x + y) + z` .
* Atama işleçleri, null birleşim `??` ve `??=` İşleçler ve koşullu operatör `?:` *doğru ilişkilendirilebilir*, yani işlemler sağdan sola yapılır. Örneğin, `x = y = z` olarak değerlendirilir `x = (y = z)` .

Öncelik ve ilişkilendirilebilirlik, parantezler kullanılarak denetlenebilir. Örneğin, ilk olarak ile `x + y * z` çarpar `y` `z` ve sonra sonucunu ekler `x` , ancak ilk olarak `(x + y) * z` sonucu ekler `x` ve `y` sonra sonucunu ile çarpar `z` .

Çoğu işleç [*aşırı*](../language-reference/operators/operator-overloading.md)yüklenebilir. İşleç aşırı yüklemesi, Kullanıcı tanımlı operatör uygulamalarının bir veya her ikisinin de Kullanıcı tanımlı sınıf veya yapı türünde olduğu işlemler için belirtilmesine izin verir.

C# [Aritmetik](../language-reference/operators/arithmetic-operators.md), [mantıksal](../language-reference/operators/boolean-logical-operators.md), [bit düzeyinde ve vardiya](../language-reference/operators/bitwise-and-shift-operators.md) işlemleri, [eşitlik](../language-reference/operators/equality-operators.md) ve [sıra](../language-reference/operators/comparison-operators.md) karşılaştırmaları gerçekleştirmeye yönelik bir dizi işleç sağlar.

Öncelik düzeyine göre sıralanan C# işleçlerinin tüm listesi için bkz. [c# işleçleri](../language-reference/operators/index.md).

## <a name="statements"></a>Deyimler

Bir programın eylemleri *deyimler*kullanılarak ifade edilir. C#, gömülü deyimler açısından tanımlanmış bir dizi farklı sayıda ifadeyi destekler.

- Bir *blok* , tek bir ifadeye izin verilen bağlamlarda birden çok deyimin yazılmasına izin verir. Bir blok, sınırlayıcılar ve arasında yazılmış deyimler listesinden oluşur `{` `}` .
- *Bildirim deyimleri* yerel değişkenleri ve sabitleri bildirmek için kullanılır.
- *İfade deyimleri* , ifadeleri değerlendirmek için kullanılır. Deyim olarak kullanılabilecek ifadeler, yöntem etkinleştirmeleri, işleci kullanılarak nesne ayırmaları `new` , ve `=` bileşik atama işleçleri kullanan atamalar, artırma ve azaltma işlemlerini ve `++` `--` işleçlerini ve `await` ifadelerini içerir.
- *Seçim deyimleri* , bazı deyimlerin değerine göre yürütme için bir dizi olası deyimden birini seçmek için kullanılır. Bu grup `if` ve deyimlerini içerir `switch` .
- *Yineleme deyimleri* , art arda gömülü bir deyimi yürütmek için kullanılır. Bu grup,, `while` , `do` `for` ve deyimlerini içerir `foreach` .
- *Sıçrama deyimleri* , denetimi aktarmak için kullanılır. Bu grup,,,, `break` `continue` `goto` `throw` `return` ve deyimlerini içerir `yield` .
- `try`... `catch` Bildirisi, bir bloğun yürütülmesi sırasında oluşan özel durumları yakalamak için kullanılır ve `try` ... `finally` deyimleri her zaman yürütülen ve özel bir durumun gerçekleşmediği sonlandırma kodunu belirtmek için kullanılır.
- `checked`Ve `unchecked` deyimleri, tam sayı türü aritmetik işlemler ve dönüştürmeler için taşma denetimi bağlamını denetlemek üzere kullanılır.
- Bu `lock` ifade, belirli bir nesne için karşılıklı dışlama kilidini almak, bir ifadeyi yürütmek ve sonra kilidi serbest bırakmak için kullanılır.
- `using`İfade, kaynak almak, bir ifadeyi yürütmek ve ardından bu kaynağı atmak için kullanılır.

Aşağıdakiler, kullanılabilecek deyimlerin türlerini listeler:

* Yerel değişken bildirimi.
* Yerel sabit bildirimi.
* İfade deyimi.
* `if` Ekstre.
* `switch` Ekstre.
* `while` Ekstre.
* `do` Ekstre.
* `for` Ekstre.
* `foreach` Ekstre.
* `break` Ekstre.
* `continue` Ekstre.
* `goto` Ekstre.
* `return` Ekstre.
* `yield` Ekstre.
* `throw` deyimler ve `try` deyimler.
* `checked` ve `unchecked` deyimleri.
* `lock` Ekstre.
* `using` Ekstre.

>[!div class="step-by-step"]
>[Önceki](types.md) 
> [Sonraki](features.md)
