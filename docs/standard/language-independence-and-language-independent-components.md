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
ms.openlocfilehash: aa569c0da5b963243596ef440ef37c08b4fae37f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288244"
---
# <a name="language-independence-and-language-independent-components"></a>Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler

.NET Framework dilden bağımsızdır. Yani, geliştirici olarak C#, C++/CLı, Eiffel, F #, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL ve Windows PowerShell gibi .NET Framework hedefleyen birçok dilden birinde geliştirme yapabilirsiniz. .NET Framework için geliştirilen sınıf kitaplıklarının türlerine ve üyelerine, başlangıçta yazıldığı dili ve özgün dilin kurallarından herhangi birini izlemeniz gerekmeden erişebilirsiniz. Bileşen geliştiricisiyseniz, kendi dilinden bağımsız olarak herhangi bir .NET Framework uygulaması tarafından erişilebilir.

> [!NOTE]
> Bu makalenin ilk bölümü, dilden bağımsız bileşenler (yani, herhangi bir dilde yazılmış uygulamalar tarafından tüketilen bileşenler) oluşturmayı tartışır. Ayrıca, birden çok dilde yazılmış kaynak kodundan tek bir bileşen veya uygulama oluşturabilirsiniz; Bu makalenin ikinci bölümünde [Diller arası birlikte çalışabilirlik](#CrossLang) bölümüne bakın.

Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşimde bulunmak için, nesneler yalnızca tüm diller için ortak olan özellikleri çağıranlar halinde kullanıma sunmalıdır. Bu ortak özellikler kümesi, oluşturulan derlemeler için uygulanan bir dizi kural olan ortak dil belirtimi (CLS) tarafından tanımlanır. Ortak dil belirtimi, [ECMA-335 Standardı: ortak dil altyapısının](https://www.ecma-international.org/publications/standards/Ecma-335.htm), Bölüm ı, yan tümceler 7 ila 11 ' de tanımlanmıştır.

Bileşeniniz Ortak dil belirtimine uyuyorsa, CLS uyumlu olması garantilenir ve CLS 'yi destekleyen herhangi bir programlama dilinde yazılan derlemelerdeki koddan erişilebilir. Kaynak kodunuza özniteliğini uygulayarak, bileşeninizin derleme zamanında ortak dil belirtimine uygun olup olmadığını belirleyebilirsiniz <xref:System.CLSCompliantAttribute> . Daha fazla bilgi için bkz. [CLSCompliantAttribute özniteliği](#CLSAttribute).

Bu makalede:

- [CLS Uyumluluk kuralları](#Rules)

  - [Türler ve tür üye imzaları](#Types)

  - [Adlandırma kuralları](#naming)

  - [Tür dönüştürme](#conversion)

  - [Diziler](#arrays)

  - [Arabirimler](#Interfaces)

  - [Numaralandırmalar](#enums)

  - [Genel olarak tür üyeleri](#members)

  - [Üye erişilebilirliği](#MemberAccess)

  - [Genel türler ve Üyeler](#Generics)

  - [Oluşturucular](#ctors)

  - [Özellikler](#properties)

  - [Ekinlikler](#events)

  - [Aşırı Yüklemeler](#overloads)

  - [Özel durumlar](#exceptions)

  - [Öznitelikler](#attributes)

- [CLSCompliantAttribute özniteliği](#CLSAttribute)

- [Diller Arası Birlikte Çalışabilirlik](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>CLS Uyumluluk kuralları

Bu bölümde, CLS uyumlu bir bileşen oluşturmak için kurallar açıklanmaktadır. Kuralların tam bir listesi için, bkz. [ECMA-335 standart: ortak dil altyapısının](https://www.ecma-international.org/publications/standards/Ecma-335.htm)bölüm ı, yan tümcesi 11.

> [!NOTE]
> Ortak dil belirtimi, tüketiciler (CLS uyumlu bir bileşene programlı olarak erişen geliştiriciler), çerçeveler (CLS uyumlu kitaplıklar oluşturmak için bir dil derleyicisi kullanan geliştiriciler) ve Extender 'lar (bir dil derleyicisi veya CLS uyumlu bileşenler oluşturan bir kod ayrıştırıcısı gibi bir araç oluşturan geliştiriciler) için geçerli olduğu için her bir kuralı CLS uyumluluğu için tartışır. Bu makale, çerçeveler için uygulanan kurallara odaklanır. Ancak, Extender 'lara uygulanan kuralların bazılarının, yansıma. yayma kullanılarak oluşturulan derlemeler için de uygulanabilir olabileceğini unutmayın.

Dilden bağımsız bir bileşen tasarlamak için, yalnızca bileşenin ortak arabirimine CLS uyumluluğu için kuralları uygulamanız gerekir. Özel uygulamanızın belirtimine uyması gerekmez.

> [!IMPORTANT]
> CLS uyumluluğu kuralları yalnızca bileşenin ortak arabirimine uygulanır, özel uygulamasına uygulanmaz.

Örneğin, dışındaki işaretsiz tamsayılar <xref:System.Byte> CLS uyumlu değildir. `Person`Aşağıdaki örnekteki sınıfı türünde bir özelliği kullanıma sunduğundan `Age` <xref:System.UInt16> , aşağıdaki kod bir derleyici uyarısı görüntüler.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

`Person` `Age` Özelliğinin türünü <xref:System.UInt16> olarak değiştirerek <xref:System.Int16> , CLS uyumlu, 16 bit işaretli bir tamsayı olan sınıfından bir sınıfı CLS uyumlu hale getirebilirsiniz. Özel alanın türünü değiştirmek zorunda değilsiniz `personAge` .

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Kitaplığın ortak arabirimi aşağıdakilerden oluşur:

- Ortak sınıfların tanımları.

- Ortak sınıfların genel üyelerinin ve türetilmiş sınıfların erişebileceği üyelerin tanımlarının tanımları (yani, korumalı üyeler).

- Ortak sınıfların ortak yöntemlerinin parametreleri ve dönüş türleri, parametreleri ve türetilmiş sınıflar tarafından erişilebilen yöntemlerin dönüş türleri.

CLS uyumluluğu kuralları aşağıdaki tabloda listelenmiştir. Kuralların metni, telif hakkı 2012 olan [ECMA-335 Standardı: ortak dil altyapısından](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(Ecma International göre) alınır. Bu kurallar hakkında daha ayrıntılı bilgi aşağıdaki bölümlerde bulunur.

|Kategori|Bkz.|Kural|Kural numarası|
|--------------|---------|----------|-----------------|
|Erişilebilirlik|[Üye erişilebilirliği](#MemberAccess)|Erişilebilirlik ile farklı bir derlemeden devralınan bir yöntemi geçersiz kılmanın dışında, devralınan Yöntemler geçersiz kılınırken erişilebilirlik değiştirilmez `family-or-assembly` . Bu durumda, geçersiz kılma erişilebilirliği olacaktır `family` .|10|
|Erişilebilirlik|[Üye erişilebilirliği](#MemberAccess)|Türlerin ve üyelerin görünürlüğü ve erişilebilirliği, üyenin görünür ve erişilebilir olduğu her üyenin İmzasındaki türlerin görünür ve erişilebilir olması gibi olacaktır. Örneğin, kendi derlemesi dışında görünen bir genel yöntem, türü yalnızca derleme içinde görünür olan bir bağımsız değişkene sahip olamaz. Herhangi bir Üyenin imzasında kullanılan bir örneklenmiş genel tür oluşturan türlerin görünürlüğü ve erişilebilirliği, üyenin görünür ve erişilebilir olduğu her durumda görünür ve erişilebilir olur. Örneğin, kendi derlemesi dışında görünen bir Üyenin imzasında bulunan bir örneklenmiş genel tür, türü yalnızca derleme içinde görünür olan genel bir bağımsız değişkene sahip olamaz.|12|
|Diziler|[Diziler](#arrays)|Diziler CLS uyumlu bir türe sahip öğeler içermelidir ve dizinin tüm boyutları daha düşük sınırlara sahip olacaktır. Yalnızca bir öğenin dizi olması ve dizinin öğe türü, aşırı yüklemeleri ayırt etmek için gerekli olacaktır. Aşırı yükleme iki veya daha fazla dizi türünü temel aldığı zaman, öğe türleri adlandırılmış türler olacaktır.|16|
|Öznitelikler|[Öznitelikler](#attributes)|Öznitelikler türünde <xref:System.Attribute?displayProperty=nameWithType> veya devralan bir türden olmalıdır.|41|
|Öznitelikler|[Öznitelikler](#attributes)|CLS yalnızca özel özniteliklerin kodlamalarının bir alt kümesine izin verir. Bu kodlarda görünecek tek türler (bkz. Bölüm IV): <xref:System.Type?displayProperty=nameWithType> ,,,,,, <xref:System.String?displayProperty=nameWithType> <xref:System.Char?displayProperty=nameWithType> <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Byte?displayProperty=nameWithType> <xref:System.Int16?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Int64?displayProperty=nameWithType> , <xref:System.Single?displayProperty=nameWithType> , <xref:System.Double?displayProperty=nameWithType> ve CLS uyumlu bir taban tamsayı türüne göre herhangi bir numaralandırma türü.|34|
|Öznitelikler|[Öznitelikler](#attributes)|CLS, herkese açık bir şekilde görünür gerekli değiştiricilere izin vermez (bkz. `modreq` Bölüm II), ancak isteğe bağlı değiştiricilere izin veriyor ( `modopt` , bkz. Bölüm II).|35|
|Oluşturucular|[Oluşturucular](#ctors)|Bir nesne Oluşturucusu, devralınan örnek verilerine herhangi bir erişim gerçekleşmeden önce temel sınıfının bazı örnek oluşturucusunu çağırmalıdır. (Bu, oluşturucuların olmaması gereken değer türleri için de geçerlidir.)|21|
|Oluşturucular|[Oluşturucular](#ctors)|Bir nesne Oluşturucusu, bir nesne oluşturmanın parçası hariç çağrılmamalıdır ve bir nesne iki kez başlatılamaz.|22|
|Numaralandırmalar|[Numaralandırmalar](#enums)|Bir numaralandırmanın temel alınan türü yerleşik bir CLS tamsayı türü olacaktır, alanın adı "value__" ve bu alan işaretlenir `RTSpecialName` .|7|
|Numaralandırmalar|[Numaralandırmalar](#enums)|<xref:System.FlagsAttribute?displayProperty=nameWithType>(Bkz. PARTITION IV Library) özel özniteliğinin varlığı veya yokluğu ile belirtilen iki farklı tür numaralandırmalar vardır. Biri adlandırılmış tamsayı değerlerini temsil eder; diğeri adlandırılmamış bir değer oluşturmak için birleştirilebilen adlandırılmış bit bayraklarını temsil eder. Öğesinin değeri `enum` belirtilen değerlerle sınırlı değil.|8|
|Numaralandırmalar|[Numaralandırmalar](#enums)|Sabit listesinin değişmez statik alanları, sabit listesinin kendi türüne sahip olacaktır.|9|
|Ekinlikler|[Ekinlikler](#events)|Bir olayı uygulayan yöntemler `SpecialName` meta verilerde işaretlenir.|29|
|Ekinlikler|[Ekinlikler](#events)|Bir olayın ve erişimcilerinin erişilebilirliği aynı olacaktır.|30|
|Ekinlikler|[Ekinlikler](#events)|`add` `remove` Bir olay için ve yöntemlerinin her ikisi de mevcut ya da yok olacaktır.|31|
|Ekinlikler|[Ekinlikler](#events)|`add` `remove` Bir olay için ve yöntemlerinin her biri, türü olay türünü tanımlayan ve öğesinden türetilebilecek bir parametre alır <xref:System.Delegate?displayProperty=nameWithType> .|32|
|Ekinlikler|[Ekinlikler](#events)|Olaylar belirli bir adlandırma düzenine bağlı olacaktır. `SpecialName`CLS kuralı 29 ' da başvuruda bulunulan öznitelik, uygun ad karşılaştırmaları içinde yok sayılacak ve tanımlayıcı kurallarına uymalecektir.|33|
|Özel durumlar|[Özel durumlar](#exceptions)|Oluşturulan nesneler türünden <xref:System.Exception?displayProperty=nameWithType> veya devralan bir türden olacaktır. Nonetheless, diğer özel durum türlerinin yayılmasını engellemek için CLS uyumlu yöntemler gerekli değildir.|40|
|Genel|[CLS uyumluluğu: kurallar](#Rules)|CLS kuralları yalnızca, tanımlayıcı derlemenin dışında erişilebilen veya görülebilen bir türün bölümleri için geçerlidir.|1|
|Genel|[CLS uyumluluğu: kurallar](#Rules)|CLS olmayan uyumlu türlerin üyeleri CLS uyumlu olarak işaretlenmemelidir.|2|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|İç içe türler, kapsayan tür olarak en az sayıda genel parametreye sahip olacaktır. İç içe bir türdeki genel parametreler, kapsayan türünün genel parametrelerine konum ile karşılık gelir.|42|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Genel bir türün adı, iç içe olmayan türde belirtilen tür parametrelerinin sayısını kodlayıp, yukarıda tanımlanan kurallara göre iç içe geçmiş tür parametrelerinin yeni tanıtılmasıyla belirtilir.|43|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Genel bir tür, temel türdeki kısıtlamaların veya arabirimlerin genel tür kısıtlamaları tarafından karşılanabileceğini güvence altına almak için yeterli kısıtlamaları yeniden bildirir.|4444|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Genel parametrelerde kısıtlama olarak kullanılan türler, CLS uyumlu olacaktır.|45|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Bir örneklenmiş genel türdeki üyelerin görünürlük ve erişilebilirliği, bir bütün olarak genel tür bildirimi yerine belirli bir örnek oluşturma kapsamına alınır. Bunun varsayılarak, CLS kuralı 12 ' nin görünürlük ve erişilebilirlik kuralları hala geçerlidir.|46|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Her soyut veya sanal genel yöntem için, varsayılan somut (soyut olmayan) bir uygulama olacaktır.|47|
|Arabirimler|[Arabirimler](#Interfaces)|CLS uyumlu arabirimler, CLS uyumlu olmayan yöntemlerin uygulanması için tanımı gerektirmez.|18|
|Arabirimler|[Arabirimler](#Interfaces)|CLS uyumlu arabirimler statik yöntemler tanımlamaz ve alanları tanımlayamazlar.|19|
|Üyeler|[Genel olarak tür üyeleri](#members)|Genel statik alanlar ve yöntemler CLS uyumlu değildir.|36|
|Üyeler|--|Bir sabit değer statik değeri, alan başlatma meta verilerinin kullanımı aracılığıyla belirtilir. CLS uyumlu bir sabit değeri, alan başlatma meta verilerinde tam olarak aynı türde (ya da değişmez değer ise) bir değere sahip olmalıdır `enum` .|13|
|Üyeler|[Genel olarak tür üyeleri](#members)|Vararg kısıtlaması CLS kapsamında değildir ve CLS tarafından desteklenen tek çağırma kuralı Standart yönetilen çağırma kuralıdır.|15|
|Adlandırma kuralları|[Adlandırma kuralları](#naming)|Derlemeler, ' de çevrimiçi olarak kullanılabilir olan ve tanımlayıcılara dahil edilip edilmelerine izin verilen karakter kümesini yöneten Unicode standart 3.0 'ın ek 7 Technical Report 15 ' i izler <https://www.unicode.org/unicode/reports/tr15/tr15-18.html> . Tanımlayıcılar Unicode normalleştirme biçimi C tarafından tanımlanan kurallı biçimde olacaktır. CLS amacıyla, küçük harfli eşlemelerde (Unicode yerel ayarı duyarsız, bire bir küçük harf eşleştirmelerde belirtildiği gibi) iki tanımlayıcı aynıdır. Diğer bir deyişle, iki tanımlayıcı CLS kapsamında farklı olarak kabul edilmelidir, ancak büyük küçük harf bakımından farklılık gösterir. Ancak, devralınan bir tanımı geçersiz kılmak için CLı, özgün bildirimin kesin kodlamasının kullanılmasını gerektirir.|4|
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|CLS uyumlu bir kapsamda sunulan tüm adlar, adların özdeş ve aşırı yükleme yoluyla çözümlenme dışında, türden bağımsız olacaktır. Diğer bir deyişle, Cts, tek bir türün bir yöntem ve bir alan için aynı adı kullanmasına izin veriyorsa, CLS değildir.|5|
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|CTS ayrı imzaların ayırt etmesine izin verdiğinden bağımsız olarak, alanlar ve iç içe türler tanımlayıcı karşılaştırmaya göre birbirinden ayrı olacaktır. Aynı ada (tanımlayıcı karşılaştırmaya göre) sahip Yöntemler, Özellikler ve olaylar, yalnızca dönüş türünden daha fazla farklı olacaktır, bu da CLS kuralı 39 ' de belirtilmeleridir.|6|
|Aşırı Yükleme|[Aşırı Yüklemeler](#overloads)|Yalnızca özellikler ve yöntemler aşırı yüklenebilir.|37|
|Aşırı Yükleme|[Aşırı Yüklemeler](#overloads)|Özellikler ve yöntemler yalnızca parametrelerinin sayısı ve türleri temel alınarak aşırı yüklenebilir, ve adlı dönüştürme işleçleri, `op_Implicit` `op_Explicit` dönüş türlerine göre de aşırı yüklenebilir.|38|
|Aşırı Yükleme|--|Bir tür içinde belirtilen iki veya daha fazla CLS uyumlu Yöntem aynı ada sahiptir ve belirli bir tür örneklemesiyse, aynı parametre ve dönüş türlerine sahiptirler, tüm bu yöntemler bu tür örneklemelerinden anlam açısından eşdeğerdir.|48|
|Türler|[Tür ve tür üye imzaları](#Types)|<xref:System.Object?displayProperty=nameWithType>CLS uyumludur. Diğer CLS uyumlu sınıflar, CLS uyumlu bir sınıftan devralınır.|23|
|Özellikler|[Özellikler](#properties)|Bir özelliğin alıcı ve ayarlayıcı yöntemlerini uygulayan yöntemler `SpecialName` meta verilerde işaretlenir.|24|
|Özellikler|[Özellikler](#properties)|Bir özelliğin erişimcileri statik, hepsi sanal veya hepsi örnek olmalıdır.|26|
|Özellikler|[Özellikler](#properties)|Bir özelliğin türü, alıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türü olacaktır. Özelliğin parametre türleri, alıcı parametrelerinin türleri ve ayarlayıcının son parametresi hariç tüm türleri olacaktır. Bu türlerin hepsi CLS uyumlu olur ve yönetilen işaretçiler olmaz (yani, başvuruya göre geçirilmemelidir).|27|
|Özellikler|[Özellikler](#properties)|Özellikler belirli bir adlandırma düzenine bağlı olacaktır. `SpecialName`CLS kuralı 24 ' te başvuruda bulunulan öznitelik, uygun ad karşılaştırmaları içinde yok sayılacak ve tanımlayıcı kurallarına uymalecektir. Bir özelliğin alıcı yöntemi, ayarlayıcı yöntemi veya her ikisi de olmalıdır.|28|
|Tür dönüştürme|[Tür dönüştürme](#conversion)|Ya da `op_Implicit` `op_Explicit` sağlanmışsa, zorlamasının sağlanması için alternatif bir yol sağlanmalıdır.|39|
|Türler|[Tür ve tür üye imzaları](#Types)|Paketlenmiş değer türleri CLS uyumlu değildir.|3|
|Türler|[Tür ve tür üye imzaları](#Types)|Bir imzada görünen tüm türler CLS uyumlu olacaktır. Örneklenmiş genel bir tür oluşturan tüm türler CLS uyumlu olacaktır.|11|
|Türler|[Tür ve tür üye imzaları](#Types)|Yazılan başvurular CLS uyumlu değildir.|14|
|Türler|[Tür ve tür üye imzaları](#Types)|Yönetilmeyen işaretçi türleri CLS uyumlu değildir.|17|
|Türler|[Tür ve tür üye imzaları](#Types)|CLS uyumlu sınıflar, değer türleri ve arabirimler, CLS uyumlu olmayan üyelerin uygulanmasını gerektirmez.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Türler ve tür üye imzaları

<xref:System.Object?displayProperty=nameWithType>Tür CLS uyumludur ve .NET Framework türü sistemindeki tüm nesne türlerinin temel türüdür. .NET Framework devralma örtük olarak (örneğin, <xref:System.String> sınıf dolaylı olarak <xref:System.Object> sınıfından devralır) veya açık (örneğin, sınıfı açıkça sınıfından devralınan sınıfından açıkça devralan sınıfından açıkça devralır <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException> <xref:System.SystemException> <xref:System.Exception> ). Türetilmiş bir türün CLS uyumlu olması için, taban türünün de CLS uyumlu olması gerekir.

Aşağıdaki örnek, temel türü CLS uyumlu olmayan türetilmiş bir türü gösterir. `Counter`İşaretsiz 32 bitlik bir tamsayıyı sayaç olarak kullanan bir temel sınıf tanımlar. Sınıfı işaretsiz bir tamsayı sarmalayarak sayaç işlevselliği sağladığından, sınıf CLS uyumlu değil olarak işaretlenir. Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter` de CLS uyumlu değildir.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Bir yöntemin dönüş türü veya özellik türü de dahil olmak üzere üye imzalarında görünen tüm türler CLS uyumlu olmalıdır. Bunlara ek olarak, genel türler için:

- Bir örneklenmiş genel tür oluşturan tüm türler CLS uyumlu olmalıdır.

- Genel parametrelerde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır.

.NET Framework [ortak tür sistemi](base-types/common-type-system.md) , doğrudan ortak dil çalışma zamanı tarafından desteklenen ve bir derlemenin meta verilerinde özel olarak kodlanmış bir dizi yerleşik tür içerir. Bu iç türlerin, aşağıdaki tabloda listelenen türler CLS uyumludur.

|CLS uyumlu tür|Description|
|-------------------------|-----------------|
|<xref:System.Byte>|8 bit işaretsiz tamsayı|
|<xref:System.Int16>|16 bit işaretli tamsayı|
|<xref:System.Int32>|32-bit işaretli tamsayı|
|<xref:System.Int64>|64-bit işaretli tamsayı|
|<xref:System.Single>|Tek duyarlıklı kayan nokta değeri|
|<xref:System.Double>|Çift duyarlıklı kayan nokta değeri|
|<xref:System.Boolean>|`true`veya `false` değer türü|
|<xref:System.Char>|UTF-16 kodlu kod birimi|
|<xref:System.Decimal>|Kayan nokta olmayan ondalık sayı|
|<xref:System.IntPtr>|Platform tanımlı boyutun işaretçisi veya işleyicisi|
|<xref:System.String>|Sıfır, bir veya daha fazla nesne koleksiyonu <xref:System.Char>|

Aşağıdaki tabloda listelenen iç türler CLS uyumlu değildir.

|Uyumlu olmayan tür|Description|CLS uyumlu alternatif|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|8 bit işaretli tamsayı veri türü|<xref:System.Int16>|
|<xref:System.TypedReference>|Bir nesne ve onun çalışma zamanı türü işaretçisi|Hiçbiri|
|<xref:System.UInt16>|16 bit işaretsiz tamsayı|<xref:System.Int32>|
|<xref:System.UInt32>|32-bit işaretsiz tamsayı|<xref:System.Int64>|
|<xref:System.UInt64>|64-bit işaretsiz tamsayı|<xref:System.Int64>(taşma olabilir), <xref:System.Numerics.BigInteger> veya<xref:System.Double>|
|<xref:System.UIntPtr>|İşaretsiz işaretçi veya tanıtıcı|<xref:System.IntPtr>|

.NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı CLS uyumlu olmayan diğer türleri içerebilir; Örneğin:

- Paketlenmiş değer türleri. Aşağıdaki C# örneği, adında ortak bir özelliği olan bir sınıf oluşturur `int*` `Value` . Bir `int*` paketlenmiş değer türü olduğundan, derleyici onu CLS uyumlu değil olarak işaretler.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Bir nesneye başvuru ve bir tür başvurusu içeren özel yapılar olan yazılı başvurular. Yazılan başvurular, .NET Framework sınıfı tarafından temsil edilir <xref:System.TypedReference> .

Bir tür CLS uyumlu değilse, <xref:System.CLSCompliantAttribute> özniteliğini değerine uygulamanız gerekir `isCompliant` `false` . Daha fazla bilgi için [CLSCompliantAttribute özniteliği](#CLSAttribute) bölümüne bakın.

Aşağıdaki örnek, bir yöntem imzasında ve genel tür örnek oluşturmada CLS uyumluluğu sorununu göstermektedir. `InvoiceItem`Türünde bir özelliği <xref:System.UInt32> , türünde bir özelliği `Nullable(Of UInt32)` ve ve türündeki parametrelere sahip bir oluşturucuyu tanımlayan bir sınıfı tanımlar <xref:System.UInt32> `Nullable(Of UInt32)` . Bu örneği derlemeye çalıştığınızda dört derleyici uyarısı alırsınız.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Derleyici uyarılarını ortadan kaldırmak için, ortak arabirimdeki CLS uyumlu olmayan türleri `InvoiceItem` uyumlu türler ile değiştirin:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Listelenen belirli türlere ek olarak, bazı tür kategorileri CLS uyumlu değildir. Bunlar, yönetilmeyen işaretçi türlerini ve işlev işaretçisi türlerini içerir. Aşağıdaki örnek bir derleyici uyarısı oluşturur çünkü bir tamsayılar dizisi oluşturmak için bir tamsayı işaretçisi kullanır.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

CLS uyumlu soyut sınıflar (diğer bir deyişle, `abstract` C# dilinde veya Visual Basic olarak işaretlenen sınıflar `MustInherit` ) için, sınıfın tüm ÜYELERI de CLS uyumlu olmalıdır.

<a name="naming"></a>

### <a name="naming-conventions"></a>Adlandırma kuralları

Bazı programlama dilleri büyük/küçük harf duyarsız olduğundan, tanımlayıcılar (ad alanları, türler ve Üyeler adları gibi) büyük/küçük harf bakımından farklı olmalıdır. Küçük harfler aynı ise, iki tanımlayıcı eşit kabul edilir. Aşağıdaki C# örneği, ve olmak üzere iki ortak sınıfı tanımlar `Person` `person` . Yalnızca büyük/küçük harf bakımından farklı olduğundan, C# derleyicisi bunları CLS uyumlu değil olarak işaretler.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Ad alanları, türler ve üyelerin adları gibi programlama Dil tanımlayıcıları, [Unicode standart 3,0, teknik rapor 15, ek 7](https://www.unicode.org/reports/tr15/tr15-18.html)' ye uymalıdır. Bunun anlamı:

- Bir tanımlayıcının ilk karakteri herhangi bir Unicode büyük harf, küçük harf, başlık harf harf, değiştirici harf, diğer harf veya harf numarası olabilir. Unicode karakter kategorileri hakkında daha fazla bilgi için bkz <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> . sabit listesi.

- Sonraki karakterler, ilk karakter olarak kategorilerden herhangi birinden olabilir ve Aralık olmayan işaretler, boşluk birleştirme işaretleri, ondalık sayılar, bağlayıcı noktalamalar ve biçimlendirme kodları da içerebilir.

Tanımlayıcıları karşılaştırmadan önce, tek bir karakter birden çok UTF-16 kodlu kod birimi ile temsil edilebilmesi için biçimlendirme kodlarını filtrelemeniz ve tanımlayıcıları Unicode normalleştirme biçimi C 'ye dönüştürmeniz gerekir. Unicode normalleştirme biçimi C 'de aynı kod birimlerini üreten karakter dizileri CLS uyumlu değildir. Aşağıdaki örnek, `Å` ANGSTROM işareti (u + 212B) karakterini içeren adlı özelliği ve `Å` LATIN büyük harf a 'Yı yukarıdaki halka (u + 00C5) karakteriyle oluşan ikinci bir özelliği tanımlar. C# ve Visual Basic derleyicileri, kaynak kodu CLS uyumlu değil olarak işarettir.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Belirli bir kapsamdaki üye adları (derleme içindeki ad alanları, bir ad alanı içindeki türler veya bir tür içindeki Üyeler), aşırı yükleme yoluyla çözümlenen adlar dışında benzersiz olmalıdır. Bu gereksinim, bir kapsamdaki birden çok üyenin farklı üye türleri oldukları sürece (örneğin, bir yöntem ve biri bir alandır) aynı adlara sahip olmasını sağlayan ortak tür sisteminden daha sıkı bir yöntemdir. Özellikle, tür üyeleri için:

- Alanlar ve iç içe türler yalnızca ada göre ayırt edilir.

- Aynı ada sahip Yöntemler, Özellikler ve olaylar, yalnızca dönüş türünden daha fazla farklı olmalıdır.

Aşağıdaki örnekte, üye adlarının kapsamları dahilinde benzersiz olması gereken gereksinim gösterilmektedir. Adında dört üye içeren adlı bir sınıfı tanımlar `Converter` `Conversion` . Üç yöntem ve biri bir özelliktir. Bir parametre içeren Yöntem <xref:System.Int64> benzersiz olarak adlandırılır, ancak <xref:System.Int32> dönüş değeri bir üyenin imzasının bir parçası olarak değerlendirilmediğinden parametre ile iki yöntem değildir. `Conversion`Özellikler, aşırı yüklenmiş yöntemlerle aynı ada sahip olmadığından, bu gereksinimi da ihlal ediyor.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Tek dillerde benzersiz anahtar sözcükler bulunur, bu nedenle ortak dil çalışma zamanını hedefleyen dillerin, anahtar sözcüklerle birlikte bulunan tanımlayıcılara (tür adları gibi) başvurmak için bazı mekanizmalar de sağlaması gerekir. Örneğin, `case` hem C# hem de Visual Basic bir anahtar sözcüktür. Ancak, aşağıdaki Visual Basic örnek, `case` `case` açma ve kapatma küme ayraçlarını kullanarak anahtar sözcükten adlı bir sınıfın ayırt edebilmesini sağlar. Aksi takdirde, örnek hata iletisi üretir, "anahtar sözcüğü tanımlayıcı olarak geçerli değildir" ve derleme başarısız olur.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

Aşağıdaki C# örneği, `case` `@` Language anahtar sözcüğünden tanımlayıcıyı ayırt etmek için simgesini kullanarak sınıfını örneklendiridebilir. Bu olmadan, C# derleyicisi iki hata iletisi görüntüler, "tür bekleniyor" ve "geçersiz ifade terimi ' Case '."

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Tür dönüştürme

Ortak dil belirtimi iki dönüştürme işlecini tanımlar:

- `op_Implicit`, veri veya duyarlık kaybına neden olmayan genişletme dönüştürmeleri için kullanılır. Örneğin, yapı, <xref:System.Decimal> `op_Implicit` integral türlerinin ve değerlerin değerlerini değerlere dönüştürmek için aşırı yüklenmiş bir işleç içerir <xref:System.Char> <xref:System.Decimal> .

- `op_Explicit`, büyüklük kaybı ile sonuçlanabilecek dönüştürmeleri daraltmak için kullanılır (bir değer, daha küçük bir aralığa sahip bir değere dönüştürülür) veya duyarlığına sahiptir. Örneğin, <xref:System.Decimal> yapısına dönüştürmek için aşırı yüklenmiş bir operatör ve değerleri,,, `op_Explicit` <xref:System.Double> <xref:System.Single> <xref:System.Decimal> <xref:System.Decimal> ve integral değerlerine dönüştürmek için ve değerlerini <xref:System.Double> <xref:System.Single> <xref:System.Char> .

Ancak, tüm diller operatör aşırı yüklemesini veya özel işleçlerin tanımını desteklemez. Bu dönüştürme işleçlerini uygulamayı seçerseniz, dönüştürmeyi gerçekleştirmek için alternatif bir yol da sağlamanız gerekir. `From` *XXX* ve `To` *XXX* yöntemleri sağlamanızı öneririz.

Aşağıdaki örnek, CLS uyumlu örtük ve açık dönüştürmeleri tanımlar. `UDouble`İmzalı çift duyarlıklı, kayan noktalı bir sayıyı temsil eden bir sınıf oluşturur. ' Dan `UDouble` <xref:System.Double> `UDouble` <xref:System.Single> , <xref:System.Double> ' a `UDouble` ve ' <xref:System.Single> `UDouble` a kadar açık dönüşümlere örtülü dönüşümler sağlar. Ayrıca `ToDouble` , örtük dönüştürme işlecine alternatif olarak bir yöntemi ve `ToSingle` ,, `FromDouble` ve `FromSingle` yöntemlerini açık dönüştürme işleçleri alternatifleri olarak tanımlar.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Diziler

CLS uyumlu diziler aşağıdaki kurallara uyar:

- Bir dizinin tüm boyutlarının alt sınırı sıfır olmalıdır. Aşağıdaki örnek, bir alt sınırı olan CLS uyumlu olmayan bir dizi oluşturur. Özniteliğin varlığına rağmen <xref:System.CLSCompliantAttribute> derleyicinin yöntemin döndürdüğü DIZININ CLS uyumlu olmadığını algılamadığına unutmayın `Numbers.GetTenPrimes` .

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Tüm dizi öğeleri CLS uyumlu türlerden oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan diziler döndüren iki yöntemi tanımlar. İlki bir değer dizisi döndürür <xref:System.UInt32> . İkincisi, <xref:System.Object> ve değerlerini içeren bir dizi <xref:System.Int32> döndürür <xref:System.UInt32> . Derleyici, türü nedeniyle ilk diziyi uyumsuz olarak tanımlasa da <xref:System.UInt32> , ikinci DIZININ CLS uyumlu olmayan öğeleri içerdiğini tanıyamaz.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Dizi parametrelerine sahip yöntemler için aşırı yükleme çözümlemesi, diziler oldukları olguyu ve öğe türlerini temel alır. Bu nedenle, aşırı yüklenmiş bir yöntemin aşağıdaki tanımı `GetSquares` CLS uyumludur.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Arabirimler

CLS uyumlu arabirimler özellikleri, olayları ve sanal yöntemleri (uygulama içermeyen yöntemler) tanımlayabilir. CLS uyumlu bir arabirim aşağıdakilerden birini içeremez:

- Statik yöntemler veya statik alanlar. Hem C# hem de Visual Basic derleyicileri, bir arabirimde statik üye tanımlarsanız derleyici hataları oluşturur.

- Alanını. Hem C# hem de Visual Basic derleyicileri, bir arabirimde alan tanımlarsanız derleyici hataları oluşturur.

- CLS uyumlu olmayan yöntemler. Örneğin, aşağıdaki arabirim tanımı, `INumber.GetUnsigned` CLS uyumlu olmayan olarak işaretlenen bir yöntemini içerir. Bu örnek bir derleyici uyarısı oluşturur.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Bu kural nedeniyle, CLS uyumlu olmayan üyeleri uygulamak için CLS uyumlu türler gerekli değildir. CLS uyumlu bir çerçeve CLS uyumlu olmayan bir arabirim uygulayan bir sınıfı kullanıma sunuyorsa, CLS uyumlu olmayan tüm üyelerin somut uygulamalarını da sağlamalıdır.

CLS uyumlu dil derleyicileri Ayrıca, bir sınıfın birden fazla arabirimde aynı ada ve imzaya sahip ayrı üye uygulamaları sağlamasına izin vermelidir.  Hem C# hem de Visual Basic, aynı adlı yöntemlerin farklı uygulamalarını sağlamak için [Açık arabirim uygulamalarını](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) destekler. Visual Basic ayrıca `Implements` , belirli bir üyenin hangi arabirime ve üyeye uyguladığını açıkça belirleyebilmenizi sağlayan anahtar sözcüğünü de destekler. Aşağıdaki örnek, `Temperature` `ICelsius` ve `IFahrenheit` arabirimlerini açık arabirim uygulamaları olarak uygulayan bir sınıf tanımlayarak bu senaryoyu göstermektedir.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Numaralandırmalar

CLS uyumlu numaralandırmalar aşağıdaki kurallara uymalıdır:

- Sabit listesinin temel alınan türü, bir iç CLS uyumlu tamsayı ( <xref:System.Byte> , <xref:System.Int16> , <xref:System.Int32> veya <xref:System.Int64> ) olmalıdır. Örneğin, aşağıdaki kod, temel türü olan bir sabit listesi tanımlamaya çalışır <xref:System.UInt32> ve bir derleyici uyarısı oluşturur.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Sabit listesi türü, özniteliğiyle işaretlenmiş adlı tek bir örnek alanına sahip olmalıdır `Value__` <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> . Bu, alan değerine örtülü olarak başvuru yapmanızı sağlar.

- Sabit listesi, türleri numaralandırmanın türüyle eşleşen değişmez static alanları içerir. Örneğin, `State` ve değerlerini içeren bir sabit listesi tanımlarsanız `State.On` `State.Off` `State.On` ve `State.Off` türü olan değişmez değer statik alanlardır `State` .

- İki tür numaralandırma vardır:

  - Birbirini dışlayan, adlandırılmış tamsayı değerleri kümesini temsil eden bir sabit listesi. Bu tür bir numaralandırma, özel özniteliğin yokluğuna göre belirtilir <xref:System.FlagsAttribute?displayProperty=nameWithType> .

  - Adlandırılmamış bir değer oluşturmak için birleştirebileceğiniz bir bit bayrakları kümesini temsil eden bir sabit listesi. Bu tür bir numaralandırma, özel özniteliğin varlığı tarafından gösterilir <xref:System.FlagsAttribute?displayProperty=nameWithType> .

  Daha fazla bilgi için, yapıya yönelik belgelere bakın <xref:System.Enum> .

- Bir numaralandırmanın değeri, belirtilen değerlerinin aralığıyla sınırlı değildir. Diğer bir deyişle, bir Numaralandırmadaki değer aralığı, temel alınan değerinin aralığıdır. <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>Yöntemini, belirtilen değerin bir numaralandırma üyesi olup olmadığını anlamak için kullanabilirsiniz.

<a name="members"></a>

### <a name="type-members-in-general"></a>Genel olarak tür üyeleri

Ortak dil belirtimi, tüm alanlara ve yöntemlere belirli bir sınıfın üyeleri olarak erişilmesini gerektirir. Bu nedenle, genel statik alanlar ve Yöntemler (yani, statik alanlar veya bir türden ayrı tanımlanmış yöntemler) CLS uyumlu değildir. Kaynak kodunuza genel bir alan veya yöntem eklemeyi denerseniz, hem C# hem de Visual Basic derleyicileri bir derleyici hatası oluşturur.

Ortak dil belirtimi yalnızca standart yönetilen çağırma kuralını destekler. Anahtar sözcükle işaretlenmiş bağımsız değişken listeleriyle yönetilmeyen çağırma kurallarını ve yöntemlerini desteklemez `varargs` . Standart yönetilen çağırma kuralıyla uyumlu değişken bağımsız değişken listeleri için, <xref:System.ParamArrayAttribute> `params` C# ' deki anahtar sözcüğü ve Visual Basic anahtar sözcüğü gibi, özniteliği veya bağımsız dilin uygulamasını kullanın `ParamArray` .

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Üye erişilebilirliği

Devralınan bir üyenin geçersiz kılınması, o üyenin erişilebilirliğini değiştiremez. Örneğin, bir temel sınıftaki ortak bir yöntem türetilmiş bir sınıftaki özel bir yöntem tarafından geçersiz kılınamaz. Bir özel durum vardır: bir `protected internal` derlemede (C# ' ta) veya `Protected Friend` (Visual Basic), farklı bir derlemedeki bir tür tarafından geçersiz kılınan bir derlemede üye. Bu durumda, geçersiz kılma erişilebilirliği olur `Protected` .

Aşağıdaki örnekte <xref:System.CLSCompliantAttribute> , özniteliği olarak ayarlandığında oluşturulan hata `true` ve `Human` öğesinden türetilen bir sınıf olan, `Animal` `Species` özelliğin erişilebilirliğini public iken Private olarak değiştirmeye çalışır. Bunun erişilebilirliği ortak olarak değiştirilirse örnek başarıyla derlenir.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Üyenin İmzasındaki türlere, bu üyeye her erişilebilir her seferinde erişilebilir olması gerekir. Örneğin, bu, ortak bir üyenin türü Private, protected veya internal olan bir parametre içeremeyeceği anlamına gelir. Aşağıdaki örnek, bir `StringWrapper` sınıf Oluşturucusu bir `StringOperationType` dize değerinin nasıl sarmalanması gerektiğini belirleyen bir iç sabit listesi değeri ortaya çıkardığı zaman sonuç veren derleyici hatasını gösterir.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Genel türler ve Üyeler

İç içe türler her zaman kapsayan türü olarak en az sayıda genel parametre içermelidir. Bu, kapsayan türdeki genel parametrelere konuma göre karşılık gelir. Genel tür de yeni genel parametreler içerebilir.

Kapsayan bir türün genel tür parametreleri ve iç içe geçmiş türleri arasındaki ilişki, tek dillerin sözdizimi tarafından gizlenebilir. Aşağıdaki örnekte, genel bir tür `Outer<T>` iki iç içe sınıf içerir `Inner1A` ve `Inner1B<U>` . `ToString`Her sınıfın devraldığı yöntemine yapılan çağrılar, <xref:System.Object.ToString%2A?displayProperty=nameWithType> her iç içe yerleştirilmiş sınıfın kapsayan sınıfının tür parametrelerini içerdiğini gösterir.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Genel tür adları, * \` n adında*, *adın* tür adı olduğu, \` bir karakter sabit değeri, *n* ise tür üzerinde belirtilen parametre sayısı veya iç içe genel türler için yeni tanıtılan tür parametrelerinin sayısı olarak kodlanır. Genel tür adlarının bu kodlaması, bir kitaplıktaki CLS uyumlu Genel türlere erişmek için yansıma kullanan geliştiricilere yöneliktir.

Kısıtlamalar genel bir türe uygulanırsa, kısıtlama olarak kullanılan her türlü tür de CLS uyumlu olmalıdır. Aşağıdaki örnek, `BaseClass` CLS uyumlu olmayan adlı bir sınıfı ve tür parametresi türünden türetmelidir adlı bir genel sınıfı tanımlar `BaseCollection` `BaseClass` . Ancak, `BaseClass` CLS uyumlu olmadığından, derleyici bir uyarı yayar.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Genel bir tür genel bir temel türden türetildiyse, temel türdeki kısıtlamaların da karşılanmasını garanti edebilmesi için herhangi bir kısıtlamayı yeniden bildirmelidir. Aşağıdaki örnek, herhangi bir `Number<T>` sayısal türü temsil eden bir tanımlar. Ayrıca `FloatingPoint<T>` , kayan nokta değerini temsil eden bir sınıfı tanımlar. Ancak, üzerinde kısıtlama uygulanmadığından kaynak kodu derlenemiyor `Number<T>` (Bu T bir değer türü olmalıdır) `FloatingPoint<T>` .

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Kısıtlama sınıfa eklenirse, örnek başarıyla derlenir `FloatingPoint<T>` .

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Ortak dil belirtimi, iç içe türler ve korumalı üyeler için bir örnek oluşturma modeli uygular. Açık genel türler, iç içe geçmiş, korunan genel bir türün belirli bir örneğini içeren imzalara sahip alanları veya üyeleri gösteremez. Genel bir temel sınıfın veya arabirimin belirli bir örneğini genişleten genel olmayan türler, iç içe geçmiş, korunan genel bir türün farklı bir örneğini içeren imzalara sahip alanları veya üyeleri gösteremez.

Aşağıdaki örnek, bir genel türü `C1<T>` (veya `C1(Of T)` Visual Basic) ve korumalı bir sınıfı `C1<T>.N` (veya `C1(Of T).N` Visual Basic) tanımlar. `C1<T>`iki yönteme sahiptir `M1` ve `M2` . Ancak, `M1` `C1<int>.N` `C1(Of Integer).N` C1 \<T> (veya) nesnesinden bir (veya) nesne döndürmeye çalıştığı için CLS uyumlu değildir `C1(Of T)` . İkinci bir sınıf, `C2` `C1<long>` (veya) öğesinden türetilir `C1(Of Long)` . İki yöntemi vardır `M3` ve `M4` . `M3`, bir `C1<int>.N` alt sınıfından (veya) bir nesne döndürmeye çalıştığı IÇIN CLS uyumlu değildir `C1(Of Integer).N` `C1<long>` . Dil derleyicilerinin daha da kısıtlayıcı olabileceğini unutmayın. Bu örnekte, derlemeyi denediğinde Visual Basic bir hata görüntüler `M4` .

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Oluşturucular

CLS uyumlu sınıfların ve yapıların içindeki oluşturucular şu kurallara uymalıdır:

- Türetilmiş bir sınıfın Oluşturucusu, devralınan örnek verilerine erişmeden önce temel sınıfının örnek oluşturucusunu çağırmalıdır. Bu gereksinim, temel sınıf oluşturucularının türetilmiş sınıfları tarafından devralınmasından kaynaklanır. Bu kural, doğrudan devralmayı desteklemeyen yapılar için geçerlidir.

  Genellikle, aşağıdaki örnekte gösterildiği gibi, derleyiciler Bu kuralı CLS uyumluluğuna bağımsız olarak uygular. `Doctor`Bir sınıftan türetilmiş bir sınıf oluşturur `Person` , ancak `Doctor` sınıfın `Person` devralınan örnek alanlarını başlatmak için sınıf oluşturucusunu çağırması başarısız olur.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Nesne Oluşturucusu bir nesne oluşturmak hariç çağrılamaz. Ayrıca, bir nesne iki kez başlatılamaz. Örneğin, bu, <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> ve serisini kaldırma yöntemlerinin <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> oluşturucuları çağırmayacağı anlamına gelir.

<a name="properties"></a>

### <a name="properties"></a>Özellikler

CLS uyumlu türlerdeki özellikler aşağıdaki kurallara uymalıdır:

- Özelliğin bir ayarlayıcı, alıcı veya her ikisi de olmalıdır. Bir derlemede, bunlar özel yöntemler olarak uygulanır, yani ayrı yöntemler olarak (alıcı `get_` *PropertyName* ve ayarlayıcı, `set_` *PropertyName*olarak adlandırılır) `SpecialName` derlemenin meta verilerinde olarak işaretlenir. C# ve Visual Basic derleyicileri, özniteliği uygulama gerekmeden bu kuralı otomatik olarak uygular <xref:System.CLSCompliantAttribute> .

- Özelliğin türü, özellik alıcısının dönüş türü ve ayarlayıcının son bağımsız değişkenidir. Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler başvuruya göre özelliğe atanamaz (yani, yönetilen işaretçiler olamaz).

- Bir özelliğin hem alıcı hem de ayarlayıcı varsa, her ikisi de sanal, hem statik hem de her iki örnek olmalıdır. C# ve Visual Basic derleyicileri, bu kuralı özellik tanımı sözdizimi aracılığıyla otomatik olarak zorlar.

<a name="events"></a>

### <a name="events"></a>Ekinlikler

Bir olay, adı ve türü ile tanımlanır. Olay türü, olayı göstermek için kullanılan bir temsilcisidir. Örneğin, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay türündedir <xref:System.ResolveEventHandler> . Olayın kendisinin yanı sıra, olay adına göre adlara sahip üç yöntem olayın uygulamasını sağlar ve `SpecialName` derlemenin meta verilerinde olarak işaretlenir:

- EventName adlı bir olay işleyicisi ekleme yöntemi `add_` *EventName*. Örneğin, olay için olay aboneliği yöntemi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> adlandırılır `add_AssemblyResolve` .

- EventName adlı bir olay işleyicisini kaldırma yöntemi `remove_` *EventName*. Örneğin, olay için kaldırma yöntemi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olarak adlandırılır `remove_AssemblyResolve` .

- EventName adlı olayın oluştuğunu belirten bir yöntem `raise_` *EventName*.

> [!NOTE]
> Ortak dil belirtiminin olayları ile ilgili kuralları, dil derleyicileri tarafından uygulanır ve bileşen geliştiricileri için saydamdır.

Olayı ekleme, kaldırma ve oluşturma yöntemleri aynı erişilebilirliği içermelidir. Bunların hepsi de statik, örnek veya sanal olması gerekir. Bir olayı ekleme ve kaldırma yöntemleri, türü olay temsilci türü olan bir parametreye sahiptir. Add ve Remove yöntemlerinin her ikisi de bulunmalıdır ya da her ikisi de olmamalıdır.

Aşağıdaki örnek, `Temperature` `TemperatureChanged` iki readsler arasındaki sıcaklık değişikliği bir eşik değerini eşitse veya aştığında bir olayı başlatan adlı CLS uyumlu bir sınıfı tanımlar. `Temperature`Sınıfı açıkça `raise_TemperatureChanged` olay işleyicilerini yürütebilmesi için bir yöntemi tanımlar.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Aşırı Yüklemeler

Ortak dil belirtimi, aşırı yüklenmiş üyelere aşağıdaki gereksinimleri uygular:

- Üyeler, parametrelerin sayısına ve herhangi bir parametre türüne göre aşırı yüklenebilir. Çağırma kuralı, dönüş türü, yönteme veya parametresine uygulanan özel değiştiriciler, bir değere veya başvuruya göre geçirilen parametrelerin, aşırı yüklemeler arasında ayrım yaparken dikkate alınıp alınmayacağını belirtir. Bir örnek için, [adlandırma kuralları](#naming) bölümündeki bir kapsam içinde adların benzersiz olması gerekliliğe ilişkin koda bakın.

- Yalnızca özellikler ve yöntemler aşırı yüklenebilir. Alanlar ve olaylar aşırı yüklenemez.

- Genel yöntemler, genel parametrelerinin sayısına bağlı olarak aşırı yüklenebilir.

> [!NOTE]
> `op_Explicit`Ve `op_Implicit` işleçleri, geri yükleme çözümlemesi için bir yöntem imzasının bir parçası olarak kabul edilen bir kural için özel durumlardır. Bu iki işleç, parametreleri ve dönüş değerleri temel alınarak aşırı yüklenebilir.

<a name="exceptions"></a>

### <a name="exceptions"></a>Özel durumlar

Özel durum nesneleri öğesinden <xref:System.Exception?displayProperty=nameWithType> türetilmiş başka bir türden veya ondan türemelidir <xref:System.Exception?displayProperty=nameWithType> . Aşağıdaki örnek, özel bir sınıfı `ErrorClass` özel durum işleme için kullanıldığında oluşan derleyici hatasını gösterir.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Bu hatayı düzeltmek için, `ErrorClass` sınıfın öğesinden devralması gerekir <xref:System.Exception?displayProperty=nameWithType> . Ayrıca, `Message` özelliğin geçersiz kılınması gerekir. Aşağıdaki örnek, CLS uyumlu bir sınıf tanımlamak için bu hataları düzeltir `ErrorClass` .

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Öznitelikler

Özel öznitelikler, özel öznitelikleri depolamak ve derlemeler, türler, Üyeler ve Yöntem parametreleri gibi programlama nesneleri hakkındaki meta verileri almak için genişletilebilir bir mekanizma sağlar. Özel öznitelikler <xref:System.Attribute?displayProperty=nameWithType> öğesinden türetilmiş bir türden veya ondan türemelidir <xref:System.Attribute?displayProperty=nameWithType> .

Aşağıdaki örnek bu kuralı ihlal ediyor. Sınıfından `NumericAttribute` türetilmeyen bir sınıfı tanımlar <xref:System.Attribute?displayProperty=nameWithType> . Derleyici hatası, sınıf tanımlandığında değil, yalnızca CLS uyumlu olmayan öznitelik uygulandığında oluşur.

[!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
[!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]

CLS uyumlu bir özniteliğin Oluşturucusu veya özellikleri yalnızca aşağıdaki türleri açığa alabilir:

- <xref:System.Boolean>

- <xref:System.Byte>

- <xref:System.Char>

- <xref:System.Double>

- <xref:System.Int16>

- <xref:System.Int32>

- <xref:System.Int64>

- <xref:System.Single>

- <xref:System.String>

- <xref:System.Type>

- Temel türü,, veya olan herhangi bir numaralandırma türü <xref:System.Byte> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> .

Aşağıdaki örnek, `DescriptionAttribute` öğesinden türetilen bir sınıfı tanımlar <xref:System.Attribute> . Sınıf oluşturucusunun türünde bir parametresi vardır, bu `Descriptor` yüzden sınıf CLS uyumlu değildir. C# derleyicisinin bir uyarı yaydığına ancak başarıyla derlendiğine dikkat edin, Visual Basic derleyici ne bir uyarı ne de hata vermez.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>CLSCompliantAttribute özniteliği

<xref:System.CLSCompliantAttribute>Özniteliği, bir program öğesinin ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır. <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29>Oluşturucu, `isCompliant` program öğesinin CLS uyumlu olup olmadığını gösteren tek bir gerekli parametresi içerir.

Derleme zamanında derleyici, CLS uyumlu olarak kabul edilen uyumlu olmayan öğeleri algılar ve bir uyarı gönderir. Derleyici, açıkça uyumsuz olacak şekilde bildirilmeyen türler veya Üyeler için uyarıları göstermez.

Bileşen geliştiricileri, <xref:System.CLSCompliantAttribute> özniteliğini iki şekilde kullanabilir:

- CLS uyumlu olan ve CLS uyumlu olmayan parçalar içeren bir bileşen tarafından açığa çıkarılan ortak arabirimin parçalarını tanımlamak için. Özniteliği belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, bu öğelerin .NET Framework hedef olan tüm diller ve araçlardan erişilebilir olmasını güvence altına alır.

- Bileşen kitaplığının ortak arabiriminin yalnızca CLS uyumlu program öğelerini kullanıma sunduğundan emin olmak için. Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı vermez.

> [!WARNING]
> Bazı durumlarda, dil derleyicileri, özniteliğin kullanılıp kullanılmadığına bakılmaksızın CLS uyumlu kuralları uygular <xref:System.CLSCompliantAttribute> . Örneğin, bir arabirimde statik üye tanımlamak CLS kuralını ihlal ediyor. Bu şekilde, bir `static` arabirimde (c# ' de) veya `Shared` (Visual Basic) üye tanımlarsanız, hem c# hem de Visual Basic derleyicileri bir hata iletisi görüntüler ve uygulamayı derleyemeyebilir.

<xref:System.CLSCompliantAttribute>Özniteliği değeri olan bir özniteliğiyle işaretlenir <xref:System.AttributeUsageAttribute> <xref:System.AttributeTargets.All?displayProperty=nameWithType> . Bu değer, <xref:System.CLSCompliantAttribute> özniteliği derlemeler, modüller, türler (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), tür üyeleri (oluşturucular, Yöntemler, özellikler, alanlar ve olaylar), parametreler, genel parametreler ve dönüş değerleri dahil olmak üzere herhangi bir program öğesine uygulamanıza olanak tanır. Ancak, uygulamada, özniteliğini yalnızca derlemeler, türler ve tür üyelerine uygulamanız gerekir. Aksi takdirde, derleyiciler özniteliği yoksayar ve kitaplığınızın ortak arabirimindeki uyumlu olmayan bir parametre, genel parametre veya dönüş değeri ile karşılaştığında Derleyici uyarıları oluşturmaya devam eder.

<xref:System.CLSCompliantAttribute>Özniteliğin değeri kapsanan program öğeleri tarafından devralınır. Örneğin, bir derleme CLS uyumlu olarak işaretlenmişse, türleri de CLS uyumludur. Bir tür CLS uyumlu olarak işaretlenmişse, iç içe geçmiş türleri ve üyeleri de CLS uyumludur.

<xref:System.CLSCompliantAttribute>Dahil edilen bir program öğesine özniteliğini uygulayarak devralınan uyumluluğu açıkça geçersiz kılabilirsiniz. Örneğin, uyumlu bir <xref:System.CLSCompliantAttribute> `isCompliant` `false` derlemede uyumlu olmayan bir tür tanımlamak için bir değeriyle özniteliğini kullanabilir ve uyumlu `isCompliant` `true` olmayan bir derlemede uyumlu bir tür tanımlamak için özniteliğini değerini kullanabilirsiniz. Uyumlu olmayan üyeleri, uyumlu bir türde de tanımlayabilirsiniz. Bununla birlikte, uyumlu olmayan bir tür uyumlu üyelere sahip olamaz, bu nedenle `isCompliant` `true` uyumsuz bir türden devralmayı geçersiz kılmak için özniteliği değeri ile kullanamazsınız.

Bileşenleri geliştirirken, <xref:System.CLSCompliantAttribute> derlemenizin, türlerinin ve ÜYELERININ CLS uyumlu olup olmadığını belirtmek için her zaman özniteliğini kullanmanız gerekir.

CLS uyumlu bileşenler oluşturmak için:

1. <xref:System.CLSCompliantAttribute>DERLEMENIZI CLS uyumlu olarak işaretlemek için öğesini kullanın.

2. Derlemede, CLS uyumlu olmayan, genel olarak sunulan herhangi bir türü, uyumsuz olarak işaretleyin.

3. CLS uyumlu türlerde herkese açık olan tüm üyeleri uyumlu değil olarak işaretleyin.

4. CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlar.

Uyumlu olmayan tüm türlerini ve üyelerini başarıyla işaretlediyseniz, derleyicisinde uyumsuz olmayan uyarılar sunulmamalıdır. Ancak, hangi üyelerin CLS uyumlu olmadığını ve ürün belgelerinizde CLS uyumlu alternatiflerini listelemeyeceğini belirtmeniz gerekir.

Aşağıdaki örnek, CLS <xref:System.CLSCompliantAttribute> uyumlu bir derlemeyi ve `CharacterUtilities` , CLS uyumlu olmayan iki üyeye sahip bir türünü tanımlamak için özniteliğini kullanır. Her iki üye de özniteliğiyle etiketlendiği `CLSCompliant(false)` için derleyici hiçbir uyarı üretmez. Sınıfı, her iki yöntem için de CLS uyumlu bir alternatif sağlar. Normalde, `ToUTF16` CLS uyumlu alternatifler sağlamak için metoda yalnızca iki aşırı yükleme ekleyeceğiz. Ancak, dönüş değerine göre Yöntemler aşırı yüklenemez, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklıdır.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Bir kitaplık yerine bir uygulama geliştiriyorsanız (yani, diğer uygulama geliştiricileri tarafından tüketilen türleri veya üyeleri açığa çıkarmadıysanız), uygulamanızın kullandığı program öğelerinin CLS uyumluluğu yalnızca dilinizin bu işlemleri desteklememesi durumunda ilgilenmektedir. Bu durumda, CLS uyumlu olmayan bir öğeyi kullanmaya çalıştığınızda dil derleyicinizin bir hata üretecektir.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Diller Arası Birlikte Çalışabilirlik

Dil bağımsızlığının birkaç olası anlamı vardır. Bu makalede, [Dil bağımsızlığı ve dilden bağımsız bileşenlerde](language-independence-and-language-independent-components.md)ele alınan bir anlamı, başka bir dilde yazılmış bir uygulamadan tek bir dilde yazılmış türleri sorunsuzca kullanmayı içerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.

Aşağıdaki örnek, iki sınıf içeren Utilities. dll adlı bir sınıf kitaplığı oluşturarak platformlar arası birlikte çalışabilirliği gösterir `NumericLib` ve `StringLib` . `NumericLib`Sınıfı C# dilinde yazılır ve `StringLib` sınıf Visual Basic yazılır. Aşağıda `ToTitleCase` sınıfında tek bir üye, `StringLib`, içeren StringUtil.vb için kaynak kodu verilmiştir.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

İki sınıfı tek bir derlemede paketlemek için, bunları modüller halinde derlemeniz gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
vbc /t:module StringUtil.vb
```

Visual Basic derleyicisinin komut satırı sözdizimi hakkında daha fazla bilgi için, bkz. [komut satırından oluşturma](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
csc /t:module NumberUtil.cs
```

C# derleyicisinin komut satırı sözdizimi hakkında daha fazla bilgi için bkz. [CSC. exe Ile komut satırı oluşturma](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Daha sonra, iki modülü bir derlemede derlemek için [bağlayıcı seçeneklerini](/cpp/build/reference/linker-options) kullanabilirsiniz:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Aşağıdaki örnek `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemlerini çağırır. Hem Visual Basic kodunun hem de C# kodunun her iki sınıftaki yöntemlere erişebileceğini unutmayın.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Visual Basic kodunu derlemek için bu komutu kullanın:

```console
vbc example.vb /r:UtilityLib.dll
```

C# ile derlemek için, derleyicinin adını **vbc** 'den **CSC**'ye değiştirin ve dosya uzantısını. vb iken. cs olarak değiştirin:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.CLSCompliantAttribute>
