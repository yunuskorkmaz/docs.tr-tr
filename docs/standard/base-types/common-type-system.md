---
title: Ortak Tür Sistemi
description: .NET'teki tür sistemi hakkında bilgi edinin.
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
ms.openlocfilehash: c574719da9b89b468b92b042e1f2b5b10fbe3c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400493"
---
# <a name="common-type-system"></a>Ortak Tür Sistemi
Ortak tür sistemi, türlerin ortak dil çalışma zamanında nasıl beyan ediliş, kullanıldığını ve yönetildiğini tanımlar ve aynı zamanda çalışma zamanının diller arası tümleştirme desteğinin önemli bir parçasıdır. Ortak tür sistemi aşağıdaki işlevleri gerçekleştirir:  
  
- Diller arası tümleştirmeyi, tür güvenliğini ve yüksek performanslı kod yürütmeyi etkinleştirmenize yardımcı olan bir çerçeve kurar.  
  
- Birçok programlama dilinin tam uygulanmasını destekleyen nesne yönelimli bir model sağlar.  
  
- Dillerin izlemesi gereken kuralları tanımlar ve bu da farklı dillerde yazılan nesnelerin birbirleriyle etkileşimkurmasını sağlamaya yardımcı olur.  
  
- Uygulama <xref:System.Boolean>geliştirmede kullanılan ilkel veri türlerini <xref:System.Byte> <xref:System.Char>(, , , <xref:System.Int32>, ve <xref:System.UInt64>) içeren bir kitaplık sağlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [.NET'teki türler](#types_in_the_net_framework)  
  
- [Tür Tanımları](#type_definitions)  
  
- [Tür Üyeleri](#type_members)  
  
- [Tip Üyelerin Özellikleri](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>
## <a name="types-in-net"></a>.NET'teki türler  
 .NET'teki tüm türler değer türleri veya başvuru türleridir.  
  
 Değer türleri, nesneleri nesnenin gerçek değeriyle temsil edilen veri türleridir. Bir değer türü örneği bir değişkene atanırsa, bu değişkene değerin yeni bir kopyası verilir.  
  
 Başvuru türleri, nesnelerin nesnenin gerçek değerine yapılan bir başvuruyla (işaretçiye benzer) temsil edildiği veri türleridir. Bir referans türü bir değişkene atanmışsa, bu değişken özgün değeri başvurur (işaret eder). Kopya yapılmaz.  
  
 .NET'teki ortak tür sistemi aşağıdaki beş tür kategorisini destekler:  
  
- [Sınıflar](#Classes)  
  
- [Yapılar](#Structures)  
  
- [Numaralandırma](#Enumerations)  
  
- [Arabirimler](#Interfaces)  
  
- [Temsilciler](#Delegates)  
  
<a name="Classes"></a>
### <a name="classes"></a>Sınıflar  
 Sınıf, doğrudan başka bir sınıftan türetilebilen ve dolaylı <xref:System.Object?displayProperty=nameWithType>olarak türetilmiş bir başvuru türüdür. Sınıf, bir nesnenin (sınıfın bir örneği olan) gerçekleştirebileceği işlemleri (yöntemler, olaylar veya özellikler) ve nesnenin içerdiği verileri (alanlar) tanımlar. Bir sınıf genellikle hem tanımı hem de uygulamayı içerse de (örneğin, uygulama olmadan yalnızca tanım içeren arabirimlerden farklı olarak), uygulaması olmayan bir veya daha fazla üyesi olabilir.  
  
 Aşağıdaki tabloda, bir sınıfın sahip olabileceği bazı özellikler açıklanmaktadır. Çalışma saatini destekleyen her dil, bir sınıf veya sınıf üyesinin bu özelliklerden birine veya daha fazlasına sahip olduğunu belirtmek için bir yol sağlar. Ancak, .NET'i hedefleyen tek tek programlama dilleri tüm bu özellikleri kullanıma sunmayabilir.  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|sealed|Başka bir sınıfın bu türden türetilemeyeceğini belirtir.|  
|uygulamalar|Sınıfın arabirim üyelerinin uygulamalarını sağlayarak bir veya daha fazla arabirim kullandığını gösterir.|  
|abstract|Sınıfın anlık olarak alınamayacağını gösterir. Kullanmak için, başka bir sınıf türetmek gerekir.|  
|Devralır|Sınıfın örneklerinin taban sınıfın belirtildiği her yerde kullanılabileceğini gösterir. Taban sınıftan devralan türetilmiş bir sınıf, taban sınıf tarafından sağlanan tüm ortak üyelerin uygulanmasını kullanabilir veya türemiş sınıf, kendi uygulamasıyla ortak üyelerin uygulanmasını geçersiz kılabilir.|  
|ihraç edilen veya ihraç edilmeyecek|Bir sınıfın tanımlandığı derlemedışında görünür olup olmadığını gösterir. Bu özellik yalnızca üst düzey sınıflar için geçerlidir, iç içe geçen sınıflar için geçerli değildir.|  
  
> [!NOTE]
> Bir sınıf bir üst sınıf veya yapı da iç içe olabilir. İç içe sınıfların da üye özellikleri vardır. Daha fazla bilgi için İç [Içe Türler'e](#NestedTypes)bakın.  
  
 Uygulaması olmayan sınıf üyeleri soyut üyelerdir. Bir veya daha fazla soyut üyesi olan bir sınıfın kendisi soyuttur; yeni örnekleri oluşturulamaz. Çalışma saatini hedefleyen bazı diller, hiçbir üyesi soyut olmasa bile bir sınıfı soyut olarak işaretlemenize izin verebiliyor. Türemiş sınıfların uygun olduğunda devralabileceği veya geçersiz kabileceği temel bir işlevsellik kümesini kapsüllemek istediğinizde soyut bir sınıf kullanabilirsiniz. Soyut olmayan sınıflara somut sınıflar denir.  
  
 Bir sınıf herhangi bir sayıda arabirim uygulayabilir, ancak tüm sınıfların örtülü olarak devraldığı ek olarak <xref:System.Object?displayProperty=nameWithType>yalnızca bir taban sınıftan devralabilir. Tüm sınıfların, sınıfın yeni örneklerini ilk olarak gösteren en az bir oluşturucusu olmalıdır. Bir oluşturucuaçıkça tanımlamazsanız, derleyicilerin çoğu otomatik olarak parametresiz bir oluşturucu sağlar.  
  
<a name="Structures"></a>
### <a name="structures"></a>Yapılar  
 Yapı, dolaylı olarak türetilen <xref:System.ValueType?displayProperty=nameWithType>ve sırayla <xref:System.Object?displayProperty=nameWithType>türetilen bir değer türüdür. Bir yapı, bellek gereksinimleri küçük olan değerleri temsil etmek ve değerleri güçlü bir şekilde daktilan yöntemlere yan değer parametreleri olarak aktarmak için çok yararlıdır. .NET'te tüm ilkel<xref:System.Boolean>veri <xref:System.Byte> <xref:System.Char>türleri <xref:System.DateTime> <xref:System.Decimal>( <xref:System.Double> <xref:System.Int16>, <xref:System.Int32> <xref:System.Int64>, <xref:System.SByte> <xref:System.Single> <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, , , , , , ve ) yapı olarak tanımlanır.  
  
 Sınıflar gibi, yapılar da hem verileri (yapının alanları) hem de bu veriler üzerinde gerçekleştirilebilecek işlemleri (yapının yöntemleri) tanımlar. Bu, yapılarda <xref:System.Object?displayProperty=nameWithType> tanımlanan sanal yöntemler ve <xref:System.ValueType?displayProperty=nameWithType> değer türünde tanımlanan yöntemler de dahil olmak üzere yapıların yöntemlerini çağırabileceğiniz anlamına gelir. Başka bir deyişle, yapıların alanları, özellikleri ve olaylarının yanı sıra statik ve statik olmayan yöntemler de olabilir. Yapıların örneklerini oluşturabilir, bunları parametre olarak geçirebilir, yerel değişkenler olarak depolayabilir veya bunları başka bir değer türü veya başvuru türünden bir alanda depolayabilirsiniz. Yapılar arabirimleri de uygulayabilir.  
  
 Değer türleri de çeşitli açılardan sınıflardan farklıdır. İlk olarak, örtülü olarak <xref:System.ValueType?displayProperty=nameWithType>devralsalar da, doğrudan herhangi bir türden miras alamazlar. Benzer şekilde, tüm değer türleri mühürlü, bu da başka bir tür bunlardan türetilebilir anlamına gelir. Ayrıca yapıcılar gerektirmez.  
  
 Her değer türü için, ortak dil çalışma zamanı, değer türüyle aynı durum ve davranışa sahip bir sınıf olan karşılık gelen kutulu türü sağlar. Değer türüörneği, bir tür <xref:System.Object?displayProperty=nameWithType>parametresini kabul eden bir yönteme geçirildiğinde kutulanır. Denetim, bir değer türünü bir by-reference parametresi olarak kabul eden bir yöntem çağrısından döndüğünde kutulu olarak (diğer bir şekilde, bir sınıf örneğinden değer türüne dönüştürülür) çözülür. Bazı diller, kutulu tür gerektiğinde özel sözdizimi kullanmanızı gerektirir; diğerleri gerektiğinde kutulu türü otomatik olarak kullanır. Bir değer türü tanımladığınızda, hem kutulanmış hem de kutulanmamış türü tanımlarsınız.  
  
<a name="Enumerations"></a>
### <a name="enumerations"></a>Numaralandırmalar  
 Numaralandırma (enum), doğrudan devralan <xref:System.Enum?displayProperty=nameWithType> ve temel ilkel bir türün değerleri için alternatif adlar sağlayan bir değer türüdür. Numaralandırma türünde bir ad, yerleşik veya imzasız tamsayı türlerinden <xref:System.Byte>(, , <xref:System.Int32>veya <xref:System.UInt64>) ve bir alan kümesi olması gereken temel bir tür vardır. Alanlar, her biri sabiti temsil eden statik edebi alanlardır. Aynı değer birden çok alana atanabilir. Bu durumda, yansıma ve dize dönüştürme için birincil numaralandırma değeri olarak değerlerden birini işaretlemeniz gerekir.  
  
 Bir numaralandırma ya da tam tersi (çalışma süresi ne olursa olsun hiçbir döküm gerekli değildir) için temel türün bir değer atayabilirsiniz. Numaralandırma nın bir örneğini oluşturabilir ve numaralandırmanın temel türünde tanımlanan yöntemlerin yanı sıra, "metodasyon" yöntemlerini <xref:System.Enum?displayProperty=nameWithType>çağırabilirsiniz. Ancak, bazı diller, temel türün bir örneği gerektiğinde (veya tam tersi) bir parametre olarak numaralandırmayı geçirmenize izin vermeyebilir.  
  
 Aşağıdaki ek kısıtlamalar için geçerlidir:  
  
- Kendi yöntemlerini tanımlayamazlar.  
  
- Arabirimleri uygulayamazlar.  
  
- Özellikleri veya olayları tanımlayamazlar.  
  
- Bunlar, yalnızca genel bir tür içinde iç içe oldukları için genel olmadıkça genel olamazlar. Diğer bir yazı, numaralandırmanın kendi türü parametreleri olamaz.  
  
    > [!NOTE]
    > Visual Basic, C#ve C++ ile oluşturulan iç içe geçme türleri (numaralandırmalar dahil) tüm genel türleri çevreleyen tüm tür parametrelerini içerir ve bu nedenle kendi tür parametreleri olmasa bile geneldir. Daha fazla bilgi için başvuru başlığındaki <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> "İç Içe Türler" konusuna bakın.  
  
 Öznitelik, <xref:System.FlagsAttribute> bit alanı olarak adlandırılan özel bir numaralandırma türünü gösterir. Çalışma zamanının kendisi geleneksel sayılar ve bit alanları arasında ayrım yapmaz, ancak diliniz bunu yapabilir. Bu ayrım yapıldığında, bit bilge işleçleri bit alanlarında kullanılabilir, ancak adsız değerler oluşturmak için sayısallaştırmalarda kullanılamaz. Sonlandırmalar genellikle haftanın günleri, ülke veya bölge adları gibi benzersiz öğelerin listeleri için kullanılır. Bit alanları genellikle `Red And Big And Fast`, ..  
  
 Aşağıdaki örnek, hem bit alanlarının hem de geleneksel sayısallaştırmaların nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>
### <a name="interfaces"></a>Arabirimler  
 Arabirim, "yapabilirim" ilişkisini veya "sahip" ilişkisini belirten bir sözleşme tanımlar. Arabirimler <xref:System.IComparable> genellikle karşılaştırma ve sıralama (ve <xref:System.IComparable%601> arabirimler), eşitlik için sınama <xref:System.IEquatable%601> (arabirim) veya bir koleksiyondaki öğeleri (ve <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> arabirimleri) sıralama gibi işlevleri uygulamak için kullanılır. Arabirimler özellikleri, yöntemleri ve olaylar, hepsi soyut üye olabilir; diğer bir şey, arabirim üyeleri ve imzalarını tanımlasa da, her arabirim üyesinin işlevselliğini tanımlamak için arabirimi uygulayan türe bırakır. Bu, arabirim uygulayan herhangi bir sınıfın veya yapının arabirimde bildirilen soyut üyeler için tanım sağlaması gerektiği anlamına gelir. Arabirim, bir veya daha fazla arabirimi de uygulamak için herhangi bir uygulama sınıfı veya yapısı gerektirebilir.  
  
 Aşağıdaki kısıtlamalar arabirimler için geçerlidir:  
  
- Bir arabirim herhangi bir erişilebilirlik ile ilan edilebilir, ancak arabirim üyelerinin tüm ortak erişilebilirlik olmalıdır.  
  
- Arabirimler oluşturucuları tanımlayamaz.  
  
- Arabirimler alanları tanımlayamaz.  
  
- Arabirimler yalnızca örnek üyeleri tanımlayabilir. Statik üyeleri tanımlayamazlar.  
  
 Birden fazla arabirim aynı imzaya sahip bir üye bildirebilir ve bu üyeler ayrı uygulamalar olabilir, çünkü her dil, üye gerektiren arabirara bir uygulama eşleme için kurallar sağlamalıdır.  
  
<a name="Delegates"></a>
### <a name="delegates"></a>Temsilciler  
 Temsilciler, C++'daki işlev işaretçilerine benzer bir amaca hizmet eden başvuru türleridir. .NET'teki olay işleyicileri ve geri arama işlevleri için kullanılırlar. İşlev işaretçilerinaksine, temsilciler güvenli, doğrulanabilir ve yazı güvenlidir. Temsilci türü, uyumlu imzası olan herhangi bir örnek yöntemini veya statik yöntemi temsil edebilir.  
  
 Temsilci parametresi, dama doçrama parametresinin türü yöntem parametresinden daha kısıtlayıcı ise, bir temsilcinin parametresi ile uyumludur, çünkü bu, temsilciye geçirilen bir bağımsız değişkenin güvenli bir şekilde geçirilebebileceğini garanti eder. yöntemi.  
  
 Benzer şekilde, yöntemin dönüş türü temsilcinin dönüş türünden daha kısıtlayıcı ysa, bir temsilcinin dönüş türü yle uyumludur, çünkü bu yöntemin geri dönüş değerinin return to ve return to kamelyenin güvenli bir şekilde atılabilir temsilci türü.  
  
 Örneğin, bir <xref:System.Collections.IEnumerable> tür parametresi ve bir dönüş <xref:System.Object> türü türü olan bir temsilci, <xref:System.Object> bir tür parametresi ve tür <xref:System.Collections.IEnumerable>geri dönüş değeri olan bir yöntemi temsil edebilir. Daha fazla bilgi ve <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>örnek kod için bkz.  
  
 Bir temsilcinin temsil eder yöntemine bağlı olduğu söylenir. Yönteme bağlı olmanın yanı sıra, bir temsilci bir nesneye bağlanabilir. Nesne yöntemin ilk parametresini temsil eder ve temsilci her çağrıldığında yönteme geçirilir. Yöntem bir örnek yöntemi ise, bağlı nesne örtülü `this` parametre`Me` olarak geçirilir (Visual Basic'te); yöntem statikse, nesne yöntemin ilk resmi parametresi olarak geçirilir ve temsilci imzası kalan parametrelerle eşleşmelidir. Daha fazla bilgi ve <xref:System.Delegate?displayProperty=nameWithType>örnek kod için bkz.  
  
 Tüm temsilciler , <xref:System.MulticastDelegate?displayProperty=nameWithType>hangi devralır <xref:System.Delegate?displayProperty=nameWithType>. C#, Visual Basic ve C++ dilleri bu türlerden kalıtıma izin vermez. Bunun yerine, temsilci bildirmek için anahtar kelimeler sağlarlar.  
  
 Temsilciler devraldığından, <xref:System.MulticastDelegate>temsilcinin bir çağırma listesi vardır, bu da temsilcinin temsil ettiği ve temsilci çağrıldığında yürütülen yöntemlerin listesidir. Listedeki tüm yöntemler, temsilci çağrıldığında sağlanan bağımsız değişkenleri alır.  
  
> [!NOTE]
> İade değeri, temsilcinin iade türü olsa bile, çağırma listesinde birden fazla yöntemi olan bir temsilci için tanımlanmaz.  
  
 Geri arama yöntemleri gibi birçok durumda, bir temsilci yalnızca bir yöntemi temsil eder ve tek işlem yapmak için gereken temsilci oluşturmak ve çağırmak vardır.  
  
 Birden çok yöntemi temsil eden temsilciler için <xref:System.Delegate> .NET, bir temsilcinin çağırma <xref:System.MulticastDelegate> listesine <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> (yöntem) yöntem ekleme, bir yöntemi (yöntem) <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> kaldırma ve çağırma listesini <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> (yöntem) alma gibi işlemleri desteklemek için ve temsilci sınıflarının yöntemlerini sağlar.  
  
> [!NOTE]
> Bu diller olay işleyicileri eklemek ve kaldırmak için sözdizimi sağladığından, C#, C++ve Visual Basic'teki olay işleyicisi temsilcileri için bu yöntemleri kullanmanız gerekmez.  

<a name="type_definitions"></a>
## <a name="type-definitions"></a>Tür Tanımları  
 Bir tür tanımı aşağıdakileri içerir:  
  
- Türünde tanımlanan öznitelikler.  
  
- Türün erişilebilirliği (görünürlük).  
  
- Türün adı.  
  
- Türün taban türü.  
  
- Türü tarafından uygulanan tüm arabirimler.  
  
- Her türün üyesi için tanımlar.  
  
### <a name="attributes"></a>Öznitelikler  
 Öznitelikler, kullanıcı tanımlı ek meta veriler sağlar. En yaygın olarak, bir tür hakkında ek bilgileri derlemesinde depolamak veya bir tür üyesinin davranışını tasarım zamanı veya çalışma zamanı ortamında değiştirmek için kullanılır.  
  
 Öznitelikler, 'den <xref:System.Attribute?displayProperty=nameWithType>devralan sınıflardır. Özniteliklerin kullanımını destekleyen dillerin her birinin bir dil öğesine öznitelikleri uygulamak için kendi sözdizimi vardır. Öznitelikler hemen hemen her dil öğesine uygulanabilir; bir öznitelik uygulanabileceği belirli öğeler, bu <xref:System.AttributeUsageAttribute> öznitelik sınıfına uygulananlarla tanımlanır.  
  
### <a name="type-accessibility"></a>Tür Erişilebilirliği  
 Tüm türler, diğer türlerden erişilebilirliklerini yöneten bir değiştiriciye sahiptir. Aşağıdaki tabloda çalışma zamanı tarafından desteklenen tür erişilebilirlikleri açıklanmaktadır.  
  
|Erişilebilirlik|Açıklama|  
|-------------------|-----------------|  
|public|Türe tüm derlemeler erişebilir.|  
|derleme|Türe yalnızca kendi derlemesi içinden erişilebilir.|  
  
 İç içe geçen bir türün erişilebilirliği, hem üyenin bildirilen erişilebilirliği hem de hemen içeren türün erişilebilirlik etki alanı tarafından belirlenen erişilebilirlik etki alanına bağlıdır. Ancak, iç içe bir türün erişilebilirlik etki alanı, içeren türü aşamaz.  
  
 Bir `M` program `T` `P` içinde bir tür olarak bildirilen iç içe bir üyenin erişilebilirlik etki alanı aşağıdaki gibi tanımlanır (kendisi bir tür `M` olabilir belirterek):  
  
- Bildirilen erişilebilirlik `M` ise, `public`erişilebilirlik etki `M` `T`alanı.  
  
- Bildirilen erişilebilirlik `M` ise, `protected internal`erişilebilirlik etki alanı `M` program metni `T` `P` ve dışında `T` `P`bildirilen türetilen herhangi bir tür program metni ile erişilebilirlik etki alanı kesişimolduğunu.  
  
- Bildirilen `M` erişilebilirlik ise, `protected`erişilebilirlik etki alanı `M` program metni `T` `T` ve türetilen herhangi bir tür ile erişilebilirlik `T`etki alanı kesişimolduğunu.  
  
- Bildirilen `M` erişilebilirlik ise, `internal`erişilebilirlik etki alanı `M` program metni `T` ile erişilebilirlik etki alanının `P`kesişimolduğunu.  
  
- Bildirilen erişilebilirlik `M` ise, `private`erişilebilirlik etki alanı `M` `T`program metnidir.  
  
### <a name="type-names"></a>Tür Adları  
 Ortak tür sistemi adlara yalnızca iki kısıtlama uygular:  
  
- Tüm adlar Unicode (16 bit) karakter dizeleri olarak kodlanır.  
  
- Adların 0x0000 gömülü (16 bit) değerine sahip olması izin verilmez.  
  
 Ancak, çoğu dil tür adlarına ek kısıtlamalar uygular. Tüm karşılaştırmalar bayt bazında yapılır ve bu nedenle büyük/küçük harf duyarlı ve yerel-bağımsızdır.  
  
 Bir tür diğer modüllerden ve derlemelerden türlere başvurulsa da, bir tür bir .NET modülü içinde tam olarak tanımlanmalıdır. (Ancak derleyici desteğine bağlı olarak, birden çok kaynak kodu dosyasına ayrılabilir.) Tür adlarının yalnızca bir ad alanı içinde benzersiz olması gerekir. Bir türü tam olarak tanımlamak için, tür adının türün uygulanmasını içeren ad alanına göre nitelikli olması gerekir.  
  
### <a name="base-types-and-interfaces"></a>Temel Türler ve Arayüzler  
 Bir tür değerleri ve davranışları başka bir türden devralabilir. Ortak tür sistemi, türlerin birden fazla taban türünden devralmasına izin vermez.  
  
 Bir tür herhangi bir sayıda arabirim uygulayabilir. Bir arabirim uygulamak için, bir tür bu arabirimin tüm sanal üyeleri uygulamak gerekir. Sanal bir yöntem türetilmiş bir tür tarafından uygulanabilir ve statik veya dinamik olarak çağrılabilir.  

<a name="type_members"></a>
## <a name="type-members"></a>Tür Üyeleri  
 Çalışma zamanı, bir türün davranışını ve durumunu belirten türün üyelerini tanımlamanızı sağlar. Tür üyeleri şunlardır:  
  
- [Alanlar](#Fields)  
  
- [Özellikler](#Properties)  
  
- [Yöntemler](#Methods)  
  
- [Oluşturucular](#Constructors)  
  
- [Olaylar](#Events)  
  
- [İç içe türleri](#NestedTypes)  
  
<a name="Fields"></a>
### <a name="fields"></a>Alanlar  
 Bir alan, türün durumunun bir bölümünü açıklar ve içerir. Alanlar çalışma zamanı tarafından desteklenen herhangi bir türde olabilir. En yaygın olarak, `private` alanlar `protected`yalnızca sınıf içinden veya türetilmiş bir sınıftan erişilebilmeleri için alanlar veya , bunlardır. Bir alanın değeri türü dışından değiştirilebilirse, özellik kümesi erişimcisi genellikle kullanılır. Genel olarak açıkta kalan alanlar genellikle salt okunur ve iki tür olabilir:  
  
- Değeri tasarım zamanında atanan sabitler. Bunlar bir sınıfın statik üyeleridir, ancak `static` (Visual`Shared` Basic'te) anahtar sözcüğü kullanılarak tanımlanmaz.  
  
- Değerleri sınıf oluşturucusunda atanabilen salt okunur değişkenler.  
  
 Aşağıdaki örnekte, salt okunur alanların bu iki kullanımı gösteriş verilmiştir.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>
### <a name="properties"></a>Özellikler  
 Bir özellik, türün değerini veya durumunu adlandırır ve özelliğin değerini alma veya ayarlama yöntemlerini tanımlar. Özellikler ilkel türler, ilkel türler, kullanıcı tanımlı türler veya kullanıcı tanımlı türlerin koleksiyonları koleksiyonları olabilir. Özellikler genellikle bir türün ortak arabirimini türün gerçek gösteriminden bağımsız tutmak için kullanılır. Bu, özelliklerin sınıfta doğrudan depolanamayan değerleri yansıtmasını (örneğin, bir özellik hesaplanmış bir değer verdiğinde) veya değerler özel alanlara atanmadan önce doğrulama gerçekleştirmesini sağlar. Aşağıdaki örnek, ikinci deseni göstermektedir.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Özelliğin kendisini eklemenin yanı sıra, okunabilir bir özellik içeren bir tür için Microsoft `get_`ara dili (MSIL) bir *özellik adı* yöntemi içerir `set_`ve yazılabilir özellik içeren bir tür için MSIL bir *özellik adı* yöntemi içerir.  
  
<a name="Methods"></a>
### <a name="methods"></a>Yöntemler  
 Yöntem, türde kullanılabilen işlemleri açıklar. Bir yöntemin imzası, tüm parametrelerinizin ve iade değerinin izin verilebilen türlerini belirtir.  
  
 Çoğu yöntem yöntem çağrıları için gereken parametrelerin kesin sayısını tanımlasa da, bazı yöntemler değişken sayıda parametreyi destekler. Bu yöntemlerin son bildirilen parametresi <xref:System.ParamArrayAttribute> öznitelik ile işaretlenir. Dil derleyicileri genellikle C# ve `params` `ParamArray` Visual Basic gibi gereksiz açık kullanımı <xref:System.ParamArrayAttribute> sağlayan bir anahtar kelime sağlar.  
  
<a name="Constructors"></a>
### <a name="constructors"></a>Oluşturucular  
 Oluşturucu, bir sınıfın veya yapının yeni örneklerini oluşturan özel bir yöntemtürüdür. Diğer yöntemler gibi, bir oluşturucu parametreleriçerebilir; ancak, yapıcıların geri dönüş değeri yoktur (diğer bir şekilde, geri dönerler). `void`  
  
 Bir sınıfın kaynak kodu açıkça bir oluşturucu tanımlamıyorsa, derleyici parametresiz bir oluşturucu içerir. Ancak, bir sınıfın kaynak kodu yalnızca parametreli oluşturucuları tanımlıyorsa, Visual Basic ve C# derleyicileri parametresiz bir oluşturucu oluşturmaz.  
  
 Bir yapının kaynak kodu yapıcıları tanımlıyorsa, parametrelendirilmelidir; bir yapı parametresiz bir oluşturucu tanımlayamaz ve derleyiciler yapılar veya diğer değer türleri için parametresiz yapıcılar oluşturmaz. Tüm değer türlerinin örtülü parametresiz bir oluşturucusu vardır. Bu oluşturucu ortak dil çalışma zamanı tarafından uygulanır ve yapının tüm alanlarını varsayılan değerlerine başladayleştirir.  
  
<a name="Events"></a>
### <a name="events"></a>Olaylar  
 Olay, yanıtlanabilecek bir olayı tanımlar ve olaya abone olma, aboneliği kaldırma ve olayı yükseltme yöntemlerini tanımlar. Olaylar genellikle diğer durum değişiklikleri türlerini bilgilendirmek için kullanılır. Daha fazla bilgi için [Etkinlikler'e](../../../docs/standard/events/index.md)bakın.  
  
<a name="NestedTypes"></a>
### <a name="nested-types"></a>İç içe Geçmiş Türler  
 İç içe geçen tür, başka bir türe üye olan bir türdür. İç içe ki türler, içerme türlerine sıkıca bağlanmalıdır ve genel amaçlı bir tür olarak yararlı olmamalıdır. İç içe geçme türü, iç içe geçme türü örnekleri kullandığında ve oluşturduğunda ve iç içe alınan türün kullanımı ortak üyelerde açıklanmadığında yararlıdır.  
  
 İç içe geçme türleri bazı geliştiriciler için kafa karıştırıcıdır ve görünürlük için zorlayıcı bir neden olmadığı sürece genel olarak görünmemelidir. İyi tasarlanmış bir kitaplıkta, geliştiriciler nesneleri anlık olarak kullanmak veya değişkenleri bildirmek için iç içe geçme türlerini nadiren kullanmak zorunda olmalıdır.  

<a name="characteristics_of_type_members"></a>
## <a name="characteristics-of-type-members"></a>Tip Üyelerin Özellikleri  
 Ortak tip sistemi, tür üyelerinin çeşitli özelliklere sahip olmasını sağlar; ancak, dillertüm bu özellikleri desteklemek için gerekli değildir. Aşağıdaki tabloda üye özellikleri açıklanmaktadır.  
  
|Özellik|Başvurabilir|Açıklama|  
|--------------------|------------------|-----------------|  
|abstract|Yöntemler, özellikler ve olaylar|Tür, yöntemin uygulanmasını sağlamaz. Soyut yöntemleri devralan veya uygulayan türler, yöntem için bir uygulama sağlamalıdır. Tek istisna, türemiş türün kendisi soyut bir tür olduğunda. Tüm soyut yöntemler sanaldır.|  
|özel, aile, meclis, aile ve meclis, aile veya meclis veya kamu|Tümü|Üyenin erişilebilirliğini tanımlar:<br /><br /> private<br /> Yalnızca üyeyle aynı türden veya iç içe geçen bir tür içinden erişilebilir.<br /><br /> aile<br /> Üyeyle aynı türde ve ondan devralan türlerden erişilebilir.<br /><br /> derleme<br /> Yalnızca türün tanımlandığı derlemede erişilebilir.<br /><br /> aile ve montaj<br /> Yalnızca hem aile hem de derleme erişimi için uygun türlerden erişilebilir.<br /><br /> aile veya montaj<br /> Yalnızca aile veya derleme erişimi için uygun türlerden erişilebilir.<br /><br /> public<br /> Herhangi bir türden erişilebilir.|  
|son|Yöntemler, özellikler ve olaylar|Sanal yöntem türetilmiş bir türde geçersiz kılınamaz.|  
|yalnızca başlatma|Alanlar|Değer yalnızca başharfe yazılabilir ve başlatmadan sonra yazılamaz.|  
|örnek|Alanlar, yöntemler, özellikler ve olaylar|Bir üye (C# `static` ve C++), `Shared` (Visual Basic), `virtual` (C# ve `Overridable` C++) veya (Visual Basic) olarak işaretlenmemişse, bir örnek üyedir (örnek anahtar sözcük yoktur). Bellekte bu tür üyelerin kopyaları kadar çok kopya olacak, onu kullanan nesneler olarak.|  
|değişmez değer|Alanlar|Alana atanan değer, yerleşik bir değer türünün derleme zamanında bilinen sabit bir değerdir. Edebi alanlar bazen sabitler olarak adlandırılır.|  
|haber lotu veya geçersiz kılma|Tümü|Üyenin aynı imzaya sahip devralınan üyelerle nasıl etkileşimde olduğunu tanımlar:<br /><br /> Newslot<br /> Aynı imzaya sahip devralınan üyeleri gizler.<br /><br /> override<br /> Devralınan sanal yöntemin tanımını değiştirir.<br /><br /> Varsayılan değer haber alanıdır.|  
|static|Alanlar, yöntemler, özellikler ve olaylar|Üye, türün belirli bir örneğine değil, üzerinde tanımlandığı türe aittir; türbir örneği oluşturulmasa bile üye vardır ve türün tüm örnekleri arasında paylaşılır.|  
|virtual|Yöntemler, özellikler ve olaylar|Yöntem türetilmiş bir tür tarafından uygulanabilir ve statik veya dinamik olarak çağrılabilir. Dinamik çağırma kullanılırsa, aramayı çalışma zamanında yapan örneğin türü (derleme zamanında bilinen tür yerine) yöntemin hangi uygulamanın çağrıldığını belirler. Sanal bir yöntemi statik olarak çağırmak için, değişkenin yöntemin istenen sürümünü kullanan bir türe atılması gerekebilir.|  
  
### <a name="overloading"></a>Aşırı Yükleme  
 Her tür üyenin benzersiz bir imzası vardır. Yöntem imzaları yöntem adı ve parametre listesinden (yöntemin bağımsız değişkenlerinin sırası ve türleri) oluşur. İmzaları farklı olduğu sürece, aynı ada sahip birden çok yöntem bir tür içinde tanımlanabilir. Aynı ada sahip iki veya daha fazla yöntem tanımlandığında, yöntemin aşırı yüklendiği söylenir. Örneğin, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> yöntem aşırı yüklenir. Bir yöntem <xref:System.Char>alır . Diğer yöntem bir <xref:System.String> ve <xref:System.Int32>bir alır .  
  
> [!NOTE]
> İade türü, yöntemin imzasının bir parçası olarak kabul edilmez. Diğer bir arada, yöntemler yalnızca dönüş türüne göre farklılık gösterirse aşırı yüklenemez.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Üyeleri Devralma, Geçersiz Kılma ve Gizleme  
 Türetilen tür, temel türünün tüm üyelerini devralır; diğer bir şey, bu üyeler türemiş türde tanımlanır ve bu türiçin kullanılabilir. Devralınan üyelerin davranışları veya nitelikleri iki şekilde değiştirilebilir:  
  
- Türetilen bir tür, aynı imzayla yeni bir üye tanımlayarak devralınan bir üyeyi gizleyebilir. Bu, daha önce genel bir üyeyi özel yapmak veya devralınan bir yöntem `final`için yeni davranış tanımlamak için yapılabilir.  
  
- Türetilen bir tür, devralınan bir sanal yöntemi geçersiz kılabilir. Geçersiz kılma yöntemi, derleme zamanında bilinen değişkenin türüyerine çalışma zamanındaki değerin türüne göre çağrılacak yöntemin yeni bir tanımını sağlar. Bir yöntem, sanal yöntem olarak `final` işaretlenmemişse ve yeni yöntem en az sanal yöntem kadar erişilebilirse, sanal bir yöntemi geçersiz kılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET API Tarayıcısı](/dotnet/api)
- [Ortak Dil Çalışma Zamanı](../../../docs/standard/clr.md)
- [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)
