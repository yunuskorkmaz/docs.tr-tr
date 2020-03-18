---
title: C# sınıflar ve Nesneler - C# Dil turu
description: C#'da yeni misiniz? Sınıflara, nesnelere ve kalıtıma genel bakışı okuyun
ms.date: 02/27/2020
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: c178e11b5667905f75538555c8a309e2fdb4a9ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159188"
---
# <a name="classes-and-objects"></a>Sınıflar ve nesneler

*Sınıflar* C# türlerinin en temelidir. Sınıf, durum (alanlar) ve eylemleri (yöntem ve diğer işlev öğeleri) tek bir birimde birleştiren bir veri yapısıdır. Bir sınıf, *nesneler*olarak da bilinen sınıfın dinamik olarak oluşturulmuş *örnekleri* için bir tanım sağlar. Sınıflar *kalıtım* ve *çok biçimlilik*desteği, *türemiş sınıflar* genişletmek ve *temel sınıfları*uzmanlaşmak mekanizmaları.

Sınıf bildirimleri kullanılarak yeni sınıflar oluşturulur. Sınıf bildirimi, sınıfın özniteliklerini ve değiştiricilersini, sınıfın adını, taban sınıfı (verilirse) ve sınıf tarafından uygulanan arabirimleri belirten bir üstbilgiyle başlar. Üstbilgi, sınır layıcılar `{` ve `}`.

Aşağıdaki kod, aşağıdaki adlı `Point`basit bir sınıfın bildirimini gösterir:

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

Sınıf örnekleri, yeni bir `new` örnek için bellek ayıran, örneği başlatması için bir oluşturucu çağırır ve örneğe bir başvuru döndürür işleç kullanılarak oluşturulur. Aşağıdaki ifadeler iki Nokta nesnesi oluşturur ve bu nesnelere iki değişkende başvuru depolar:

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

Nesneye artık erişilemediğinde nesne tarafından işgal edilen bellek otomatik olarak geri alınır. C#'daki nesneleri açıkça ele almak ne gerekli ne de mümkün.

## <a name="members"></a>Üyeler

Bir sınıfın üyeleri statik üyeler veya örnek üyelerdir. Statik üyeler sınıflara, örnek üyeler ise nesnelere (sınıf örnekleri) aittir.

Aşağıdaki liste, bir sınıfın içerebileceği üye türlerine genel bir bakış sağlar.

- Sabitler
  - Sınıfla ilişkili sabit değerler
- Alanlar
  - Sınıfın değişkenleri
- Yöntemler
  - Sınıf tarafından gerçekleştirilebilecek hesaplamalar ve eylemler
- Özellikler
  - Sınıfın adlandırılmış özelliklerini okuma ve yazma ile ilgili eylemler
- Dizin Oluşturucular
  - Bir dizi gibi sınıfın dizileme örnekleriile ilişkili eylemler
- Olaylar
  - Sınıf tarafından oluşturulabilen bildirimler
- İşleçler
  - Sınıf tarafından desteklenen dönüşümler ve ifade işleçleri
- Oluşturucular
  - Sınıfın veya sınıfın kendi örneklerini başlatmaiçin gereken eylemler
- Sonlandırıcılar
  - Sınıfın örnekleri kalıcı olarak atılmadan önce gerçekleştirecek eylemler
- Türler
  - Sınıf tarafından bildirilen iç içe geçen türler

## <a name="accessibility"></a>Erişilebilirlik

Bir sınıfın her üyesi, üyeye erişebilen program metninin bölgelerini denetleyen ilişkili bir erişilebilirlik vardır. Erişilebilirliğin altı olası biçimi vardır. Erişim değiştiriciler aşağıda özetlenmiştir.

- `public`
  - Erişim sınırlı değildir.
- `protected`
  - Erişim bu sınıf veya bu sınıftan türetilen sınıfları ile sınırlıdır.
- `internal`
  - Erişim geçerli derlemeyle sınırlıdır (.exe, .dll, vb.).
- `protected internal`
  - Erişim, içeren sınıfla, içeren sınıftan türetilen sınıfla veya aynı derlemedeki sınıfla sınırlıdır.
- `private`
  - Erişim bu sınıfla sınırlıdır.
