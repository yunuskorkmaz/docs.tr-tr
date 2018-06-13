---
title: Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- language interoperability
- Common Language Specification
- cross-language interoperability
- CLS
- runtime, language interoperability
- common language runtime, language interoperability
ms.assetid: 4f0b77d0-4844-464f-af73-6e06bedeafc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf18fb7238eb35b5ceb1624c14b83486485ddc1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579632"
---
# <a name="language-independence-and-language-independent-components"></a>Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler
.NET Framework bağımsız dilidir. Bir geliştirici olarak size .NET Framework, C#, C + gibi hedef birçok dilde birinde geliştirebilirsiniz, yani +/ CLI, Eiffel, F #, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL ve Windows PowerShell. Türleri ve sınıf kitaplıkları için .NET Framework, bunlar ilk olarak yazılmış içinde dili bilmenize gerek kalmadan ve özgün dil kuralları birini izleyin gerek kalmadan geliştirilen üyeleri erişebilir. Bileşen geliştiriciyseniz bileşeniniz dili bağımsız olarak herhangi bir .NET Framework uygulama tarafından erişilebilir.  
  
> [!NOTE]
>  Dilden bağımsız bileşenler oluşturma bu ilk bölümü, bu makalenin ele — diğer bir deyişle, herhangi bir dilde yazılan uygulamaları tarafından kullanılabilecek bileşenler. Çeşitli dillerde yazılmış kaynak koddan tek bir bileşen ya uygulaması oluşturabilirsiniz; bkz: [diller arası birlikte çalışabilirlik](#CrossLang) ikinci bölümü, bu makalenin.  
  
 Tam olarak herhangi bir dilde yazılmış diğer nesnelerle etkileşim kurmak için nesneleri, tüm diller için ortak olan özellikleri arayanlara kullanıma gerekir. Bu ortak bir özellikler kümesi ortak dil belirtimi (CLS tarafından), hangi oluşturulmuş derlemeler için geçerli bir kurallar kümesidir tanımlanır. Ortak dil belirtimi bölüm ı yan tümceleri 7 11 /'ile tanımlanan [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Bileşeniniz ortak dil belirtimi uyuyorsa, CLS uyumlu olması garanti ve CLS destekleyen tüm programlama dilinde yazılmıştır derlemelerde koddan erişilebilir. Bileşeniniz ortak dil belirtimi derleme zamanında uygulayarak uyup uymadığını belirleyebilirsiniz <xref:System.CLSCompliantAttribute> özniteliği için kaynak kodu. Daha fazla bilgi için bkz: [CLSCompliantAttribute özniteliği](#CLSAttribute).  
  
 Bu makalede:  
  
-   [CLS uyumluluk kuralları](#Rules)  
  
    -   [Türleri ve türü üye imzaları](#Types)  
  
    -   [Adlandırma kuralları](#naming)  
  
    -   [Tür dönüştürmeleri](#conversion)  
  
    -   [Diziler](#arrays)  
  
    -   [Arabirimler](#Interfaces)  
  
    -   [Sabit Listeleri](#enums)  
  
    -   [Genel üyeleri yazın](#members)  
  
    -   [Üye erişilebilirlik](#MemberAccess)  
  
    -   [Genel türler ve üyeleri](#Generics)  
  
    -   [Oluşturucular](#ctors)  
  
    -   [Özellikler](#properties)  
  
    -   [Olaylar](#events)  
  
    -   [Overloads](#overloads)  
  
    -   [Özel Durumlar](#exceptions)  
  
    -   [Öznitelikler](#attributes)  
  
-   [CLSCompliantAttribute özniteliği](#CLSAttribute)  
  
-   [Diller arası birlikte çalışabilirlik](#CrossLang)  
  
<a name="Rules"></a>   
## <a name="cls-compliance-rules"></a>CLS uyumluluk kuralları  
 Bu bölümde, CLS uyumlu bir bileşen oluşturmak için kurallar açıklanmaktadır. Bölüm ı yan tümcesi 11 / kuralları tam bir listesi için bkz [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
> [!NOTE]
>  Çerçeveler (dil derleyici oluşturmak için kullandığınız geliştiriciler tüketicilere CLS uyumlu bir bileşen program aracılığıyla erişme (geliştiriciler) uygularken ortak dil belirtimi CLS uyumluluğu için her bir kural açıklanır. CLS-compliant kitaplıklar) ve Extender'larının (dil derleyici veya CLS uyumlu bileşenleri oluşturan bir kod ayrıştırıcı gibi bir araç oluşturan geliştiriciler). Çerçeveler için uygularken bu makalede kurallarında odaklanır. Ancak, bazı Extender'larının için geçerli olan kurallar da Reflection.Emit kullanılarak oluşturulan derlemeleri uygulayabilir unutmayın.  
  
 Dilden bağımsızdır bir bileşen tasarlamak için yalnızca, bileşenin ortak arabirim CLS uyumluluğu için kurallar uygulama gerekir. Özel uygulamanızı belirtimine uygun olarak yok.  
  
> [!IMPORTANT]
>  CLS uyumluluğu için kurallar, yalnızca kendi özel uygulama için bir bileşenin ortak arabirimi uygulanır.  
  
 Örneğin, tamsayılar dışında imzasız <xref:System.Byte> CLS uyumlu değildir. Çünkü `Person` sınıfı aşağıdaki örnekte sunar bir `Age` türünde özellik <xref:System.UInt16>, aşağıdaki kod derleyici uyarısı görüntüler.  
  
 [!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
 [!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]  
  
 Yapabileceğiniz `Person` sınıf CLS uyumlu türünü değiştirerek `Age` özelliğinden <xref:System.UInt16> için <xref:System.Int16>, CLS uyumlu, 16 bit işaretli tamsayıyı olduğu. Özel türünü değiştirmek zorunda değilsiniz `personAge` alan.  
  
 [!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
 [!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]  
  
 Kitaplığın ortak arabirimi aşağıdakilerden oluşur:  
  
-   Ortak sınıfları tanımlar.  
  
-   Ortak sınıflar ortak üyeleri ve türetilen sınıflar (diğer bir deyişle, korumalı üyeleri) erişilebilir üyelerinin tanımları tanımları.  
  
-   Parametreler ve genel yöntemlerin ortak sınıflar, parametreler ve dönüş türleri ve yöntemleri türetilmiş sınıflara erişilebilir dönüş türü.  
  
 CLS uyumluluğu için kuralları aşağıdaki tabloda listelenmiştir. Kurallar metin alanından verbatim alınır [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm), telif hakkı 2012 Ecma uluslararası tarafından olduğu. Aşağıdaki bölümlerde bu kuralları hakkında daha ayrıntılı bilgi bulunamadı.  
  
|Kategori|Bkz. |Kural|Kural numarası|  
|--------------|---------|----------|-----------------|  
|Erişilebilirlik|[Üye erişilebilirlik](#MemberAccess)|Erişilebilirlik değil değiştirilmesi geçersiz kılma ne zaman bir yöntemini geçersiz kılma farklı bir derlemeden erişilebilirliği devralınan dışında yöntemleri, devralınan zaman `family-or-assembly`. Bu durumda, geçersiz kılma erişilebilirlik sahip `family`.|10|  
|Erişilebilirlik|[Üye erişilebilirlik](#MemberAccess)|Üye görünür ve erişilebilir olduğunda imza türlerinde herhangi bir üyenin görünür ve erişilebilir olacaktır, görünürlük ve erişilebilirlik türleri ve üyeleri olacaktır. Örneğin, kendi derlemenin dışından görülebilir genel bir yöntem türü yalnızca derlemede görünür olan bir bağımsız değişken sahip. Üye görünür ve erişilebilir olduğunda görünürlük ve herhangi bir üyenin imzada kullanılan bir oluşturulmuş genel tür oluşturma türlerinin erişilebilirlik görünür ve erişilebilir olacaktır. Örneğin, bir oluşturulmuş genel tür imzada mevcut kendi derlemenin dışından görünür bir üyenin türü yalnızca derlemede görünür olan genel bir bağımsız değişken sahip.|12|  
|Diziler|[Diziler](#arrays)|Diziler CLS uyumlu bir türü olan öğeleri sahip ve tüm boyutlar dizinin alt sınırlarını sıfır sahip. Yalnızca bir dizi ve dizi öğesi türü bir öğedir olgu aşırı arasında ayrım yapmak için gerekli. Ne zaman aşırı yüklemesi iki dayalı olan veya daha fazla dizi öğesi türleri türleri adlı.|16|  
|Öznitelikler|[Öznitelikler](#attributes)|Öznitelik türü olacaktır <xref:System.Attribute?displayProperty=nameWithType>, veya ondan devralan bir tür.|41|  
|Öznitelikler|[Öznitelikler](#attributes)|CLS yalnızca bir alt kümesini özel özniteliklerin Kodlamalar izin verir. (Bölüm IV bakın) bu Kodlamalar görünür yalnızca türleri şunlardır: <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> , ve herhangi bir numaralandırma türü CLS uyumlu bir temel tamsayı türünde dayanır.|34|  
|Öznitelikler|[Öznitelikler](#attributes)|CLS herkese görünür gerekli değiştiricileri izin verme (`modreq`, Bölüm II bakın), isteğe bağlı değiştiricileri izin vermez ancak (`modopt`, Bölüm II bakın) anlamadığı.|35|  
|Oluşturucular|[Oluşturucular](#ctors)|Devralınan örnek veriler için herhangi bir erişim oluşmadan önce bir nesne oluşturucusu bazı örnek oluşturucusu olduğu temel sınıfın çağrısı. (Bu oluşturucular olmak zorunda değildir değer türleri için geçerli değildir.)|21|  
|Oluşturucular|[Oluşturucular](#ctors)|Bir nesne Oluşturucusu dışındaki bir nesnenin oluşturmanın bir parçası çağrılması değil ve bir nesne iki kez başlatılmamış.|22|  
|Numaralandırmalar|[Sabit Listeleri](#enums)|Enum temel türü bir yerleşik CLS tamsayı türü olacaktır, alanın adını "value__" olacaktır ve bu alan işaretli `RTSpecialName`.|7|  
|Numaralandırmalar|[Sabit Listeleri](#enums)|Varlığı veya yokluğuna göre tarafından gösterilen Numaralandırmaların iki farklı tür vardır <xref:System.FlagsAttribute?displayProperty=nameWithType> (bkz. Bölüm IV kitaplık) özel bir öznitelik. Bir adlandırılmış tamsayı değerlerini temsil eder; diğer temsil adsız bir değer üretmek için birleştirilmiş bir bit bayrakları adlı. Değeri bir `enum` belirtilen değerlere sınırlı değildir.|8|  
|Numaralandırmalar|[Sabit Listeleri](#enums)|Bir numaralandırma sabit değeri statik alanları ve enum türüne sahip.|9|  
|Olaylar|[Olaylar](#events)|Bir olay uygulamak yöntemleri olarak işaretlenmiş `SpecialName` themetadata içinde.|29|  
|Olaylar|[Olaylar](#events)|Bir olay ve onun erişimciler erişilebilirlik aynı olacaktır.|30|  
|Olaylar|[Olaylar](#events)|`add` Ve `remove` yöntemleri bir olay ya da her ikisini de gelecektir için mevcut olmalı veya belirtilmemelidir.|31|  
|Olaylar|[Olaylar](#events)|`add` Ve `remove` yöntemleri bir olay her bir parametre türü alan için olay türünü tanımlar ve bu türetilen <xref:System.Delegate?displayProperty=nameWithType>.|32|  
|Olaylar|[Olaylar](#events)|Olaylar, belirli bir adlandırma deseni uyması. `SpecialName` CLS kural 29 başvuruda bulunulan öznitelik uygun adı karşılaştırmaları göz ardı ve tanımlayıcı kurallarına.|33|  
|Özel Durumlar|[Özel Durumlar](#exceptions)|Oluşturulan nesnelerin türü olacaktır <xref:System.Exception?displayProperty=nameWithType> veya ondan devralan bir tür. Öte yandan, CLS uyumlu yöntemlerini diğer tür özel durumlar yayılmasını engellemek için gerekli değildir.|40|  
|Genel|[CLS uyumluluğu: kuralları](#Rules)|CLS kuralları erişilebilir veya görünür outsideof tanımlama derleme olan yalnızca parçaları türü için geçerlidir.|1.|  
|Genel|[CLS uyumluluğu: kuralları](#Rules)|CLS dışı uyumlu türleri üyeleri CLS uyumlu olarak işaretlenmemiş.|2|  
|Genel Türler|[Genel türler ve üyeleri](#Generics)|İç içe geçmiş türler en az sayıda genel parametreler kendilerini kapsayan türle sahip. Genel bir iç içe geçmiş tür parametrelerinde kapsayan türü genel parametreler konuma göre karşılık gelir.|42|  
|Genel Türler|[Genel türler ve üyeleri](#Generics)|Genel bir tür adı olmayan iç içe geçmiş türünde bildirilen ya da yeni yukarıda tanımlanan kurallarına göre iç içe yoksa türe giriş türü parametre sayısı kodlayın.|43|  
|Genel Türler|[Genel türler ve üyeleri](#Generics)|Genel bir tür kısıtlamalar temel türü veya arabirimleri tarafından genel tür kısıtlamaları getirilmez güvence altına almak için yeterli kısıtlamaları redeclare.|4444|  
|Genel Türler|[Genel türler ve üyeleri](#Generics)|Genel parametreler üzerinde kısıtlamalar olarak kullanılan türleri kendilerini CLS uyumlu olacaktır.|45|  
|Genel Türler|[Genel türler ve üyeleri](#Generics)|Görünürlük ve bir oluşturulmuş genel tür üyeleri (iç içe geçmiş türler dahil) erişilebilirliğini bir bütün olarak genel tür bildirimi yerine belirli örneklemesi Kapsamınızın dikkate. Bu varsayıldığında, CLS kuralının 12 görünürlük ve erişilebilirlik kuralları hala geçerlidir.|46|  
|Genel Türler|[Genel türler ve üyeleri](#Generics)|Her soyut veya sanal genel yöntemi için bir varsayılan somut (soyut) uygulaması olacaktır.|47|  
|Arabirimler|[Arabirimler](#Interfaces)|Bunları uygulamak için CLS uyumlu arabirimleri CLS olmayan compliantmethods tanımını gerektirmeyecek.|18|  
|Arabirimler|[Arabirimler](#Interfaces)|CLS uyumlu arabirimlerde statik yöntemler tanımlamak değil ya da alanları tanımla.|19|  
|Üyeler|[Genel üyeleri yazın](#members)|Genel statik alanları ve yöntemleri CLS uyumlu değildir.|36|  
|Üyeler|--|Değişmez değer statik değerini alan başlatma meta veri kullanımı ile belirtilir. CLS uyumlu bir sabit değişmez değeri olarak tam olarak aynı türde alan başlatma meta verilerinde belirtilmiş bir değere sahip olmalıdır (veya bu değişmez değeri ise, temel türde bir `enum`).|13|  
|Üyeler|[Genel üyeleri yazın](#members)|Vararg kısıtlaması CLS parçası değildir ve yalnızca çağırma kuralı CLS tarafından desteklenen standart çağırma yönetiliyor.|15|  
|Adlandırma kuralları|[Adlandırma kuralları](#naming)|Derlemeleri eki 7, teknik rapor 15 başlatmak ve tanımlayıcıları, kullanılabilir onlineat dahil edilmesi için izin verilen karakter kümesini yöneten Unicode Standard3.0 izleyin http://www.unicode.org/unicode/reports/tr15/tr15-18.html. Tanımlayıcıları Unicode normalleştirme Form c tarafından tanımlanan thecanonical biçiminde olacaktır CLS amacıyla iki tanımlayıcılara aynı küçük eşlemelerini (Unicode yerel ayar-küçük harfe duyarlı bir toonelowercase eşlemeleri tarafından belirtildiği şekilde) aynı olması durumunda. Diğer bir deyişle, differentunder CLS ele alınması için iki tanımlayıcı bunların birden fazla yalnızca kendi durumda farklı. Ancak, aninherited tanımı geçersiz kılmak için CLI özgün bildirimi kesin kodlama kullanılabilir gerektirir.|4|  
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|Tüm adları CLS uyumlu bir kapsamda tanıtılan aynı ve aşırı yükleme aracılığıyla çözülmüş olduğu dışında ayrı bağımsız ofkind olacaktır. Diğer bir deyişle, bir yöntem ve bir alan için aynı adı kullanmak için tek bir türü CTSallows sırasında CLS desteklemez.|5|  
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|Alanlar ve iç içe geçmiş türler tarafından tanımlayıcı karşılaştırma tek başına farklı olacaktır, ayırt edici olarak ayrı imzaları eventhough CTS sağlar. Yöntemler, özellikler ve olayları sahip aynı adda (tanımlayıcı karşılaştırma) dönüş türüne göre çok daha fazlası farklı dışındaki CLS kural 39 belirtildiği gibi.|6|  
|Aşırı Yükleme|[Overloads](#overloads)|Yalnızca özelliklerini ve yöntemlerini aşırı yüklenmiş.|37|  
|Aşırı Yükleme|[Overloads](#overloads)|Özellikleri ve yöntemleri aşırı yüklenebilir yalnızca sayısı ve türleri adlı dönüşüm işleçleri dışında kendi parametreleri temel `op_Implicit` ve `op_Explicit`, kendi dönüş türüne bağlı olarak, aynı zamanda aşırı yüklenebilir.|38|  
|Aşırı Yükleme|--|Tür tarafından bildirilen iki veya daha fazla CLS uyumlu yöntemler türü örneklemesi, belirli bir dizi için aynı sistemine varsa aynı parametre ve dönüş türleri, thenall bu yöntemler bu tür örneklemesi anlam olarak eşdeğer olacaktır.|48|  
|Türler|[Ve üye imzaları yazın.](#Types)|<xref:System.Object?displayProperty=nameWithType> CLS uyumlu değil. CLS uyumlu herhangi bir sınıf CLS uyumlu bir sınıftan devralınan.|23|  
|Özellikler|[Özellikler](#properties)|Bir özellik shallbe'Set ' yordamı yöntemleri uygulamak yöntemleri işaretlenmiş `SpecialName` meta veriler.|24|  
|Özellikler|[Özellikler](#properties)|Bir özelliğin erişimciler tüm statik olacaktır, tüm sanal veya tüm örneği olmalıdır.|26|  
|Özellikler|[Özellikler](#properties)|Bir özelliğin türünü alıcı dönüş türü ve kurucu son bağımsız değişkeni tür olacaktır. Özelliğin parametre türlerini alıcı ve tüm türleri parametreleri ancak kurucu son parametre türleri olacaktır. Tüm bu tür CLS uyumlu olacaktır ve yönetilen işaretçileri tutulamaz (yani, başvuruya göre geçirilmesi değil).|27|  
|Özellikler|[Özellikler](#properties)|Özellikler, belirli bir adlandırma deseni uyması. `SpecialName` CLS kural 24 başvuruda bulunulan öznitelik uygun adı karşılaştırmaları göz ardı ve tanımlayıcı kurallarına. Özellik alıcısı yöntemi, ayarlayıcı yöntemi veya ikisine birden sahip.|28|  
|Tür dönüştürmeleri|[Tür dönüştürmeleri](#conversion)|Her iki `op_Implicit` veya `op_Explicit` zorlama sağlama alternatif bir yol sağlanan sağlanır.|39|  
|Türler|[Ve üye imzaları yazın.](#Types)|Paketlenmiş değer türleri CLS uyumlu değildir.|3|  
|Türler|[Ve üye imzaları yazın.](#Types)|İmza görünen tüm türleri CLS uyumlu olacaktır. Bir oluşturulmuş genel tür oluşturma tüm türleri CLS uyumlu olacaktır.|11|  
|Türler|[Ve üye imzaları yazın.](#Types)|Belirlenmiş başvurular CLS uyumlu değildir.|14|  
|Türler|[Ve üye imzaları yazın.](#Types)|Yönetilmeyen işaretçi türleri CLS uyumlu değildir.|17|  
|Türler|[Ve üye imzaları yazın.](#Types)|CLS uyumlu sınıfları, değer türleri ve arabirimleri CLS uyumlu olmayan üyeler uyarlamasını gerektirmeyecek.|20|  
  
<a name="Types"></a>   
### <a name="types-and-type-member-signatures"></a>Türleri ve türü üye imzaları  
 <xref:System.Object?displayProperty=nameWithType> Türü CLS uyumlu olduğundan ve .NET Framework türü sistemindeki tüm nesne türlerini taban türü değil. .NET Framework'teki devralma olduğu ya da örtük (örneğin, <xref:System.String> örtük olarak sınıfının devraldığı <xref:System.Object> sınıfı) veya açık (örneğin, <xref:System.Globalization.CultureNotFoundException> açıkça sınıfının devraldığı <xref:System.ArgumentException> sınıfı, hangi açıkça devraldığı <xref:System.SystemException> açıkça devraldığı sınıfı <xref:System.Exception> sınıfı). CLS uyumlu olacak şekilde türetilen tür için temel türü de CLS uyumlu olmalıdır.  
  
 Aşağıdaki örnek, temel türü CLS uyumlu olmayan türetilmiş bir tür gösterir. Bir taban tanımlar `Counter` işaretsiz bir 32 bit tamsayı sayacı olarak kullanan sınıfı. Sınıfı, bir işaretsiz tamsayı kaydırma tarafından sayaç işlevselliği sağladığından, sınıf-CLS uyumlu olmayan olarak işaretlenir. Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter`, ayrıca CLS uyumlu değil.  
  
 [!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
 [!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]  
  
 Bir yöntemin dönüş türü veya bir özellik türü de dahil olmak üzere üye imzalarında görünür tüm türleri CLS ile uyumlu olması gerekir. Ayrıca, genel türleri için:  
  
-   Oluşturulan genel bir tür oluşturan tüm türleri CLS ile uyumlu olması gerekir.  
  
-   Genel parametreler üzerinde kısıtlamalar olarak kullanılan tüm türleri CLS ile uyumlu olması gerekir.  
  
 .NET Framework [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md) bir derlemenin meta verilerde doğrudan ortak dil çalışma zamanı tarafından desteklenir ve özel olarak kodlanmış yerleşik türler içerir. İç bu tür, aşağıdaki tabloda listelenen CLS uyumlu türleridir.  
  
|CLS uyumlu türü|Açıklama|  
|-------------------------|-----------------|  
|<xref:System.Byte>|8 bit işaretsiz tamsayıyı|  
|<xref:System.Int16>|16 bit işaretli tamsayıyı|  
|<xref:System.Int32>|32 bit işaretli tamsayıyı|  
|<xref:System.Int64>|64 bit işaretli tamsayıyı|  
|<xref:System.Single>|Tek duyarlıklı kayan noktalı değeri|  
|<xref:System.Double>|Çift duyarlıklı kayan noktalı değeri|  
|<xref:System.Boolean>|`true` veya `false` değer türü|  
|<xref:System.Char>|UTF-16 kodlu kod birimi|  
|<xref:System.Decimal>|Olmayan kayan noktalı ondalık sayı|  
|<xref:System.IntPtr>|İşaretçi veya platform tarafından tanımlanan bir boyut tanıtıcısı|  
|<xref:System.String>|Sıfır, bir veya daha fazla koleksiyon <xref:System.Char> nesneleri|  
  
 Aşağıdaki tabloda listelenen iç türleri CLS uyumlu değil.  
  
|Uyumlu türü|Açıklama|CLS uyumlu alternatifi|  
|-------------------------|-----------------|--------------------------------|  
|<xref:System.SByte>|8 bit işaretli tamsayıyı veri türü|<xref:System.Int16>|  
|<xref:System.TypedReference>|Bir nesne ve çalışma zamanı türü işaretçi|Yok.|  
|<xref:System.UInt16>|16 bit işaretsiz tamsayıyı|<xref:System.Int32>|  
|<xref:System.UInt32>|32 bit işaretsiz tamsayıyı|<xref:System.Int64>|  
|<xref:System.UInt64>|64 bit işaretsiz tamsayıyı|<xref:System.Int64> (taşma), <xref:System.Numerics.BigInteger>, veya <xref:System.Double>|  
|<xref:System.UIntPtr>|İmzasız işaretçi veya tanıtıcısı|<xref:System.IntPtr>|  
  
 .NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı CLS ile uyumlu olmayan diğer türleri içerebilir; Örneğin:  
  
-   Paketlenmiş değer türleri. Aşağıdaki C# örnek türünde ortak bir özelliği olan bir sınıfı oluşturur `int*` adlı `Value`. Çünkü bir `int*` paketlenmiş değer türü derleyici-CLS uyumlu olmayan olarak işaretler.  
  
     [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]  
  
-   Bir nesneye başvuru ve türüne bir başvuru içeren özel yapılar belirlenmiş başvurular. Belirlenmiş başvurular tarafından .NET Framework'teki temsil <xref:System.TypedReference> sınıfı.  
  
 Bir tür CLS ile uyumlu değilse, uygulamalıdır <xref:System.CLSCompliantAttribute> ile öznitelik bir `isCompliant` değerini `false` ona. Daha fazla bilgi için bkz: [CLSCompliantAttribute özniteliği](#CLSAttribute) bölümü.  
  
 Aşağıdaki örnek, CLS uyumluluğu yöntem imzası ve genel tür oluşturmada sorun gösterilmektedir. Bunu tanımlayan bir `InvoiceItem` türünde bir özellik sınıfıyla <xref:System.UInt32>, türünde bir özellik `Nullable(Of UInt32)`ve türünde parametrelere sahip bir oluşturucu <xref:System.UInt32> ve `Nullable(Of UInt32)`. Bu örneği derlemek çalıştığınızda dört derleyici uyarıları alın.  
  
 [!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
 [!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]  
  
 Derleyici uyarılarını kaldırmak için CLS uyumlu olmayan türler yerini `InvoiceItem` uyumlu türleri olan ortak arabirim:  
  
 [!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
 [!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]  
  
 Listelenen belirli türlerine ek olarak bazı kategorileri türlerinin CLS uyumlu değildir. Bu, yönetilmeyen işaretçi türleri ve işlev işaretçisi türleri içerir. Aşağıdaki örnek, dizisi oluşturmak için bir işaretçi bir tamsayıya kullandığından derleyici uyarısı oluşturur.  
  
 [!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]  
  
 CLS uyumlu için soyut sınıflar (diğer bir deyişle, sınıflar olarak işaretlenmiş `abstract` C# veya olarak `MustInherit` Visual Basic'te), sınıfın tüm üyelerini de CLS ile uyumlu olması gerekir.  
  
<a name="naming"></a>   
### <a name="naming-conventions"></a>Adlandırma kuralları  
 Bazı programlama dilleri büyük/küçük harfe duyarsızdır olduğundan (örneğin, ad alanlarını, türleri ve üyeleri adları) tanımlayıcılar örnekten daha fazla farklı olmalıdır. İki tanımlayıcı küçük eşlemelerini aynıysa eşdeğer olarak değerlendiriliyor. Aşağıdaki C# örnek iki ortak sınıf tanımlar `Person` ve `person`. Yalnızca örneğe göre farklılık gösterdiğinden, C# Derleyici bunları değil CLS uyumlu işaretler.  
  
 [!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]  
  
 Ad alanlarını, türleri ve üyeleri, adları gibi Dil tanımlayıcıları programlama gerekir uygun [Unicode standart 3.0, teknik rapor 15, eki 7](https://www.unicode.org/reports/tr15/tr15-18.html). Bunun anlamı:  
  
-   İlk karakteri bir tanımlayıcı olarak herhangi bir Unicode büyük harf, küçük harf, büyük/küçük harf başlık, değiştiricisi, diğer mektup olması veya numarası harf. Unicode karakter kategorileri hakkında daha fazla bilgi için bkz: <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> numaralandırması.  
  
-   Sonraki karakterler kategorileri hiçbirini ilk karakter olarak olabilir ve aralık birleştirme işaretleri, ondalık sayılar, bağlayıcı noktalama işaretleri ve biçimlendirme kodları aralıksız işaretlerini de içerir.  
  
 Tanımlayıcıları karşılaştırmak önce biçimlendirme veya kodları filtre ve tek bir karakter birden çok UTF-16 kodlu kod birimler tarafından temsil edilebilir bulunduğundan Unicode normalleştirme Form C tanımlayıcıları dönüştürülemiyor. Unicode normalleştirme Form C aynı kodu birimlerinde üretmek karakter sıralarının CLS uyumlu değildir. Aşağıdaki örnek adlı bir özelliğini tanımlar `Å`ANGSTROM işareti (U + 212B) karakterinin oluşur ve ikinci bir özelliğe adlı `Å`, LATIN büyük harf A ile HALKASI YUKARIDA (U + 00 C 5) karakterinin oluşur. C# ve Visual Basic derleyicileri CLS uyumlu olmayan olarak kaynak koduna bayrak.  
  
 [!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
 [!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]  
  
 Üye adlarının (örneğin, ad alanları bir ad alanı içindeki tür veya üye türünde bir derleme içinde) belirli bir kapsam içinde dışında aşırı yükleme aracılığıyla çözülür adları benzersiz olmalıdır. Bu gereksinim, farklı türde üye olduğu sürece, aynı adlara sahip bir kapsamı içinde birden çok üye sağlar ortak tür sistemi daha daha sıkı (örneğin, bir yöntem biridir ve bir alan biridir). Tür üyeleri için özel olarak:  
  
-   Alanlar ve iç içe geçmiş türler adıyla ayırt edilir.  
  
-   Yöntemler, özellikler ve aynı ada sahip olayları birden fazla yalnızca dönüş türüne göre farklı olmalıdır.  
  
 Aşağıdaki örnek üye adlarını kendi kapsamı içinde benzersiz olmalıdır gereksinim gösterilmektedir. Adlı bir sınıf tanımlar `Converter` adlı dört üyeleri içeren `Conversion`. Üç yöntemlerdir ve bir özelliktir. İçeren yöntemi bir <xref:System.Int64> parametresi benzersiz olarak adlandırılır, ancak iki yöntemle bir <xref:System.Int32> parametresi değildir, çünkü dönüş değeri bir üyenin imza bir parçası olarak kabul edilmez. `Conversion` Özelliği özelliklerin aşırı yüklenmiş yöntemler adıyla aynı olduğundan bu gereksinim ayrıca ihlal.  
  
 [!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
 [!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]  
  
 Dilleri hedefleyen ortak dil çalışma zamanı da anahtar sözcükler ile çakıştığı tanımlayıcıları (gibi tür adları) başvuran için bazı mekanizma sağlamanız gerekir benzersiz anahtar sözcükler, tek tek dilleri içerir. Örneğin, `case` hem C# ve Visual Basic bir anahtar sözcüktür. Ancak, aşağıdaki Visual Basic örnek adlı bir sınıf belirsizliğini ortadan kaldırmak mümkün `case` gelen `case` açma ve küme ayraçları kapatma kullanarak anahtar sözcüğü. Aksi takdirde, örnek "Anahtar sözcüğü bir tanımlayıcı olarak geçerli değil" hata iletisi oluşturmak ve bu derlemek başarısız.  
  
 [!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]  
  
 Aşağıdaki C# örnek örneği yapabiliyor `case` kullanarak sınıfı `@` dil anahtar sözcüğünü tanımlayıcıdan belirsizliğini ortadan kaldırmak için simge. Bu olmadan, C# Derleyici iki hata iletileri, "Tür bekleniyor" ve "geçersiz ifade terimi 'case'." görüntüler  
  
 [!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]  
  
<a name="conversion"></a>   
### <a name="type-conversion"></a>Tür dönüştürmeleri  
 Ortak dil belirtimi iki dönüşüm işleçleri tanımlar:  
  
-   `op_Implicit`, hangi veri veya duyarlık kaybına neden değil dönüşümleri için kullanılır. Örneğin, <xref:System.Decimal> yapısı içeren bir aşırı yüklenmiş `op_Implicit` tam sayı türleri değerini dönüştürmek için işleci ve <xref:System.Char> değerler <xref:System.Decimal> değerleri.  
  
-   `op_Explicit`, hangi daraltma (daha küçük bir aralık sahip bir değer için bir değer dönüştürülen) büyüklük veya duyarlık kaybına yol açabilir dönüşümleri için kullanılır. Örneğin, <xref:System.Decimal> yapısı içeren bir aşırı yüklenmiş `op_Explicit` dönüştürmek için işleci <xref:System.Double> ve <xref:System.Single> değerler <xref:System.Decimal> ve dönüştürmek için <xref:System.Decimal> değerlere tam sayı değerleri <xref:System.Double>, <xref:System.Single>, ve <xref:System.Char>.  
  
 Ancak, tüm diller İşleç aşırı yüklemesi ya da özel işleçleri tanımını desteklemez. Bu dönüşüm işleçleri uygulamak isterseniz dönüştürme gerçekleştirmek için alternatif bir yöntem sağlaması gerekir. Sağlamanızı öneririz `From` *Xxx* ve `To` *Xxx* yöntemleri.  
  
 Aşağıdaki örnek, CLS uyumlu örtük ve açık dönüştürmeler tanımlar. Oluşturduğu bir `UDouble` imzalı çift duyarlıklı, kayan noktalı sayıyı temsil eden sınıf. Örtük dönüşümler sağlayan `UDouble` için <xref:System.Double> ve açık dönüştürmeler `UDouble` için <xref:System.Single>, <xref:System.Double> için `UDouble`, ve <xref:System.Single> için `UDouble`. Ayrıca tanımlayan bir `ToDouble` örtük dönüşüm işleci alternatif olarak yöntemi ve `ToSingle`, `FromDouble`, ve `FromSingle` açık dönüşüm işleçleri alternatifleri olarak yöntemler.  
  
 [!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
 [!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]  
  
<a name="arrays"></a>   
### <a name="arrays"></a>Diziler  
 CLS uyumlu diziler aşağıdaki kurallara uygun:  
  
-   Bir dizinin tüm boyutları alt sınırı sıfır olmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan bir dizi alt sınır bir oluşturur. Unutmayın, varlığını rağmen <xref:System.CLSCompliantAttribute> özniteliği derleyici algılamazsa tarafından döndürülen dizi `Numbers.GetTenPrimes` yöntem CLS uyumlu değildir.  
  
     [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
     [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]  
  
-   Tüm dizi öğeleri CLS uyumlu türleri oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan dizileri döndürür iki yöntemleri tanımlar. İlk bir dizi döndürür <xref:System.UInt32> değerleri. İkinci döndürür bir <xref:System.Object> içeren bir dizi <xref:System.Int32> ve <xref:System.UInt32> değerleri. İlk dizi uyumsuz olarak nedeniyle derleyici tanımlasa da, <xref:System.UInt32> türü, başarısız ikinci dizi CLS uyumlu olmayan öğeler içeriyor tanımadığı.  
  
     [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
     [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]  
  
-   Dizi parametrelerine sahip yöntemleri için aşırı yükleme çözünürlüğü diziler oldukları dayanarak açık nedeni olduğunu ve bunların öğe türü bilinmiyor. Bu nedenle, aşırı yüklenmiş bir aşağıdaki tanımını `GetSquares` yöntem CLS uyumlu değil.  
  
     [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
     [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Arabirimler  
 CLS uyumlu arabirimleri özellikleri, olayları ve sanal yöntemler (uygulaması yöntemleriyle) tanımlayabilirsiniz. CLS uyumlu bir arabirim aşağıdakilerden herhangi birini içeremez:  
  
-   Statik yöntemler veya statik alanları. Bir arabirim, statik bir üyenin tanımlarsanız, C# ve Visual Basic derleyicileri derleyici hataları oluşturur.  
  
-   Alanlar. Bir alan bir arabirim tanımlarsanız, C# ve Visual Basic derleyicileri derleyici hataları oluşturur.  
  
-   CLS uyumlu olmayan yöntemleri. Örneğin, aşağıdaki arabirim tanımı bir yöntem içerir `INumber.GetUnsigned`, yani olarak-CLS uyumlu olmayan olarak işaretlenmiş. Bu örnek derleyici uyarısı oluşturur.  
  
     [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
     [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]  
  
     Bu kural nedeniyle CLS uyumlu türleri CLS uyumlu olmayan üyeler uygulamak için gerekli değildir. CLS dışı uyumlu arabirimini uygulayan bir sınıf CLS uyumlu bir çerçeve kullanıma, CLS uyumlu olmayan tüm üyelerin somut uygulamaları da sağlamalıdır.  
  
 CLS uyumlu dil derleyicileri aynı ad ve imza birden çok arabirimlerde sahip üyeler ayrı uygulamalarını için bir sınıf de izin vermeniz gerekir.  Hem C# ve Visual Basic Destek [açık arabirim uygulamaları](~/docs/csharp/programming-guide/interfaces/explicit-interface-implementation.md) aynı adlı yöntemlerin farklı uygulamaları sağlamak için. Visual Basic de destekler `Implements` belirli bir üye hangi arabirimi ve üye açıkça tanımlamanızı sağlayan anahtar sözcüğü uygular. Aşağıdaki örnekte, tanımlayarak bu senaryo gösterilmektedir bir `Temperature` uygulayan sınıf `ICelsius` ve `IFahrenheit` arabirimleri açık arabirim uygulamaları olarak.  
  
 [!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
 [!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]  
  
<a name="enums"></a>   
### <a name="enumerations"></a>Numaralandırmalar  
 CLS uyumlu numaralandırmalar bu kurallara uymalıdır:  
  
-   Temel alınan numaralandırması iç CLS uyumlu Tamsayı türünde olmalıdır (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, veya <xref:System.Int64>). Örneğin, temel alınan türü olan bir numaralandırma tanımlamak aşağıdaki kodu çalışır <xref:System.UInt32> ve derleyici uyarısı oluşturur.  
  
     [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
     [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]  
  
-   Bir numaralandırma türü adlı tek örnek alanı olmalıdır `Value__` ile işaretlenmiş <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> özniteliği. Bu alan değeri örtük olarak başvuru sağlar.  
  
-   Numaralandırma, türü numaralandırma türüyle eşleşen değişmez değer statik alanları içerir. Örneğin, tanımladığınız bir `State` değerlerle numaralandırma `State.On` ve `State.Off`, `State.On` ve `State.Off` türü olan iki değişmez değer statik alanları `State`.  
  
-   Numaralandırmalar iki tür vardır:  
  
    -   Birbirini dışlayan kümesini temsil eden numaralandırma adlı tamsayı değerleri. Bu numaralandırma türü yokluğu tarafından gösterilen <xref:System.FlagsAttribute?displayProperty=nameWithType> özel öznitelik.  
  
    -   Adsız bir değer üretmek için birleştirebilirsiniz bit bayrakları kümesini temsil eden bir numaralandırması. Bu numaralandırma türü varlığını tarafından gösterilen <xref:System.FlagsAttribute?displayProperty=nameWithType> özel öznitelik.  
  
     Daha fazla bilgi için belgelerine bakın <xref:System.Enum> yapısı.  
  
-   Numaralandırma değeri, belirtilen değer aralığı için sınırlı değildir. Diğer bir deyişle, numaralandırma değerlerinin aralığını temel değerini aralığıdır. Kullanabileceğiniz <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> belirtilen bir değeri bir numaralandırma üyesi olup olmadığının yöntemi.  
  
<a name="members"></a>   
### <a name="type-members-in-general"></a>Genel üyeleri yazın  
 Ortak dil belirtimi, tüm alanları ve belirli bir sınıfın bir üyesi olarak erişilecek yöntemleri gerektirir. Bu nedenle, genel statik alanları ve yöntemleri (diğer bir deyişle, statik alanları veya dışında bir türü tanımlanmadı yöntemleri) CLS uyumlu değildir. Genel alan veya yöntem kaynak kodunuzda eklemeye çalışırsanız, C# ve Visual Basic derleyicileri derleyici hatası oluşturur.  
  
 Yalnızca standart çağırma yönetilen ortak dil belirtimi destekler. Yönetilmeyen çağırma kurallarını desteklemez ve değişken bağımsız değişken listeleri yöntemleriyle işaretlenmiş `varargs` anahtar sözcüğü. Standart yönetilen çağırma kuralı ile uyumlu olan değişken bağımsız değişken listeleri için kullanmak <xref:System.ParamArrayAttribute> özniteliği ya da tek tek dil uygulaması gibi `params` C# anahtar sözcüğü ve `ParamArray` Visual Basic anahtar sözcüğü.  
  
<a name="MemberAccess"></a>   
### <a name="member-accessibility"></a>Üye erişilebilirlik  
 Devralınmış bir üyeyi geçersiz kılma bu üyede erişilebilirliğini değiştiremezsiniz. Örneğin, bir taban sınıf ortak yönteminde, türetilmiş bir sınıf içinde özel bir yöntem tarafından değiştirilemiyor. Bir istisna vardır: bir `protected internal` (C# ' ta) veya `Protected Friend` (Visual Basic'te) farklı bir derlemedeki bir türe göre geçersiz bir derleme üyesi. Bu durumda, geçersiz kılma erişilebilirliğini olduğu `Protected`.  
  
 Aşağıdaki örnek hata gösterilmektedir oluşturulan <xref:System.CLSCompliantAttribute> özniteliği `true`, ve `Person`, hangi bir sınıfın türetildiği `Animal`, erişilebilirliğini değiştirmeye çalışırsa `Species` özelliğinden Genel özel. Kendi erişilebilirlik ortak olarak değiştirilirse örnek başarıyla derler.  
  
 [!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
 [!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]  
  
 Bu üye erişilebilir olduğunda imza türlerinde üyenin erişilebilir olması gerekir. Örneğin, bu ortak üyesi özel, korumalı veya dahili türü olan bir parametre içeremez anlamına gelir. Aşağıdaki örnek sonuçları derleyici hatası gösterilmektedir, bir `StringWrapper` sınıfı oluşturucusu kullanıma sunan bir iç `StringOperationType` bir dize değeri nasıl alınmalı belirler numaralandırma değeri.  
  
 [!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
 [!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]  
  
<a name="Generics"></a>   
### <a name="generic-types-and-members"></a>Genel türler ve üyeleri  
 İç içe geçmiş türler, kendilerini kapsayan türle her zaman en az sayıda genel parametrelere sahip. Bunlar, kendilerini kapsayan türle genel parametreler konuma göre karşılık gelir. Genel tür yeni genel parametreler de içerir.  
  
 Genel tür parametreleri içeren bir türde ve iç içe geçmiş türler arasındaki ilişki tek tek dilleri sözdizimi tarafından gizlenmiş olabilir. Aşağıdaki örnekte, genel bir tür `Outer<T>` iki iç içe geçmiş sınıflar içeren `Inner1A` ve `Inner1B<U>`. Çağrıları `ToString` her sınıfının devraldığı yöntemi <xref:System.Object.ToString%2A?displayProperty=nameWithType>, her iç içe geçmiş sınıf kapsayan sınıfı tür parametrelerini içerdiğini gösterir.  
  
 [!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
 [!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]  
  
 Genel tür adları biçiminde kodlanmış *adı\`n*, burada *adı* tür adı \` bir karakter değişmez değeri olduğu ve *n* sayısı Tür parametreleri türü veya, iç içe geçmiş genel türler, sayısı için yeni olarak bildirilen parametreleri sunmuştur. Bu genel tür adları CLS uyumlu bir Kitaplığı'nda genel türler erişmek için yansıma kullanan geliştiriciler öncelikle ilgisini kodlamadır.  
  
 Bir genel kısıtlamalar uyguladıysanız kısıtlamaları da CLS ile uyumlu olması gerektiği kullanılan türleri yazın. Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` yani değil CLS ile uyumlu ve adlı genel bir sınıf `BaseCollection` , tür parametresi öğesinden türetilmelidir `BaseClass`. Ancak çünkü `BaseClass` CLS uyumlu olmayan bir uyarı derleyicisi yayar.  
  
 [!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
 [!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]  
  
 Genel bir tür genel bir temel türden türetilmiş, böylece temel türü kısıtlamaları da karşılanır garanti edebilir kısıtlamalar redeclare gerekir. Aşağıdaki örnek tanımlayan bir `Number<T>` herhangi bir sayısal tür temsil edebilir. Ayrıca tanımlayan bir `FloatingPoint<T>` kayan temsil eden sınıf noktası değeri. Bu kısıtlama geçerli değildir çünkü ancak, Kaynak Kodu derlemek başarısız `Number<T>` (T değeri türü olması gerekir) için `FloatingPoint<T>`.  
  
 [!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
 [!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]  
  
 Kısıtlama eklenirse, örnek başarıyla derlenen `FloatingPoint<T>` sınıfı.  
  
 [!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
 [!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]  
  
 Ortak dil belirtimi, iç içe geçmiş türler için koruyucu örneklemesi başına modeli uygular ve korumalı üyeler. Açık genel türler alanları veya iç içe geçmiş, korumalı bir genel türü belirli bir örnek oluşturma içeren imzaları üyeleriyle gösteremez. Belirli bir örnek oluşturma genel temel sınıf veya arabirim genişletmek olmayan genel türleri, alanlar veya iç içe geçmiş, korumalı bir genel türü farklı bir örnek oluşturma içeren imzaları üyeleriyle gösteremez.  
  
 Aşağıdaki örnek, genel bir tür tanımlar `C1<T>` (veya `C1(Of T)` Visual Basic'te) ve korumalı bir sınıf `C1<T>.N` (veya `C1(Of T).N` Visual Basic'te). `C1<T>` iki yöntemi vardır `M1` ve `M2`. Ancak, `M1` döndürmeye çalışır CLS uyumlu olmadığından bir `C1<int>.N` (veya `C1(Of Integer).N`) C1 nesnesinden\<T > (veya `C1(Of T)`). İkinci sınıfı `C2`, türetildiği `C1<long>` (veya `C1(Of Long)`). İki yöntemi vardır `M3` ve `M4`. `M3` döndürmeye çalışır CLS uyumlu olmadığından bir `C1<int>.N` (veya `C1(Of Integer).N`) öğesinin bir alt nesne `C1<long>`. Dil derleyicileri daha kısıtlayıcı olabileceğini unutmayın. Derlemeye çalıştığında bu örnekte, Visual Basic hata görüntüler. `M4`.  
  
 [!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
 [!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]  
  
<a name="ctors"></a>   
### <a name="constructors"></a>Oluşturucular  
 CLS uyumlu sınıfları ve yapıları oluşturucular bu kurallara uymalıdır:  
  
-   Devralınan örnek veri erişim izni vermeden önce türetilmiş bir sınıf oluşturucusunun olduğu temel sınıfın örneği oluşturucusu çağırmanız gerekir. Taban sınıf oluşturucular kendi türetilmiş sınıflar tarafından devralınır değil due için bu gereksinim olabilir. Bu kural doğrudan devralma desteklemeyen yapıları için geçerli değildir.  
  
     Genellikle, bu kural aşağıdaki örnekte gösterildiği gibi CLS uyumluluğu bağımsız olarak derleyicileri uygulayın. Oluşturduğu bir `Doctor` türetilmiş sınıf bir `Person` sınıfı, ancak `Doctor` sınıfı başarısız çağırmak `Person` devralınan örneği alanları başlatmak için sınıf oluşturucu.  
  
     [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
     [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]  
  
-   Bir nesne oluşturucusu, nesneyi oluşturmak için dışında çağrılamaz. Ayrıca, bir nesne iki kez başlatılamaz. Örneğin, bunun anlamı <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> ve yöntemleri gibi seri durumundan çıkarma <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> oluşturucular çağırmalısınız değil.  
  
<a name="properties"></a>   
### <a name="properties"></a>Özellikler  
 CLS uyumlu türleri özelliklerinde bu kurallara uymalıdır:  
  
-   Özellik ayarlayıcı, bir alıcı ya da her ikisini de olması gerekir. Derlemede, bu özel yöntemleri, ayrı yöntemleri olarak görünürler yani uygulanır (alıcı adlı `get_` *propertyname* ve kurucu `set_` *propertyname*) olarak işaretlenmiş `SpecialName` derlemenin meta verileri. C# ve Visual Basic derleyicileri uygulamak için otomatik olarak gerek kalmadan bu kural zorlama <xref:System.CLSCompliantAttribute> özniteliği.  
  
-   Bir özelliğin özellik alıcısı dönüş türü ve kurucu son bağımsız değişkeni türüdür. Bu tür CLS uyumlu olması gerekir ve bağımsız değişkenler atanamaz özelliğine başvuruya göre (diğer bir deyişle, bunlar yönetilen işaretçileri olamaz).  
  
-   Bir özelliği hem alıcı hem de ayarlayıcı varsa, bunlar hem de sanal olmalıdır hem statik ya da her iki örneği. C# ve Visual Basic derleyicileri otomatik olarak bu kural aracılığıyla kendi özellik tanımı sözdizimi uygulayın.  
  
<a name="events"></a>   
### <a name="events"></a>Olaylar  
 Bir olay adını ve türünü tarafından tanımlanır. Olay türü olay göstermek için kullanılan bir temsilcisidir. Örneğin, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay türüdür <xref:System.ResolveEventHandler>. Olayın kendisi, ek olarak, üç yöntem olay adına göre adlarıyla olayın uygulamasını sağlamak ve olarak işaretlenmiş `SpecialName` derlemenin meta verilerini de:  
  
-   Adlı bir olay işleyicisi eklemek için bir yöntem `add_` *EventName*. Örneğin, abonelik için olay yöntemi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay adlandırılan `add_AssemblyResolve`.  
  
-   Adlı bir olay işleyicisi kaldırmak için bir yöntem `remove_` *EventName*. Örneğin, temizleme yöntemi için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay adlandırılan `remove_AssemblyResolve`.  
  
-   Olay oluştu, belirten yöntemi adlı `raise_` *EventName*.  
  
> [!NOTE]
>  Ortak dil belirtimi'nın kuralları olayları ile ilgili çoğu dil derleyicileri tarafından uygulanan ve Bileşen geliştiriciler için saydamdır.  
  
 Eklemek için yöntemleri, kaldırma ve olayı tetiklenmeden aynı erişilebilirlik olması gerekir. Bunlar ayrıca tüm statik olmalıdır örneği veya sanal. İçin yöntemler ekleme ve kaldırma bir olay türü olay temsilci türü olan bir parametre vardır. Add ve remove yöntemlerini hem de mevcut olmalıdır veya her ikisi de yok.  
  
 Aşağıdaki örnek adlı CLS uyumlu bir sınıfı tanımlar `Temperature` olayını bir `TemperatureChanged` iki okumalar arasında sıcaklık değişikliği değerine eşit veya eşik değeri, olay. `Temperature` Sınıfı açıkça tanımlayan bir `raise_TemperatureChanged` yöntemi olan olay işleyicileri seçmeli olarak çalıştırabilirsiniz.  
  
 [!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
 [!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]  
  
<a name="overloads"></a>   
### <a name="overloads"></a>Aşırı Yüklemeler  
 Ortak dil belirtimi aşırı yüklenmiş üyeler aşağıdaki gereksinimleri getirir:  
  
-   Üyeleri parametrelerin sayısı ve herhangi bir parametre türünü temel alan aşırı yüklenmiş. Çağırma kuralı, dönüş türü, özel değiştiricileri yöntemi veya onun parametresi uygulanır ve parametreleri değere veya başvuruya göre geçirilir dikkate alınmaz zaman overloads arasında ayrım yapma. Adları gereksinim bir kapsam içinde benzersiz olmalıdır, bir örnek için kodu görmek [adlandırma kuralları](#naming) bölümü.  
  
-   Yalnızca özelliklerini ve yöntemlerini aşırı yüklenmiş. Alanlar ve olayları aşırı yüklenemez.  
  
-   Genel yöntemler genel parametrelerini sayısına göre aşırı yüklenmiş.  
  
> [!NOTE]
>  `op_Explicit` Ve `op_Implicit` işleçleri aşırı yükleme çözünürlüğü için bir yöntem imzası parçası değeri dikkate alınmaz döndüren kural istisnalar mevcuttur. Bu iki işleç parametrelerini ve dönüş değerlerine göre aşırı yüklenmiş.  
  
<a name="exceptions"></a>   
### <a name="exceptions"></a>Özel Durumlar  
 Özel durum nesneleri öğesinden türetilmelidir <xref:System.Exception?displayProperty=nameWithType> veya başka bir türden türetilmiş <xref:System.Exception?displayProperty=nameWithType>. Aşağıdaki örnek adlı özel bir sınıf sonuçlara derleyici hatası gösterilmektedir `ErrorClass` özel durum işleme için kullanılır.  
  
 [!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
 [!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]  
  
 Bu hatayı düzeltmek için `ErrorClass` sınıfı öğesinden devralmalıdır <xref:System.Exception?displayProperty=nameWithType>. Ayrıca, `Message` özelliği geçersiz. Aşağıdaki örnek tanımlamak için bu hataları düzeltir bir `ErrorClass` CLS uyumlu sınıfı.  
  
 [!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
 [!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]  
  
<a name="attributes"></a>   
### <a name="attributes"></a>Öznitelikler  
 In.NET Framework derlemeleri özel öznitelikler özel öznitelikleri depolamak ve derlemeler, türleri, üyeleri ve yöntem parametreleri gibi nesneler programlama hakkındaki meta verilerini alma için genişletilebilir bir mekanizma sağlar. Özel öznitelikler öğesinden türetilmelidir <xref:System.Attribute?displayProperty=nameWithType> veya türetilmiş bir türden <xref:System.Attribute?displayProperty=nameWithType>.  
  
 Aşağıdaki örnek, bu kural ihlal ediyor. Bunu tanımlayan bir `NumericAttribute` türünden türemez sınıfı <xref:System.Attribute?displayProperty=nameWithType>. Derleyici Hatası sınıfı tanımlanmadığında yalnızca zaman CLS uyumlu olmayan özniteliği, uygulanan sonuçları unutmayın.  
  
 [!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
 [!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]  
  
 Oluşturucunun ya da CLS uyumlu bir özniteliğin özelliklerini yalnızca şu türleri getirebilir:  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Byte>  
  
-   <xref:System.Char>  
  
-   <xref:System.Double>  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int64>  
  
-   <xref:System.Single>  
  
-   <xref:System.String>  
  
-   <xref:System.Type>  
  
-   Temel alınan türü olan herhangi bir numaralandırma türü <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, veya <xref:System.Int64>.  
  
 Aşağıdaki örnek tanımlayan bir `DescriptionAttribute` öğesinden türetilen sınıf <xref:System.Attribute>. Türünde bir parametre sınıfı kurucusunun `Descriptor`, bu sınıf CLS uyumlu değil. Visual Basic derleyici türünün bir uyarı veya hata yayar ancak C# Derleyici bir uyarı gösterir ancak başarıyla derlenen unutmayın.  
  
 [!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
 [!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]  
  
<a name="CLSAttribute"></a>   
## <a name="the-clscompliantattribute-attribute"></a>CLSCompliantAttribute özniteliği  
 <xref:System.CLSCompliantAttribute> Öznitelik, bir program öğesi ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır. <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> Oluşturucusu içeren tek bir gerekli parametre `isCompliant`, bir program öğesi CLS ile uyumlu olup olmadığını gösterir.  
  
 Derleme zamanında derleyici CLS ile uyumlu olması için varsayılan ve bir uyarı yayar uyumlu olmayan öğeler algılar. Derleyici uyarıları türler veya uyumlu olması için açıkça bildirilen üyeler için yayma değil.  
  
 Bileşen geliştiricileri kullanabilir <xref:System.CLSCompliantAttribute> öznitelik iki yolla:  
  
-   CLS uyumlu bir bileşen tarafından kullanıma sunulan ortak arabirimi bölümlerini ve CLS uyumlu olmayan bölümleri tanımlamak için. Kullanımı öznitelik belirli programın öğeleri CLS ile uyumlu işaretlemek için kullanıldığında, bu öğeleri tüm diller ve .NET Framework hedefleyen Araçlar menüsünden erişilebilir olduğunu güvence altına alır.  
  
-   Bileşen kitaplığın ortak arabirim, CLS uyumlu program öğelerini oluşturduğuna emin olmak için. Öğeleri CLS ile uyumlu değilse, derleyicileri genellikle bir uyarı verecek.  
  
> [!WARNING]
>  Bazı durumlarda, dil derleyicileri mi bakılmaksızın CLS uyumlu kuralları zorla <xref:System.CLSCompliantAttribute> özniteliği kullanılır. Örneğin, bir arabirim, statik bir üyenin tanımlama CLS kuralını ihlal ediyor. Tanımlarsanız bu şekilde, bir `static` (C# ' ta) veya `Shared` (Visual Basic'te) bir arabirim üye, hem C# ve Visual Basic derleyicileri bir hata iletisi görüntülenir ve uygulama derlemek başarısız olur.  
  
 <xref:System.CLSCompliantAttribute> Özniteliği ile işaretlenmiş bir <xref:System.AttributeUsageAttribute> değerine sahip öznitelik <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Bu değer uygulamanıza imkan sağlayan <xref:System.CLSCompliantAttribute> özniteliği derlemeler, modüller de dahil olmak üzere herhangi bir program öğesi için türleri (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), üyeleri (Oluşturucular, yöntemler, özellikler, alanları ve olaylar), yazın Parametreler, genel parametreler ve dönüş değerleri. Bununla birlikte, pratikte, öznitelik yalnızca derlemeler, türleri ve tür üyeleri uygulamalıdır. Aksi takdirde derleyicileri öznitelik yoksay ve her genel parametresi, uyumlu olmayan bir parametre karşılaştığınız veya dönüş değeri kitaplığınızın ortak arabiriminde derleyici uyarıları oluşturmaya devam.  
  
 Değeri <xref:System.CLSCompliantAttribute> özniteliği kapsanan program öğeleri tarafından devralınır. Bir derlemeyi CLS ile uyumlu işaretlenmişse, örneğin, türlerinden ayrıca CLS uyumlu değildir. Bir tür CLS ile uyumlu işaretlenmişse, kendi iç içe geçmiş türler ve üyeleri ayrıca CLS uyumlu değildir.  
  
 Devralınan uyumluluk uygulayarak açıkça geçersiz kılabilirsiniz <xref:System.CLSCompliantAttribute> özniteliği kapsanan bir program öğesi için. Örneğin, kullanabileceğiniz <xref:System.CLSCompliantAttribute> ile öznitelik bir `isCompliant` değerini `false` uyumlu bir derleme ve, uyumlu olmayan bir tür tanımlamak için öznitelik kullanabilirsiniz bir `isCompliant` değerini `true` uyumlu bir türü tanımlamak için bir uyumlu olmayan derleme. Ayrıca, uyumlu bir türü uyumlu olmayan üyeler tanımlayabilirsiniz. Ancak, dolayısıyla özniteliğiyle kullanamaz uyumlu üyeler uyumlu olmayan bir türü olamaz bir `isCompliant` değerini `true` uyumlu olmayan türünden devralma geçersiz kılmak için.  
  
 Bileşenleri geliştirirken, her zaman kullanmalısınız <xref:System.CLSCompliantAttribute> derlemenizi, kendi türleri ve üyeleri CLS ile uyumlu olup olmadığını belirtmek için öznitelik.  
  
 CLS uyumlu bileşenleri oluşturmak için:  
  
1.  Kullanım <xref:System.CLSCompliantAttribute> Derleme CLS uyumlu olarak işaretlemek için.  
  
2.  CLS uyumlu olarak uyumlu olmayan derlemesindeki genel olarak sunulan türler işaretleyin.  
  
3.  CLS uyumlu türleri uyumsuz olarak genel kullanıma sunulan tüm üyelerinde işaretleyin.  
  
4.  CLS uyumlu alternatifi CLS uyumlu olmayan üyeler için sağlar.  
  
 Tüm uyumlu olmayan türleri ve üyeleri başarıyla işaretlediyseniz, derleyici hiçbir uyumsuzluk uyarıları yayma değil. Ancak, hangi üyeleri CLS uyumlu değildir ve bunların CLS uyumlu alternatifleri, ürün belgelerinde listesinde belirtmeniz gerekir.  
  
 Aşağıdaki örnek kullanır <xref:System.CLSCompliantAttribute> CLS uyumlu bir derleme ve bir tür tanımlamak için öznitelik `CharacterUtilities`, iki CLS uyumlu olmayan üyeler içeriyor. Her iki üyeleri ile etiketlenir çünkü `CLSCompliant(false)` özniteliği, derleyici hiçbir uyarılar üretir. Sınıf, CLS uyumlu alternatifi için iki yöntem de sağlar. Normalde, biz yalnızca iki aşırı eklediğiniz `ToUTF16` yöntem CLS uyumlu alternatifleri sağlayın. Ancak, dönüş değerini temel yöntemlerini aşırı yüklenemez olduğundan, uyumlu olmayan yöntemleri adlarından adları CLS uyumlu yöntemlerin farklıdır.  
  
 [!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
 [!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]  
  
 Varsa (diğer bir deyişle, türler veya diğer uygulama geliştiriciler tarafından kullanılan üyeler gösterme değil ise) bir kitaplık yerine bir uygulama geliştirdiğiniz, uygulamanızı tüketen program öğelerin CLS uyumluluğu ilgi yalnızca dilinizi bunları desteklemiyorsa . Bu durumda, CLS uyumlu olmayan bir öğe kullanmaya çalıştığınızda, dil derleyici bir hata oluşturur.  
  
<a name="CrossLang"></a>   
## <a name="cross-language-interoperability"></a>Diller Arası Birlikte Çalışabilirlik  
 Dil bağımsızlığının birkaç olası anlamı vardır. Makalede açıklanan bir anlamı [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md), sorunsuz bir şekilde başka bir dilde bir uygulamadan bir dilinde yazılmış türleri tüketen içerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.  
  
 Aşağıdaki örnekte, iki sınıf içerir Utilities.dll adlı bir sınıf kitaplığı oluşturarak diller arası birlikte çalışabilirlik gösterilmektedir `NumericLib` ve `StringLib`. `NumericLib` Sınıfı yazılır C# ' ta ve `StringLib` sınıfı, Visual Basic'te yazılır. Aşağıda `ToTitleCase` sınıfında tek bir üye, `StringLib`, içeren StringUtil.vb için kaynak kodu verilmiştir.  
  
 [!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]  
  
 Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.  
  
 [!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]  
  
 Tek bir derleme iki sınıflarda paketlemek için modüllerine derlemesi gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:  
  
```  
vbc /t:module StringUtil.vb   
```  
  
 Visual Basic derleyici komut satırı sözdizimi hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
 C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:  
  
```  
csc /t:module NumberUtil.cs  
```  
  
 C# derleyici komut satırı sözdizimi hakkında daha fazla bilgi için bkz: [komut satırı yapı ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
 Daha sonra [bağlantı aracını (Link.exe)](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129) iki modülleri derlemeye derlemek için:  
  
```  
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll   
```  
  
 Aşağıdaki örnek daha sonra çağırır `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemleri. Visual Basic kodu ve C# kodu her iki sınıfları yöntemleri erişebilir olduğuna dikkat edin.  
  
 [!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
 [!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]  
  
 Visual Basic kodunu derlemek için bu komutu kullanın:  
  
```  
vbc example.vb /r:UtilityLib.dll  
```  
  
 C# ile derlemek için derleyiciden adını değiştirmek **vbc** için **csc**ve dosya uzantısı için .cs .vb değiştirin:  
  
```  
csc example.cs /r:UtilityLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.CLSCompliantAttribute>
