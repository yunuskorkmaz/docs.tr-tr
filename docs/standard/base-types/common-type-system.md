---
title: "Ortak Tür Sistemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 26ee5cffd5e04a8c78cf5913b286fadfaab03c7c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="common-type-system"></a>Ortak Tür Sistemi
Ortak tür sistemi nasıl türleri bildirilen kullanılan ve ortak dil çalışma zamanı'nda yönetilen tanımlar ve ayrıca diller arası Integration zamanının desteği önemli bir parçasıdır. Ortak tür sistemi aşağıdaki işlevleri gerçekleştirir:  
  
-   Etkinleştirme diller arası tümleştirme, tür güvenliği ve yüksek performanslı kodu yürütme yardımcı olan bir çerçeve oluşturur.  
  
-   Tam pek çok programlama dilleri destekliyor nesne yönelimli bir modeli sağlar.  
  
-   Farklı dillerde yazılmış nesneleri birbiriyle etkileşim kurabilen yardımcı olun dilleri izlemelidir, kuralları tanımlar.  
  
-   Temel veri türlerini içeren bir kitaplık sağlar (gibi <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.Int32>, ve <xref:System.UInt64>) uygulama geliştirme kullanılır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [.NET türleri](#types_in_the_net_framework)  
  
-   [Tür Tanımları](#type_definitions)  
  
-   [Tür Üyeleri](#type_members)  
  
-   [Tür üyeleri özellikleri](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>.NET türleri  
 .NET içindeki tüm türler olan değer türleri veya başvuru türleri.  
  
 Değer türleri olan nesneleri nesnenin gerçek değeri tarafından temsil edilen veri türleridir. Bir değişkene bir değer türü örneği atanırsa, bu değişkenin değerini yeni bir kopyasını verilir.  
  
 Başvuru türleri olan nesneleri başvuru (bir işaretçi benzer) nesnenin gerçek değeri olarak temsil edilir veri türleridir. Bir başvuru türü bir değişkene atanırsa, bu değişken (nokta) başvuran özgün değeri. Hiçbir kopyalama yapılır.  
  
 .NET içinde ortak tür sistemi türleri aşağıdaki beş kategorilerini destekler:  
  
-   [Sınıflar](#Classes)  
  
-   [Yapılar](#Structures)  
  
-   [Sabit Listeleri](#Enumerations)  
  
-   [Arabirimler](#Interfaces)  
  
-   [Temsilciler](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Sınıflar  
 Bir sınıf, türetilmiş doğrudan başka bir sınıftan ve, türetilen dolaylı bir başvuru türüdür <xref:System.Object?displayProperty=nameWithType>. Sınıf (sınıfının bir örneği olan) bir nesne (yöntem, olayları ya da Özellikler) gerçekleştirebileceğiniz işlemler tanımlar ve veri nesnesi (alanları) içerir. Bir sınıf tanımı ve (aksine, yalnızca uygulama olmadan tanımını içeren arabirimler, örneğin,), uygulama genellikle içerse uygulaması olan bir veya daha fazla üye sahip olabilir.  
  
 Aşağıdaki tabloda bir sınıf olabilir özellikleri bazıları açıklanmaktadır. Çalışma zamanı destekleyen her bir dilin bir sınıf belirtmek için bir yol sağlar veya sınıf üyesi bir veya daha fazla şu özelliklere sahiptir. Ancak, tek tek programlama dilleri hedefleyen .NET şu özelliklere kullanımına değil.  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|korumalı|Başka bir sınıf bu türden türetilmiş belirtir.|  
|uygulamalar|Arabirim üyeleri uygulamaları sağlayarak sınıfı bir veya daha fazla arabirimin kullandığını gösterir.|  
|abstract|Sınıf örneği gösterir. Kullanmak için başka bir sınıf ondan türetilmesi gerekir.|  
|devralır|Sınıfın örnekleri, temel sınıfın belirtilen herhangi bir yere kullanılabileceğini gösterir. Taban sınıfından devralıyor türetilmiş bir sınıf temel sınıfı tarafından sağlanan herhangi bir ortak üye uyarlamasını kullanabilir veya türetilmiş bir sınıf kendi uygulama Genel üyeler uygulamasıyla geçersiz kılabilirsiniz.|  
|dışa aktarılan ya da dışa aktarılamaz|Bir sınıf içinde tanımlandığı derleme dışında görünür olup olmadığını gösterir. Bu özellik yalnızca üst düzey sınıflar ve iç içe geçmiş sınıflar için geçerlidir.|  
  
> [!NOTE]
>  Bir sınıfı ayrıca bir üst sınıf veya yapı iç içe. İç içe geçmiş sınıflar da üye özelliklere sahiptir. Daha fazla bilgi için bkz: [iç içe geçmiş türler](#NestedTypes).  
  
 Hiç uygulamanız sınıf üyeleri soyut üyeleridir. Bir veya daha fazla soyut üye olan bir sınıfı kendisi değildir soyut; yeni örneklerini oluşturulamıyor. Çalışma zamanı hedef bazı dillerde, üyelerine hiçbiri soyut olsa bile, bir sınıf soyut olarak işaretlemek olanak tanır. Temel bir kapsülleyen istediğinizde bir Özet sınıf kullanabilirsiniz türetilmiş sınıfları işlev kümesi devralır veya uygun olduğunda geçersiz kılar. Özet olmayan sınıflar somut sınıflar adlandırılır.  
  
 Bir sınıf herhangi bir sayıda arabirim uygulayabilirsiniz, ancak ek olarak yalnızca bir taban sınıftan devralabilirsiniz <xref:System.Object?displayProperty=nameWithType>, hangi tüm sınıflar örtük olarak devral gelen. Tüm sınıflar, yeni sınıfın örneği başlatır en az bir oluşturucuya sahip olmalıdır. Bir oluşturucu açıkça tanımlamıyorsa, çoğu derleyicileri otomatik olarak varsayılan (parametresiz) Oluşturucusu sağlar.  
  
<a name="Structures"></a>   
### <a name="structures"></a>Yapılar  
 Örtük olarak türeyen bir değer türü yapısıdır <xref:System.ValueType?displayProperty=nameWithType>, sırayla türetilen <xref:System.Object?displayProperty=nameWithType>. Bir yapı, bellek gereksinimleri küçük değerlerini temsil eden ve değerleri parametreleri kesin türü belirtilmiş yöntemleri değeri olarak parametre olarak geçirme çok yararlı olacaktır. . NET'te, tüm temel veri türleri (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, ve <xref:System.UInt64>) yapıları olarak tanımlanır.  
  
 Sınıflar gibi yapıları verileri (yapısı alanları) ve bu verileri (yapısı yöntemleri) gerçekleştirilen işlemleri tanımlayın. Yapıları tanımlanan sanal yöntemleri de dahil olmak üzere üzerinde yöntemleri çağırabilirsiniz yani <xref:System.Object?displayProperty=nameWithType> ve <xref:System.ValueType?displayProperty=nameWithType> sınıfları ve değer türü kendisini tanımlanmış herhangi bir yöntem. Diğer bir deyişle, yapıları alanları, özellikleri ve olayları yanı sıra statik ve statik olmayan yöntemleri olabilir. Yapıları örneklerini oluşturmak, parametre olarak geçirmek, yerel değişkenleri olarak depolamak veya başka bir değer türü bir alana depolamaya veya türü başvuru. Yapıları arabirimleri de uygulayabilirsiniz.  
  
 Değer türleri birçok bakımdan sınıfları ayrıca farklıdır. İlk olarak, bunlar örtük olarak devralınmalıdır rağmen <xref:System.ValueType?displayProperty=nameWithType>, herhangi bir türünden doğrudan devral olamaz. Benzer şekilde, başka bir türü onlardan türetilebilir, yani tüm değer türleri korumalıdır. Bunlar ayrıca oluşturucular gerek yoktur.  
  
 Her değer türü için ortak dil çalışma zamanı aynı durumu ve değer türü davranışlara sahiptir sınıftır karşılık gelen bir Kutulu türü sağlar. Değer türü örneği türünde bir parametre kabul eden bir yönteme geçirildiğinde Kutulu <xref:System.Object?displayProperty=nameWithType>. Sarmalanmamış (diğer bir deyişle, bir sınıfın bir örnekten bir değer türü örneğine geri dönüştürülmüş) denetim döndüğünde yöntemi çağrısından değer türü başvurusu tarafından parametre olarak kabul eder. Bazı diller Kutulu türü gerekli olduğunda özel bir sözdizimi kullanmanızı gerektirir; gerektiğinde başkalarının otomatik olarak paketlenmiş türünü kullanın. Değer türü tanımladığınızda, paketlenmiş hem sarmalanmamış türü tanımlama.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Numaralandırmalar  
 Doğrudan öğesinden devralınan bir değer türü numaralandırma (numaralandırma) olduğunda <xref:System.Enum?displayProperty=nameWithType> ve kaynakları adları temel alınan bir ilkel türü değerleri için alternatif. Bir numaralandırma türü yerleşik işaretli veya işaretsiz tamsayı türlerden biri olmalıdır bir temel alınan türü olan bir ada sahip (gibi <xref:System.Byte>, <xref:System.Int32>, veya <xref:System.UInt64>) ve alanları kümesi. Her biri bir sabiti temsil eden statik değişmez değer alanları alanlardır. Aynı değeri için birden çok alan atanabilir. Bu durumda, değerlerden biri yansıma ve dize dönüştürme için birincil numaralandırma değeri olarak işaretlemeniz gerekir.  
  
 Türünde bir değer (tür atama yok çalışma zamanı tarafından gerekli değildir) temel bir numaralandırma ve tersi yönde atayabilirsiniz. Numaralandırma örneği oluşturun ve yöntemlerini çağırın <xref:System.Enum?displayProperty=nameWithType>, numaralandırmanın temel türünde tanımlanan olarak herhangi bir yöntem yanı sıra. Ancak, bazı dillerde, temel alınan türünün bir örneği gerekli olduğunda bir numaralandırma parametre olarak geçirmek sağlayabilir değil (veya tersi).  
  
 Numaralandırmalar için aşağıdaki ek kısıtlamalar geçerlidir:  
  
-   Bunlar kendi yöntemleri tanımlayamazsınız.  
  
-   Bunlar arabirimleri uygulayamaz.  
  
-   Bunlar, özellikleri veya olayları tanımlayamazsınız.  
  
-   Genel bir tür içinde yalnızca içe çünkü genel edilmedikleri sürece genel, olamaz. Diğer bir deyişle, bir numaralandırma türü parametrelerinin kendi sahip olamaz.  
  
    > [!NOTE]
    >  Visual Basic, C# ve C++ ile oluşturulan iç içe geçmiş türler (numaralandırmalar dahil) tüm kapsayan genel türleri tür parametrelerini içerir ve kendi tür parametreleri olmasa bile, bu nedenle genel. Daha fazla bilgi için bkz: "Türleri iç içe geçmiş" <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> başvuru konusu.  
  
 <xref:System.FlagsAttribute> Öznitelik bir bit alanı adlı numaralandırması özel bir tür gösterir. Çalışma zamanı kendisini geleneksel numaralandırmalar ve bit alanları arasında ayrım yapmaz ancak dilinizi bunu. Bu ayrım yapıldığında, bit düzeyinde işleçler bit alanları, ancak numaralandırmalar, adlandırılmamış değerlerini oluşturmak için kullanılabilir. Numaralandırmalar genellikle gün hafta, ülke veya bölge adları gibi benzersiz öğelerin listesi için kullanılır ve benzeri. Bit alanları genellikle nitelikleri veya birlikte gibi oluşabilecek miktarları listesi için kullanılan `Red And Big And Fast`.  
  
 Aşağıdaki örnek bit alanları ve geleneksel numaralandırmalar nasıl kullanılacağını gösterir.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Arabirimler  
 Bir "yapabilirsiniz" ilişkiyi belirten bir sözleşme bir arabirim tanımlar veya "sahip bir" ilişki. Arabirimleri genellikle karşılaştırma ve sıralama gibi işlevlerini uygulamak için kullanılır ( <xref:System.IComparable> ve <xref:System.IComparable%601> arabirimleri), eşitlik için test ( <xref:System.IEquatable%601> arabirimi), veya bir koleksiyondaki öğelerin numaralandırma ( <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601> arabirimleri). Arabirim özellikleri, yöntemleri ve olaylar, soyut üyelerini tümü olabilir; üyeleri ve bunların imza arabirimi tanımlar, diğer bir deyişle, bu, her arabirim üyesini işlevselliğini tanımlamak için arabirimini uygulayan türü bırakır, ancak. Başka bir deyişle, herhangi bir sınıf veya bir arabirimini uygulayan yapısı arabirimde bildirilen soyut üyelerini tanımlarında sağlamanız gerekir. Bir arabirim herhangi uygulayan sınıf veya yapı de bir veya daha fazla diğer arabirimleri uygulamak için gerektirebilir.  
  
 Arabirimleri aşağıdaki kısıtlamalar geçerlidir:  
  
-   Bir arabirim ile tüm erişilebilirlik bildirilebilir ancak arabirim üyeleri tüm ortak erişilebilirlik olması gerekir.  
  
-   Arabirimleri oluşturucular tanımlayamazsınız.  
  
-   Arabirimleri alanları tanımlayamazsınız.  
  
-   Arabirimleri yalnızca örnek üyelerin tanımlayabilirsiniz. Bunlar statik üyeler tanımlanamaz.  
  
 Birden fazla arabirimi aynı imzaya sahip bir üye bildirebilir olduğundan, bir uygulama üye gerektiren arabirimine eşlemek için her bir dilin kuralları sağlamanız gerekir ve bu üyeleri ayrı uygulamaları olabilir.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Temsilciler  
 Temsilciler c++'ta, işlev işaretçileri benzeyen bir amaca hizmet başvuru türleridir. Olay işleyicileri ve .NET geri çağırma işlevleri için kullanılır. İşlev işaretçileri aksine temsilciler güvenli, doğrulanabilir ve güvenli yazın. Bir temsilci türü herhangi bir örnek yöntemi veya uyumlu bir imzaya sahip statik yöntemi temsil edebilir.  
  
 Bu temsilci atamak için geçirilen bağımsız değişken için güvenli bir şekilde geçirilebilir güvence altına alır çünkü temsilci parametresinin türü yöntemi parametresinin türü kısıtlayıcı ise temsilcisi bir parametre karşılık gelen bir yöntem parametresi ile uyumlu. yöntem.  
  
 Bu dönüş türü yönteminin dönüş değeri güvenle çevirebilirsiniz güvence altına alır çünkü yöntemin dönüş türünü temsilci dönüş türünden daha kısıtlayıcı ise benzer şekilde, bir temsilci dönüş türü bir yöntemi, dönüş türü ile uyumlu. Temsilci e.  
  
 Örneğin, türünde bir parametreye sahip bir temsilci <xref:System.Collections.IEnumerable> ve dönüş türü <xref:System.Object> türünde bir parametre içeren bir yöntem gösterebilir <xref:System.Object> ve bir dönüş değeri <xref:System.Collections.IEnumerable>. Daha fazla bilgi ve örnek kod için bkz: <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>.  
  
 Bir temsilci temsil ettiği yönteme bağlı olmayı kabul edilir. Yöntemine bağlanan ek olarak bir temsilci nesneye bağlı olabilir. Nesne yönteminin ilk parametresini temsil eder ve temsilci çağrılır her zaman yönteme geçirilen. Yöntem örnek yöntemi ise, ilişkili nesne örtük geçirilen `this` parametre (`Me` Visual Basic'te); yöntemi statik nesne yöntemi resmi ilk parametre olarak geçirilir ve temsilci imza eşleşmelidir Kalan parametreleri. Daha fazla bilgi ve örnek kod için bkz: <xref:System.Delegate?displayProperty=nameWithType>.  
  
 Tüm temsilcileri devralınmalıdır <xref:System.MulticastDelegate?displayProperty=nameWithType>, devralan <xref:System.Delegate?displayProperty=nameWithType>. C#, Visual Basic ve C++ dilleri devralma bu türlerinden izin vermez. Bunun yerine, temsilciler bildirmek için anahtar sözcükleri girin.  
  
 Temsilciler öğesinden devraldığı <xref:System.MulticastDelegate>, bir temsilci temsilciyi temsil eder ve temsilci çağrıldığında yürütülme yöntemlerin listesi bir çağrı listesi vardır. Listedeki tüm yöntemleri temsilci çağrıldığında sağlanan bağımsız değişkenler alırsınız.  
  
> [!NOTE]
>  Temsilci bir dönüş türüne sahip olsa bile dönüş değeri kendi çağırma listesinde birden fazla yöntemi olan bir temsilci için tanımlı değil.  
  
 Çoğu durumda, gibi geri arama yöntemleri ile temsil eden bir temsilci yalnızca bir yöntem ve yapmanız gereken tek Eylemler temsilci oluşturma ve onu çağırma.  
  
 Birden fazla yöntemi temsil eden temsilciler .NET yöntemlerinin sağlar <xref:System.Delegate> ve <xref:System.MulticastDelegate> temsilci yöntem bir temsilcinin çağırma listesine ekleme gibi işlemleri desteklemek için sınıflar ( <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> yöntemi), bir yöntem ( kaldırma<xref:System.Delegate.Remove%2A?displayProperty=nameWithType> yöntemi) ve çağırma listesi alınıyor ( <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> yöntemi).  
  
> [!NOTE]
>  Bu diller için ekleme ve kaldırma olay işleyicileri sözdizimi sağladığından bu yöntemleri için C#, C++ ve Visual Basic, olay işleyici temsilcileri kullanmak gerekli değildir.  
  
 
  
<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Tür tanımları  
 Bir tür tanımı aşağıdakileri içerir:  
  
-   Türünde tanımlanmış tüm öznitelikler.  
  
-   Tür erişilebilirlik (görünürlük).  
  
-   Tür adı.  
  
-   Tür temel türü.  
  
-   Türü tarafından uygulanan tüm arabirimler.  
  
-   Her tür üyeleri tanımlar.  
  
### <a name="attributes"></a>Öznitelikler  
 Öznitelikler ek kullanıcı tanımlı meta veri sağlar. En yaygın olarak, bunlar kendi bütünleştirilmiş kodunda bir türü hakkında ek bilgi depolamak için ya da Tasarım zamanı ya da çalışma zamanı ortamı türü üyesi ya da davranışını değiştirmek için kullanılır.  
  
 Öznitelikleri sınıflardır kendilerini devralınan <xref:System.Attribute?displayProperty=nameWithType>. Özniteliklerin her destek dilleri öznitelikleri bir dil öğesine uygulama için kendi sözdizimine sahip. Öznitelikler, neredeyse her dil öğesine uygulanabilir; için bir öznitelik uygulanabilir belirli öğeleri tarafından tanımlanan <xref:System.AttributeUsageAttribute> bu öznitelik sınıfı uygulanır.  
  
### <a name="type-accessibility"></a>Türü erişilebilirlik  
 Tüm türleri kendi erişilebilirlik diğer türlerinden yöneten bir değiştirici sahip. Aşağıdaki tabloda çalışma zamanı tarafından desteklenen tür eriþebilirlik açıklanmaktadır.  
  
|Erişilebilirlik|Açıklama|  
|-------------------|-----------------|  
|public|Türü tarafından tüm derlemelerde erişilebilir.|  
|derleme|Türü, derleme içinde yalnızca erişilebilir.|  
  
 İç içe geçmiş tür erişilebilirliğini üyesinin bildirilen erişilebilirlik ve hemen kapsayan tür erişilebilirlik etki alanı tarafından belirlenir kendi erişilebilirlik etki bağlıdır. Ancak, iç içe geçmiş tür erişilebilirlik etki alanı, kapsayan tür aşamaz.  
  
 Erişilebilirlik etki alanı iç içe üyesi `M` bir türü bildirilmiş `T` bir programdan `P` şu şekilde tanımlanır (Bu belirtmeye `M` kendisini bir türü olabilir):  
  
-   Varsa bildirilen erişilebilirliğini `M` olan `public`, Erişilebilirlik etki alanı `M` erişilebilirlik etki alanıdır `T`.  
  
-   Varsa bildirilen erişilebilirliğini `M` olan `protected internal`, Erişilebilirlik etki alanı `M` kesişimi erişilebilirlik etki alanının olduğu `T` program metnini ile `P` ve türetilmiş herhangi bir türde program metin `T` dışında bildirilen `P`.  
  
-   Varsa bildirilen erişilebilirliğini `M` olan `protected`, Erişilebilirlik etki alanı `M` kesişimi erişilebilirlik etki alanının olduğu `T` program metnini ile `T` ve türetilmişherhangibirtür`T`.  
  
-   Varsa bildirilen erişilebilirliğini `M` olan `internal`, Erişilebilirlik etki alanı `M` kesişimi erişilebilirlik etki alanının olduğu `T` program metnini ile `P`.  
  
-   Varsa bildirilen erişilebilirliğini `M` olan `private`, Erişilebilirlik etki alanı `M` program metni olur `T`.  
  
### <a name="type-names"></a>Tür Adları  
 Ortak tür sistemi adları yalnızca iki kısıtlamaları getirir:  
  
-   Tüm adlar Unicode (16-bit) karakter dizeleri olarak kodlanır.  
  
-   Adları bir katıştırılmış 0x0000 (16-bit) değerine sahip olacak şekilde izin verilmez.  
  
 Bununla birlikte, çoğu dil tür adları ek kısıtlamaları zorunlu tuttukları. Tüm karşılaştırmaları bir bayt bayt temelinde gerçekleştirilir ve bu nedenle büyük küçük harfe duyarlı ve yerel ayar bağımsız.  
  
 Bir tür türleri diğer modüller ve derlemeler başvurabilir karşın, bir .NET modülünde bir türü tam olarak tanımlanması gerekir. (Derleyici desteği bağlı olarak, ancak bu birden çok kaynak kodu dosyasına ayrılabilir.) Tür adları yalnızca ad alanı içinde benzersiz olması. Tam olarak bir türünü tanımlamak için tür adı, türü uyarlamasını içeren ad tarafından nitelenmiş olmalıdır.  
  
### <a name="base-types-and-interfaces"></a>Taban türleri ve arabirimleri  
 Bir tür değerleri ve davranışları başka bir türden devralabilirsiniz. Ortak tür sistemi türleri birden çok taban türünden devralan izin vermiyor.  
  
 Bir türü herhangi bir sayıda arabirim uygulayabilirsiniz. Bir arabirim için bir tür tüm sanal üyeleri bu arabirimi uygulamalıdır. Sanal bir yöntem tarafından türetilmiş bir tür uygulanabilir ve statik veya dinamik olarak çağrılır.  
  
  
  
<a name="type_members"></a>   
## <a name="type-members"></a>Tür üyeleri  
 Çalışma zamanı davranışı ve bir türünün durumunu belirtir, türün üyeleri tanımlamanızı sağlar. Tür üyeleri şunları içerir:  
  
-   [Alanlar](#Fields)  
  
-   [Özellikler](#Properties)  
  
-   [Yöntemler](#Methods)  
  
-   [Oluşturucular](#Constructors)  
  
-   [Olaylar](#Events)  
  
-   [İç içe geçmiş türler](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Alanlar  
 Bir alan açıklar ve tür durumu bölümünü içerir. Alanlar, çalışma zamanı tarafından desteklenen herhangi bir türde olabilir. En yaygın olarak, ya da alanlardır `private` veya `protected`, böylece erişilebilir yalnızca sınıf içinde veya türetilmiş bir sınıf. Bir alanın değerini türünü dışında değiştirilebilir, bir özellik set erişimcisi genellikle kullanılır. Genel olarak sunulan alanlar genellikle salt okunurdur ve iki türde olabilir:  
  
-   Sabitler, tasarım zamanında değeri atanır. Bu, bir sınıfın statik üyeleri bunlar kullanarak tanımlanmayan ancak `static` (`Shared` Visual Basic'te) anahtar sözcüğü.  
  
-   Değerleri bir sınıf oluşturucu atanabilir salt okunur değişkenler.  
  
 Aşağıdaki örnek, salt okunur alanlarının iki bu kullanımları gösterilmektedir.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Özellikler  
 Bir özellik adları bir değer veya türünün durumunu ve alma veya özelliğin değeri ayarlamak için yöntemleri tanımlar. İlkel türler, basit türler, kullanıcı tanımlı türler veya kullanıcı tanımlı türler koleksiyonlarının özelliklerini olabilir. Özellikleri genellikle bir türde ortak arabirimi tür gerçek gösteriminden bağımsız tutmak için kullanılır. Bu, doğrudan (örneğin, bir özelliğin hesaplanan değeri döndürdüğünde) sınıfında depolanmaz değerleri yansıtacak şekilde veya değerleri için özel alanlar atandığını önce doğrulama gerçekleştirmek için özellikleri sağlar. Aşağıdaki örnek, ikinci düzeni gösterilmektedir.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Özellik dahil ek olarak, okunabilir bir özellik içeren bir türü için Microsoft Ara dili (MSIL) içeren bir `get_` *propertyname* yöntemi ve bir yazılabilir içeren bir türü için MSIL özelliği içeren bir `set_` *propertyname* yöntemi.  
  
<a name="Methods"></a>   
### <a name="methods"></a>Yöntemler  
 Yöntemi türüne göre kullanılabilen işlemleri açıklanmaktadır. Bir yöntemin imzası izin verilen türleri tüm parametreler ve dönüş değerini belirtir.  
  
 Yöntem çağrıları için gerekli parametreleri kesin sayısı çoğu yöntemlerini tanımlama rağmen bazı yöntemler parametreleri değişken sayıda destekler. Bu yöntemlerin parametresi ile işaretlenmiş son bildirilen <xref:System.ParamArrayAttribute> özniteliği. Dil derleyicileri genellikle sağlayan bir anahtar sözcük gibi `params` C# ve `ParamArray` Visual Basic'te açık kullanımını yapıyorsa <xref:System.ParamArrayAttribute> gereksiz.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Oluşturucular  
 Bir oluşturucusu bir özel bir sınıf veya yapı yeni örneklerini oluşturur yöntemi türüdür. Diğer herhangi bir yöntem gibi bir Oluşturucu parametreleri içerebilir; Ancak, Oluşturucular bir dönüş değerine sahip (diğer bir deyişle, döndürmeleri `void`).  
  
 Kaynak kodu bir sınıf için bir oluşturucu açıkça tanımlamıyorsa derleyici varsayılan (parametresiz) Oluşturucusu içerir. Ancak, bir sınıf için kaynak kodunu yalnızca parametreli oluşturucular tanımlıyorsa, Visual Basic ve C# Derleyicileri parametresiz bir kurucusu oluşturmaz.  
  
 Bir yapı için kaynak kodunu oluşturucular tanımlıyorsa, bunlar parametreli gerekir; Varsayılan (parametresiz) Oluşturucusu bir yapı tanımlayamazsınız ve derleyicileri yapıları veya diğer değer türleri için parametresiz oluşturucular oluşturmaz. Tüm değer türleri bir örtük varsayılan oluşturucusu olmalı. Bu oluşturucu ortak dil çalışma zamanı tarafından uygulanır ve tüm alanları varsayılan değerlerine yapısının başlatır.  
  
<a name="Events"></a>   
### <a name="events"></a>Olaylar  
 Bir olay için yanıt bir olay tanımlar ve olayı tetiklenmeden abone olma ve aboneliği sonlandırma için yöntemleri tanımlar. Olaylar, genellikle diğer türleri durum değişiklikleri bildirmek için kullanılır. Daha fazla bilgi için bkz: [olayları](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>İç içe Geçmiş Türler  
 Diğer bir türünün bir üyesi olan bir türü bir iç içe geçmiş türüdür. İç içe geçmiş türler içeren tipine sıkı şekilde bağlı ve genel amaçlı bir tür olarak yararlı olmamalıdır. İç içe geçmiş türler bildiri türü kullanır ve iç içe geçmiş tür örneklerini oluşturur ve iç içe geçmiş tür kullanımı genel üyeler gösterilmeyen olduğunda yararlıdır.  
  
 İç içe geçmiş türler için bazı geliştiriciler karmaşıktır ve görünürlük ilgi çekici bir nedeni olmadıkça herkese görünür olmamalıdır. İyi tasarlanmış bir kitaplıkta geliştiriciler nadiren nesneleri örneği veya değişkenleri bildirmek için iç içe geçmiş türler kullanmaya olması gerekir.  
  
  
  
<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Tür üyeleri özellikleri  
 Ortak tür sistemi türü üyelerinin çeşitli özelliklere sahip olanak tanır; Ancak, bu özellikleri desteklemek için dilleri gerekmez. Aşağıdaki tabloda üye özelliklerini açıklar.  
  
|Özelliği|İçin geçerli olabilir|Açıklama|  
|--------------------|------------------|-----------------|  
|abstract|Yöntemler, özellikler ve olaylar|Türü yöntemin uygulaması sağlamaz. Devralmalı ya da soyut yöntemler uygulama türlerini yöntemi için uygulama sağlamanız gerekir. Türetilmiş bir tür kendisini soyut bir tür olduğunda tek özel durumdur. Tüm soyut yöntemler sanal.|  
|özel, aile, derleme, ailesi ve derleme, Aile veya derleme ya da ortak|Tümü|Üye erişilebilirliğini tanımlar:<br /><br /> private<br /> Erişilebilir yalnızca iç içe geçmiş tür veya üye aynı türde içinde.<br /><br /> Ailesi<br /> İçinden erişilebilir aynı üye olarak ve ondan devralır türetilen türlerin yazın.<br /><br /> derleme<br /> Yalnızca türünün tanımlandığı derleme erişilebilir.<br /><br /> Aile ve derleme<br /> Uygun türlerinden erişilebilir ailesi ve derleme erişim.<br /><br /> Aile veya derleme<br /> Uygun türlerinden erişilebilir ailesi veya derleme erişim.<br /><br /> public<br /> Her tür erişilebilir.|  
|son|Yöntemler, özellikler ve olaylar|Sanal bir yöntem, türetilen türde de değiştirilemiyor.|  
|yalnızca başlatma|Alanlar|Değer yalnızca başlatılabilir ve sonra başlatma yazılamaz.|  
|örnek|Alanlar, yöntemleri, özellikleri ve olayları|Bir üye olarak işaretlenmemiş olması `static` (C# ve C++) `Shared` (Visual Basic) `virtual` (C# ve C++) veya `Overridable` (Visual Basic) (örnek anahtar sözcük yoktur) örnek üyesine değil. Bu tür üyeler bellekte kullanmak nesneleri olarak kadar kopyasını olacaktır.|  
|değişmez değer|Alanlar|Alanına atanan değer yerleşik değer türü derleme zamanında bilinen sabit bir değerdir. Değişmez değer alanları sabitleri da adlandırılır.|  
|NewSlot veya geçersiz kılma|Tümü|Üye aynı imzaya sahip devralınan üyeleri ile nasıl etkileşim kurduğu tanımlar:<br /><br /> NewSlot<br /> Devralınan aynı imzaya sahip üyeleri gizler.<br /><br /> override<br /> Devralınan sanal bir yöntem tanımının yerini alır.<br /><br /> Newslot varsayılandır.|  
|static|Alanlar, yöntemleri, özellikleri ve olayları|Üye türünde değil belirli bir örneği için tanımlandıktan türüne ait; üye türünün bir örneği oluşturulmaz ve türünün tüm örneklerini arasında paylaşılan olsa bile bulunmaktadır.|  
|virtual|Yöntemler, özellikler ve olaylar|Bu yöntem tarafından türetilmiş bir tür uygulanabilir ve statik veya dinamik olarak çağrılır. Dinamik çağırma kullanılırsa, hangi yöntemin kullanımı adlı çalışma zamanında çağrı yapar örneğin türünü (derleme zamanında bilinen türü yerine) belirler. Sanal bir yöntem statik olarak çağırmak için değişkenin yöntemi istenen sürümünü kullanan bir türe gerekebilir.|  
  
### <a name="overloading"></a>Aşırı Yükleme  
 Her tür üyesi benzersiz bir imza içeriyor. Yöntem imzaları yöntem adı ve parametre listesi (sırası ve yöntemin bağımsız değişken türleri) oluşur. Kendi imzaları farklı olduğu sürece, aynı ada sahip birden çok yöntem içinde bir tür tanımlanabilir. Aynı ada sahip iki veya daha fazla yöntem tanımlandığında, yöntemi aşırı yüklenmiş kabul edilir. Örneğin, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> yöntemi aşırı yüklü. Bir yöntemi alır bir <xref:System.Char>. Başka bir yöntem geçen bir <xref:System.String> ve bir <xref:System.Int32>.  
  
> [!NOTE]
>  Dönüş türü bir yöntemin imzası parçası dikkate alınmaz. Diğer bir deyişle, bunlar yalnızca dönüş türüne göre farklıysa yöntemlerini aşırı yüklenemez.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Devralma özelliği, geçersiz kılma ve üyeleri gizleme  
 Türetilmiş bir tür, temel türdeki tüm üyelerin devralır; diğer bir deyişle, bu üyeler üzerinde tanımlı ve türetilmiş bir tür için kullanılabilir. Devralınan üyeleri niteliklerini ve davranış iki yolla değiştirilebilir:  
  
-   Türetilmiş bir tür aynı imzaya sahip yeni bir üye tanımlayarak devralınmış bir üyeyi gizleyebilirsiniz. Bu önceden ortak üyesi özel yapmak veya olarak işaretlenmiş bir devralınan yöntemi yeni davranışını tanımlamak için yapılabilir `final`.  
  
-   Türetilmiş bir tür devralınan sanal bir yöntem geçersiz kılabilirsiniz. Geçersiz kılma yöntemi yeni bir derleme zamanında bilinen değişkeninin türü yerine çalışma zamanında değer türüne göre çağrılacak yöntem tanımını sağlar. Yalnızca sanal yöntemi olarak işaretlenmişse bir yöntem sanal bir yöntem kılabilirsiniz `final` ve yeni yöntemi en az sanal yöntemi olarak erişilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET sınıf kitaplığı](http://go.microsoft.com/fwlink/?LinkID=217856)  
 [Ortak dil çalışma zamanı](../../../docs/standard/clr.md)  
 [.NET içinde Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)