- `private protected`
  - Erişim, aynı derleme içinde içeren türden türetilen içeren sınıf veya sınıfla sınırlıdır.

## <a name="type-parameters"></a>Tip parametreleri

Sınıf tanımı, sınıf adını açı ayraçlarıyla izleyerek bir tür parametresi kümesi belirtebilir. Tür parametreleri daha sonra sınıf bildirimleri gövdesinde sınıf üyelerini tanımlamak için kullanılabilir. Aşağıdaki örnekte, tip `Pair` parametreleri `TFirst` `TSecond`ve:

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

Tür parametreleri almak için bildirilen bir *sınıf türüne genel sınıf türü*denir. Yapı, arabirim ve temsilci türleri de genel olabilir.
Genel sınıf kullanıldığında, tür parametrelerinin her biri için tür bağımsız değişkenleri sağlanmalıdır:

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

Yukarıdaki gibi `Pair<int,string>` sağlanan tür bağımsız değişkenleri ile genel bir *tür, yapılı türü*olarak adlandırılır.

## <a name="base-classes"></a>Temel sınıflar

Bir sınıf bildirimi, bir üst üste ve taban sınıfın adı ile sınıf adı ve türü parametrelerini izleyerek bir taban sınıf belirtebilir. Taban sınıf belirtimiattüründen türeyen ile `object`aynıdır. Aşağıdaki örnekte, taban sınıf `Point3D` `Point`ve taban `Point` sınıf: `object`

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

Bir sınıf, taban sınıfının üyelerini devralır. Devralma, bir sınıfın örnek ve statik oluşturucular ve taban sınıfın sonlandırıcıları dışında taban sınıfının tüm üyelerini dolaylı olarak içerdiği anlamına gelir. Türetilen bir sınıf devraldığı üyelere yeni üyeler ekleyebilir, ancak devralınan üye tanımını kaldıramaz. Önceki örnekte, `Point3D` ve `x` `y` `Point`alanları devralır ve `Point3D` her örneküç `x` `y`alan `z`içerir, , ve .

Örtük dönüştürme, bir sınıf türünden taban sınıf türlerinden herhangi biri için vardır. Sınıf türünden bir değişken, o sınıfın bir örneğine veya türetilmiş herhangi bir sınıfın örneğine başvuruyapabilir. Örneğin, önceki sınıf bildirimleri göz önüne `Point` alındığında, tür `Point` bir `Point3D`değişken a veya a başvuruolabilir:

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>Alanlar

*Alan,* bir sınıfla veya bir sınıf örneğiyle ilişkili bir değişkendir.

Statik değiştirici ile bildirilen bir alan statik bir alan tanımlar. Statik alan tam olarak bir depolama konumunu tanımlar. Bir sınıfın kaç örneği oluşturulursa oluşturulsun, statik alanın yalnızca bir kopyası vardır.

Statik değiştirici olmadan bildirilen bir alan bir örnek alan tanımlar. Bir sınıfın her örneği, o sınıfın tüm örnek alanlarının ayrı bir kopyasını içerir.

Aşağıdaki `Color` örnekte, sınıfın her örneğinde , ve `r` `g` `b` örnek alanlarının ayrı bir kopyası vardır, `Black`ancak `White` `Red`, `Green`, `Blue` , ve statik alanların yalnızca bir kopyası vardır:

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

Önceki örnekte gösterildiği gibi, *salt okunur alanlar* `readonly` bir değiştirici ile bildirilebilir. Bir `readonly` alana atama, yalnızca alanın bildiriminin bir parçası olarak veya aynı sınıftaki bir oluşturucuda oluşabilir.

## <a name="methods"></a>Yöntemler

*Yöntem,* bir nesne veya sınıf tarafından gerçekleştirilebilecek bir hesaplama veya eylem uygulayan bir üyedir. *Statik yöntemlere* sınıf aracılığıyla erişilir. *Örnek yöntemlerine* sınıfın örnekleri aracılığıyla erişilir.

Yöntemler, yönteme aktarılan değerleri veya değişken başvuruları temsil eden *parametrelerin*bir listesine ve yöntem tarafından hesaplanan ve döndürülen değerin türünü belirten bir *dönüş türüne*sahip olabilir. Yöntemin dönüş türü, `void` bir değer döndürmemesidir.

