---
title: Ortak Tür Sistemi
description: .NET 'teki tür sistemini keşfedebilir. .NET 'teki türler (değer türleri veya başvuru türleri), tür tanımı, tür üyeleri ve tür üye özellikleri hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- type system
- common type system
- assemblies [.NET Framework], types
- reference types
- value types
- cross-language interoperability
- namespaces [.NET Framework], types
- types, about types
ms.assetid: 53c57c96-83e1-4ee3-9543-9ac832671a89
ms.openlocfilehash: 4e3fc4cb03a0b8fd63b41bd912374c29eef3a29a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555165"
---
# <a name="common-type-system"></a>Ortak tür sistemi

Ortak tür sistemi, türlerin ortak dil çalışma zamanında nasıl bildirildiği, kullanıldığı ve yönetildiğini tanımlar ve ayrıca çalışma zamanının çapraz dil tümleştirmesi desteğinin önemli bir parçasıdır. Ortak tür sistemi aşağıdaki işlevleri gerçekleştirir:  
  
- Diller arası tümleştirmeyi, tür güvenliğini ve yüksek performanslı kod yürütmeyi etkinleştirmeye yardımcı olan bir çerçeve oluşturur.  
  
- Birçok programlama dilinin tam uygulamasını destekleyen nesne odaklı bir model sağlar.  
  
- Dillerin izlenmesi gereken kuralları tanımlar, bu da farklı dillerde yazılmış nesnelerin birbirleriyle etkileşime geçmesini sağlar.  
  
- <xref:System.Boolean> <xref:System.Byte> <xref:System.Char> <xref:System.Int32> <xref:System.UInt64> Uygulama geliştirmede kullanılan temel veri türlerini (,,,, ve) içeren bir kitaplık sağlar.
  
## <a name="types-in-net"></a>.NET 'teki türler

 .NET 'teki tüm türler değer türleri ya da başvuru türleridir.  
  
 Değer türleri, nesneleri nesnenin gerçek değeri ile temsil edilen veri türleridir. Bir değer türü örneği bir değişkene atanırsa, bu değişkene değerin yeni bir kopyası verilir.  
  
 Başvuru türleri, nesneleri nesnenin gerçek değerine (bir işaretçiye benzer şekilde) bir başvuruya göre temsil edilen veri türleridir. Bir değişkene başvuru türü atanmışsa, bu değişken özgün değeri (işaret eder). Hiçbir kopya yapılmadı.  
  
 .NET 'teki ortak tür sistemi aşağıdaki beş tür kategorisini destekler:  
  
