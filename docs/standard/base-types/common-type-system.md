---
title: Ortak Tür Sistemi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c8db725e25fe441c875a25cba97eb2090d4c071
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036291"
---
# <a name="common-type-system"></a>Ortak Tür Sistemi
Ortak tür sistemi nasıl türleri bildirilen kullanılan ve ortak dil çalışma zamanı'nda yönetilen tanımlar ve çalışma zamanının diller arası tümleştirme desteğinin önemli bir bölümü de olan. Ortak tür sistemi şu işlevleri gerçekleştirir:  
  
-   Etkinleştirme diller arası tümleştirme, tür güvenliği ve yüksek performanslı kod yürütmesine yardımcı olan bir çerçeve oluşturur.  
  
-   Birçok programlama dilinin tam uygulamasını destekleyen bir nesne odaklı bir model sağlar.  
  
-   Dillerin izlemesi gereken, farklı dillerde yazılan nesneler birbiriyle etkileşim kurabilir yardımcı olun kuralları tanımlar.  
  
-   Temel veri türlerini içeren bir kitaplık sağlar (gibi <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.Int32>, ve <xref:System.UInt64>) uygulama geliştirmesinde kullanılan.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [. NET'te türleri](#types_in_the_net_framework)  
  
-   [Tür Tanımları](#type_definitions)  
  
-   [Tür Üyeleri](#type_members)  
  
-   [Tür üye özellikleri](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>. NET'te türleri  
 . NET'te tüm türleri ötekisi değer türü veya başvuru türleri.  
  
 Değer türleri, nesneleri nesnenin gerçek değeri tarafından temsil edilen veri türleridir. Bir değer türü örneği bir değişkene atanırsa, bu değişkene değerin yeni bir kopyasını verilir.  
  
 Başvuru türleri, nesneleri, nesnenin gerçek değerine başvuru (işaretçiyle benzer) tarafından temsil edilen veri türleridir. Bir başvuru türü bir değişkene atanırsa, bu değişken (noktalarına) başvuruyor. özgün değer. Bir kopya yapılmadı.  
  
 . NET'te ortak tür sistemi, türlerin şu beş kategorisini destekler:  
  
-   [Sınıflar](#Classes)  
  
-   [Yapılar](#Structures)  
  
-   [Sabit Listeleri](#Enumerations)  
  
-   [Arabirimler](#Interfaces)  
  
-   [Temsilciler](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Sınıflar  
 Bir başvuru türü, türetilmiş başka bir sınıftan doğrudan ve dolaylı olarak sınıfından türetilen sınıftır <xref:System.Object?displayProperty=nameWithType>. Sınıf (sınıfının bir örneği olan) bir nesne (yöntemler, olaylar veya Özellikler) gerçekleştirebileceğiniz işlemler tanımlar ve nesneyi (alanlar) içeren veriler. Bir sınıfı tanım ve uygulamayı (farklı uygulama olmadan yalnızca tanım içeren arabirimleri, örneğin,), genellikle kapsamasına rağmen uygulaması olmayan bir veya daha fazla üye olabilir.  
  
 Aşağıdaki tabloda bir sınıfın sahip olabileceği özellikleri bazılarını açıklar. Çalışma zamanını destekleyen her dil bir sınıf belirtmek için bir yol sağlar veya sınıf üyesi bir veya daha fazla şu özelliklere sahiptir. Ancak, bireysel programlama dilleri hedefleyen .NET tüm bu özellikleri kullanıma sunamazsınız.  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|korumalı|Başka bir sınıfın bu türden türetilemeyeceğini belirtir.|  
|uygulamalar|Arabirim üyelerinin uygulamalarını sağlayarak sınıfın bir veya daha fazla arabirim kullandığını gösterir.|  
|abstract|Sınıfın oluşturulamadığını gösterir. Kullanmak için başka bir sınıf türetmeniz gerekir.|  
|Devralan|Sınıf örneklerinin taban sınıfın belirtildiği her yerde kullanılabileceğini gösterir. Taban sınıfından devralan türetilmiş bir sınıf taban sınıfı tarafından sağlanan herhangi bir genel üyeler uygulamasını kullanabilir veya türetilmiş sınıf kendi uygulaması ile genel üyeler uygulamasını geçersiz kılabilir.|  
|dışa aktarılan veya aktarılmayan|Bir sınıf içinde tanımlandığı derlemenin dışında görünür olup olmadığını gösterir. Bu özellik yalnızca üst düzey sınıflar ve iç içe geçmiş sınıflar için geçerlidir.|  
  
> [!NOTE]
>  Bir sınıf, bir üst sınıfta veya yapıda da yuvalanabilir. İç içe sınıflarda üye özellikleri de vardır. Daha fazla bilgi için [iç içe türler](#NestedTypes).  
  
 Hiçbir uygulamaya sahip olmayan sınıf üyeleri soyut üyelerdir. Bir veya daha fazla soyut üye olan bir sınıfı kendisi, soyut; Yeni örnekleri oluşturulamaz. Çalışma zamanını hedefleyen bazı diller bile üyelerinin hiçbiri soyut bir sınıfı soyut olarak işaretlemenize olanak tanır. Temel bir yalıtılacak istediğinizde soyut bir sınıfı kullanabilirsiniz kümesi türetilmiş sınıfların devralabileceği veya uygun olduğunda geçersiz. Soyut olmayan sınıflar somut sınıf olarak adlandırılır.  
  
 Bir sınıf herhangi bir sayıda arabirim uygulayabilir, ancak ek olarak yalnızca bir temel sınıftan devralabilir <xref:System.Object?displayProperty=nameWithType>, öğesinden, tüm sınıflar örtük olarak devralır. Tüm sınıflar, sınıfın yeni örneklerini başlatan en az bir oluşturucusu olmalıdır. Açıkça bir oluşturucu tanımlamazsanız, çoğu derleyici otomatik olarak varsayılan (parametresiz) bir oluşturucu sağlar.  
  
<a name="Structures"></a>   
### <a name="structures"></a>Yapılar  
 Den örtük olarak bir değer türü yapısıdır <xref:System.ValueType?displayProperty=nameWithType>, hangi sırayla türetilmiş olan <xref:System.Object?displayProperty=nameWithType>. Bir yapı, bellek gereksinimleri küçük değerleri temsil eden ve değerleri kesin yazılmış parametrelere sahip yöntemlere yan değer parametreleriyle geçirmek için çok kullanışlıdır. . NET'te, tüm basit veri türleri (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, ve <xref:System.UInt64>) yapı olarak tanımlanır.  
  
 Sınıflar gibi yapılar, hem verileri (yapının alanları) hem de bu verileri (yapının yöntemleri) gerçekleştirilebilecek işlemleri tanımlayın. Bu yapıları üzerinde tanımlanan sanal yöntemler de dahil olmak üzere, yöntemler çağırabileceğiniz anlamına gelir <xref:System.Object?displayProperty=nameWithType> ve <xref:System.ValueType?displayProperty=nameWithType> sınıfları ve değer türünde tanımlanan herhangi bir yöntem. Diğer bir deyişle, yapıların alanları, özellikleri ve olayları yanı sıra statik ve statik olmayan yöntemleri olabilir. Yapıların örneklerini oluşturabilir, parametreler olarak geçebilir, bunları yerel değişkenler olarak saklayabilir veya başka bir değer türünün bir alana depolamaya veya başvuru türü. Yapılar, arabirimler de uygulayabilen.  
  
 Değer türleri, aynı zamanda birçok bakımdan sınıflardan farklılık gösterir. İlk olarak, örtük olarak devralındığı rağmen <xref:System.ValueType?displayProperty=nameWithType>, her türden doğrudan devralamazlar. Benzer şekilde, diğer hiçbir tür bunlardan türetilemez, yani tüm değer türleri mühürlüdür. Bunlar Oluşturucu ayrıca gerektirmez.  
  
 Her bir değer türü için ortak dil çalışma zamanı aynı durum ve davranışlara değer türü olan bir sınıfı, karşılık gelen bir Kutulu türü sağlar. Türünde bir parametre kabul eden bir yönteme geçildiğinde bir değer türü örneği kutulanmaz <xref:System.Object?displayProperty=nameWithType>. Kutulanır (diğer bir deyişle, bir sınıfın bir örneğinden bir değer türü örneğine geri dönüştürülür) denetim döndürdüğünde başvuru ile parametre olarak bir değer türü kabul eden yöntem çağrısından. Bazı diller, Kutulu tür gerektiğinde özel sözdizim kullanmanızı gerektirirken; gerektiğinde diğer otomatik olarak Kutulu türü kullanır. Bir değer türü tanımladığınızda kutulanmış ve kutulanmamış türü tanımlarsınız.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Numaralandırmalar  
 Bir sabit listesi (enum) doğrudan devralan bir değer türüdür <xref:System.Enum?displayProperty=nameWithType> ve kaynakları adları temel alınan bir basit türü değerleri için alternatif. Bir numaralandırma türü, yerleşik imzalı veya imzasız tamsayı türlerinin biri olması gereken bir temel türü olan bir ada sahip (gibi <xref:System.Byte>, <xref:System.Int32>, veya <xref:System.UInt64>) ve alanları kümesi. Alanların her biri bir sabiti temsil eden statik değişmez değerli alanlardır. Aynı değer birden fazla alana atanabilir. Bu durumda, yansıma ve dize dönüştürme için birincil numaralandırma değeri olarak değerlerden birini işaretlemelisiniz.  
  
 (Hiçbir dönüştürme çalışma zamanı tarafından gerekli değildir) temel alınan türü bir sabit listesi ve bir değer atayabilirsiniz. Bir numaralandırma örneği oluşturun ve yöntemlerini çağırmak <xref:System.Enum?displayProperty=nameWithType>sabit listesinin temel alınan türü üzerinde tanımlanan yöntemlerini de gibi. Ancak, bazı diller temeldeki türün bir örneği gerekli olduğunda bir numaralandırma parametre olarak geçirmenize izin vermeyebilir (veya tersi).  
  
 Aşağıdaki ek kısıtlamalar sabit listelere uygulanır:  
  
-   Kendi yöntemlerini tanımlayamazlar.  
  
-   Arabirimleri uygulayamazlar.  
  
-   Özellikleri veya etkinlikleri tanımlayamazlar.  
  
-   Genel tür içinde yalnızca içe nedeniyle genel olmadıkları sürece genel olamazlar. Diğer bir deyişle, bir numaralandırma kendi Tür parametrelerine sahip olamaz.  
  
    > [!NOTE]
    >  Visual Basic, C# ve C++ ile oluşturulan iç içe türleri (numaralandırmalar dahil) tüm kapsayan genel türlerin tür parametrelerini içerir ve bu nedenle, kendi tür parametreleri yoksa bile geneldir. Daha fazla bilgi için bkz: "İç içe türler" <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> başvuru konusu.  
  
 <xref:System.FlagsAttribute> Özniteliği bir bit alanı adı verilen sabit listesi özel bir tür gösterir. Çalışma zamanının kendisi geleneksel numaralandırmalar ve bit alanları arasında farklılık gözetmez, ancak diliniz bunu yapabilir. Bu ayrım yapıldığında, Bitsel işleçler bit alanlarında, numaralandırmalarda, isimsiz değerler oluşturmak için kullanılabilir. Numaralandırmalar genellikle benzersiz öğeleri listelerken gün haftanın, ülke veya bölge adlarının bir listesi için kullanılır ve benzeri. Bit alanları genellikle kalitelerini veya birlikte gibi oluşabilecek miktarlar listesi için kullanılan `Red And Big And Fast`.  
  
 Aşağıdaki örnek, hem bit alanlarının hem de Geleneksel Sabit listelerin kullanmayı gösterir.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Arabirimler  
 Bir arabirim bir "yapılabilir" ilişkisi belirten bir sözleşmeyi tanımlar veya bir "olan bir" ilişkisi. Arabirimleri genellikle sıralama ve karşılaştırma gibi işlevselliği uygulamak için kullanılır ( <xref:System.IComparable> ve <xref:System.IComparable%601> arabirimleri), eşitlik için sınamak ( <xref:System.IEquatable%601> arabirimi), veya bir koleksiyondaki öğelerin numaralandırma ( <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601> arabirimleri). Arabirimler, özellikleri, yöntemleri ve olayları, bunların tümü soyut üyeleridir olabilir; arabirim üyeleri ve bunların imzalarını tanımlasa da diğer bir deyişle, bu, her bir arabirim üyesinin işlevselliğini tanımlamayı arabirimi uygulayan türe bırakır. Başka bir deyişle, herhangi bir sınıf veya bir arabirimi uygulayan yapının arabirimde bildirilen soyut üyelerin tanımlarını sağlaması gerekir. Arabirim uygulama sınıfı veya yapısına bir veya daha fazla diğer arabirimleri de uygulamak gerekebilir.  
  
 Aşağıdaki ek kısıtlamalar arayüzlere uygulanır:  
  
-   Bir arabirim herhangi bir erişilebilirlikle bildirilebilir, ancak arabirim üyeleri genel erişilebilirliğin tamamına sahip olmalıdır.  
  
-   Arabirimler oluşturucuları tanımlayamaz.  
  
-   Arabirimler alanları tanımlayamaz.  
  
-   Arabirimler yalnızca örnek üyelerini tanımlayabilir. Statik üyeleri tanımlayamazlar.  
  
 Daha fazla arabirim aynı imzaya sahip bir üye bildirebilirsiniz olduğundan, bir uygulama, üyeyi gerektiren arabirime eşlemek için her dil kuralları sağlaması gerekir ve bu üyeler farklı uygulamalara sahip olabilir.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Temsilciler  
 Temsilciler C++'taki işlev işaretçilerine benzer bir amaca hizmet eden başvuru türleridir. Olay işleyicileri ve. NET'te geri çağırma işlevleri için kullanılırlar. İşlev işaretçilerinden farklı olarak temsilciler güvenli, doğrulanabilir ve tür kullanımı. Bir temsilci türü herhangi bir örnek yöntemi veya uyumlu bir imzaya sahip statik yöntemi temsil edebilir.  
  
 Çünkü bu temsilciye iletilen bir bağımsız değişken için güvenli bir şekilde geçirilebilir garanti eder. temsilci parametresinin türünü yöntem parametre türünden daha kısıtlayıcı bir parametre bir temsilcinin bir yöntemin karşılık gelen parametre ile uyumludur yöntem.  
  
 Bu yöntemin dönüş değerini dönüş türü için güvenli bir şekilde dönüştürülebilen gönderilmesini sağladığından yöntemin dönüş türünü temsilcinin dönüş türünden daha kısıtlayıcı benzer şekilde, bir temsilcinin dönüş türü bir yöntemin dönüş türüyle uyumludur metot temsilcisinin e.  
  
 Örneğin, türünde bir parametreye sahip. temsilci <xref:System.Collections.IEnumerable> ve dönüş türü <xref:System.Object> türünde bir parametreye sahip bir yöntemi temsil edebilir <xref:System.Object> ve bir dönüş değeri <xref:System.Collections.IEnumerable>. Daha fazla bilgi ve örnek kod için bkz. <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>.  
  
 Temsilcinin temsil ettiği yönteme bağlı bildirilir. Yöntemine bağlanan ek olarak, bir temsilci bir nesneye bağlı olabilir. Nesne yöntemin ilk parametresini temsil eder ve temsilci her çağrıldığında yönteme iletilir. Yöntemi bir örnek yöntem ise, ilişkili nesne örtülü geçirilen `this` parametre (`Me` Visual Basic'te); yöntem statik ise nesne yöntemin ilk resmi parametresi geçirilir ve temsilci imzası eşleşmelidir kalan parametreler. Daha fazla bilgi ve örnek kod için bkz. <xref:System.Delegate?displayProperty=nameWithType>.  
  
 Tüm temsilciler devralınacak <xref:System.MulticastDelegate?displayProperty=nameWithType>, işlevinden devralan <xref:System.Delegate?displayProperty=nameWithType>. C#, Visual Basic ve C++ dilleri devralma bu türlerden izin vermez. Bunun yerine, temsilciler bildirmek için anahtar sağlar.  
  
 Temsilciler devralınacak çünkü <xref:System.MulticastDelegate>, temsilci temsilcinin gösterdiği ve temsilci çağrıldığında yürütülen yöntemlerin bir listesi olan çağrı listesine sahiptir. Temsilci çağrıldığında sağlanan bağımsız değişkenler listedeki tüm yöntemleri alır.  
  
> [!NOTE]
>  Dönüş değeri temsilcinin dönüş türüne sahip olsa bile, çağırma listesinde birden fazla yöntem olan bir temsilci için tanımlanmamış.  
  
 Çoğu durumda, geri çağırma yöntemleri ile bir temsilcinin gösterdiği gibi yalnızca bir yöntem ve tek yapmanız gereken eylemler temsilci oluşturur ve onu çağırır.  
  
 Birden çok yöntemi temsil eden temsilciler .NET yöntemlerini sağlar. <xref:System.Delegate> ve <xref:System.MulticastDelegate> temsilci temsilcinin çağırma listesine yöntem ekleme gibi işlemleri desteklemek için sınıflar ( <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> yöntemi), bir yöntem ( kaldırılıyor<xref:System.Delegate.Remove%2A?displayProperty=nameWithType> yöntemi) ve çağırma listesi almak ( <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> yöntemi).  
  
> [!NOTE]
>  Bu diller için ekleme ve kaldırma olay işleyicileri söz dizimi sağladığından C#, C++ ve Visual Basic olay işleyicisi temsilcileri için bu yöntemleri kullanmak gerekli değildir.  
  
 
  
<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Tür tanımları  
 Bir tür tanımı aşağıdakileri içerir:  
  
-   Tür üzerinde tanımlı herhangi bir öznitelik.  
  
-   Türün erişilebilirliği (görünürlük).  
  
-   Türün adı.  
  
-   Türün temel türü.  
  
-   Tür tarafından uygulanan her arabirim.  
  
-   Her türün üyeleri için tanımlar.  
  
### <a name="attributes"></a>Öznitelikler  
 Öznitelikler kullanıcı tanımlı ek meta veriler sağlar. En yaygın olarak, bunlar, derlemesi içinde bir türle ilgili ek bilgi depolamak veya tasarım zamanı veya çalışma zamanı ortamı ya da bir tür üye davranışını değiştirmek için kullanılır.  
  
 Öznitelikleri devralınan sınıflar olduğu <xref:System.Attribute?displayProperty=nameWithType>. Öznitelikleri her kullanımını destekleyen dillerin bir dil öğesi için öznitelikleri uygulamak üzere kendi sözdizimi vardır. Öznitelikler, neredeyse her dil öğesine uygulanabilir; bir özniteliğin uygulanabileceği belirli öğeler tarafından tanımlanan <xref:System.AttributeUsageAttribute> o öznitelik sınıfına uygulanır.  
  
### <a name="type-accessibility"></a>Tür erişilebilirliği  
 Tüm türlerin diğer türlerden kendi erişilebilirlik yöneten bir değiştiricisi vardır. Aşağıdaki tabloda, çalışma zamanı tarafından desteklenen tür erişilebilirlikleri açıklanmıştır.  
  
|Erişilebilirlik|Açıklama|  
|-------------------|-----------------|  
|public|Tüm derlemeler türü erişilebilir.|  
|derleme|Yalnızca derlemesi içinden erişilebilir türüdür.|  
  
 İç içe türün erişilebilirliği, üyenin bildirilen erişilebilirliği ve hemen içeren türün erişilebilirlik etki alanı tarafından belirlenir onun erişilebilirlik etki alanı bağlıdır. Ancak, iç içe türün erişilebilirlik etki alanı, kapsayan türdeki aşamaz.  
  
 Erişilebilirlik etki alanı iç içe üyenin `M` bir türde bildirilen `T` bir programın `P` şu şekilde tanımlanır (dikkate alınarak `M` kendisi bir tür olabilir):  
  
-   Varsa öğesinin bildirilen erişilebilirliği `M` olduğu `public`, Erişilebilirlik etki alanı `M` erişilebilirlik etki alanıdır `T`.  
  
-   Varsa öğesinin bildirilen erişilebilirliği `M` olduğu `protected internal`, Erişilebilirlik etki alanı `M` erişilebilirlik etki alanının kesişimidir `T` öğesinin program metni ile `P` ve türetilen her türlü program metni `T` dışında bildirilen `P`.  
  
-   Varsa öğesinin bildirilen erişilebilirliği `M` olduğu `protected`, Erişilebilirlik etki alanı `M` erişilebilirlik etki alanının kesişimidir `T` öğesinin program metni ile `T` ve türetilenhertür`T`.  
  
-   Varsa öğesinin bildirilen erişilebilirliği `M` olduğu `internal`, Erişilebilirlik etki alanı `M` erişilebilirlik etki alanının kesişimidir `T` öğesinin program metni ile `P`.  
  
-   Varsa öğesinin bildirilen erişilebilirliği `M` olduğu `private`, Erişilebilirlik etki alanı `M` öğesinin program metnidir `T`.  
  
### <a name="type-names"></a>Tür Adları  
 Ortak tür sistemi, adlar üzerinde yalnızca iki kısıtlama uygular:  
  
-   Tüm adlar Unicode (16-bit) karakter dizeleri olarak kodlanır.  
  
-   Adları 0x0000 bir gömülü (16-bit) değeri için izin verilmez.  
  
 Ancak, çoğu dil tür adlarına ek kısıtlamalar büyük oranda yansıtmaktadır. Tüm karşılaştırmalar bayt bayt temelinde gerçekleştirilir ve bu nedenle büyük/küçük harfe ve yerel ayarlardan bağımsızdır.  
  
 Bir tür diğer modül ve derlemelerdeki türleri başvurmasına rağmen bir tür tam bir .NET modülü içinde tanımlanması gerekir. (Derleyici desteğine bağlı olarak, ancak bunu birden çok kaynak kodu dosyalarına bölünebilir.) Tür adları yalnızca ad alanı içinde benzersiz olması. Bir türü tamamen tanımlamak için tür adı türün uygulamasını içeren ad alanı tarafından nitelendirilmelidir.  
  
### <a name="base-types-and-interfaces"></a>Temel türler ve arabirimler  
 Bir tür değerleri ve davranışları başka türden devralabilir. Ortak tür sistemi, türleri, birden fazla temel tür devralmasına izin vermez.  
  
 Bir tür herhangi bir sayıda arabirim uygulayabilir. Bir arabirim uygulamak için bir tür o arabirimin tüm sanal üyelerini uygulamalıdır. Sanal bir yöntem, türetilmiş bir tür tarafından uygulanabilir ve statik veya dinamik olarak çağrılabilir.  
  
  
  
<a name="type_members"></a>   
## <a name="type-members"></a>Tür üyeleri  
 Çalışma zamanı türünün durumunu ve davranışını belirtir, türün üyeleri tanımlamanıza olanak sağlar. Tür üyeleri şunları içerir:  
  
-   [Alanlar](#Fields)  
  
-   [Özellikler](#Properties)  
  
-   [Yöntemler](#Methods)  
  
-   [Oluşturucular](#Constructors)  
  
-   [Olaylar](#Events)  
  
-   [İç içe geçmiş türler](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Alanlar  
 Bir alan açıklar ve türün durumunun kısmını içerir. Alanlar, çalışma zamanı tarafından desteklenen herhangi bir türde olabilir. En yaygın olarak, ya da alanları `private` veya `protected`, böylece bunlar yalnızca sınıf içinden veya türetilmiş sınıftan erişilebilir. Bir özellik kümesi erişimcisi, genellikle bir alanın değeri türünün dışından değiştirilip değiştirilmediğini kullanılır. Genel olarak gösterilen alanlar genellikle salt okunurdur ve iki türde olabilir:  
  
-   Sabitler, değeri tasarım zamanında atanır. Bunlar kullanılarak tanımlanmamış olsalar da bunlar bir sınıfın statik üyeleri `static` (`Shared` Visual Basic'te) anahtar sözcüğü.  
  
-   Sınıf oluşturucuda değerleri atanabilir salt okunur değişkenler.  
  
 Aşağıdaki örnek, salt okunur alanların bu iki kullanımı gösterilmiştir.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Özellikler  
 Bir özellik türün durumu veya adları ve alma veya özelliğin değerini ayarlama için yöntemleri tanımlar. Özellikler, ilkel türler, ilkel türler, kullanıcı tanımlı türler veya kullanıcı tanımlı türler koleksiyonlarının olabilir. Özellikler genellikle türün gerçek temsilinden bağımsız bir türdeki genel arabirimi tutmak için kullanılır. Bu özellikler sınıfında (örneğin, hesaplanan değeri bir özelliğini döndürür) doğrudan depolanmaz değerleri yansıtacak şekilde ya da değerler özel alanlara atanmadan önce doğrulama gerçekleştirmesine olanak sağlar. Aşağıdaki örnekte ikinci Düzen gösterilmiştir.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Özelliği dahil olmak üzere yanı sıra okunabilir bir özellik içeren bir tür için Microsoft Ara dilini (MSIL) içeren bir `get_` *propertyname* yöntemi ve bir yazılabilir içeren bir tür için MSIL özelliği içeren bir `set_` *propertyname* yöntemi.  
  
<a name="Methods"></a>   
### <a name="methods"></a>Yöntemler  
 Bir yöntem tür üzerinde kullanılabilir işlemleri açıklar. Bir yöntemin imzası, izin verilen türlerini tüm parametre ve dönüş değerini belirtir.  
  
 Pek çok yöntem yöntem çağrıları için gerekli parametrelerin kesin sayısını tanımlamasına rağmen bazı yöntemler değişik sayıda parametreyi destekler. Bu yöntemlerin parametre ile işaretlenmiş son bildirilen <xref:System.ParamArrayAttribute> özniteliği. Dil derleyicileri tipik olarak sağlayan bir anahtar sözcüğü gibi `params` C# ve `ParamArray` Visual Basic'te getiren açık kullanımını <xref:System.ParamArrayAttribute> gereksiz.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Oluşturucular  
 Bir oluşturucu özel bir sınıf veya yapının yeni örneklerini oluşturan yöntemi türüdür. Diğer herhangi bir yöntemi gibi bir oluşturucu parametreler içerebilir. ancak oluşturucuların dönüş değeri yoktur (diğer bir deyişle, döndürmeleri `void`).  
  
 Bir sınıfın kaynak kodu açıkça bir oluşturucu tanımlamıyorsa, derleyici varsayılan (parametresiz) Oluşturucu içerir. Ancak, bir sınıfın kaynak kodu yalnızca parametreli yapıcıları tanımlıyorsa, Visual Basic ve C# Derleyicileri parametresiz bir oluşturucu oluşturmaz.  
  
 Bir yapı için kaynak kodu oluşturucular tanımlıyorsa, bunlar parametrelenmelidir; bir yapı varsayılan (parametresiz) bir oluşturucu tanımlayamaz ve derleyiciler yapılar ya da diğer değer türleri için parametresiz oluşturucular oluşturmaz. Tüm değer türleri örtülü varsayılan bir oluşturucuya sahip. Bu oluşturucu, ortak dil çalışma zamanı tarafından uygulanır ve tüm alanları varsayılan değerlerine yapısının başlatır.  
  
<a name="Events"></a>   
### <a name="events"></a>Olaylar  
 Olaya abone bir olayı tanımlar ve abone olma, yanıtlanabilen ve olayı için yöntemleri tanımlar. Olaylar genellikle diğer tür durum değişikliklerini bildirmek için kullanılır. Daha fazla bilgi için [olayları](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>İç içe Geçmiş Türler  
 İç içe türü başka bir tür üyesi olan bir türdür. İç içe geçmiş türler, içeren türlerine sıkı şekilde bağlı ve genel amaçlı bir tür olarak yararlı olmaması gerekir. İç içe geçmiş türler bildirim türü kullanır ve iç içe türün örneklerini oluşturur ve iç içe türün kullanımı ortak üyelerde gösterilmez yararlıdır.  
  
 İç içe türler bazı geliştiriciler için kafa karıştırıcı olabilir ve bir zorunlu bir neden olmadıkça herkese görünür olmamalıdır. İyi tasarımlanmış bir kitaplıkta geliştiriciler, iç içe geçmiş türler nesneler oluşturmak veya değişkenleri bildirmek için kullanılacak nadiren olmalıdır.  
  
  
  
<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Tür üye özellikleri  
 Tür üyelerinin çeşitli özelliklere sahip ortak tür sistemi sağlar; ancak dillerin tüm bu özellikleri desteklemesi gerekmez. Aşağıdaki tabloda üye özellikleri açıklanmıştır.  
  
|Özelliği|Uygulayabilirsiniz|Açıklama|  
|--------------------|------------------|-----------------|  
|abstract|Yöntemler, özellikler ve olaylar|Türü yöntemin uygulamasını sağlamıyor. Devralan veya soyut yöntemlerini uygulayan türler, yöntem için bir uygulama sağlamanız gerekir. Türetilmiş bir tür kendisini soyut bir tür olduğunda, tek özel durum olur. Tüm soyut yöntemler sanaldır.|  
|özel, aile, derleme, Aile ve derleme, Aile veya derleme veya genel|Tümü|Üyenin erişilebilirliğini tanımlar:<br /><br /> private<br /> Erişilebilir yalnızca üyeyle aynı tür içinden veya iç içe bir tür.<br /><br /> Ailesi<br /> İçinden erişilebilir aynı üye olarak ve ondan devralınan türetilmiş türler yazın.<br /><br /> derleme<br /> Yalnızca türünün tanımlandığı derleme içinde erişilebilir.<br /><br /> Aile ve derleme<br /> Yalnızca uygun bulunmuş türlerden erişilebilir Aile ve derleme erişimi için.<br /><br /> Aile veya derleme<br /> Yalnızca uygun bulunmuş türlerden erişilebilir Aile veya derleme erişimi için.<br /><br /> public<br /> Her türden erişilebilinir.|  
|son|Yöntemler, özellikler ve olaylar|Sanal yöntem türetilmiş türde geçersiz kılınamaz.|  
|yalnızca başlatma|Alanlar|Değer yalnızca başlatılabilir ve başlatma yazılamaz.|  
|örnek|Alanlar, yöntemler, özellikler ve olaylar|Bir üye olarak işaretlenmemişse `static` (C# ve C++) `Shared` (Visual Basic) `virtual` (C# ve C++) veya `Overridable` (Visual Basic) (örnek anahtar sözcük yoktur) bir örnek üyesi olduğu. Bellekte bu tür üyelerin onu kullanan nesne olduğu kadar kopyasını olacaktır.|  
|değişmez değer|Alanlar|Alana atanan değer yerleşik değer türünde derleme zamanında bilinen sabit bir değerdir. Değişmez değer alanlarını bazen sabitler de denir.|  
|NewSlot veya geçersiz kılma|Tümü|Üyenin aynı imzaya sahip devralan üyeler ile nasıl etkileştiğini tanımlar:<br /><br /> NewSlot<br /> Gizler, aynı imzaya sahip üyeler devralınır.<br /><br /> override<br /> Devralınan sanal bir yöntemin tanımını değiştirir.<br /><br /> Newslot varsayılandır.|  
|static|Alanlar, yöntemler, özellikler ve olaylar|Üye türü değil belirli bir örneğine, tanımlandığı türe aittir; üye türünün bir örneği oluşturulmadı ve bu türün tüm örnekleri arasında paylaşıldığından bile var.|  
|virtual|Yöntemler, özellikler ve olaylar|Bu yöntem, türetilmiş bir tür tarafından uygulanabilir ve statik veya dinamik olarak çağrılabilir. Dinamik çağırma kullanılıyorsa, çalışma zamanında çağrıyı yapan örnek türü (derleme zamanında bilinen tür değil) yöntemin hangi uygulamasının çağırıldığına karar verir. Statik olarak sanal bir yöntem çağırmak için değişkenin, istenen yöntem sürümünü kullanan bir türe yayınlanması gerekebilir.|  
  
### <a name="overloading"></a>Aşırı Yükleme  
 Her tür üyesinin benzersiz bir imzası vardır. Yöntem imzaları yöntem adı ve parametre listesi (sırasını ve yöntemin bağımsız değişkenlerinin türlerine) oluşur. İmzalarının farklı olduğu sürece bir tür içinde aynı ada sahip birden çok yöntem tanımlanabilir. Aynı ada sahip iki veya daha fazla yöntem tanımlandığında yöntemin aşırı yüklü olduğu söylenir. Örneğin, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> yöntemi aşırı yüklüdür. Bir yöntemi alır bir <xref:System.Char>. Diğer yöntem alır bir <xref:System.String> ve <xref:System.Int32>.  
  
> [!NOTE]
>  Dönüş türü, yönetim imzasının bir parçası olarak kabul edilmez. Diğer bir deyişle, bunlar yalnızca dönüş türüne göre farklılık gösteriyorsa yöntemler aşırı yüklenemez.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Devralma, geçersiz kılma ve üyeleri gizleme  
 Türetilmiş bir tür temel türünün tüm üyelerini devralır; diğer bir deyişle, bu üyeler tanımlanır ve türetilmiş bir tür için kullanılabilir. Davranışı veya nitelikleri devralınan üyelerin iki yolla değiştirilebilir:  
  
-   Türetilmiş bir tür devralınmış bir üyeyi aynı imzayla yeni bir üye tanımlayarak gizleyebilir. Bu önceden genel bir üyeyi özel yapmak veya olarak işaretlenmiş bir devralınan yönteme ilişkin yeni davranış tanımlamak için yapılabilir `final`.  
  
-   Türetilmiş bir tür devralınan sanal yöntemi geçersiz kılabilirsiniz. Geçersiz kılma yöntemi, çalışma zamanı yerine derleme zamanında bilinen değişken türü değerin türüne göre çağrılacak yöntemin yeni tanımını sağlar. Yalnızca sanal yöntem olarak işaretlenmişse bir yöntem sanal bir yöntemi geçersiz kılabilir `final` ve yeni yöntemi en azından sanal yöntem kadar ulaşılabilirse geçersiz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET API tarayıcısı](/dotnet/api)  
- [Ortak dil çalışma zamanı](../../../docs/standard/clr.md)  
- [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)