Türleri gibi, yöntemler de yöntem çağrıldığında tür bağımsız değişkenleri belirtilmesi gereken tür parametreleri kümesi olabilir. Türlerin aksine, tür bağımsız değişkenleri genellikle bir yöntem çağrısının bağımsız değişkenlerinden çıkarılabilir ve açıkça verilmemesi gerekmez.

Yöntemin *imzası,* yöntemin beyan edildiği sınıfta benzersiz olmalıdır. Bir yöntemin imzası yöntemin adı, tür parametreleri ve sayısı, değiştiriciler ve parametrelerin türleri oluşur. Bir yöntemin imzası iade türünü içermez.

### <a name="parameters"></a>Parametreler

Parametreler, değerleri veya değişken başvuruları yöntemlere aktarmak için kullanılır. Yöntemin parametreleri, yöntem çağrıldığı zaman belirtilen *bağımsız değişkenlerden* gerçek değerlerini alır. Dört tür parametre vardır: değer parametreleri, referans parametreleri, çıkış parametreleri ve parametre dizileri.

Giriş bağımsız değişkenlerini geçirmek için bir *değer parametresi* kullanılır. Değer parametresi, parametre için geçirilen bağımsız değişkenden ilk değerini alan yerel bir değişkene karşılık gelir. Değer parametresindeki değişiklikler, parametre için geçirilen bağımsız değişkeni etkilemez.

Değer parametreleri, ilgili bağımsız değişkenlerin atlanabilmesi için varsayılan değer belirterek isteğe bağlı olabilir.

Bir *başvuru parametresi* başvuru ile bağımsız değişkenleri geçirmek için kullanılır. Bir başvuru parametresi için geçirilen bağımsız değişken, belirli bir değere sahip bir değişken olmalıdır ve yöntemin yürütülmesi sırasında, başvuru parametresi bağımsız değişkenle aynı depolama konumunu temsil eder. Bir başvuru parametresi `ref` değiştirici ile bildirilir. Aşağıdaki örnek, parametrelerin `ref` kullanımını gösterir.

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

Bağımsız değişkenleri başvuruyla geçirmek için bir *çıktı parametresi* kullanılır. Arayan tarafından sağlanan bağımsız değişkene açıkça bir değer atamanızı gerektirmemesi dışında, başvuru parametresine benzer. `out` Bir çıkış parametresi değiştirici ile bildirilir. Aşağıdaki örnek, C# `out` 7'de tanıtılan sözdizimi kullanarak parametrelerin kullanımını göstermektedir.

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

*Parametre dizisi,* değişken sayıda bağımsız değişkenin bir yönteme geçirilmesine izin verir. `params` Bir parametre dizisi değiştirici ile bildirilir. Bir yöntemin yalnızca son parametresi bir parametre dizisi olabilir ve parametre dizisinin türü tek boyutlu bir dizi türü olmalıdır. <xref:System.Console?displayProperty=nameWithType> Sınıfın Yazma ve Yazma Çizgisi yöntemleri parametre dizi kullanımının iyi örnekleridir. Aşağıdaki gibi beyan edilmiştir.

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

Parametre dizisini kullanan bir yöntem de, parametre dizisi tam olarak bir dizi türünün normal parametresi gibi görünür. Ancak, parametre dizilime sahip bir yöntemin çağrılması, parametre dizitüründen tek bir bağımsız değişkeni veya parametre dizisinin öğe türünün herhangi bir değişkenini geçmek mümkündür. İkinci durumda, bir dizi örneği otomatik olarak oluşturulur ve verilen bağımsız değişkenler ile başharfe. Bu örnek

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

aşağıdakileri yazmaya eşdeğerdir.

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>Yöntem gövdesi ve yerel değişkenler

Yöntemin gövdesi, yöntem çağrıldığı zaman yürütülecek ifadeleri belirtir.