- [Sınıflar](#classes)  
  
- [Yapılar](#structures)  
  
- [Numaralandırmalar](#enumerations)  
  
- [Arabirimler](#interfaces)  
  
- [Temsilciler](#delegates)  
  
### <a name="classes"></a>Sınıflar

 Sınıf, doğrudan başka bir sınıftan türetilebilen ve örtülü olarak türetilmiş bir başvuru türüdür <xref:System.Object?displayProperty=nameWithType> . Sınıfı, bir nesnenin (sınıfın bir örneği olan) gerçekleştirebileceği işlemleri (Yöntemler, olaylar veya Özellikler) ve nesnenin içerdiği verileri (alanlar) tanımlar. Bir sınıf genellikle hem tanım hem de uygulama içerse de (örneğin, yalnızca uygulama olmadan tanım içeren arabirimlerin aksine), hiçbir uygulamaya sahip olmayan bir veya daha fazla üyesi olabilir.  
  
 Aşağıdaki tabloda bir sınıfın sahip olabileceği bazı özellikler açıklanmaktadır. Çalışma zamanını destekleyen her dil, bir sınıf veya sınıf üyesinin bu özelliklerden birini veya daha fazlasını olduğunu göstermek için bir yol sağlar. Ancak, .NET ' i hedefleyen bireysel programlama dilleri, bu özelliklerin tümünü kullanabilir hale gelebilir.  
  
|Özellik|Description|  
|--------------------|-----------------|  
|sealed|Başka bir sınıfın bu türden türetilemeyeceğini belirtir.|  
|uygulamalar|Sınıfın, arabirim üyesi uygulamalar sunarak bir veya daha fazla arabirim kullandığını gösterir.|  
|abstract|Sınıfın örneklendirilmediğini belirtir. Bunu kullanmak için, bundan başka bir sınıf türetmeniz gerekir.|  
|alıp|Sınıfın örneklerinin temel sınıfın belirtildiği her yerde kullanılabileceğini gösterir. Temel sınıftan devralan türetilmiş bir sınıf, temel sınıf tarafından sağlanmış olan herhangi bir ortak üyenin uygulamasını kullanabilir veya türetilmiş sınıf ortak üyelerin uygulamasını kendi uygulamasıyla geçersiz kılabilir.|  
|verildi veya verilmez|Bir sınıfın tanımlandığı derlemenin dışında görünür olup olmadığını gösterir. Bu özellik yalnızca üst düzey sınıflar için geçerlidir, iç içe geçmiş sınıflara uygulanmaz.|  
  
> [!NOTE]
> Bir sınıf Ayrıca bir üst sınıf veya yapıda iç içe olabilir. İç içe sınıflarda üye özellikleri de vardır. Daha fazla bilgi için bkz. [Iç Içe türler](#nested-types).  
  
 Hiçbir uygulamaya sahip olmayan sınıf üyeleri soyut üyeleridir. Bir veya daha fazla soyut üyeye sahip bir sınıf kendi soyuttur; Yeni bunun örnekleri oluşturulamaz. Çalışma zamanını hedefleyen bazı diller, üyelerinden hiçbiri soyut olmasa bile bir sınıfı soyut olarak işaretlemenize olanak tanır. Uygun olduğunda türetilen sınıfların devraldığı veya geçersiz kılabileceği temel bir işlev kümesini kapsüllemek istediğinizde bir soyut sınıf kullanabilirsiniz. Soyut olmayan sınıflar somut sınıflar olarak adlandırılır.  
  
 Bir sınıf herhangi bir sayıda arabirim uygulayabilir, ancak öğesine ek olarak yalnızca bir temel sınıftan kalıtımla alabilir <xref:System.Object?displayProperty=nameWithType> . Bu, tüm sınıfların örtük olarak devralınır. Tüm sınıfların, sınıfının yeni örneklerini Başlatan en az bir oluşturucusu olmalıdır. Açıkça bir Oluşturucu tanımlamadıysanız, çoğu derleyiciler parametresiz bir Oluşturucu otomatik olarak sağlayacaktır.  
  
### <a name="structures"></a>Yapılar

 Bir yapı, öğesinden türetilmiş bir değer türüdür ve bu <xref:System.ValueType?displayProperty=nameWithType> , sırasıyla öğesinden türetilir <xref:System.Object?displayProperty=nameWithType> . Bir yapı, bellek gereksinimleri küçük olan değerleri temsil etmek ve değerleri, kesin olarak belirlenmiş parametrelere sahip yöntemlere değer olarak parametre olarak geçirmek için yararlıdır. .NET sürümünde, tüm ilkel veri türleri (,,,,,,,,, <xref:System.Boolean> <xref:System.Byte> <xref:System.Char> <xref:System.DateTime> <xref:System.Decimal> <xref:System.Double> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.SByte> , <xref:System.Single> , <xref:System.UInt16> , <xref:System.UInt32> , ve <xref:System.UInt64> ) yapılar olarak tanımlanır.  
  
 Sınıflar gibi yapılar, verileri (yapının alanları) ve bu verilerde gerçekleştirilebilecek işlemleri (yapının yöntemleri) tanımlar. Bu, ve sınıflarında tanımlanmış sanal yöntemler <xref:System.Object?displayProperty=nameWithType> <xref:System.ValueType?displayProperty=nameWithType> ve değer türü üzerinde tanımlanan Yöntemler dahil olmak üzere yapılar üzerinde Yöntemler çağırabilmeniz anlamına gelir. Diğer bir deyişle, yapılar alanları, özellikleri ve olayları ve statik ve statik olmayan yöntemleri içerebilir. Yapıların örneklerini oluşturabilir, bunları parametre olarak geçirebilir, yerel değişkenler olarak saklayabilir veya başka bir değer türü veya başvuru türündeki bir alanda saklayabilirsiniz. Yapılar, arabirimleri de uygulayabilir.  
  
 Değer türleri, farklı bir şekilde sınıflardan de farklılık gösterir. Birincisi, ' den örtük olarak kalıtımla alsa da <xref:System.ValueType?displayProperty=nameWithType> , hiçbir türden doğrudan devralınabilir. Benzer şekilde, tüm değer türleri Sealed olur ve bu, başka bir türün bunlardan türetilemeyeceğini belirtir. Ayrıca oluşturucular gerektirmez.  
  
 Her değer türü için ortak dil çalışma zamanı, değer türüyle aynı durum ve davranışa sahip bir sınıf olan, karşılık gelen paketlenmiş bir tür sağlar. Değer türünün bir örneği, türünde bir parametre kabul eden bir yönteme geçirildiğinde paketlenmelidir <xref:System.Object?displayProperty=nameWithType> . Denetim kutulanır (yani, bir sınıfın örneğinden bir değer türünün örneğine dönüştürülür) denetim, bir değer türünü başvuru parametresi olarak kabul eden bir yöntem çağrısından geri döndüğünde. Bazı diller kutulanmış tür gerektiğinde özel sözdizimi kullanmanızı gerektirir; diğerleri gerektiğinde kutulanmış türü otomatik olarak kullanır. Bir değer türü tanımladığınızda, hem paketlenmiş hem de kutulanmamış türü tanımlarsınız.  
  
### <a name="enumerations"></a>Listelemeler

 Sabit Listesi doğrudan öğesinden devralan <xref:System.Enum?displayProperty=nameWithType> ve temel bir temel türün değerleri için alternatif adlar sağlayan bir değer türüdür. Sabit listesi türü, yerleşik imzalı veya işaretsiz tamsayı türlerinden biri olması gereken temel bir tür olan bir ada sahiptir (örneğin <xref:System.Byte> , <xref:System.Int32> , veya <xref:System.UInt64> ) ve bir alan kümesi. Alanlar, her biri bir sabiti temsil eden statik sabit değerli alanlardır. Aynı değer birden çok alana atanabilir. Bu gerçekleştiğinde, bir değerden birini yansıma ve dize dönüştürmesi için birincil numaralandırma değeri olarak işaretlemeniz gerekir.  
  
 Temel alınan türün bir değerini bir sabit listesine atayabilir ve tam tersi de (çalışma zamanı için atama gerekmez). Bir sabit listesinin bir örneğini oluşturabilir ve yöntemlerinin <xref:System.Enum?displayProperty=nameWithType> yanı sıra numaralandırmanın temel alınan türünde tanımlanan yöntemleri çağırabilirsiniz. Ancak, bazı diller, temel alınan türden bir örnek gerektiğinde (veya tam tersi) bir sabit listesini parametre olarak geçirmenize izin vermiyor.  
  
 Aşağıdaki ek kısıtlamalar Numaralandırmalar için geçerlidir:  
  
- Kendi yöntemlerini tanımlayamazlar.  
  
- Arabirimler uygulayamaz.  
  
- Özellikleri veya olayları tanımlayamazlar.  
  
- Bunlar genel olmamaları dışında, genel olmayan, genel bir tür içinde iç içe olmadıkları için genel olamaz. Diğer bir deyişle, bir numaralandırma kendi tür parametrelerine sahip olamaz.  
  
    > [!NOTE]
    > Visual Basic, C# ve C++ ile oluşturulan iç içe türler (numaralandırmalar dahil), kapsayan tüm genel türlerin tür parametrelerini içerir ve bu nedenle, kendilerine ait tür parametrelerine sahip olmasalar bile geneldir. Daha fazla bilgi için başvuru konusunun "Iç Içe türler" başlığına bakın <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> .  
  
 <xref:System.FlagsAttribute>Öznitelik, bit alanı olarak adlandırılan özel bir numaralandırma türünü gösterir. Çalışma zamanının kendisi geleneksel numaralandırmalar ve bit alanları arasında ayrım yapmaz, ancak diliniz bunu gösterebilir. Bu ayrım yapıldığında, bir bit düzeyinde işleçler, adlandırılmamış değerler oluşturmak için bit alanlarında kullanılabilir ancak numaralandırmalar üzerinde kullanılamaz. Numaralandırmalar genellikle haftanın günleri, ülke veya bölge adları gibi benzersiz öğelerin listeleri için kullanılır. Bit alanları, genellikle gibi ortaya çıkabilecek kalitelerin veya miktarların listesi için kullanılır `Red And Big And Fast` .  
  
 Aşağıdaki örnek, hem bit alanları hem de geleneksel Numaralandırmaların nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  

### <a name="interfaces"></a>Arabirimler

 Arabirim, "yapabilir" ilişki veya "bir" a "ilişkisi belirten bir sözleşmeyi tanımlar. Arabirimler genellikle karşılaştırma ve sıralama ( <xref:System.IComparable> ve <xref:System.IComparable%601> arabirimler), eşitlik için test etme ( <xref:System.IEquatable%601> arabirim) veya bir koleksiyondaki öğeleri numaralandırma ( <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601> arabirimler) gibi işlevleri uygulamak için kullanılır. Arabirimler, hepsi soyut üye olan özellikler, Yöntemler ve olaylar içerebilir; diğer bir deyişle, arabirim üyeleri ve bunların imzalarını tanımlasa da, her arabirim üyesinin işlevselliğini tanımlamak için arabirimini uygulayan türe bırakır. Bu, bir arabirimi uygulayan herhangi bir sınıfın veya yapının, arabiriminde belirtilen soyut üyelere yönelik tanımlar sağlaması gerektiği anlamına gelir. Bir arabirim, bir veya daha fazla arabirimi de uygulamak için herhangi bir uygulama sınıfı veya yapısının kullanılmasını gerektirebilir.  
  
 Aşağıdaki kısıtlamalar arabirimler için geçerlidir:  
  
- Bir arabirim herhangi bir erişilebilirliği ile bildirilebilecek, ancak arabirim üyelerinin herkese genel erişilebilirliği olması gerekir.  
  
- Arabirimler oluşturucuları tanımlanamaz.  
  
- Arabirimler alanları tanımlayabilir.  
  
- Arabirimler yalnızca örnek üyelerini tanımlayabilir. Statik üyeleri tanımlayamazlar.  
  
 Her dil, birden fazla arabirim aynı imzaya sahip bir üyeyi bildirebildiğinden ve bu Üyeler ayrı uygulamalara sahip olabileceğinden, bir uygulamayı üye gerektiren arabirime eşlemek için kurallar sağlamalıdır.  

### <a name="delegates"></a>Temsilciler

 Temsilciler, C++ içindeki işlev işaretçilerinden benzer bir amaçla sunan başvuru türleridir. .NET 'teki olay işleyicileri ve geri çağırma işlevleri için kullanılırlar. İşlev işaretçilerinden farklı olarak, temsilciler güvenli, doğrulanabilir ve tür güvenlidir. Bir temsilci türü, uyumlu imzaya sahip herhangi bir örnek yöntemini veya statik yöntemi temsil edebilir.  
  
 Temsilci parametresinin türü Yöntem parametresinin türünden daha kısıtlayıcıysa, temsilcinin bir parametresi, yönteme karşılık gelen bir bağımsız değişkenin yönteme güvenli bir şekilde geçirilebildiğinden, bir yöntemin ilgili parametresiyle uyumludur.  
  
 Benzer şekilde, yöntemin dönüş türü temsilcinin dönüş türüne göre daha kısıtlayıcıysa, bir temsilcinin dönüş türü bir yöntemin dönüş türü ile uyumludur. Bu, yöntemin dönüş değerinin temsilcinin dönüş türüne güvenle yayınlanabilmesi güvence altına alır.  
  
 Örneğin, türünde bir parametre ve dönüş türü olan bir temsilci, türünde bir <xref:System.Collections.IEnumerable> <xref:System.Object> parametre <xref:System.Object> ve dönüş değeri türünde bir yöntemi temsil edebilir <xref:System.Collections.IEnumerable> . Daha fazla bilgi ve örnek kod için bkz <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> ..  
  
 Bir temsilcinin temsil ettiği yönteme bağlanması söylenir. Yönteme bağlanılmalarının yanı sıra, bir temsilci bir nesneye de bağlanabilir. Nesnesi, yöntemin ilk parametresini temsil eder ve temsilci her çağrıldığında yöntemine geçirilir. Yöntem bir örnek yöntemi ise, bağlantılı nesne örtük parametre olarak geçirilir `this` ( `Me` Visual Basic); yöntem statikse, nesne yöntemin ilk biçimsel parametresi olarak geçirilir ve temsilci imzası kalan parametrelerle eşleşmelidir. Daha fazla bilgi ve örnek kod için bkz <xref:System.Delegate?displayProperty=nameWithType> ..  
  
 ' Den devralan tüm temsilciler öğesinden devralır <xref:System.MulticastDelegate?displayProperty=nameWithType> <xref:System.Delegate?displayProperty=nameWithType> . C#, Visual Basic ve C++ dilleri, bu türlerden devralmaya izin vermez. Bunun yerine, temsilcileri bildirmek için anahtar sözcükler sağlarlar.  
  
 Temsilciler öğesinden devraldığı için, temsilcinin <xref:System.MulticastDelegate> temsil ettiği ve temsilci çağrıldığında yürütülen yöntemlerin listesi olan bir çağrı listesi vardır. Listedeki tüm yöntemler, temsilci çağrıldığında sağlanan bağımsız değişkenleri alır.  
  
> [!NOTE]
> Dönüş değeri, temsilci bir dönüş türüne sahip olsa bile, çağırma listesinde birden fazla metodu olan bir temsilci için tanımlı değil.  
  
 Birçok durumda, örneğin geri çağırma yöntemleriyle, bir temsilci yalnızca bir yöntemi temsil eder ve gerçekleştirmeniz gereken tek eylem temsilciyi oluşturur ve çağırır.  
  
 .NET, birden çok yöntemi temsil eden temsilciler için, bir <xref:System.Delegate> <xref:System.MulticastDelegate> temsilcinin çağrı listesine (yöntemi) bir yöntem ekleme <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> , bir yöntemi kaldırma ( <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> yöntemi) ve çağırma listesini alma (yöntemi) gibi işlemleri desteklemek için ve temsilci sınıflarının yöntemlerini sağlar <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> .  
  
> [!NOTE]
> Bu diller, olay işleyicilerini ekleme ve kaldırma için sözdizimi sağladığından C#, C++ ve Visual Basic olay işleyici temsilcileri için bu yöntemlerin kullanılması gerekli değildir.  

## <a name="type-definitions"></a>Tür tanımları

 Bir tür tanımı şunları içerir:  
  
- Tür üzerinde tanımlanan öznitelikler.  
  
- Türün erişilebilirliği (görünürlük).  
  
- Türün adı.  
  
- Türün temel türü.  
  
- Tür tarafından uygulanan Arabirimler.  
  
- Türün üyelerinin her biri için tanımlar.  
  
### <a name="attributes"></a>Öznitelikler  
 Öznitelikler, Kullanıcı tanımlı ek meta veriler sağlar. En yaygın olarak, kendi derlemesinde bir tür hakkındaki ek bilgileri depolamak veya tasarım zamanı ya da çalışma zamanı ortamında bir tür üyesinin davranışını değiştirmek için kullanılır.  
  
 Öznitelikleri, ' den devraldığı sınıflardır <xref:System.Attribute?displayProperty=nameWithType> . Özniteliklerin kullanımını destekleyen dillerin, öznitelikleri bir dil öğesine uygulamak için kendi sözdizimi vardır. Öznitelikler, neredeyse tüm dil öğeleri için uygulanabilir; bir özniteliğin uygulanabileceğini belirleyen belirli öğeler, <xref:System.AttributeUsageAttribute> Bu öznitelik sınıfına uygulanan öğesi tarafından tanımlanır.  
  
### <a name="type-accessibility"></a>Tür erişilebilirliği  
 Tüm türlerin, diğer türlerden erişilebilirliğini yöneten bir değiştiricisi vardır. Aşağıdaki tabloda, çalışma zamanı tarafından desteklenen tür erişilebilirlik türleri açıklanmaktadır.  
  
|Erişilebilirlik|Description|  
|-------------------|-----------------|  
|public|Türe tüm derlemeler tarafından erişilebilir.|  
|derleme|Türe yalnızca kendi derlemesi içinden erişilebilir.|  
  
 İç içe bir türün erişilebilirliği, hem belirtilen üyenin hem de hem de hem de kapsayan türdeki erişilebilirlik etki alanı tarafından belirlenen erişilebilirlik etki alanına bağlıdır. Ancak, iç içe geçmiş bir türün erişilebilirlik etki alanı, kapsayan türden bu türü aşamaz.  
  
 Bir program içindeki bir tür içinde bildirildiği iç içe bir üyenin erişilebilirlik etki alanı, `M` `T` `P` aşağıdaki gibi tanımlanır (bunun `M` kendisi bir tür olabileceğini belirtmekte):  
  
- ' Nin belirtilen erişilebilirliği ise, öğesinin erişilebilirlik etki alanıdır `M` `public` `M` `T` .  
  
- ' Nin belirtilen erişilebilirliği ise, öğesinin erişilebilirlik etki alanı, ' ın ' ın ' ın ' a ait `M` `protected internal` `M` olan erişilebilirlik etki alanının `T` `P` ve dışında bildirildiği herhangi bir türün program metniyle kesişmesi olur `T` `P` .  
  
- ' Nin belirtilen erişilebilirliği ise, öğesinin erişilebilirlik etki alanı, `M` `protected` ' ın `M` `T` Program metni `T` ve öğesinden türetilen herhangi bir tür ile erişilebilirlik etki alanının kesişimidir `T` .  
  
- ' Nin belirtilen erişilebilirliği `M` ise `internal` , öğesinin erişilebilirlik etki alanı, ' ın ' ın `M` erişilebilirlik etki alanının kesişimidir `T` `P` .  
  
- ' Nin belirtilen erişilebilirliği `M` ise `private` , öğesinin erişilebilirlik etki alanı `M` öğesinin program metni olur `T` .  
  
### <a name="type-names"></a>Tür Adları  
 Ortak tür sistemi, adlar üzerinde yalnızca iki kısıtlama uygular:  
  
- Tüm adlar Unicode (16 bit) karakter dizeleri olarak kodlanır.  
  
- Adların, 0x0000 Embedded (16 bit) değerine sahip olması için izin verilmez.  
  
 Ancak, çoğu dilin tür adlarında ek kısıtlamalar vardır. Tüm karşılaştırmalar bayt olarak bir bayt temelinde gerçekleştirilir ve bu nedenle büyük/küçük harfe duyarlıdır ve yerel ayara bağımsızdır.  
  
 Bir tür diğer modüllerdeki ve derlemelerdeki türlere başvuru yapabilse de, bir tür bir .NET modülü içinde tam olarak tanımlanmalıdır. (Derleyici desteğine bağlı olarak, birden çok kaynak kodu dosyasına ayrılabilir.) Tür adlarının yalnızca bir ad alanı içinde benzersiz olması gerekir. Bir türü tam olarak tanımlamak için tür adı, türü uygulamasını içeren ad alanı tarafından nitelenmelidir.  
  
### <a name="base-types-and-interfaces"></a>Temel türler ve arabirimler  
 Bir tür, başka bir türden değerleri ve davranışları devralınabilir. Ortak tür sistemi, türlerin birden fazla temel türden devralmasını izin vermez.  
  
 Bir tür, herhangi bir sayıda arabirim uygulayabilir. Bir arabirim uygulamak için bir türün, bu arabirimin tüm sanal üyelerini uygulaması gerekir. Sanal bir yöntem, türetilmiş bir tür tarafından uygulanabilir ve statik veya dinamik olarak çağrılabilir.  

## <a name="type-members"></a>Tür üyeleri

 Çalışma zamanı, bir türün davranışını ve durumunu belirten, türünden Üyeler tanımlamanızı sağlar. Tür üyeleri şunları içerir:  
  
- [Alanlar](#fields)  
  
- [Özellikler](#properties)  
  
- [Yöntemler](#methods)  
  
- [Oluşturucular](#constructors)  
  
- [Ekinlikler](#events)  
  
- [İç içe geçmiş türler](#nested-types)  

### <a name="fields"></a>Alanlar

 Bir alan, türün durumunun bir parçasını tanımlar ve içerir. Alanlar, çalışma zamanı tarafından desteklenen herhangi bir türde olabilir. En yaygın olarak, alanlar `private` veya `protected` , yalnızca sınıfın içinden veya türetilmiş bir sınıftan erişilebilir olmaları sağlanır. Bir alanın değeri, türünün dışından değiştirilebiliyorsanız, genellikle bir özellik kümesi erişimcisi kullanılır. Genel olarak gösterilen alanlar genellikle salt okunurdur ve iki türden olabilir:  
  
- Değer, tasarım zamanında atanmış olan sabitler. Bunlar, `static` ( `Shared` Visual Basic) anahtar sözcüğü kullanılarak tanımlanmamakla birlikte, bir sınıfın statik üyeleridir.  
  
- Değerleri sınıf oluşturucusunda atanabileceği salt okunurdur.  
  
 Aşağıdaki örnekte, salt okunurdur alanlarının bu iki kullanımı gösterilmektedir.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  

### <a name="properties"></a>Özellikler

 Bir özellik, türün bir değerini veya durumunu adlandırır ve özelliğin değerini almak veya ayarlamak için yöntemleri tanımlar. Özellikler basit türler, temel türler koleksiyonları, Kullanıcı tanımlı türler veya Kullanıcı tanımlı türlerin koleksiyonları olabilir. Özellikler genellikle türün gerçek gösteriminden bağımsız olarak bir türün genel arabirimini tutmak için kullanılır. Bu, özelliklerin doğrudan sınıfında depolanmayan değerleri yansıtmasını sağlar (örneğin, bir özellik hesaplanan bir değer döndürdüğünde) veya değerler özel alanlara atanmadan önce doğrulama gerçekleştirir. Aşağıdaki örnek, son stili gösterir.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Özelliğin kendisini eklemenin yanı sıra, okunabilir bir özelliği içeren bir türün Microsoft ara dili (MSIL) bir `get_` *PropertyName* yöntemi ve yazılabilir özelliği içeren BIR tür için MSIL yöntemi bir `set_` *PropertyName* yöntemi içerir.  

### <a name="methods"></a>Yöntemler

 Bir yöntemi, türünde kullanılabilir olan işlemleri açıklar. Yöntemin imzası, tüm parametrelerinin ve dönüş değerinin izin verilen türlerini belirtir.  
  
 Çoğu Yöntem Yöntem çağrıları için gerekli parametrelerin tam sayısını tanımlasa da, bazı yöntemler değişken sayıda parametreyi destekler. Bu yöntemlerin son tanımlanmış parametresi <xref:System.ParamArrayAttribute> özniteliğiyle işaretlenir. Dil derleyicileri, genellikle gereksiz bir şekilde `params` kullanımını sağlayan C# ve Visual Basic gibi bir anahtar sözcük sağlar `ParamArray` <xref:System.ParamArrayAttribute> .  

### <a name="constructors"></a>Oluşturucular

 Oluşturucu, bir sınıfın veya yapının yeni örneklerini oluşturan özel bir yöntem türüdür. Diğer tüm yöntemler gibi, bir Oluşturucu parametreleri içerebilir; Ancak, oluşturucuların dönüş değeri yoktur (yani döndürürler `void` ).  
  
 Bir sınıfın kaynak kodu açıkça bir Oluşturucu tanımlamıyorsa, derleyici parametresiz bir Oluşturucu içerir. Ancak, bir sınıfın kaynak kodu yalnızca parametreli oluşturucular tanımlıyorsa, Visual Basic ve C# derleyicileri parametresiz bir Oluşturucu oluşturmaz.  
  
 Bir yapının kaynak kodu oluşturucuları tanımlıyorsa, bunlar parametreli olmalıdır; bir yapı parametresiz bir Oluşturucu tanımlayabilir ve derleyiciler yapılar veya diğer değer türleri için parametresiz oluşturucular oluşturmaz. Tüm değer türlerinde örtük olarak parametresiz bir Oluşturucu vardır. Bu Oluşturucu ortak dil çalışma zamanı tarafından uygulanır ve yapının tüm alanlarını varsayılan değerlerine başlatır.  

### <a name="events"></a>Ekinlikler

 Bir olay, yanıtlamış olabilecek bir olayı tanımlar ve ' a abone olunmakta olan, etkinliği kaldırmak ve olayı yükseltmek için Yöntemler tanımlar. Olaylar genellikle diğer durum değişikliği türlerini bilgilendirmek için kullanılır. Daha fazla bilgi için bkz. [Olaylar](../events/index.md).  

### <a name="nested-types"></a>İç içe geçmiş türler

 İç içe bir tür, başka bir türün üyesi olan bir türdür. İç içe türler kapsayan türlerine sıkı bir biçimde bağlanmalıdır ve genel amaçlı bir tür olarak yararlı olmamalıdır. İç içe türler, bildirim türü kullandığında ve iç içe türün örneklerini oluşturduğunda ve iç içe türün kullanılması Ortak üyelerde gösterilmediği durumlarda faydalıdır.  
  
 İç içe türler bazı geliştiricilere kafa karıştırıcı ve görünürlük açısından etkileyici bir neden olmadıkça herkese açık olmamalıdır. İyi tasarlanmış bir kitaplıkta, geliştiricilerin nesneleri başlatmak veya değişkenleri bildirmek için nadiren iç içe türler kullanması gerekir.  

## <a name="characteristics-of-type-members"></a>Üye türü özellikleri

 Ortak tür sistemi, tür üyelerinin çeşitli özelliklere sahip olmasına olanak sağlar; Ancak, dillerin tüm bu özellikleri desteklemesi gerekmez. Aşağıdaki tabloda üye özellikleri açıklanmaktadır.  
  
|Özellik|Uygulanabilir|Description|  
|--------------------|------------------|-----------------|  
|abstract|Yöntemler, Özellikler ve olaylar|Tür, yöntemin uygulamasını sağlamaz. Soyut yöntemleri devraldığı veya uygulayan türler, yöntemi için bir uygulama sağlamalıdır. Tek özel durum, türetilmiş türün bir soyut tür olduğu durumdur. Tüm soyut yöntemler sanal.|  
|Özel, Aile, derleme, Aile ve derleme, Aile veya derleme ya da ortak|Tümü|Üyenin erişilebilirliğini tanımlar:<br /><br /> private<br /> Yalnızca üyeyle aynı tür içinden veya iç içe yerleştirilmiş bir tür içinde erişilebilir.<br /><br /> aile<br /> Üyeyle aynı tür içinden ve ondan kalıtımla alan türetilmiş türlerden erişilebilir.<br /><br /> derleme<br /> Yalnızca türün tanımlandığı derlemede erişilebilir.<br /><br /> Aile ve derleme<br /> Yalnızca aile ve derleme erişimi için uygun olan türlerden erişilebilir.<br /><br /> Aile veya derleme<br /> Yalnızca aile veya derleme erişimi için uygun olan türlerden erişilebilir.<br /><br /> public<br /> Herhangi bir türden erişilebilir.|  
|son|Yöntemler, Özellikler ve olaylar|Sanal yöntem türetilmiş bir türde geçersiz kılınamaz.|  
|yalnızca başlatma|Alanlar|Değer yalnızca başlatılabilir ve başlatma sonrasında yazılamaz.|  
|örnek|Alanlar, Yöntemler, Özellikler ve olaylar|Bir üye `static` (c# ve c++), `Shared` (Visual Basic), `virtual` (c# ve c++) veya (Visual Basic) olarak işaretli değilse, `Overridable` bir örnek üyesidir (örnek anahtar sözcüğü yoktur). Bellekte bu tür üyelerin, onu kullanan nesneler olduğu gibi birçok kopyası olacaktır.|  
|değişmez değer|Alanlar|Alana atanan değer, yerleşik bir değer türünün derleme zamanında bilinen sabit bir değerdir. Değişmez değer alanları bazen sabitler olarak adlandırılır.|  
|newslot veya override|Tümü|Üyenin aynı imzaya sahip devralınmış üyelerle nasıl etkileşime gireceğini tanımlar:<br /><br /> NewSlot<br /> Aynı imzaya sahip devralınmış üyeleri gizler.<br /><br /> override<br /> Devralınan bir sanal yöntemin tanımını değiştirir.<br /><br /> Varsayılan, gazetik ' dır.|  
|static|Alanlar, Yöntemler, Özellikler ve olaylar|Üye, türünün belirli bir örneğine değil, tanımlandığı türe aittir; üye, türün bir örneği oluşturulmasa bile vardır ve bu, türün tüm örnekleri arasında paylaşılır.|  
|virtual|Yöntemler, Özellikler ve olaylar|Yöntemi türetilmiş bir tür tarafından uygulanabilir ve statik veya dinamik olarak çağrılabilir. Dinamik çağırma kullanılırsa, çağrı çalışma zamanında (derleme zamanında bilinen tür yerine) yapan örnek türü, yöntemin hangi uygulamanın çağrılacağını belirler. Statik olarak sanal bir yöntemi çağırmak için, değişkenin istenen sürümünü kullanan bir türe dönüştürülmesi gerekebilir.|  
  
### <a name="overloading"></a>Aşırı Yükleme  
 Her tür üyesinin benzersiz bir imzası vardır. Yöntem imzaları yöntem adından ve bir parametre listesinden oluşur (yöntemin bağımsız değişkenlerinin sırası ve türleri). Aynı ada sahip birden çok yöntem, imzaları farklı olduğu sürece bir tür içinde tanımlanabilir. Aynı ada sahip iki veya daha fazla yöntem tanımlandığında, yöntemi aşırı yüklenmiş olarak kabul edilir. Örneğin, ' de, <xref:System.Char?displayProperty=nameWithType> <xref:System.Char.IsDigit%2A> yöntemi aşırı yüklenmiştir. Bir yöntem bir alır <xref:System.Char> . Diğer yöntem bir ve kullanır <xref:System.String> <xref:System.Int32> .  
  
> [!NOTE]
> Dönüş türü yöntemin imzasının bir parçası olarak kabul edilmez. Diğer bir deyişle, yalnızca dönüş türüne göre farklılık gösteren yöntemler aşırı yüklenemez.  
  
### <a name="inherit-override-and-hide-members"></a>Üyeleri devralma, geçersiz kılma ve gizleme  
 Türetilmiş bir tür, temel türünün tüm üyelerini devralır; diğer bir deyişle, bu Üyeler üzerinde tanımlanır ve türetilmiş türü için kullanılabilir. Devralınan üyelerin davranışı veya nitelikleri iki şekilde değiştirilebilir:  
  
- Türetilmiş bir tür, aynı imzaya sahip yeni bir üye tanımlayarak, devralınan bir üyeyi gizleyebilir. Bu, daha önce genel bir üyeyi özel yapmak veya olarak işaretlenen devralınmış bir yöntem için yeni davranış tanımlamak üzere yapılabilir `final` .  
  
- Türetilmiş bir tür, devralınan sanal bir yöntemi geçersiz kılabilir. Geçersiz kılma yöntemi, derleme zamanında bilinen değişkenin türü yerine, çalışma zamanında çağrılacak yöntemin yeni bir tanımını sağlar. Bir yöntem sanal yöntemi yalnızca sanal yöntem olarak işaretli değilse `final` ve yeni yöntem en azından sanal yöntem olarak erişilebilir olduğunda geçersiz kılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET API tarayıcısı](../../../api/index.md)
- [Ortak Dil Çalışma Zamanı](../clr.md)
- [.NET 'te tür dönüştürme](type-conversion.md)
