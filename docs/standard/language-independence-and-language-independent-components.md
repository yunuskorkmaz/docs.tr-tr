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
ms.openlocfilehash: 6ecb2c2e6a80f36ea1426b6145fd89b869a77f1b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663014"
---
# <a name="language-independence-and-language-independent-components"></a>Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler

.NET Framework dilden bağımsızdır ' dir. Bu bir geliştirici olarak, birinde gibi .NET Framework hedefleyen birçok dilde geliştirebileceğiniz anlamına gelir C#, C++/CLI, Eiffel, F#, IronPython, Ironruby, PowerBuilder, Visual Basic, Visual COBOL ve Windows PowerShell. Türler ve üyeler sınıf kitaplıkları, bunlar ilk olarak yazılmış içinde dili bilmek zorunda kalmadan ve herhangi bir özgün dil kuralları izlemeye gerek kalmadan olmadan .NET Framework için geliştirilen erişebilirsiniz. Bileşen geliştiricisiyseniz, diline bakılmaksızın herhangi bir .NET Framework uygulama tarafından bileşeniniz erişilebilir.

> [!NOTE]
> Bu ilk kısmı bu makalede, dilden bağımsız bileşenlerin oluşturulması açıklanmaktadır — diğer bir deyişle, herhangi bir dilde yazılmış uygulamalar tarafından tüketilebilecek bileşenlerin. Birden çok dilde yazılmış kaynak kodundan tek bileşen veya uygulama da oluşturabilirsiniz; bkz: [diller arası birlikte çalışabilirlik](#CrossLang) ikinci bölümündeki bu makalede.

Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşim kurmayı nesneleri arayanlara tüm diller için ortak olan özellikleri göstermesi gerekir. Bu ortak özellikler kümesi, oluşturulmuş derlemeler için uygulanan bir kurallar kümesi olan ortak dil belirtimi (CLS ile), tanımlanır. Ortak dil belirtimi bölüm ı, yan tümceler 7 ila 11'de tanımlanan [ECMA-335 standardı: Ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Bileşeniniz ortak dil belirtimi için uyuyorsa, CLS uyumlu olması sağlanır ve CLS destekleyen programlama diliyle yazılmış derlemedeki koddan erişilebilir. Bileşeniniz ortak dil belirtimi için derleme zamanında uygulayarak uyup uymadığını belirleyebilirsiniz <xref:System.CLSCompliantAttribute> özniteliğini kaynak kodunuza. Daha fazla bilgi için [CLSCompliantAttribute özniteliği](#CLSAttribute).

Bu makalede:

- [CLS uyumluluğu kuralları](#Rules)

  - [Türler ve tür üyesi imzaları](#Types)

  - [Adlandırma kuralları](#naming)

  - [Tür dönüştürme](#conversion)

  - [Diziler](#arrays)

  - [Arabirimler](#Interfaces)

  - [Sabit Listeleri](#enums)

  - [Genel olarak tür üyeleri](#members)

  - [Üye erişilebilirliği](#MemberAccess)

  - [Genel türler ve Üyeler](#Generics)

  - [Oluşturucular](#ctors)

  - [Özellikler](#properties)

  - [Olaylar](#events)

  - [Overloads](#overloads)

  - [Özel Durumlar](#exceptions)

  - [Öznitelikler](#attributes)

- [CLSCompliantAttribute özniteliği](#CLSAttribute)

- [Diller arası birlikte çalışabilirlik](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>CLS uyumluluğu kuralları

Bu bölüm, CLS uyumlu bileşen oluşturma kurallarını anlatır. Kuralları tam listesi için bölüm ı, madde 11'ine bakın [ECMA-335 standardı: Ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Çerçeveler (oluşturmak için bir dil derleyicisi kullanan geliştiriciler tüketiciler (CLS uyumlu bir bileşen programlı olarak erişen geliştiriciler), geçerli olduğundan ortak dil belirtimi CLS uyumuyla ilgili her kuralı açıklanır. CLS-compliant kitaplıkları) ve Genişleticileri (bir dil derleyicisi veya CLS uyumlu bileşenler oluşturan kod ayrıştırıcısı gibi bir araç oluşturan geliştiriciler). Bu makale, çerçeveler için geçerli olarak kurallarında odaklanır. Ancak, Genişleticiler için geçerli kurallar bazıları da Reflection.Emit kullanılarak oluşturulan derlemeler için uygulanabilir unutmayın.

Dilden bağımsız bir bileşen tasarlamak için yalnızca CLS kurallarını bileşeninizin genel arabirimine uygulamanız gerekir. Özel uygulamanızın belirtime uygun gerekmez.

> [!IMPORTANT]
> CLS uyumluluğu kuralları yalnızca bileşenin özel uygulaması için bir bileşenin genel arabirimi uygulanır.

Örneğin, dışındaki imzalanmamış tamsayılar <xref:System.Byte> CLS uyumlu değildir. Çünkü `Person` sınıfı aşağıdaki örnekte gösterir bir `Age` türünün özelliği <xref:System.UInt16>, aşağıdaki kod bir derleyici uyarısı görüntüler.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

Yapabileceğiniz `Person` CLS uyumlu sınıf türünü değiştirerek `Age` özelliğinden <xref:System.UInt16> için <xref:System.Int16>, CLS uyumlu, 16 bit işaretli bir tamsayı olduğu. Özel türünü değiştirmek zorunda değilsiniz `personAge` alan.

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Kitaplığın Genel arabirimi aşağıdakilerden oluşur:

- Ortak sınıfların tanımları.

- Ortak sınıfların ortak üyelerinin ve üyelerin erişilebilir türetilmiş sınıflar (yani, korumalı üyeler) tanımları tanımları.

- Parametreleri ve ortak sınıfların ve parametreleri genel yöntemlerin dönüş türleri ve türetilen sınıflar için erişilebilir yöntemlerin dönüş türleri.

CLS uyumluluğu kuralları, aşağıdaki tabloda listelenmiştir. Metin kuralları ndan alınmıştır [ECMA-335 standardı: Ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm), Ecma International telif hakkı 2012 olduğu. Aşağıdaki bölümlerde bu kurallar hakkında daha ayrıntılı bilgi bulunur.

|Kategori|Bkz.|Kural|Kural numarası|
|--------------|---------|----------|-----------------|
|Erişilebilirlik|[Üye erişilebilirliği](#MemberAccess)|Devralınan dışında olduğunda bir yöntemini geçersiz kılma farklı bir derlemeden devralınan yöntemi geçersiz kılma erişilebilirlik değiştirilmemelidir `family-or-assembly`. Bu durumda geçersiz kılma erişilebilirlik olmalıdır `family`.|10|
|Erişilebilirlik|[Üye erişilebilirliği](#MemberAccess)|Görünürlük ve erişilebilirliği türleri ve üyeleri üye bizzat görünür ve erişilebilir olduğunda herhangi bir üyenin İmzasındaki türler görünür ve erişilebilir olmasını olacaktır. Örneğin, kendi derlemesi dışında görülebilir bir genel yöntem türü yalnızca derleme içinde görünür olan bir bağımsız değişkene sahip olamaz. Üye bizzat görünür ve erişilebilir olduğunda görünürlük ve erişilebilirliği herhangi bir üyenin imzasında kullanılan örneklenmiş bir genel tür oluşturan türlerin görünür ve erişilebilir olmalıdır. Örneğin, örneklenmiş bir genel tür imzasında bulunan kendi derlemesi dışında görülebilir bir üyenin, türü yalnızca derleme içinde görünür olan bir genel bağımsız değişkene sahip olamaz.|12|
|Diziler|[Diziler](#arrays)|Diziler CLS uyumlu türü olan öğeleri olmalıdır ve tüm boyutlar dizinin alt sınırı sıfır olmalıdır. Yalnızca bir dizi ve dizinin öğe türü bir öğedir olgu aşırı yükler arasında ayrım yapmak için gerekli. Ne zaman aşırı yükleme iki alan ya da daha fazla dizi öğesi türleri türleri adlı.|16|
|Öznitelikler|[Öznitelikler](#attributes)|Öznitelikleri türü olacaktır <xref:System.Attribute?displayProperty=nameWithType>, ya da bundan devralan bir tür.|41|
|Öznitelikler|[Öznitelikler](#attributes)|CLS yalnızca bir özel özniteliklerin kodlamalarının alt kümesine izin verir. (Bkz. Bölüm IV) bu kodlamalarda görünmesi gereken türleri yalnızca şunlardır: <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> , ve herhangi bir numaralandırma türü CLS uyumlu temel tamsayı türüne dayalı.|34|
|Öznitelikler|[Öznitelikler](#attributes)|CLS ortak olarak görünür gerekli değiştiricilere izin vermiyor (`modreq`, bkz. Bölüm II), isteğe bağlı değiştiricilere izin vermez ancak (`modopt`, bkz. Bölüm II) anlamadığı.|35|
|Oluşturucular|[Oluşturucular](#ctors)|Devralınan örnek verilerine herhangi bir erişim oluşmadan önce nesne Oluşturucu, temel sınıfının bazı örnek oluşturucusu oluşturucularını çağırmalıdır (Bu oluşturuculara sahip olmak zorunda olmayan değer türleri için geçerli değildir.)|21|
|Oluşturucular|[Oluşturucular](#ctors)|Nesne Oluşturucu dışında bir nesnenin oluşturmanın bir parçası çağrılmamalıdır ve nesne iki kez başlatılmamış.|22|
|Numaralandırmalar|[Sabit Listeleri](#enums)|Temel bir enum türü yerleşik bir CLS tamsayı türü olacaktır, alanın adı "value__" olacaktır ve bu alanın işaretlenmesi `RTSpecialName`.|7|
|Numaralandırmalar|[Sabit Listeleri](#enums)|Bir varlığı veya yokluğu ile gösterilen iki ayrı türü vardır <xref:System.FlagsAttribute?displayProperty=nameWithType> (bkz: bölüm IV kitaplığı) özel öznitelik. Biri, adlandırılmış tamsayı değerlerini temsil eder; diğer temsil eder, adlandırılmamış değer üretmek için birleştirilebilen bit bayrakları adı. Değerini bir `enum` belirtilen değerlerle sınırlı değildir.|8|
|Numaralandırmalar|[Sabit Listeleri](#enums)|Bir enumun değişmez statik alanları numaralandırma türüne sahip olamaz.|9|
|Olaylar|[Olaylar](#events)|Bir olay uygulayan yöntemler olarak işaretlenmeyecektir `SpecialName` meta verilerinde.|29|
|Olaylar|[Olaylar](#events)|Bir olay ve onun erişimcilerinin erişilebilirliği aynı olacaktır.|30|
|Olaylar|[Olaylar](#events)|`add` Ve `remove` yöntemleri için bir olay ya da her ikisini de gelecektir mevcut olmalı veya olmamalıdır.|31|
|Olaylar|[Olaylar](#events)|`add` Ve `remove` yöntemleri bir olay her bir parametre türü almalı olay türünü tanımlar ve öğesinden türetilmelidir <xref:System.Delegate?displayProperty=nameWithType>.|32|
|Olaylar|[Olaylar](#events)|Olaylar, belirli bir adlandırma desenine uymalıdır. `SpecialName` CLS kural 29 başvurulan özniteliği uygun ad karşılaştırmalarında yoksayılmalı ve tanımlayıcı kurallarına uymalıdır.|33|
|Özel Durumlar|[Özel Durumlar](#exceptions)|Oluşan nesneler, türü olacaktır <xref:System.Exception?displayProperty=nameWithType> veya ondan devralınan bir türde. Öte yandan, CLS uyumlu yöntemler diğer tür özel durumların yayılmasını engellemek için gerekli değildir.|40|
|Genel|[CLS uyumluluğu: kurallar](#Rules)|CLS kuralları yalnızca erişilebilir veya derlemenin dışında görünür olan bir tür bölümlerini uygulanır.|1\.|
|Genel|[CLS uyumluluğu: kurallar](#Rules)|CLS olmayan uyumlu türlerin üyeleri CLS uyumlu olarak işaretlenmeyecektir.|2|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|İç içe geçmiş türler en az kadar genel parametresi kapsayan tür olmalıdır. İç içe bir türde genel parametreler kapsayan türdeki genel parametrelere konuma göre karşılık gelir.|42|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Genel bir tür adını iç içe olmayan türde bildirilen veya yukarıda tanımlanan kurallara göre iç içe türü için yeni sunulan tür parametrelerinin sayısı kodlayın.|43|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Genel tür, genel tür kısıtlamaları tarafından temel türü veya arabirim kısıtlama getirilmez garanti edecek yeterli kısıtlamaları yeniden bildirmek.|4444|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Genel parametreler üzerinde kısıtlama olarak kullanılan türler kendilerini CLS uyumlu olmalıdır.|45|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Görünürlük ve erişilebilirliği (iç içe türler dahil) oluşturulmuş bir genel türde üyelerin bir bütün olarak genel tür bildirimi yerine belirli bir örnek Kapsamınızın göz önünde bulundurulmalıdır. Bu varsayılırsa, CLS kuralı 12 görünürlük ve erişilebilirlik kuralları hala geçerlidir.|46|
|Genel Türler|[Genel türler ve Üyeler](#Generics)|Her Özet veya sanal genel yöntem için varsayılan bir somut (soyut olmayan) uygulama olacaktır.|47|
|Arabirimler|[Arabirimler](#Interfaces)|CLS uyumlu arabirimler CLS olmayan uyumlu yöntem tanımına uygulamak için gerektirmez.|18|
|Arabirimler|[Arabirimler](#Interfaces)|CLS uyumlu arabirimler statik yöntemleri tanımlamak değil ya da alanlarını tanımlarlar.|19|
|Üyeler|[Genel olarak tür üyeleri](#members)|Genel statik alanlar ve yöntemler CLS uyumlu değildir.|36|
|Üyeler|--|Bir değişmez statik değeri, alan başlatma meta verileri kullanılarak belirtilir. CLS uyumlu bir hazır değer değişmez değer olarak tam olarak aynı türde olan alan başlatma meta verilerinde belirtilen bir değeri olmalıdır (veya hazır bilgi ise temel türdeki bir `enum`).|13|
|Üyeler|[Genel olarak tür üyeleri](#members)|Vararg kısıtlaması CLS'nin parçası değildir ve CSL tarafından desteklenen tek çağırma kuralı, standart yönetimli çağırma kuralıdır olduğu.|15|
|Adlandırma kuralları|[Adlandırma kuralları](#naming)|Derlemeleri Annex 7, teknik rapor 15, başlatmak ve tanımlayıcıları, kullanılabilir adresindeki çevrimiçi eklenmesi için izin verilen karakter kümesini yöneten Unicode Standard3.0 izleyin <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>. Tanımlayıcıları Unicode normalleştirme Form c tarafından tanımlanan kurallı biçimde olmalıdır Harfli eşlemeler (Unicode yerel ayara duyarlı, bire bir küçük harf eşlemeler tarafından belirtildiği gibi) aynıysa CLS amacıyla, iki tanımlayıcı aynıdır. Diğer bir deyişle, iki tanımlayıcı CLS altında farklı kabul edilmesi için daha çok, farklı olacaktır. Ancak, devralınan bir tanımı geçersiz kılmak için CLI'yı özgün bildirimin kesin kodlama kullanılmasını gerektirir.|4|
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|CLS uyumlu kapsamda sunulan tüm adlar, ayrı bağımsız tür adları aynı ve aşırı yükleme olduğu dışında tutulamaz. Diğer bir deyişle, CTSallows tek bir türün bir yöntem ve bir alan için aynı adı kullanın, buna izin vermez.|5|
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|CTS sağlayan ayrı imzaların ayırt edici olarak rağmen alanlar ve iç içe geçmiş türler yalnızca, tanımlayıcı karşılaştırması ile farklı olacaktır. Yöntemler, özellikler ve olaylar (tanımlayıcı karşılaştırmasına göre) aynı ada sahip yalnızca dönüş türüne göre farklı olmalıdır da CLS kuralı 39'da belirtilen hariç.|6|
|Aşırı Yükleme|[Overloads](#overloads)|Özellikler ve yöntemler aşırı yüklenebilir.|37|
|Aşırı Yükleme|[Overloads](#overloads)|Özellikler ve yöntemler aşırı yüklenebilir yalnızca sayı ve dönüştürme işleçleri dışında parametre türleri temel `op_Implicit` ve `op_Explicit`, kendi dönüş türüne bağlı olarak, aynı zamanda aşırı yüklenebilir.|38|
|Aşırı Yükleme|--|Bir türde bildirilen iki veya daha fazla CLS uyumlu yöntem aynı ada sahip ve belirli bir tür örneklemeleri kümesi, aynı parametre ve dönüş türleri, tüm bu yöntemleri bu tür anlamsal olarak eşdeğer olacaktır.|48|
|Türler|[Tür ve tür üyesi imzaları](#Types)|<xref:System.Object?displayProperty=nameWithType> CLS uyumludur. CLS uyumlu herhangi bir sınıf, CLS uyumlu bir sınıftan devralmalıdır.|23|
|Özellikler|[Özellikler](#properties)|Bir özelliğin alıcı ve ayarlayıcı yöntemleri uygulayan yöntemler olarak işaretlenmeyecektir `SpecialName` meta verilerinde.|24|
|Özellikler|[Özellikler](#properties)|Özelliğin erişimcileri tüm statik olmalıdır, tüm sanal ya da tamamen örnek olmalıdır.|26|
|Özellikler|[Özellikler](#properties)|Özellik türü alıcının dönüş türü ve ayarlayıcının son bağımsız değişken türü olmalıdır. Özelliğin parametrelerinin türleri türler alıcı ve tüm tür parametreleri ancak ayarlayıcının son parametre olmalıdır. Tüm bu türler CLS uyumlu olmalıdır ve işaretçileri yönetemezler tutulamaz (yani, başvuruyla geçirilmemelidir).|27|
|Özellikler|[Özellikler](#properties)|Özellikler, belirli bir adlandırma desenine uymalıdır. `SpecialName` CLS kural 24 başvurulan özniteliği uygun ad karşılaştırmalarında yoksayılmalı ve tanımlayıcı kurallarına uymalıdır. Bir özelliğin bir alıcı yöntemi, ayarlayıcı yöntemi veya her ikisi de olmalıdır.|28|
|Tür dönüştürme|[Tür dönüştürme](#conversion)|Ya da `op_Implicit` veya `op_Explicit` zorlama sağlama aracı alternatif bir yol sağlanacaktır sağlanır.|39|
|Türler|[Tür ve tür üyesi imzaları](#Types)|Paketlenmiş değer türleri CLS uyumlu değildir.|3|
|Türler|[Tür ve tür üyesi imzaları](#Types)|Bir imzada görünen tüm türler CLS uyumlu olmalıdır. Örneklenen bir genel türü oluşturan tüm türler CLS uyumlu olmalıdır.|11|
|Türler|[Tür ve tür üyesi imzaları](#Types)|Türü belirlenmiş başvurular, CLS uyumlu değildir.|14|
|Türler|[Tür ve tür üyesi imzaları](#Types)|Yönetilmeyen işaretçi türleri CLS uyumlu değildir.|17|
|Türler|[Tür ve tür üyesi imzaları](#Types)|CLS uyumlu sınıflar, değer türleri ve arabirimler, CLS uyumlu olmayan üyelerinin uygulamasını gerektirmez.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Türler ve tür üyesi imzaları

<xref:System.Object?displayProperty=nameWithType> Türü CLS uyumlu ve .NET Framework tür sistemindeki tüm nesne türlerinin temel türü değil. .NET Framework'te devralma ya da olan örtülü (örneğin, <xref:System.String> sınıfı örtük olarak devraldığı <xref:System.Object> sınıfı) veya açık (örneğin, <xref:System.Globalization.CultureNotFoundException> sınıfı açık olarak devralınılır <xref:System.ArgumentException> sınıfı, hangi Açık <xref:System.SystemException> açıkça öğesinden devralan sınıf <xref:System.Exception> sınıfı). Türetilmiş bir tür CLS uyumlu olacak şekilde bilgi için kendi temel türü de CLS uyumlu olmalıdır.

Aşağıdaki örnek, temel türü CLS uyumlu değil, türetilmiş bir tür gösterir. Temel tanımlar `Counter` sayaç olarak imzalanmamış bir 32 bitlik tamsayı kullanan sınıf. Sınıfı, bir işaretsiz tamsayıyı kaydırarak sayaç işlevi sağladığından, sınıf CLS uyumlu olmayan olarak işaretlenir. Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter`, ayrıca CLS uyumlu değil.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Bir yöntemin dönüş türü veya özellik türü dahil olmak üzere, üye imzalarında görüntülenen tüm türler CLS uyumlu olmalıdır. Ayrıca, genel türler için:

- Örneklenen bir genel türü oluşturan tüm türler CLS uyumlu olmalıdır.

- Genel parametreler üzerinde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır.

.NET Framework [ortak tür sistemi](../../docs/standard/base-types/common-type-system.md) bir derlemenin meta verilerde özel olarak kodlanmış, doğrudan ortak dil çalışma zamanı tarafından desteklenen yerleşik türler içerir. Bu gerçek türlerden, aşağıdaki tabloda listelenen türler CLS uyumludur.

|CLS uyumlu türü|Açıklama|
|-------------------------|-----------------|
|<xref:System.Byte>|8 bitlik işaretsiz tamsayı|
|<xref:System.Int16>|16 bit işaretli tamsayı|
|<xref:System.Int32>|32 bitlik işaretli tamsayı|
|<xref:System.Int64>|64-bit işaretli tamsayı|
|<xref:System.Single>|Tek duyarlıklı kayan nokta değeri|
|<xref:System.Double>|Çift duyarlıklı kayan nokta değeri|
|<xref:System.Boolean>|`true` veya `false` değer türü|
|<xref:System.Char>|UTF-16 kodlu kod birimi|
|<xref:System.Decimal>|Ondalık sayı olmayan kayan nokta|
|<xref:System.IntPtr>|İşaretçisi veya tutamacı bir platform tanımlı boyutun|
|<xref:System.String>|Sıfır, bir veya daha fazla koleksiyonu <xref:System.Char> nesneleri|

Aşağıdaki tabloda listelenen gerçek türler CLS uyumlu değildir.

|Uyumsuz tür|Açıklama|CLS uyumlu alternatif|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|8 bitlik işaretli tamsayı veri türü|<xref:System.Int16>|
|<xref:System.TypedReference>|Bir nesne ve onun çalışma zamanı türü işaretçisi|None|
|<xref:System.UInt16>|16-bit işaretsiz tamsayı|<xref:System.Int32>|
|<xref:System.UInt32>|32-bit işaretsiz tamsayı|<xref:System.Int64>|
|<xref:System.UInt64>|64-bit işaretsiz tamsayı|<xref:System.Int64> (taşabilir), <xref:System.Numerics.BigInteger>, veya <xref:System.Double>|
|<xref:System.UIntPtr>|İmzalanmamış işaretçi veya işleç|<xref:System.IntPtr>|

.NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı, CLS uyumlu olmayan diğer türleri içerebilir. Örneğin:

- Paketlenmiş değer türleri. Aşağıdaki C# örneği bir ortak özellik türü olan bir sınıf oluşturur `int*` adlı `Value`. Çünkü bir `int*` bir kutulanmış değer türü olduğundan Derleyici bunu CLS-uyumlu değil olarak işaretler.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Yazılı başvurular, bir nesneye başvuru ve bir türe başvuru içeren özel bir yapıdır. Yazılan başvurular .NET Framework tarafından temsil edilir <xref:System.TypedReference> sınıfı.

Bir tür CLS uyumlu değilse, uygulamalıdır <xref:System.CLSCompliantAttribute> özniteliğini bir `isCompliant` değerini `false` ona. Daha fazla bilgi için [CLSCompliantAttribute özniteliği](#CLSAttribute) bölümü.

Aşağıdaki örnek, bir yöntem imzası ve genel tür örneği oluşturmada CLS uyumluluğu sorununu göstermektedir. Tanımladığı bir `InvoiceItem` sınıf türünde bir özellik ile <xref:System.UInt32>, türünde bir özellik `Nullable(Of UInt32)`ve tür parametreleri olan bir oluşturucusu <xref:System.UInt32> ve `Nullable(Of UInt32)`. Bu örneği derlemeye çalıştığınızda, dört derleyici uyarısı alırsınız.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Derleyici uyarılarını ortadan kaldırmak için CLS uyumlu olmayan türleri yerine `InvoiceItem` genel arabiriminde:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Listelenen belirli türlere ek olarak, bazı türden kategoriler CLS uyumlu değildir. Bunlar, yönetilmeyen işaretçi türleri ve işlev işaretçi türlerini içerir. Aşağıdaki örnek, tamsayı dizisi oluşturmak için bir tamsayı işaretçisi kullandığından bir derleyici uyarısı oluşturur.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

CLS uyumlu soyut sınıflar (olarak işaretlenen sınıflar `abstract` C# veya olarak `MustInherit` Visual Basic'te), sınıfın tüm üyeleri de CLS uyumlu olmalıdır.

<a name="naming"></a>

### <a name="naming-conventions"></a>Adlandırma kuralları

Bazı programlama dilleri büyük/küçük harfe duyarsızdır çünkü tanımlayıcılarını (örneğin, ad alanları, türler ve üyeler adları) daha fazla farklı olmalıdır. İki tanımlayıcı küçük eşlemeleri aynı ise eşdeğer olarak kabul edilir. Aşağıdaki C# örneği iki genel sınıfı tanımlar `Person` ve `person`. Bunlar yalnızca büyük küçük harfle farklı olduğundan, C# derleyicisi bunları CLS uyumlu değil işaretler.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Ad alanları, türler ve üyeler, adları gibi Dil tanımlayıcıları programlama uygun olması gerekir [Unicode standartı 3.0, teknik rapor 15, ek 7](https://www.unicode.org/reports/tr15/tr15-18.html). Bunun anlamı:

- Bir tanımlayıcının ilk karakteri olması herhangi bir Unicode büyük harf, küçük harf, başlık biçimindeki harf, değiştirici harf, başka bir harf veya harf numarası. Unicode karakter kategorileri hakkında daha fazla bilgi için bkz: <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> sabit listesi.

- İzleyen karakterler, ilk karakter olarak kategorilerden birini olabilir ve aralıksız işaretler, aralık birleştirme işaretleri, ondalık sayılar, bağlayıcı noktalamalar ve biçimlendirme kodları da içerebilir.

Tanımlayıcıları karşılaştırmadan önce biçimlendirme kodlarını filtrelemeniz ve tek bir karakter birden çok UTF-16 kodlu kod birimi tarafından temsil edilebildiğinden tanımlayıcıları Unicode normalleştirme formu C'ye dönüştürmeniz gerekir. Unicode normalleştirme formu C'de aynı kod birimlerini üreten karakter sıraları CLS uyumlu değildir. Aşağıdaki örnek adlı bir özellik tanımlar `Å`ANGSTROM SIGN (U + 212B) karakterinden oluşan oluşur ve adlı ikinci `Å`, LATIN CAPITAL LETTER A WITH RING ABOVE (U + 00 C 5) karakterinden oluşan oluşur. C# ve Visual Basic derleyicileri, kaynak kodunu CLS uyumlu olmayan olarak bayrak.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

(Örneğin, bir ad alanı içindeki türleri ya da bir tür içindeki üyelerden bir derleme içinde ad uzayları) belirli bir kapsam içindeki üye adları, aşırı yükleme yoluyla çözülmüş adlar dışında benzersiz olmalıdır. Bu gereksinim kapsamı içinde farklı türde üye oldukları sürece aynı adlara sahip birden çok üye veren ortak tür sistemi, daha fazla katı (örneğin, bir yöntem biridir ve bir alan biridir). Özellikle, tür üyeleri için:

- Alanlar ve iç içe geçmiş türler yalnızca ad ile ayırt edilir.

- Yöntemler, özellikler ve aynı ada sahip olaylar birden fazla sadece dönüş türüne göre farklı olmalıdır.

Aşağıdaki örnek üye adlarının kendi kapsamı içinde benzersiz olması şartını göstermektedir. Adlı bir sınıf tanımlar `Converter` adlı dört üye içeren `Conversion`. Üçü yöntemdir ve birisi bir özelliktir. İçeren yöntemi bir <xref:System.Int64> parametresi benzersiz olarak adlandırılır, ancak iki yöntemle bir <xref:System.Int32> parametresi değildir, çünkü dönüş değeri bir üyenin imzasının bir parçası olarak kabul edilmez. `Conversion` Özelliği Özellikler aşırı yüklenmiş yöntemlerle aynı ada sahip olamaz çünkü bu gereksinim, ayrıca ihlal.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Diller ortak dil çalışma zamanını hedefleyen de anahtar sözcükleri ile Birleşen tanımlayıcıları (Tür adları gibi) başvuran bazı mekanizma sağlamanız gerekir tek tek dillerde benzersiz anahtar sözcükler içerir. Örneğin, `case` hem C# ve Visual Basic'te bir anahtar sözcüktür. Ancak, aşağıdaki Visual Basic örnek adlı bir sınıfın belirsizliğini ortadan kaldırabilir, `case` gelen `case` açma ve kapatma küme ayraçlarını kullanarak anahtar sözcüğü. Aksi takdirde, örnek "Anahtar sözcüğü, bir tanımlayıcı olarak geçerli değil" hata iletisini oluşturur ve bu derleme başarısız.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

Aşağıdaki C# örnek örneğini oluşturabilir, `case` sınıfı kullanarak `@` dil anahtar kelimesi tanımlayıcıdan ayırt etmek için simge. Bu olmadan, C# derleyicisi iki hata iletisi, "Tür bekleniyor" ve "geçersiz ifade terimi 'case'." görüntülenir

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Tür dönüştürme

Ortak dil belirtimi iki dönüştürme işleci tanımlar:

- `op_Implicit`, veri veya duyarlık kaybına neden olmayan dönüştürmesi için kullanılır. Örneğin, <xref:System.Decimal> yapısı içeren aşırı yüklenmiş bir `op_Implicit` tam sayı türlerinin değerlerini dönüştürmek için işleci ve <xref:System.Char> değerler <xref:System.Decimal> değerleri.

- `op_Explicit`, büyüklük (bir değer daha küçük bir aralığı olan bir değere dönüştürülür) veya duyarlık kaybına neden dönüştürmeleri daraltma için kullanılır. Örneğin, <xref:System.Decimal> yapısı içeren aşırı yüklenmiş bir `op_Explicit` dönüştürme işleci <xref:System.Double> ve <xref:System.Single> değerler <xref:System.Decimal> ve dönüştürmek için <xref:System.Decimal> değerlerini tam sayı değerlerine <xref:System.Double>, <xref:System.Single>, ve <xref:System.Char>.

Ancak, tüm diller, İşleç aşırı yüklemesi veya özel işleçlerin tanımını desteklemez. Bu dönüştürme işleçlerini uygulamayı seçerseniz dönüştürmeyi gerçekleştirmenin alternatif bir yolu da sağlamanız gerekir. Sağlamanızı öneririz `From` *Xxx* ve `To` *Xxx* yöntemleri.

Aşağıdaki örnek, CLS uyumlu örtülü ve açık dönüştürmeleri tanımlar. Oluşturur bir `UDouble` imzalı çift duyarlıklı, kayan noktalı sayıyı temsil eden sınıf. Örtük dönüştürmelerine sağlayan `UDouble` için <xref:System.Double> ve açık dönüşümlerse `UDouble` için <xref:System.Single>, <xref:System.Double> için `UDouble`, ve <xref:System.Single> için `UDouble`. Ayrıca tanımlar bir `ToDouble` yöntemi örtülü dönüştürme işlecine bir alternatif olarak ve `ToSingle`, `FromDouble`, ve `FromSingle` açık dönüştürme işleçleri için alternatif yöntemler.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Diziler

CLS uyumlu diziler şu kurallara uyar:

- Tüm boyutlar bir dizinin alt sınırı sıfır olmalıdır. Aşağıdaki örnek, bir alt sınırı bir olan CLS uyumlu olmayan bir dizi oluşturur. Unutmayın varlığına rağmen <xref:System.CLSCompliantAttribute> özniteliği, derleyici tarafından saptanmayan tarafından döndürülen dizinin `Numbers.GetTenPrimes` yöntemi CLS uyumlu değil.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Tüm dizi öğeleri, CLS uyumlu türlerden oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan bir dizi döndüren iki yöntemi tanımlar. İlk bir dizi döndürür <xref:System.UInt32> değerleri. İkinci döndürür bir <xref:System.Object> içeren bir dizi <xref:System.Int32> ve <xref:System.UInt32> değerleri. Derleyici ilk diziyi uyumlu nedeniyle tanımlasa da, <xref:System.UInt32> türü başarısız ikinci dizinin CLS uyumlu olmayan öğeler içerdiğini anlayamaz.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Dizi parametreleri olan yöntemler için aşırı yükleme çözünürlüğü olduklarından dayanarak gerçeğine ve kendi öğe türünde ' dir. Bu nedenle, aşırı yüklenmiş bir aşağıdaki tanımını `GetSquares` yöntemi CLS uyumludur.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Arabirimler

CLS uyumlu arabirimler, özellikleri, olayları ve sanal yöntemleri (uygulama içermeyen yöntemleri) tanımlayabilir. CLS uyumlu bir arabirim şunlardan herhangi birini içeremez:

- Statik yöntemler veya static alanlar. C# ve Visual Basic derleyicileri, bir arabirimde statik bir üye tanımlarsanız derleyici hataları oluşturur.

- Alanları. C# ve Visual Basic derleyicileri, bir arabirimde bir alan tanımlarsanız derleyici hataları oluşturur.

- CLS uyumlu olmayan yöntemleri. Örneğin, aşağıdaki arabirim tanımı bir yöntem içerir `INumber.GetUnsigned`, yani olarak CLS uyumlu olmayan olarak işaretlenmiş. Bu örnek, bir derleyici uyarısı oluşturur.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Bu kural nedeniyle, CLS uyumlu türler CLS uyumlu olmayan üyeleri uygulamak için gerekli değildir. CLS uyumlu bir çerçeve, CLS olmayan uyumlu arabirimi uygulayan bir sınıfı gösterirse, CLS uyumlu olmayan tüm üyelerinin somut uygulamalarını da sağlamanız gerekir.

CLS uyumlu dil derleyicileri de birden fazla arabirimde aynı ada ve imzaya sahip üyelerin ayrı uygulamalarını sağlamak bir sınıf izin vermeniz gerekir.  Hem C# ve Visual Basic desteği [açık arabirim uygulamalarını](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) , aynı adlı yöntemlerin farklı uygulamalarını sağlamak için. Visual Basic de destekler `Implements` belirli bir üyenin hangi arabirimi ve açıkça atamak sağlayan anahtar sözcüğü uygular. Aşağıdaki örnek, tanımlayarak bu senaryoyu gösteren bir `Temperature` uygulayan sınıf `ICelsius` ve `IFahrenheit` arabirimlerini açık arabirim uygulamalarını olarak.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Numaralandırmalar

CLS uyumlu numaralandırmalar şu kurallara uymalıdır:

- Sabit listesinin temel alınan türü bir iç CLS uyumlu tamsayı olmalıdır (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, veya <xref:System.Int64>). Aşağıdaki kod gibi temel alınan türü olan bir numaralandırma tanımlamayı dener <xref:System.UInt32> ve bir derleyici uyarısı oluşturur.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Bir numaralandırma türü adlı tek bir örnek alanına sahip olmalıdır `Value__` ile işaretlenmiş <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> özniteliği. Bu, alan değerine dolaylı başvuru sağlar.

- Bir numaralandırma eşleşen türleri numaralandırma türüyle eşleşen değişmez statik alanları içerir. Örneğin, tanımladığınız bir `State` sabit listesi değerleri ile `State.On` ve `State.Off`, `State.On` ve `State.Off` türü olan sabit statik alanlarsa olan `State`.

- Numaralandırmanın iki türü vardır:

  - Birbirini dışlayan bir dizi adlandırılmış tamsayı değerlerini temsil eden bir sabit listesi. Bu numaralandırma türü yokluğuyla <xref:System.FlagsAttribute?displayProperty=nameWithType> özel öznitelik.

  - Adlandırılmamış değer üretmek için birleştirilebilen bit bayrakları kümesini temsil eden bir sabit listesi. Bu numaralandırma türü varlığını tarafından belirtilen <xref:System.FlagsAttribute?displayProperty=nameWithType> özel öznitelik.

  Daha fazla bilgi için belgelerine bakın <xref:System.Enum> yapısı.

- Bir numaralandırma değeri, belirtilen değerler aralığıyla sınırlı değildir. Diğer bir deyişle, bir numaralandırmada değerler aralığı kendi temel değer aralığıdır. Kullanabileceğiniz <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> bir belirtilen değerin bir numaralandırma üyesi olup olmadığını belirlemek için yöntemi.

<a name="members"></a>

### <a name="type-members-in-general"></a>Genel olarak tür üyeleri

Ortak dil belirtimi, tüm alanlar ve yöntemler, belirli bir sınıfın üyesi olarak erişilmesini gerektirir. Bu nedenle, genel statik alanlar ve yöntemler (diğer bir deyişle, statik alanlar veya bir türden ayrı tanımlanan yöntemler) CLS uyumlu değildir. Genel alan veya yöntem kaynak kodunuzu eklemeye çalışırsanız, C# ve Visual Basic derleyicileri bir derleyici hatası oluşturur.

Ortak dil belirtimi yalnızca standart yönetilen çağırma kuralı destekler. Yönetilmeyen çağırma kurallarını desteklemeyen ve yöntemleri değişken bağımsız değişken listesiyle işaretlenmiş `varargs` anahtar sözcüğü. Standart yönetilen çağırma kuralı ile uyumlu olan değişken bağımsız değişken listeleri için <xref:System.ParamArrayAttribute> özniteliği veya tek tek dilin uygulamasını gibi `params` C# anahtar sözcüğü ve `ParamArray` Visual Basic'teki.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Üye erişilebilirliği

Devralınmış bir üyeyi geçersiz kılmak o üyenin erişilebilirliğini değiştiremezsiniz. Örneğin, genel bir temel sınıf yöntemi özel bir yöntem türetilmiş bir sınıf tarafından geçersiz kılınamaz. Bir istisna vardır: bir `protected internal` (C# ' de) veya `Protected Friend` (Visual Basic'te) üyesi farklı bir derlemedeki bir türe tarafından geçersiz kılınan bir derlemedeki. Bu durumda geçersiz kılma erişimi olan `Protected`.

Oluşan hata aşağıdaki örnekte oluşturulan <xref:System.CLSCompliantAttribute> özniteliği `true`, ve `Human`, bir sınıf, türetilir `Animal`, erişilebilirliğini özele değiştirmeye `Species` özelliği Genel özel. Erişilebilirlik genel olarak değişirse örnek başarıyla derler.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Bir üyenin İmzasındaki türler, üye erişilebilir olduğunda erişilebilir olması gerekir. Örneğin, bu genel bir üyenin, türü özel, korumalı veya iç olan bir parametre içeremez anlamına gelir. Sonuçları derleyici hatası aşağıdaki örnekte, bir `StringWrapper` sınıf oluşturucusu bir iç sunan `StringOperationType` bir dize değerinin nasıl sarılacağını belirleyen sabit listesi değeri.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Genel türler ve Üyeler

İç içe geçmiş türler, her zaman kapsayan türü en az sayıda genel parametrelere sahip. Bunlar, kapsayan türdeki genel parametrelere konuma göre karşılık gelir. Genel tür de yeni genel parametreler ekleyebilirsiniz.

Genel tür parametreleri bir kapsayan tür ile onun iç içe geçmiş türler arasındaki ilişki, tek tek dillerin sözdizimi tarafından gizlenmiş olabilir. Aşağıdaki örnekte, genel tür `Outer<T>` içeren iki iç içe geçmiş sınıflar `Inner1A` ve `Inner1B<U>`. Çağrıları `ToString` her sınıf öğesinden devralan yöntemi <xref:System.Object.ToString%2A?displayProperty=nameWithType>, iç içe geçmiş sınıf her sınıfın kapsayan sınıf türü parametreleri içerdiğini gösterir.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Genel tür adları biçiminde kodlanır *adı\`n*burada *adı* tür adıdır \` bir karakter değişmez değeridir ve *n* sayısı Tür parametreleri türü veya iç içe geçmiş genel türler, sayısı için yeni olarak bildirilen parametreleri sunmuştur. Bu genel tür adları kodlaması öncelikle bir kitaplıktaki CLS uyumlu genel türlere erişmek için yansımayı kullanan geliştiricileri ilgilendirir.

Bir genel kısıtlamalar uygulanırsa kısıtlamaları de CLS uyumlu olmalıdır olarak kullanılan türler yazın. Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` yani değil CLS uyumlu ve adlı bir genel sınıf `BaseCollection` tür parametresi türetilmesi gereken `BaseClass`. Ancak `BaseClass` CLS uyumlu değilse derleyici bir uyarı gösterir.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Genel bir tür genel bir temel türden türetilirse, temel tür kısıtlamaları da karşılanır karşılanmasını garantileyebilmesi için kısıtlamaları gerekir. Aşağıdaki örnekte tanımlayan bir `Number<T>` herhangi bir sayısal türü temsil edebilir. Ayrıca tanımlar bir `FloatingPoint<T>` sınıfı temsil eder bir kayan nokta değeri. Bu kısıtlama geçerli değildir çünkü Bununla birlikte, Kaynak Kodu derlemek, başarısız `Number<T>` (T bir değer türü olması gerekir) için `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Kısıtlama eklenirse örnek başarıyla derler `FloatingPoint<T>` sınıfı.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Ortak dil belirtimi, bir iç içe geçmiş türler için her örnekleme başına koruyucu modeli uygular ve korumalı üyeler. Açık genel türler, belirli bir örneğini oluşturmada iç içe, korunan bir genel tür içeren imzaları olan alanları veya üyeleri gösteremez. Genel temel sınıfı veya arabiriminin belirli bir örneğini genişleten genel olmayan türler, farklı bir örneğini oluşturmada iç içe, korunan bir genel tür içeren imzaları olan alanları veya üyeleri gösteremez.

Aşağıdaki örnek bir genel tür tanımlar `C1<T>` (veya `C1(Of T)` Visual Basic'te) ve korumalı bir sınıf `C1<T>.N` (veya `C1(Of T).N` Visual Basic'te). `C1<T>` iki yönteme sahiptir `M1` ve `M2`. Ancak, `M1` getirmeyi denediğinden CLS uyumlu değil bir `C1<int>.N` (veya `C1(Of Integer).N`) C1 nesneden\<T > (veya `C1(Of T)`). İkinci bir sınıf `C2`, türetilen `C1<long>` (veya `C1(Of Long)`). İki yönteme sahiptir `M3` ve `M4`. `M3` getirmeyi denediğinden CLS uyumlu değil bir `C1<int>.N` (veya `C1(Of Integer).N`) öğesinin nesneden `C1<long>`. Dil derleyicileri daha kısıtlayıcı olabileceğine dikkat edin. Derlemeye çalıştığında bu örnekte, Visual Basic bir hata gösterir. `M4`.

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Oluşturucular

CLS uyumlu sınıf ve yapılardaki oluşturucular bu kuralları izlemelidir:

- Devralınan örnek verilerine erişmeden önce bir oluşturucu türetilmiş bir sınıfın temel sınıfının örnek oluşturucusunu çağırmalıdır. Temel sınıf Kurucularını kendi türetilmiş sınıfları tarafından miras alınmamasından ötürü olabilir, bu gereksinim olmasıdır. Bu kural doğrudan devralmayı desteklemeyen yapılar için geçerli değildir.

  Genellikle, derleyiciler bu kuralı aşağıdaki örnekte gösterildiği gibi CLS uyumluluğundan bağımsız olarak uygular. Oluşturur bir `Doctor` türetilen sınıf bir `Person` sınıfı, ancak `Doctor` sınıfı başarısız olursa çağrılacak `Person` devralınan örnek alanları başlatmak için sınıfın Oluşturucusu.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Nesne Oluşturucu, nesne oluşturma dışında çağrılamaz. Ayrıca, bir nesne iki kez başlatılamaz. Örneğin, yani <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> ve yöntemler gibi seri durumdan çıkarma <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> oluşturucular çağırmamalıdır.

<a name="properties"></a>

### <a name="properties"></a>Özellikler

CLS uyumlu türlerdeki özellikler şu kurallara uymalıdır:

- Bir özelliğin bir Ayarlayıcısı, alıcısı veya her ikisi de olmalıdır. Bir derlemede, bunlar özel yöntemler olarak deyişle ayrı yöntemler olarak görünür uygulanır (alıcı adlı `get_` *propertyname* ayarlayıcı `set_` *propertyname*) olarak işaretlenmiş `SpecialName` derlemenin meta verilerinde. C# ve Visual Basic derleyicileri otomatik olarak uygulamak için gerek kalmadan bu kuralı zorunlu <xref:System.CLSCompliantAttribute> özniteliği.

- Bir özelliğin özellik alıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türüdür. Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler atanamaz özelliği başvuruya göre (diğer bir deyişle, bunlar yönetilen işaretçiler olamaz).

- Bir özellik hem alıcı hem de ayarlayıcı varsa, bunlar hem de sanal olmalıdır hem statik veya her ikisi de örnek. C# ve Visual Basic derleyicileri otomatik olarak kendi özellik tanımı sözdizimleri aracılığıyla bu kuralı uygular.

<a name="events"></a>

### <a name="events"></a>Olaylar

Bir olay adı ve türüne göre tanımlanır. Olay türü olayı göstermek için kullanılan bir temsilcidir. Örneğin, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay türüdür <xref:System.ResolveEventHandler>. Olayın kendisinin yanı sıra, olay adına dayandırılan adlara sahip üç yöntem olayın uygulanmasını sağlar ve olarak işaretlenmiş `SpecialName` derlemenin meta verilerinde:

- Adlı bir olay işleyicisi eklemek için bir yöntem `add_` *EventName*. Örneğin, olay aboneliği yöntemi için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay adlı `add_AssemblyResolve`.

- Adlı bir olay işleyicisini kaldırma yöntemi `remove_` *EventName*. Örneğin, kaldırma yöntemi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay adlı `remove_AssemblyResolve`.

- Adlı olayın oluştuğunu belirten bir yöntem `raise_` *EventName*.

> [!NOTE]
> Olaylara ilişkin ortak dil belirtimi kurallarının çoğu, dil derleyiciler tarafından uygulanır ve Bileşen geliştiriciler için saydamdır.

Ekleme yöntemleri, kaldırma ve olayı tetiklenmeden aynı erişilebilirliği olmalıdır. Bunlar ayrıca tümü statik olmalıdır örneği veya sanal. Yöntem ekleme ve kaldırma olay türü olay temsilci türü olan bir parametreye sahip. Ekleme ve kaldırma yöntemlerinin her ikisi de bulunmalıdır veya ikisi de olmamalıdır.

Aşağıdaki örnekte adlı, CLS uyumlu bir sınıf tanımlar `Temperature` oluşturan bir `TemperatureChanged` iki okuma arasındaki sıcaklık değişikliği değerine eşit veya eşik değeri, olay. `Temperature` Sınıfı açıkça tanımlayan bir `raise_TemperatureChanged` yöntemi olan olay işleyicileri seçmeli olarak çalıştırabilirsiniz.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Aşırı Yüklemeler

Ortak dil belirtimi, aşırı yüklenmiş üyelerde aşağıdaki gereksinimleri karşılamalıdır:

- Parametre sayısı ve herhangi bir parametre türüne göre üyeler aşırı yüklenebilir. Çağırma kuralı, dönüş türü özel değiştiriciler yönteme veya parametresine uygulanan ve parametrelerin değere veya başvuruya göre iletilir dikkate alınmaz aşırı yükler arasında ayrım yapılırken. Adları gereksinim bir kapsam içinde benzersiz olmalıdır. Örneğin, kodu görmek [adlandırma kuralları](#naming) bölümü.

- Özellikler ve yöntemler aşırı yüklenebilir. Alanlar ve olaylar aşırı yüklenemez.

- Genel yöntemler, genel parametrelerinin sayısına göre aşırı yüklenebilir.

> [!NOTE]
> `op_Explicit` Ve `op_Implicit` işleçler şunlardır: değer olarak kabul edilmez aşırı yükleme çözümlemesi için bir yöntem imzasının parçası döndüren kuralının istisnalarıdır. Bu iki işleç hem parametreleri hem de dönüş değerlerine bağlı olarak aşırı yüklenebilir.

<a name="exceptions"></a>

### <a name="exceptions"></a>Özel Durumlar

Özel durum nesneleri türetilmesi gereken <xref:System.Exception?displayProperty=nameWithType> veya başka bir türden türetilmiş <xref:System.Exception?displayProperty=nameWithType>. Aşağıdaki örnekte adlı özel bir sınıf olmadığında ortaya çıkar.%nÇözüm derleyici hatası `ErrorClass` özel durum işleme için kullanılır.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Bu hatayı düzeltmek için `ErrorClass` sınıfı devralmalıdır <xref:System.Exception?displayProperty=nameWithType>. Ayrıca, `Message` özelliği geçersiz kılınmalıdır. Aşağıdaki örnek tanımlamak için bu hataları düzeltir bir `ErrorClass` CLS uyumlu sınıf.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Öznitelikler

.NET Framework derlemelerindeki özel öznitelikler özel öznitelikleri depolamak ve programlama derlemeler, türler, üye ve yöntem parametreleri gibi nesneler hakkındaki meta verileri almak için genişletilebilir bir mekanizma sağlar. Özel öznitelikler türetilmesi gereken <xref:System.Attribute?displayProperty=nameWithType> veya türetilmiş bir türden <xref:System.Attribute?displayProperty=nameWithType>.

Aşağıdaki örnek bu kuralı ihlal ediyor. Tanımladığı bir `NumericAttribute` türünden türemez sınıfı <xref:System.Attribute?displayProperty=nameWithType>. Derleyici Hatası sınıfın tanımlı değil, yalnızca CLS uyumlu olmayan öznitelik, uygulandığında sonuçları verdiğine dikkat edin.

[!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
[!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]

Oluşturucu veya CLS uyumlu bir özniteliğin özellikleri sadece aşağıdaki türleri getirebilir:

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

- Temel alınan türü olan herhangi bir numaralandırma türü <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, veya <xref:System.Int64>.

Aşağıdaki örnekte tanımlayan bir `DescriptionAttribute` türetilen sınıf <xref:System.Attribute>. Sınıf oluşturucu türünde bir parametreye sahip `Descriptor`, bu nedenle sınıf CLS uyumlu değildir. Visual Basic derleyicinin ne bir uyarı ne de hata yayar ise C# derleyicisinin bir uyarı yaydığına ancak başarıyla derler unutmayın.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>CLSCompliantAttribute özniteliği

<xref:System.CLSCompliantAttribute> Özniteliği bir program öğesinin ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır. <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> Oluşturucu içeren bir tek gerekli parametresi `isCompliant`, program öğesinin CLS uyumlu olup olmadığını gösterir.

Derleme zamanında derleyici, CLS uyumlu olduğu varsayılan uyum olmayan ve bir uyarı verir uyumlu olmayan öğeleri algılar. Derleyici, tür veya uyumlu olması için açıkça bildirilen üyeler için uyarı yayımlamaz.

Bileşen geliştiriciler <xref:System.CLSCompliantAttribute> özniteliğini iki şekilde:

- Bir bileşen tarafından açıklanan genel arabirimin CLS uyumlu parçalarını ve CLS uyumlu olmayan parçalarını tanımlamak için. Öznitelik belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, kullanımı bu öğelerin tüm diller ve .NET Framework'ü hedefleyen Araçlar erişilebilir olmasını garanti eder.

- Bileşen kitaplığının ortak arabiriminin yalnızca CLS uyumlu program öğelerini göstermesini sağlamak için. Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı verir.

> [!WARNING]
> Bazı durumlarda, dil derleyicileri, bağımsız olarak CLS uyumlu kuralları zorunlu <xref:System.CLSCompliantAttribute> özniteliği kullanılır. Örneğin, bir arabirimde bir statik üye tanımlama, CLS kuralını ihlal ediyor. Bu şekilde tanımlarsanız, bir `static` (C# ' de) veya `Shared` (Visual Basic'te) üyesi bir arabirim içinde hem C# ve Visual Basic derleyicileri bir hata iletisi görüntüler ve uygulamayı derleyemez.

<xref:System.CLSCompliantAttribute> Özniteliği ile işaretlenmiş bir <xref:System.AttributeUsageAttribute> değerine sahip öznitelik <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Bu değer, uygulamanıza olanak sağlar. <xref:System.CLSCompliantAttribute> özniteliği derlemeler, modüller, dahil olmak üzere tüm program öğesi için türler (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), üyeleri (Oluşturucular, yöntemler, özellikler, alanlar ve olaylar), yazın. Parametreler, genel parametreler ve dönüş değerleri. Ancak, uygulamada, özniteliği yalnızca derlemeler, türler ve tür üyeleri uygulamanız gerekir. Aksi takdirde, derleyiciler yoksayar ve karşılaştığınız uyumlu olmayan bir parametre, genel parametre veya dönüş değeri kitaplığınızın ortak arabiriminde her derleyici uyarıları oluşturmaya devam edin.

Değerini <xref:System.CLSCompliantAttribute> özniteliği içerdiği program ögeleri tarafından devralınır. Bir derleme CLS uyumlu olarak işaretlenmişse, örneğin, türlerinden de CLS uyumludur. Bir tür CLS uyumlu olarak işaretlenmişse, iç içe geçmiş türleri ve üyeleri de CLS uyumludur.

Uygulayarak devralınan uyumluluğu açıkça kılabilirsiniz <xref:System.CLSCompliantAttribute> özniteliği içerdiği program öğesine. Örneğin, kullanabilirsiniz <xref:System.CLSCompliantAttribute> özniteliğini bir `isCompliant` değerini `false` özniteliği ile uyumlu bir derlemeyi ve, uyumlu olmayan bir tür tanımlamak için kullanabilirsiniz bir `isCompliant` değerini `true` uyumlu tür tanımlamak için bir uyumlu olmayan derleme. Uyumlu bir türde uyumlu olmayan üyeler de tanımlayabilirsiniz. Ancak, ile özniteliği kullanamazsınız. Bu nedenle uyumlu olmayan bir türün uyumlu üyeleri olamaz bir `isCompliant` değerini `true` uyumlu olmayan bir türden devralmayı geçersiz kılmak için.

Bileşenleri geliştirirken her zaman kullanmalısınız <xref:System.CLSCompliantAttribute> derlemenizin, türlerinin ve üyelerinin CLS uyumlu olup olmadığını belirtmek için özniteliği.

CLS uyumlu bileşenler oluşturmak için:

1. Kullanım <xref:System.CLSCompliantAttribute> Derleme CLS uyumlu olarak işaretlemek için.

2. CLS uyumlu değil olarak uyumlu olmayan derlemedeki genel olarak sunulan türlerini işaretleyin.

3. Herhangi bir genel olarak sunulan üye CLS uyumlu türlerde uyumlu olmayan olarak işaretleyin.

4. CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlar.

Tüm uyumlu olmayan türleri ve üyeleri başarılı bir şekilde işaretlediyseniz, derleyici tüm uyumsuz uyarılarını yayınlamaz. Ancak hangi üyelerin CLS uyumlu değildir ve ürün belgelerinizde bunların CLS uyumlu alternatifler listesinde gösterilmelidir.

Aşağıdaki örnekte <xref:System.CLSCompliantAttribute> CLS uyumlu bir derlemeyi ve bir tür tanımlamak için öznitelik `CharacterUtilities`, CLS uyumlu olmayan iki üyesi olan. Her iki üyeleri ile etiketlendiğinden `CLSCompliant(false)` özniteliği, derleyici uyarı üretmez. Sınıfı, her iki yöntem için CLS uyumlu bir alternatif de sağlar. Normalde, iki aşırı yüklemesi için yalnızca ekleriz `ToUTF16` yöntemi CLS uyumlu alternatifler sağlamak için. Ancak, dönüş değerini temel alarak yöntemler aşırı yüklenemez olduğundan, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklı.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Varsa (diğer bir deyişle, türleri ve diğer uygulama geliştiricileri tarafından tüketilebilecek üyeleri göstermiyorsanız) kitaplık yerine bir uygulama geliştiriyorsanız, uygulamanızın kullandığı program öğelerinin CLS uyumluluğu yalnızca diliniz onları desteklemiyorsa ilgi olan . Bu durumda, CLS uyumlu olmayan bir öğe kullanmaya çalıştığınızda dil derleyici bir hata oluşturur.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Diller Arası Birlikte Çalışabilirlik

Dil bağımsızlığının birkaç olası anlamı vardır. Makalede açıklanan bir anlamı [dil bağımsızlığı ve dilden bağımsız bileşenler](../../docs/standard/language-independence-and-language-independent-components.md), tek bir dilde başka bir dilde yazılmış bir uygulamadan gelen türleri sorunsuzca kullanmayı içerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.

Aşağıdaki örnekte, iki sınıf içerir Utilities.dll adlı bir sınıf kitaplığı oluşturarak diller arası birlikte çalışabilirlik gösterilmektedir `NumericLib` ve `StringLib`. `NumericLib` Sınıfı C# ile yazılan ve `StringLib` sınıfı, Visual Basic'te yazılır. Aşağıda `ToTitleCase` sınıfında tek bir üye, `StringLib`, içeren StringUtil.vb için kaynak kodu verilmiştir.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

Tek bir derleme için iki sınıf paketlemek için modülleri derlemeniz gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
vbc /t:module StringUtil.vb
```

Visual Basic derleyici komut satırı sözdizimi hakkında daha fazla bilgi için bkz. [komut satırından derleme](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
csc /t:module NumberUtil.cs
```

C# derleyici komut satırı sözdizimi hakkında daha fazla bilgi için bkz. [yapı komut satırı ile csc.exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Daha sonra [bağlayıcı seçenekleri](/cpp/build/reference/linker-options) iki modül bir birleştirme dosyasına derlemek için:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Aşağıdaki örnek daha sonra çağırır `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemleri. Hem Visual Basic kodunu hem de C# kod hem sınıflarını yöntemlerdeki erişmesi mümkün olduğunu unutmayın.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Visual Basic kodunu derlemek için bu komutu kullanın:

```console
vbc example.vb /r:UtilityLib.dll
```

C# ile derlemek için derleyicinin adını değiştirmek **vbc** için **csc**ve dosya uzantısını .vb yerine .cs olarak değiştirin:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.CLSCompliantAttribute>