Bir yöntem gövdesi, yöntemin çağrılması için özel değişkenler bildirebilir. Bu tür değişkenlere *yerel değişkenler*denir. Yerel bir değişken bildirimi bir tür adı, bir değişken adı ve büyük olasılıkla bir başlangıç değeri belirtir. Aşağıdaki örnekte, başlangıç `i` değeri sıfır olan yerel bir `j` değişken ve başlangıç değeri olmayan yerel bir değişken beyan edin.

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# değeri elde edilmeden önce *kesinlikle atanması* için yerel bir değişken gerektirir. Örneğin, önceki `i` bildirimi bir başlangıç değeri içermediyse, derleyici, programdaki bu noktalarda `i` kesinlikle `i` atanmayacağı için sonraki kullanımlar için bir hata bildirir.

Yöntem, denetimi `return` arayana döndürmek için deyimleri kullanabilir. Dönen bir `void`yöntemde, `return` ifadeler bir ifade belirtemez. Geçersiz olmayan dönen bir yöntemde, `return` ifadeler iade değerini hesaplayan bir ifade içermelidir.

### <a name="static-and-instance-methods"></a>Statik ve örnek yöntemleri

Statik değiştirici ile bildirilen bir *yöntem statik*bir yöntemdir. Statik bir yöntem belirli bir örnekte çalışmaz ve yalnızca doğrudan statik üyelere erişebilir.

Statik değiştirici olmadan bildirilen bir *yöntem bir örnek yöntemidir.* Örnek yöntemi belirli bir örneküzerinde çalışır ve hem statik hem de örnek üyelere erişebilir. Bir örnek yönteminin çağrıldığı örnek açıkça '' `this`olarak erişilebilir. Statik bir `this` yöntemde başvurmak bir hatadır.

Aşağıdaki `Entity` sınıfın hem statik hem de örnek üyeleri vardır.

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

Her `Entity` örnek bir seri numarası (ve muhtemelen burada gösterilmeyen bazı diğer bilgiler) içerir. Oluşturucu `Entity` (bir örnek yöntemi gibi) bir sonraki kullanılabilir seri numarası ile yeni örneği başharfe olarak laştırır. Oluşturucu bir örnek üye olduğundan, hem `serialNo` örnek alana hem de `nextSerialNo` statik alana erişme izni verilir.

Ve `GetNextSerialNo` `SetNextSerialNo` statik yöntemler `nextSerialNo` statik alana erişebilir, ancak `serialNo` örnek alanına doğrudan erişmeleri hata olur.

Aşağıdaki örnek, Varlık sınıfının kullanımını gösterir.

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

Örnek `SetNextSerialNo` `GetNextSerialNo` yöntem sınıfın `GetSerialNo` örneklerinde çağrılırken, sınıfüzerinde statik yöntemler çağrılır.

### <a name="virtual-override-and-abstract-methods"></a>Sanal, geçersiz kılma ve soyut yöntemler

Bir örnek yöntem bildirimi `virtual` bir değiştirici içeriyorsa, *yöntemin sanal*bir yöntem olduğu söylenir. Sanal değiştirici olmadığında, yöntemin *sanal olmayan*bir yöntem olduğu söylenir.

Sanal bir yöntem çağrıldığında, bu çağırmanın gerçekleştiği örneğin *çalışma zamanı türü,* çağırmak için gerçek yöntem uygulamasını belirler. Sanal olmayan bir yöntem çağırmasında, örneğin *derleme zamanı türü* belirleyici faktördür.

Sanal yöntem türetilmiş bir sınıfta *geçersiz* kılınabilir. Bir örnek yöntem bildirimi bir geçersiz kılma değiştirici içeriyorsa, yöntem aynı imza ile devralınan bir sanal yöntemi geçersiz kılar. Sanal yöntem bildirimi yeni bir yöntem sunarken, geçersiz kılma yöntemi bildirimi, bu yöntemin yeni bir uygulamasını sağlayarak varolan bir devralınan sanal yöntemüzerinde uzmanlaşmıştır.

Soyut bir *yöntem,* hiçbir uygulama ile sanal bir yöntemdir. Soyut bir yöntem soyut değiştirici ile bildirilir ve yalnızca soyut olarak bildirilen bir sınıfta izin verilir. Soyut olmayan her türemiş sınıfta soyut bir yöntem geçersiz kılınmalıdır.

Aşağıdaki örnek, bir ifade `Expression`ağacı düğümünü temsil eden soyut bir sınıf `Constant` `VariableReference`ve `Operation`sabitler, değişken başvurular ve aritmetik işlemler için ifade ağacı düğümlerini uygulayan üç türemiş sınıf bildirir. (Bu örnek benzer, ancak ifade ağacı türleri ile karıştırılmamalıdır).

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

Önceki dört sınıf aritmetik ifadeleri modellemek için kullanılabilir. Örneğin, bu sınıfların örneklerini kullanarak, ifade `x + 3` aşağıdaki gibi temsil edilebilir.

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

Verilen `Evaluate` ifadeyi `Expression` değerlendirmek ve bir `double` değer üretmek için bir örneğin yöntemi çağrılır. Yöntem değişken `Dictionary` adları (girişlerin anahtarları olarak) ve değerleri (girişlerin değerleri olarak) içeren bir bağımsız değişken alır. Soyut `Evaluate` bir yöntem olduğundan, türetilen `Expression` soyut olmayan `Evaluate`sınıflar geçersiz kılınmalıdır.

Bir `Constant`'uygulama `Evaluate` sadece depolanan sabit döndürür. Bir `VariableReference`'s uygulaması sözlükteki değişken adını arar ve elde edilen değeri döndürür. Bir `Operation`'s uygulaması ilk sol ve sağ operands değerlendirir (özyinelemeli `Evaluate` yöntemleri çağırarak) ve daha sonra verilen aritmetik işlemi gerçekleştirir.

Aşağıdaki program farklı `Expression` değerler `x * (y + 2)` `x` için ifade değerlendirmek için `y`sınıfları kullanır ve .

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>Yöntem aşırı yükleme

Yöntem *aşırı yükleme,* aynı sınıftaki birden çok yöntemin, benzersiz imzaları olduğu sürece aynı ada sahip olmasını sağlar. Derleyici, aşırı yüklü bir yöntemin çağrılmasını derlediğinizde, çağırmak için belirli bir yöntemi belirlemek için *aşırı yük çözünürlüğünü* kullanır. Aşırı yükleme çözümü, bağımsız değişkenler ile en iyi eşleşen yöntemi bulur veya tek bir en iyi eşleşme bulunamazsa hata bildirir. Aşağıdaki örnekte, aşırı yük çözünürlüğü etkin olarak gösterilmektedir. Yöntemdeki her çağrı için `UsageExample` yapılan açıklama, hangi yöntemin çağrıldığını gösterir.

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

Örnekte gösterildiği gibi, bağımsız değişkenleri tam parametre türlerine ve/veya açıkça tür bağımsız değişkenlerine ekleyerek her zaman belirli bir yöntem seçilebilir.

## <a name="other-function-members"></a>Diğer işlev üyeleri

Yürütülebilir kod içeren üyeler, bir sınıfın *işlev üyeleri* olarak topluca bilinir. Önceki bölümde, birincil işlev üyeleri türleri olan yöntemler açıklanmaktadır. Bu bölümde C# tarafından desteklenen diğer işlev üyeleri türleri açıklanır: oluşturucular, özellikler, dizin leyiciler, olaylar, işleçler ve sonlandırıcılar.

Aşağıdaki örnek, büyüyebilir `MyList<T>`bir nesne listesini uygulayan genel bir sınıf olarak adlandırılır. Sınıf, en yaygın işlev türlerinden birkaç örnek içerir.

> [!NOTE]
> Bu örnek, `MyList` .NET standardı <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>ile aynı olmayan bir sınıf oluşturur. Bu tur için gerekli kavramları göstermek yok, ancak bu sınıf için bir yedek değildir.

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>Oluşturucular

C# hem örnek hem de statik oluşturucuları destekler. *Örnek oluşturucu,* bir sınıfın örneğini başlatması için gereken eylemleri uygulayan bir üyedir. *Statik oluşturucu,* bir sınıfın kendisini ilk yüklendiğinde başlatması için gereken eylemleri uygulayan bir üyedir.

Bir oluşturucu, iade türü olmayan ve içeren sınıfla aynı ada sahip bir yöntem gibi bildirilir. Bir oluşturucu bildirimi statik bir değiştirici içeriyorsa, statik bir oluşturucu bildirir. Aksi takdirde, bir örnek oluşturucu bildirir.

Örnek oluşturucular aşırı yüklenebilir ve isteğe bağlı parametrelere sahip olabilir. Örneğin, `MyList<T>` sınıf tek bir isteğe bağlı `int` parametre ile bir örnek oluşturucu bildirir. Örnek oluşturucular `new` işleç kullanılarak çağrılır. Aşağıdaki ifadeler, isteğe bağlı bağımsız değişkeni `MyList` olan ve olmayan sınıfın oluşturucusu kullanılarak iki `MyList<string>` örnek ayırır.

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

Diğer üyelerin aksine, örnek oluşturucular kalıtsal değildir ve bir sınıfın sınıfta gerçekten beyan edilen bu yapıcılar dışında örnek oluşturucuları yoktur. Bir sınıf için örnek oluşturucu sağlanmışsa, parametreleri olmayan boş bir sınıf otomatik olarak sağlanır.

### <a name="properties"></a>Özellikler

*Özellikler* alanların doğal bir uzantısıdır. Her ikisi de ilişkili türleri olan üyeler adlandırılmış ve alanlara ve özelliklere erişmek için sözdizimi aynıdır. Ancak, alanların aksine, özellikler depolama konumlarını ifade etmez. Bunun yerine, özelliklerin, değerleri okunduğunda veya yazıldığında yürütülecek deyimleri belirten *erişime sahip olmaları* gerekir.

Bir özellik, beyannamenin bir erişime erişimve/veya sınırlayıcılar `{` arasında yazılmış bir set erişimci `}` yle sona ermesi ve yarı kolonla sonlandırmak yerine bir alan gibi bildirilir. Hem erişime sahip hem de ayarlanmış bir erişime sahip bir özellik *okuma yazma özelliğidir,* yalnızca erişime sahip bir özellik yalnızca *okuma özelliğidir*ve yalnızca ayarlanmış bir erişime sahip olan bir özellik *yalnızca yazma özelliğidir.*

Get accessor özellik türü bir dönüş değeri ile parametresiz bir yönteme karşılık gelir. Bir atamanın hedefi dışında, bir özellik ifadede başvurulduğunda, özelliğin değerini hesaplamak için mülkün erişime giren aracı çağrılır.

Kümeli erişimci, değeri adında tek bir parametreye sahip ve dönüş türü olmayan bir yönteme karşılık gelir. Bir özellik bir atamanın hedefi olarak veya ++veya --, operand olarak başvurulduğunda, ayarlanan erişimyeni değeri sağlayan bir bağımsız değişkenle çağrılır.

Sınıf, `MyList<T>` `Count` `Capacity`sırasıyla salt okunur ve okunan iki özelliği bildirir. Aşağıdaki kod, bu özelliklerin kullanımına bir örnektir:

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

Alanlara ve yöntemlere benzer şekilde, C# hem örnek özelliklerini hem de statik özellikleri destekler. Statik özellikler statik değiştirici ile bildirilir ve örnek özellikleri onsuz bildirilir.

Bir özelliğin erişimcisi sanal olabilir. Bir özellik bildirimi `virtual`, `abstract`, `override` veya değiştirici içeriyorsa, bu özellik erişim (ler) için geçerlidir.

### <a name="indexers"></a>Dizin Oluşturucular

*Dizinleyici,* nesnelerin diziyle aynı şekilde dizilmesini sağlayan bir üyedir. Bir dizinleyici, üyenin `this` adının sınır dışı edenler `[` ve . `]` Parametreler dizinleyicinin erişime atasında mevcuttur. Özelliklere benzer şekilde, dizinleyiciler okuma-yazma, salt okunur ve yalnızca yazma olabilir ve dizinleyicinin erişimi sanal olabilir.

Sınıf, `MyList<T>` bir parametre alan tek bir `int` okuma-yazma dizinleyicisi bildirir. Dizinleyici, örnekleri değerlerle dizine `MyList<T>` ekmemi `int` mümkün kılar. Örnek:

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

Dizinleyiciler aşırı yüklenebilir, bu da bir sınıfın parametrelerinin sayısı veya türleri farklı olduğu sürece birden çok dizinleyici bildirebileceği anlamına gelir.

### <a name="events"></a>Olaylar

*Olay,* bir sınıfın veya nesnenin bildirim sağlamasını sağlayan bir üyedir. Bir olay, bildirimin bir olay anahtar sözcüğü içerdiğini ve türünün bir temsilci türü olması dışında bir alan gibi bildirilir.

Olay üyesini bildiren bir sınıf içinde, olay bir temsilci türündeki alan gibi olur (olay soyut değilse ve erişime girenleri bildirmezse). Alan, olaya eklenen olay işleyicilerini temsil eden bir temsilciye başvuruda bulunuyor. Olay işleyicileri yoksa, alan `null`.

`Changed`Sınıf, `MyList<T>` listeye yeni bir öğenin eklendiğini belirten tek bir olay üyesi ni bildirir. Değiştirilen olay, önce `OnChanged` olayın olup `null` olmadığını denetleyen sanal yöntem tarafından yükseltilir (yani işleyicileri yok). Bir olayı yükseltme kavramı, olay tarafından temsil edilen temsilciyi çağırmakla tam olarak eşdeğerdir, bu nedenle, olayları yükseltmek için özel bir dil yapısı yoktur.

İstemciler *olaylara olay işleyicileri*aracılığıyla tepki verir. Olay işleyicileri `+=` işleç kullanılarak eklenir ve `-=` işleci kullanılarak kaldırılır. Aşağıdaki örnek, bir olay işleyicisi `Changed` `MyList<string>`bir .

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

Bir olayın temel depolama denetiminin istendiği gelişmiş senaryolar için, olay `add` bildirimi `remove` açıkça bir özelliğin `set` erişimine benzeyen bir durum bildirimi sağlayabilir ve erişilenler.

### <a name="operators"></a>İşleçler

*İşleç,* belirli bir ifade işlecinin bir sınıfın örneklerine uygulanmasının anlamını tanımlayan bir üyedir. Üç tür işleç tanımlanabilir: unary işleçleri, ikili işleçler ve dönüşüm işleçleri. Tüm operatörler olarak `public` `static`beyan edilmelidir.

Sınıf `MyList<T>` iki işleç `operator ==` bildirir `operator !=`ve bu nedenle bu işleçleri örneklere uygulayan ifadelere `MyList` yeni bir anlam verir. Özellikle, işleçler eşitlik `MyList<T>` yöntemlerini kullanarak içerdiği nesnelerin her birini karşılaştırarak olarak iki örnek eşitliği tanımlar. Aşağıdaki örnek, `==` iki `MyList<int>` örneği karşılaştırmak için işleci kullanır.

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

İki `Console.WriteLine` liste `True` aynı sırada aynı değerlere sahip aynı sayıda nesne içerdiğinden ilk çıktılar. Tanımlanmamış `MyList<T>` `operator ==`olsaydı, `Console.WriteLine` ilk çıktı `False` `a` olurdu `b` çünkü `MyList<int>` ve farklı örnekleri başvurur.

### <a name="finalizers"></a>Sonlandırıcılar

*Sonlandırıcı,* bir sınıfın örneğini sonuçlandırmak için gereken eylemleri uygulayan bir üyedir. Sonlandırıcıların parametreleri olamaz, erişilebilirlik değiştiriciler olamaz ve açıkça çağrılabilir. Bir örneğin sonlandırıcı, çöp toplama sırasında otomatik olarak çağrılır.

Çöp toplayıcı, nesneleri ne zaman toplayacaklarına ve sonlandırıcıları çalıştırmaya karar verirken geniş enlem lemesine izin verilir. Özellikle, sonlandırıcı çağrılarının zamanlaması belirleyici değildir ve sonlandırıcılar herhangi bir iş parçacığı üzerinde yürütülebilir. Bu ve diğer nedenlerle, sınıflar sonlandırıcıları yalnızca başka çözümler mümkün olmadığında uygulamalıdır.

İfade `using` nesne imha için daha iyi bir yaklaşım sağlar.

> [!div class="step-by-step"]
> [Önceki](statements.md)
> [Sonraki](arrays.md)
