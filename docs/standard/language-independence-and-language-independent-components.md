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
ms.openlocfilehash: 725884d8ab6d6d9009ad1cdd7bc185889cd5e485
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243069"
---
# <a name="language-independence-and-language-independent-components"></a>Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler

.NET Framework dilden bağımsızdır. Bu, bir geliştirici olarak C#, C++/CLI, Eyfel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL ve Windows PowerShell gibi .NET Framework'ü hedefleyen birçok dilden birinde geliştirebileceğiniz anlamına gelir. .NET Framework için geliştirilen sınıf kitaplıklarının türlerine ve üyelerine, orijinal dilin kurallarını izlemeden, orijinal dilin dillerini bilmeden erişebilirsiniz. Bileşen geliştiricisiyseniz, bileşeninize dili ne olursa olsun herhangi bir .NET Framework uygulaması erişebilir.

> [!NOTE]
> Bu makalenin ilk bölümünde, dilden bağımsız bileşenler,yani herhangi bir dilde yazılmış uygulamalar tarafından tüketilebilen bileşenler oluşturma tartışılır. Ayrıca, birden çok dilde yazılmış kaynak kodundan tek bir bileşen veya uygulama oluşturabilirsiniz; bu makalenin ikinci bölümünde [Çapraz Diller Arası Birlikte çalışabilirlik](#CrossLang) bölümüne bakın.

Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşimde kalmak için, nesnelerin arayanlara yalnızca tüm dillerde ortak olan bu özellikleri ortaya çıkarmaları gerekir. Bu yaygın özellik kümesi, oluşturulan derlemeler için geçerli olan bir kural kümesi olan Ortak Dil Belirtimi (CLS) tarafından tanımlanır. Ortak Dil Belirtimi Bölüm I, Clauses 7 ile 11 [ECMA-335 Standart: Ortak Dil Altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm)tanımlanır.

Bileşeniniz Ortak Dil Belirtimi'ne uygunsa, CLS uyumlu olduğu garanti edilir ve CLS'yi destekleyen herhangi bir programlama dilinde yazılmış derlemelerde koddan erişilebilir. Bileşeninizin ortak dil belirtimine uygun olup olmadığını kaynak kodunuza <xref:System.CLSCompliantAttribute> özniteliği uygulayarak derleme zamanında belirleyebilirsiniz. Daha fazla bilgi için [CLSCompliant Attribute özniteliğine](#CLSAttribute)bakın.

Bu makalede:

- [CLS uyumluluk kuralları](#Rules)

  - [Üye imzatürleri ve türleri](#Types)

  - [Adlandırma kuralları](#naming)

  - [Tür dönüştürme](#conversion)

  - [Diziler](#arrays)

  - [Arabirimler](#Interfaces)

  - [Numaralandırma](#enums)

  - [Genel olarak tip üyeleri](#members)

  - [Üye erişilebilirliği](#MemberAccess)

  - [Genel türler ve üyeler](#Generics)

  - [Oluşturucular](#ctors)

  - [Özellikler](#properties)

  - [Olaylar](#events)

  - [Aşırı Yüklemeler](#overloads)

  - [Özel durumlar](#exceptions)

  - [Öznitelikler](#attributes)

- [CLSCompliantAttribute özniteliği](#CLSAttribute)

- [Diller Arası Birlikte Çalışabilirlik](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>CLS uyumluluk kuralları

Bu bölümde CLS uyumlu bir bileşen oluşturma kuralları tartışılmaktadır. Kuralların tam listesi için, [ECMA-335 Standardının](https://www.ecma-international.org/publications/standards/Ecma-335.htm)Bölüm I, Madde 11: Ortak Dil Altyapısı'na bakın.

> [!NOTE]
> Ortak Dil Belirtimi, tüketiciler (CLS uyumlu bir bileşene programlı olarak erişen geliştiriciler), çerçeveler (CLS uyumlu kitaplıklar oluşturmak için bir dil derleyicisi kullanan geliştiriciler) ve genişleticiler (dil derleyicisi veya CLS uyumlu bileşenler oluşturan bir kod parleyicisi gibi bir araç oluşturan geliştiriciler) için geçerli olduğu için CLS uyumluluğu için her kuralı tartışır. Bu makalede, çerçeveler için geçerli olarak kurallar üzerinde duruluyor. Ancak, genişleticiler için geçerli olan bazı kuralların Reflection.Emit kullanılarak oluşturulan derlemeler için de geçerli olabileceğini unutmayın.

Dilden bağımsız bir bileşen tasarlamak için CLS uyumluluğu kurallarını bileşeninizin ortak arabirimine uygulamanız gerekir. Özel uygulamanız belirtime uymak zorunda değildir.

> [!IMPORTANT]
> CLS uyumluluğu için kurallar, özel uygulaması için değil, yalnızca bir bileşenin ortak arabirimi için geçerlidir.

Örneğin, CLS uyumlu olmadığı dışında <xref:System.Byte> imzalanmamış tümsalar. Aşağıdaki `Person` örnekteki sınıf bir tür `Age` <xref:System.UInt16>özelliği ortaya çıkardığından, aşağıdaki kod derleyici uyarısı görüntüler.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

ClS uyumlu, 16 bit imzalı bir `Age` tamsayı <xref:System.Int16>olan özelliğin <xref:System.UInt16> türünü değiştirerek `Person` sınıf CLS uyumlu hale getirebilirsiniz. Özel `personAge` alanın türünü değiştirmeniz gerekmez.

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

Bir kitaplığın ortak arabirimi aşağıdakilerden oluşur:

- Ortak sınıfların tanımları.

- Ortak sınıfların genel üyelerinin tanımları ve türemiş sınıflara erişilebilen üyelerin tanımları (diğer bir şekilde korunan üyeler).

- Genel sınıfların ortak yöntemlerinin parametreleri ve dönüş türleri ile türemiş sınıflar için erişilebilir parametreler ve dönüş yöntemleri.

CLS uyumluluk kuralları aşağıdaki tabloda listelenmiştir. Kuralların metni [ECMA-335 Standardı: Ortak Dil Altyapısından,](https://www.ecma-international.org/publications/standards/Ecma-335.htm)Telif Hakkı 2012 Ecma International tarafından aynen alınmıştır. Bu kurallar hakkında daha ayrıntılı bilgi aşağıdaki bölümlerde yer aldı.

|Kategori|Bkz.|Kural|Kural numarası|
|--------------|---------|----------|-----------------|
|Erişilebilirlik|[Üye erişilebilirliği](#MemberAccess)|Erişilebilirlik, erişilebilirlik `family-or-assembly`ile farklı bir derlemeden devralınan bir yöntemi geçersiz kılmak dışında, devralınan yöntemleri geçersiz kılarak erişilebilirlik değiştirilemez. Bu durumda, geçersiz kılma erişilebilirlik `family`olacaktır.|10|
|Erişilebilirlik|[Üye erişilebilirliği](#MemberAccess)|Türlerin ve üyelerin görünürlüğü ve erişilebilirliği, herhangi bir üyenin imzasındaki türlerin görünür ve erişilebilir olması durumunda görünür ve erişilebilir olacaktır. Örneğin, derlemesi dışında görünen genel bir yöntem, türü yalnızca derleme içinde görünen bir bağımsız değişkene sahip olmayacaktır. Herhangi bir üyenin imzasında kullanılan anlık genel bir türü oluşturan türlerin görünürlüğü ve erişilebilirliği, üyenin kendisi görünür ve erişilebilir olduğunda görünür ve erişilebilir olacaktır. Örneğin, derlemesi dışında görünen bir üyenin imzasında bulunan anlık genel bir tür, türü yalnızca derleme içinde görünen genel bir bağımsız değişkene sahip olmayacaktır.|12|
|Diziler|[Diziler](#arrays)|Diziler CLS uyumlu türe sahip öğelere sahip olacak ve dizinin tüm boyutları sıfır ın alt sınırlarına sahip olacaktır. Yalnızca bir öğenin bir dizi olması ve dizinin öğe türüaşırı yüklemeleri ayırt etmek için gerekli olacaktır. Aşırı yükleme iki veya daha fazla dizi türüne dayandığında eleman türleri türleri adlandırılacaktır.|16|
|Öznitelikler|[Öznitelikler](#attributes)|Öznitelikler, ondan <xref:System.Attribute?displayProperty=nameWithType>devralan bir tür veya tür olacaktır.|41|
|Öznitelikler|[Öznitelikler](#attributes)|CLS yalnızca özel özniteliklerin kodlamalarının bir alt kümesine izin verir. Bu kodlamalarda görünecek tek tür (bkz. Bölüm <xref:System.Type?displayProperty=nameWithType>IV): , <xref:System.Byte?displayProperty=nameWithType> <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType> <xref:System.String?displayProperty=nameWithType> <xref:System.Char?displayProperty=nameWithType> <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType> <xref:System.Double?displayProperty=nameWithType>, , <xref:System.Int64?displayProperty=nameWithType>, , , , , , ve CLS uyumlu bir temel tamsayı türüne dayalı numaralandırma türü.|34|
|Öznitelikler|[Öznitelikler](#attributes)|CLS, genel olarak görünür olarak görülebilen gerekli değiştiricilere izin vermez (,`modreq`Bkz. Bölüm II), ancak isteğe bağlı değiştiricilere izin verir (`modopt`, Bölüm II'ye bakınız) anlamaz.|35|
|Oluşturucular|[Oluşturucular](#ctors)|Bir nesne oluşturucu, devralınan örnek verilerine herhangi bir erişim oluşmadan önce taban sınıfının bazı örnek oluşturucularını çağırır. (Bu, oluşturucuları olmayan değer türleri için geçerli değildir.)|21|
|Oluşturucular|[Oluşturucular](#ctors)|Bir nesne oluşturucu, bir nesnenin oluşturulmasının bir parçası dışında çağrılmayacaktır ve bir nesne iki kez başharfe batılamaz.|22|
|Numaralandırmalar|[Numaralandırma](#enums)|Bir enum un altında yatan türü dahili CLS tamsayı türü olacak, alanın adı "value__" olacak `RTSpecialName`ve bu alan işaretlenecektir.|7|
|Numaralandırmalar|[Numaralandırma](#enums)|(Bölüm IV Kitaplığı bakınız) özel özniteliğinin <xref:System.FlagsAttribute?displayProperty=nameWithType> varlığı veya yokluğuyla gösterilen iki farklı enum türü vardır. Biri adlandırılmış veyasededeğerleri temsil eder; diğeri, adsız bir değer oluşturmak için biraraya getirilebilen adlandırılmış bit bayraklarını temsil eder. A `enum` değeri belirtilen değerlerle sınırlı değildir.|8|
|Numaralandırmalar|[Numaralandırma](#enums)|Bir enumun gerçek statik alanları, enumun kendi türüne sahip olacaktır.|9|
|Olaylar|[Olaylar](#events)|Bir olayı uygulayan yöntemler meta `SpecialName` verilerde işaretlenir.|29|
|Olaylar|[Olaylar](#events)|Bir olayın ve onun erişenegelenlerinin erişilebilirliği aynı olacaktır.|30|
|Olaylar|[Olaylar](#events)|Bir `add` `remove` olayın yöntemleri ve yöntemleri hem mevcut hem de yok olacaktır.|31|
|Olaylar|[Olaylar](#events)|Bir `add` `remove` olayın ve yöntemlerin her biri, olayın türünü tanımlayan ve 'den <xref:System.Delegate?displayProperty=nameWithType>türetilecek bir parametre alır.|32|
|Olaylar|[Olaylar](#events)|Olaylar belirli bir adlandırma desenine uygun olacaktır. `SpecialName` CLS kural 29'da belirtilen öznitelik, uygun ad karşılaştırmalarında yoksayılır ve tanımlayıcı kurallarına uyar.|33|
|Özel durumlar|[Özel durumlar](#exceptions)|Atılan nesneler, ondan devralan <xref:System.Exception?displayProperty=nameWithType> tür veya tür olmalıdır. Bununla birlikte, CLS uyumlu yöntemler, diğer özel durum türlerinin yayılmasını engellemek için gerekli değildir.|40|
|Genel|[CLS uyumluluğu: Kurallar](#Rules)|CLS kuralları yalnızca tanımlayıcı derlemenin dışında erişilebilen veya görülebilen bir türdeki parçalar için geçerlidir.|1|
|Genel|[CLS uyumluluğu: Kurallar](#Rules)|CLS uyumlu olmayan türlerin üyeleri CLS uyumlu olarak işaretlenmeyecek.|2|
|Genel Türler|[Genel türler ve üyeler](#Generics)|İç içe geçmiş türler, en az çevreleyen tür kadar sayıda genel parametreye sahip olacaktır. İç içe bir türdeki genel parametreler, kendi çevreleyen türündeki genel parametrelere göre konuma göre karşılık gelir.|42|
|Genel Türler|[Genel türler ve üyeler](#Generics)|Genel bir türün adı, iç içe geçmemiş türde beyan edilen veya iç içe geçen türe yeni getirilen tür parametrelerinin sayısını yukarıda açıklanan kurallara göre kodlar.|43|
|Genel Türler|[Genel türler ve üyeler](#Generics)|Genel bir tür, temel türdeki kısıtlamaların veya arabirimlerin genel tür kısıtlamaları tarafından karşılanacağını garanti etmek için yeterli kısıtlamaları yeniden beyan eder.|4444|
|Genel Türler|[Genel türler ve üyeler](#Generics)|Genel parametrelerde kısıtlama olarak kullanılan türler CLS uyumlu olacaktır.|45|
|Genel Türler|[Genel türler ve üyeler](#Generics)|Üyelerin (iç içe gelişmiş türler dahil) anlık genel bir türdeki görünürlüğü ve erişilebilirliği, genel tür bildiriminin bir bütün olarak yerine belirli anlık olarak kapsamı olarak kabul edilecektir. Bunu varsayarsak, CLS kural 12'nin görünürlük ve erişilebilirlik kuralları hala geçerlidir.|46|
|Genel Türler|[Genel türler ve üyeler](#Generics)|Her soyut veya sanal genel yöntem için varsayılan bir somut (soyut olmayan) uygulama olacaktır.|47|
|Arabirimler|[Arabirimler](#Interfaces)|CLS uyumlu arabirimler, bunları uygulamak için CLS uyumlu olmayan yöntemlerin tanımlanmasını gerektirmez.|18|
|Arabirimler|[Arabirimler](#Interfaces)|CLS uyumlu arabirimler statik yöntemleri tanımlamaz ve alanları tanımlamaz.|19|
|Üyeler|[Genel olarak tip üyeleri](#members)|Genel statik alanlar ve yöntemler CLS uyumlu değildir.|36|
|Üyeler|--|Bir literal statik değeri alan başlatma meta verilerinin kullanımı ile belirtilir. CLS uyumlu bir literal, alan başlatma meta verilerinde tam olarak literal (veya temel türde, eğer bu gerçek `enum`bir gerçek se) ile aynı türde belirtilen bir değere sahip olmalıdır.|13|
|Üyeler|[Genel olarak tip üyeleri](#members)|Vararg kısıtlaması CLS'nin bir parçası değildir ve CLS tarafından desteklenen tek çağrı sözleşmesi standart yönetilen arama kuralıdır.|15|
|Adlandırma kuralları|[Adlandırma kuralları](#naming)|Derlemeler, unicode Standard3.0'ın Teknik Raporu'nun Ek 7'sini izleyerek, başlangıç <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>ve tanımlayıcılara dahil edilmesine izin verilen karakter kümesini yönetecek. Tanımlayıcılar, Unicode Normalizasyon Formu C ile tanımlanan kanonik formatta olacaktır. CLS amaçları için, küçük harf eşlemeleri (Unicode yerel duyarsız, bire bir küçük harf eşlemeleri tarafından belirtildiği gibi) aynıysa iki tanımlayıcı aynıdır. Diğer bir deyişle, iki tanımlayıcının CLS altında farklı kabul edilmesi için, sadece kendi durumunda daha farklı olacaktır. Ancak, devralınan bir tanımı geçersiz kılmak için CLI, özgün bildirimin kesin kodlamasının kullanılmasını gerektirir.|4|
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|CLS uyumlu bir kapsamda tanıtılan tüm adlar, adların aynı olduğu ve aşırı yükleme yoluyla çözüldüğü durumlar dışında farklı türde bağımsız olacaktır. Diğer bir zamanda, CTS tek bir türe bir yöntem ve alan için aynı adı kullanmasına izin verirken, CLS bunu yapmaz.|5|
|Aşırı Yükleme|[Adlandırma kuralları](#naming)|CtS farklı imzaların ayırt edilmesine izin vermesine rağmen, alanlar ve iç içe doğru türler yalnızca tanımlayıcı karşılaştırmasına göre ayrı olacaktır. Aynı ada sahip yöntemler, özellikler ve olaylar (tanımlayıcı karşılaştırmasına göre) CLS Kural 39'da belirtilenler dışında, dönüş türünden daha fazlasına göre değişir.|6|
|Aşırı Yükleme|[Aşırı Yüklemeler](#overloads)|Yalnızca özellikler ve yöntemler aşırı yüklenebilir.|37|
|Aşırı Yükleme|[Aşırı Yüklemeler](#overloads)|Özellikler ve yöntemler, yalnızca parametrelerinin sayısına ve türlerine göre, `op_Implicit` `op_Explicit`adlandırılmış dönüştürme işleçleri dışında ve dönüş türlerine göre aşırı yüklenebilecek aşırı yüklenebilir.|38|
|Aşırı Yükleme|--|Bir türde bildirilen iki veya daha fazla CLS uyumlu yöntem aynı ada sahipse ve belirli bir tür anlık yineleme kümesi için aynı parametre ve dönüş türlerine sahipse, tüm bu yöntemler bu tür anlık belirlemelerde anlamsal olarak eşdeğer olacaktır.|48|
|Türler|[Üye imzalarının türü ve türü](#Types)|<xref:System.Object?displayProperty=nameWithType>CLS uyumludur. CLS uyumlu diğer herhangi bir sınıf, CLS uyumlu bir sınıftan devralınacaktır.|23|
|Özellikler|[Özellikler](#properties)|Bir özelliğin alıcı ve ayarlayıcı yöntemlerini uygulayan `SpecialName` yöntemler meta verilerde işaretlenir.|24|
|Özellikler|[Özellikler](#properties)|Bir mülkün erişime girenlerin tümü statik, tümü sanal veya örnek olacaktır.|26|
|Özellikler|[Özellikler](#properties)|Bir özelliğin türü, ayarlayıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türü olacaktır. Özelliğin parametrelerinin türleri, ayarlayıcının parametrelerinin türleri ve ayarlayıcının son parametresi dışında tüm parametrelerin türleri olacaktır. Bu türlerin tümü CLS uyumlu olacaktır ve yönetilmeyecektir (yani, referans la geçirilmeyecek).|27|
|Özellikler|[Özellikler](#properties)|Özellikler belirli bir adlandırma desenine bağlıdır. `SpecialName` CLS kural 24'te belirtilen öznitelik, uygun ad karşılaştırmalarında yoksayılır ve tanımlayıcı kurallarına uyar. Bir özellik bir getter yöntemi, bir ayarlayıcı yöntemi veya her ikisi de olacaktır.|28|
|Tür dönüştürme|[Tür dönüştürme](#conversion)|Herhangi `op_Implicit` bir `op_Explicit` veya sağlanan, zorlama sağlamak için alternatif bir yol sağlanacaktır.|39|
|Türler|[Üye imzalarının türü ve türü](#Types)|Kutulu değer türleri CLS uyumlu değildir.|3|
|Türler|[Üye imzalarının türü ve türü](#Types)|İmzada görünen tüm türler CLS uyumlu olacaktır. Anlık genel bir tür oluşturan tüm türler CLS uyumlu olacaktır.|11|
|Türler|[Üye imzalarının türü ve türü](#Types)|Yazılan başvurular CLS uyumlu değildir.|14|
|Türler|[Üye imzalarının türü ve türü](#Types)|Yönetilmeyen işaretçi türleri CLS uyumlu değildir.|17|
|Türler|[Üye imzalarının türü ve türü](#Types)|CLS uyumlu sınıflar, değer türleri ve arabirimler, CLS uyumlu olmayan üyelerin uygulanmasını gerektirmez.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Üye imzatürleri ve türleri

Tür <xref:System.Object?displayProperty=nameWithType> CLS uyumludur ve .NET Framework türü sistemindeki tüm nesne türlerinin temel türüdür. .NET Framework'deki devralma ya örtülüdür <xref:System.String> (örneğin, sınıf <xref:System.Object> örtük olarak sınıftan devralır) veya açıktır (örneğin, <xref:System.Globalization.CultureNotFoundException> sınıf açıkça <xref:System.ArgumentException> <xref:System.SystemException> <xref:System.Exception> sınıftan devralan ve sınıftan açıkça devralan sınıf). Türetilen bir türün CLS uyumlu olabilmesi için, taban türü de CLS uyumlu olmalıdır.

Aşağıdaki örnekte, taban türü CLS uyumlu olmayan türetilmiş bir tür gösterilmektedir. İmzasız 32 `Counter` bit tamsayı kullanan bir taban sınıfı sayaç olarak tanımlar. Sınıf imzasız bir karşıcıyı sararak sayaç işlevselliği sağladığından, sınıf CLS uyumlu olmayan olarak işaretlenir. Sonuç olarak, türetilmiş `NonZeroCounter`bir sınıf, CLS uyumlu değildir.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Bir yöntemin dönüş türü veya özellik türü de dahil olmak üzere üye imzalarda görünen tüm türler CLS uyumlu olmalıdır. Buna ek olarak, genel türleri için:

- Anında genel bir tür oluşturan tüm türler CLS uyumlu olmalıdır.

- Genel parametrelerde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır.

.NET Framework [ortak türü sistemi,](../../docs/standard/base-types/common-type-system.md) ortak dil çalışma zamanı tarafından doğrudan desteklenen ve bir derlemenin meta verilerinde özel olarak kodlanan bir dizi yerleşik türleri içerir. Bu içsel türlerden, aşağıdaki tabloda listelenen türleri CLS uyumludur.

|CLS uyumlu tip|Açıklama|
|-------------------------|-----------------|
|<xref:System.Byte>|8 bit imzasız tümseci|
|<xref:System.Int16>|16 bit imzalı tümseci|
|<xref:System.Int32>|32 bit imzalı tümseci|
|<xref:System.Int64>|64 bit imzalı tümseci|
|<xref:System.Single>|Tek hassas kayan nokta değeri|
|<xref:System.Double>|Çift duyarlıklı kayan nokta değeri|
|<xref:System.Boolean>|`true`veya `false` değer türü|
|<xref:System.Char>|UTF-16 kodlanmış kod birimi|
|<xref:System.Decimal>|Kayan olmayan nokta ondalık sayı|
|<xref:System.IntPtr>|Platform tanımlı bir boyutun işaretçisi veya tutamacı|
|<xref:System.String>|Sıfır, bir veya daha <xref:System.Char> fazla nesnenin toplanması|

Aşağıdaki tabloda listelenen içsel türleri CLS uyumlu değildir.

|Uyumlu olmayan tür|Açıklama|CLS uyumlu alternatif|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|8 bit imzalı imzalı veri türü|<xref:System.Int16>|
|<xref:System.TypedReference>|Bir nesneye ve çalışma zamanı türüne işaretçi|None|
|<xref:System.UInt16>|16 bit imzasız tümseci|<xref:System.Int32>|
|<xref:System.UInt32>|32 bit imzasız tümseci|<xref:System.Int64>|
|<xref:System.UInt64>|64 bit imzasız tümseci|<xref:System.Int64>(taşabilir), <xref:System.Numerics.BigInteger>veya<xref:System.Double>|
|<xref:System.UIntPtr>|İmzasız işaretçi veya tanıtıcı|<xref:System.IntPtr>|

.NET Framework Class Kitaplığı veya başka bir sınıf kitaplığı CLS uyumlu olmayan diğer türleri içerebilir; örneğin:

- Kutulu değer türleri. Aşağıdaki C# örneği, . adlı `int*` `Value`türde bir ortak özelliği olan bir sınıf oluşturur Kutulu `int*` bir değer türü olduğundan, derleyici onu CLS uyumlu olmayan olarak işaretler.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Bir nesneye ve bir türe başvuru içeren özel yapılar olan yazılı başvurular. Yazılan başvurular .NET Framework'de <xref:System.TypedReference> sınıf tarafından temsil edilir.

Bir tür CLS uyumlu değilse, özniteliği <xref:System.CLSCompliantAttribute> bir `isCompliant` değerle `false` uygulamanız gerekir. Daha fazla bilgi için [CLSCompliant Attribute özniteliği bölümüne](#CLSAttribute) bakın.

Aşağıdaki örnekte, bir yöntem imzasında ve genel tür anında cls uyumluluğu sorunu gösteriş göstermektedir. Bu `InvoiceItem` tür <xref:System.UInt32>bir özelliği olan bir sınıf tanımlar `Nullable(Of UInt32)`, türü bir özellik <xref:System.UInt32> , `Nullable(Of UInt32)`ve türü parametreleri ile bir yapıcı ve . Bu örneği derlemeye çalıştığınızda dört derleyici uyarısı alırsınız.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Derleyici uyarılarını ortadan kaldırmak `InvoiceItem` için, genel arabirimdeki CLS uyumlu olmayan türleri uyumlu türlerle değiştirin:

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Listelenen belirli türlere ek olarak, bazı tür kategorileri CLS uyumlu değildir. Bunlar, yönetilmeyen işaretçi türleri ve işlev işaretçisi türlerini içerir. Aşağıdaki örnek, bir tamsayı dizisi oluşturmak için bir tamsayı işaretçisi kullandığından derleyici uyarısı oluşturur.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

CLS uyumlu soyut sınıflar için (diğer `abstract` bir deyişle, `MustInherit` c# veya Visual Basic'te olduğu gibi işaretlenmiş sınıflar), sınıfın tüm üyeleri de CLS uyumlu olmalıdır.

<a name="naming"></a>

### <a name="naming-conventions"></a>Adlandırma kuralları

Bazı programlama dilleri büyük/küçük harf duyarlı olduğundan, tanımlayıcılar (ad alanlarının adları, türleri ve üyeleri gibi) büyük/küçük harften daha fazla farklılık gösterir. Küçük eşlemeleri aynıysa, iki tanımlayıcı eşdeğer olarak kabul edilir. Aşağıdaki C# örneği iki ortak `Person` sınıf `person`tanımlar ve . Yalnızca duruma göre farklılık gösterirler, C# derleyicisi bunları CLS uyumlu değil olarak işaretler.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Ad alanları, türleri ve üyeleri gibi programlama dili tanımlayıcıları [Unicode Standart 3.0, Teknik Rapor 15, Ek 7'ye](https://www.unicode.org/reports/tr15/tr15-18.html)uygun olmalıdır. Bu şu anlama gelir:

- Bir tanımlayıcının ilk karakteri herhangi bir Unicode büyük harf, küçük harf, başlık büyük harf, değiştirici mektup, diğer harf veya harf numarası olabilir. Unicode karakter kategorileri hakkında <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType> bilgi için numaralandırmaya bakın.

- Sonraki karakterler ilk karakter olarak kategorilerden herhangi birinden olabilir ve aralık olmayan işaretleri, işaretleri birleştirme aralığı, ondalık sayılar, bağlayıcı noktalama işaretleri ve biçimlendirme kodlarını da içerebilir.

Tanımlayıcıları karşılaştırmadan önce, biçimlendirme kodlarını filtrelemeniz ve tanımlayıcıları Unicode Normalization Form C'ye dönüştürmeniz gerekir, çünkü tek bir karakter birden çok UTF-16 kodlanmış kod birimi tarafından temsil edilebilir. Unicode Normalization Form C'de aynı kod birimlerini oluşturan karakter dizileri CLS uyumlu değildir. Aşağıdaki örnek, ANGSTROM `Å`SIGN (U+212B) karakterinden oluşan bir özellik ve `Å`LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5) karakterinden oluşan ikinci bir özelliği tanımlar. Hem C# hem de Visual Basic derleyicileri kaynak kodu CLS uyumlu olmayan olarak işaretler.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Belirli bir kapsamdaki üye adları (derlemedeki ad alanları, ad alanı içindeki türler veya bir tür içindeki üyeler gibi) aşırı yükleme yoluyla çözülen adlar dışında benzersiz olmalıdır. Bu gereksinim, farklı türde üye oldukları sürece kapsam daki birden çok üyenin aynı adlara sahip olmasını sağlayan ortak tür sisteminden daha sıkıdır (örneğin, biri bir yöntem, diğeri bir alandır). Özellikle, tür üyeleri için:

- Alanlar ve iç içe türler tek başına adıyla ayırt edilir.

- Aynı ada sahip yöntemler, özellikler ve olaylar, dönüş türünden daha fazla olmalıdır.

Aşağıdaki örnek, üye adların kendi kapsamları içinde benzersiz olması gereksinimini göstermektedir. Adı geçen dört `Converter` üyeyi içeren `Conversion`bir sınıf tanımlar. Üçü yöntem, biri de bir özellik. Parametre <xref:System.Int64> içeren yöntem benzersiz adlandırılmış, ancak parametreli <xref:System.Int32> iki yöntem değildir, çünkü iade değeri üyenin imzasının bir parçası olarak kabul edilmez. Özellikler `Conversion` aşırı yüklenen yöntemlerle aynı ada sahip olamayacağından, özellik de bu gereksinimi ihlal eder.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Tek tek diller benzersiz anahtar kelimeler içerir, bu nedenle ortak dil çalışma zamanını hedefleyen diller, anahtar kelimelerle çakışan tanımlayıcılara (tür adları gibi) başvurmak için bazı mekanizmalar da sağlamalıdır. Örneğin, `case` hem C# hem de Visual Basic'te kullanılan bir anahtar kelimedir. Ancak, aşağıdaki Visual Basic örneği, açılış ve kapanış `case` ayraçlarını kullanarak `case` anahtar kelimeden adlı bir sınıfı ayrıştırabilir. Aksi takdirde, örnek hata iletisi üretir, "Anahtar kelime tanımlayıcı olarak geçerli değildir" ve derlemek için başarısız.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

Aşağıdaki C# örneği, tanımlayıcıyı `case` `@` dil anahtar kelimesinden çıkarmak için sembolü kullanarak sınıfı anında atabiliyor. Bu olmadan, C# derleyicisi iki hata iletisi görüntüler: "Bekleneni yazın" ve "Geçersiz ifade terimi 'büyük/küçük harf'."

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Tür dönüştürme

Ortak Dil Belirtimi iki dönüşüm işleci tanımlar:

- `op_Implicit`, veri veya kesinlik kaybına neden olmayan dönüşümleri genişletmek için kullanılır. Örneğin, <xref:System.Decimal> yapı, integral türleri `op_Implicit` ve <xref:System.Char> değerlerinin değerlerini değerlere <xref:System.Decimal> dönüştürmek için aşırı yüklü bir işleç içerir.

- `op_Explicit`, büyüklük kaybına neden olabilecek dönüşümleri daraltmak için kullanılır (bir değer daha küçük aralıklı bir değere dönüştürülür) veya kesinlik. Örneğin, <xref:System.Decimal> yapı dönüştürmek ve `op_Explicit` <xref:System.Double> <xref:System.Single> değerleri integral değerlere <xref:System.Decimal> dönüştürmek <xref:System.Decimal> için aşırı yüklü <xref:System.Double> <xref:System.Single>bir <xref:System.Char>işleç içerir, , , ve .

Ancak, tüm diller operatörün aşırı yüklenmesi veya özel işleçlerin tanımını desteklemez. Bu dönüşüm işleçlerini uygulamayı seçerseniz, dönüşümü gerçekleştirmek için alternatif bir yol da sağlamanız gerekir. `From` *Xxx* ve `To` *Xxx* yöntemlerini sağlamanızı öneririz.

Aşağıdaki örnek, CLS uyumlu örtülü ve açık dönüşümleri tanımlar. İmzalanmış çift `UDouble` duyarlıklı, kayan nokta numarasını temsil eden bir sınıf oluşturur. `UDouble` Örtülü dönüşümleri, <xref:System.Double> açık dönüşümlerden `UDouble` <xref:System.Single>, <xref:System.Double> `UDouble` <xref:System.Single> ve . `UDouble` Ayrıca, `ToDouble` bir yöntemi örtülü dönüştürme işlecine alternatif `ToSingle` `FromDouble`olarak `FromSingle` tanımlar ve açık dönüştürme işleçlerine alternatif olarak , ve yöntemleri tanımlar.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Diziler

CLS uyumlu diziler aşağıdaki kurallara uygundur:

- Bir dizinin tüm boyutları sıfırın alt sınırı olmalıdır. Aşağıdaki örnek, daha düşük bir sınıra sahip CLS uyumlu olmayan bir dizi oluşturur. Öznitelik varlığına <xref:System.CLSCompliantAttribute> rağmen, derleyici `Numbers.GetTenPrimes` yöntem tarafından döndürülen dizi CLS uyumlu olmadığını algılamaz unutmayın.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Tüm dizi öğeleri CLS uyumlu türlerden oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan dizileri döndüren iki yöntem tanımlar. İlk değerler dizisi <xref:System.UInt32> döndürür. İkinci içerir <xref:System.Object> <xref:System.Int32> ve <xref:System.UInt32> değerleri içeren bir dizi döndürür. Derleyici, türü nedeniyle ilk diziyi uyumlu <xref:System.UInt32> olmayan olarak tanımlasa da, ikinci dizinin CLS uyumlu olmayan öğeler içerdiğini fark edememektedir.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- Dizi parametreleri olan yöntemler için aşırı yükleme çözünürlüğü, dizi olmaları ve eleman türüne dayanır. Bu nedenle, aşırı yüklü `GetSquares` bir yöntemin aşağıdaki tanımı CLS uyumludur.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Arabirimler

CLS uyumlu arabirimler özellikleri, olayları ve sanal yöntemleri (uygulama olmadan yöntemler) tanımlayabilir. CLS uyumlu bir arabirim aşağıdakilerden herhangi biri olamaz:

- Statik yöntemler veya statik alanlar. Bir arabirimde statik bir üye tanımlarsanız, hem C# hem de Visual Basic derleyicileri derleyici hataları oluşturur.

- Alanları. Bir arabirimde bir alan tanımlarsanız, hem C# hem de Visual Basic derleyicileri derleyici hataları oluşturur.

- CLS uyumlu olmayan yöntemler. Örneğin, aşağıdaki arabirim tanımı, `INumber.GetUnsigned`CLS uyumlu olmayan olarak işaretlenmiş bir yöntem içerir. Bu örnek derleyici uyarısı oluşturur.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  Bu kural nedeniyle, CLS uyumlu olmayan üyeleri uygulamak için CLS uyumlu türleri gerekmez. CLS uyumlu bir çerçeve, CLS uyumlu olmayan bir arabirim uygulayan bir sınıfı ortaya çıkarırsa, CLS uyumlu olmayan tüm üyelerin somut uygulamalarını da sağlamalıdır.

CLS uyumlu dil derleyicileri, bir sınıfın birden çok arabirimde aynı ad ve imzaya sahip üyelerin ayrı uygulamalarını sağlamasına da izin vermelidir.  Hem C# hem de Visual Basic, aynı adlandırılmış yöntemlerin farklı uygulamalarını sağlamak için [açık arabirim uygulamalarını](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) destekler. Visual Basic ayrıca, belirli bir üyenin `Implements` hangi arabirimi ve üyeyi uyguladığını açıkça belirlemenize olanak tanıyan anahtar kelimeyi de destekler. Aşağıdaki örnek, açık arabirim uygulamaları `Temperature` olarak ve `ICelsius` `IFahrenheit` arabirimleri uygulayan bir sınıf tanımlayarak bu senaryoyu göstermektedir.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Numaralandırmalar

CLS uyumlu sayısallaştırmalar aşağıdaki kurallara uymalıdır:

- Numaralandırmanın altında yatan tip içsel BIR CLS uyumlu bir toplamcı<xref:System.Byte> <xref:System.Int16>olmalıdır <xref:System.Int32>( <xref:System.Int64>, , , veya ). Örneğin, aşağıdaki kod, temel türü olan <xref:System.UInt32> bir numaralandırma tanımlamaya çalışır ve derleyici uyarısı oluşturur.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Bir numaralandırma türü öznitelik ile `Value__` <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType> işaretlenmiş tek bir örnek alanı adlı olmalıdır. Bu, alan değerini dolaylı olarak referans almanızı sağlar.

- Numaralandırma, türleri numaralandırmanın kendisiyle eşleşen gerçek statik alanları içerir. Örneğin, `State` `State.On` bir numaralandırma ve `State.Off`, her `State.On` `State.Off` ikisi de türü `State`.

- İki tür sayısallaştırma vardır:

  - Birbirini dışlayan, tamsayı değerleri kümesini temsil eden numaralandırma. Bu tür numaralandırma, <xref:System.FlagsAttribute?displayProperty=nameWithType> özel özniteliğin yokluğuyla gösterilir.

  - Adsız bir değer oluşturmak için biraraya getirebilen bit bayrakları kümesini temsil eden numaralandırma. Bu tür numaralandırma, <xref:System.FlagsAttribute?displayProperty=nameWithType> özel özniteliğin varlığıyla gösterilir.

  Daha fazla bilgi için yapıiçin belgelere <xref:System.Enum> bakın.

- Numaralandırmanın değeri, belirtilen değerlerin aralığıyla sınırlı değildir. Başka bir deyişle, numaralandırmadaki değer aralığı, temel değerinin aralığıdır. Belirtilen değerin <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> numaralandırmanın bir üyesi olup olmadığını belirlemek için yöntemi kullanabilirsiniz.

<a name="members"></a>

### <a name="type-members-in-general"></a>Genel olarak tip üyeleri

Ortak Dil Belirtimi, tüm alanların ve yöntemlerin belirli bir sınıfın üyesi olarak erişilmesini gerektirir. Bu nedenle, genel statik alanlar ve yöntemler (diğer bir şekilde statik alanlar veya bir tür dışında tanımlanan yöntemler) CLS uyumlu değildir. Kaynak kodunuza genel bir alan veya yöntem eklemeye çalışırsanız, hem C# hem de Visual Basic derleyicileri derleyici hatası oluşturur.

Ortak Dil Belirtimi yalnızca standart yönetilen arama kuralını destekler. `varargs` Anahtar kelimeyle işaretlenmiş değişken bağımsız değişken listeleriyle yönetilmeyen çağrı kurallarını ve yöntemlerini desteklemez. Standart yönetilen arama kuralıyla uyumlu değişken bağımsız değişken <xref:System.ParamArrayAttribute> listeleri için, `params` C#'daki anahtar kelime ve Visual Basic'teki `ParamArray` anahtar kelime gibi özniteliği veya tek tek dilin uygulamasını kullanın.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Üye erişilebilirliği

Devralınan bir üyenin geçersiz kılınması, bu üyenin erişilebilirliğini değiştiremez. Örneğin, taban sınıftaki ortak yöntem, türemiş bir sınıftaki özel bir yöntem tarafından geçersiz kılınamaz. Bir istisna vardır: `protected internal` (C#' `Protected Friend` da) veya (Visual Basic'te) üye, farklı bir derlemedeki bir tür tarafından geçersiz kılınan bir derlemede. Bu durumda, geçersiz kılmanın `Protected`erişilebilirliği.

Aşağıdaki örnek, <xref:System.CLSCompliantAttribute> öznitelik ayarlandığında `true`oluşturulan hatayı göstermektedir ve `Human`türetilen `Animal`bir sınıf olan `Species` özelliğin erişilebilirliğini ortaktan özele değiştirmeye çalışır. Erişilebilirliği genel olarak değiştirilirse, örnek başarıyla derlenir.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Bir üyenin imzasındaki türlere, bu üyeye erişilebildiğinde erişilebiliyor olmalıdır. Örneğin, bu, ortak bir üyenin türü özel, korumalı veya dahili bir parametre içeremeyeceği anlamına gelir. Aşağıdaki örnekte, bir sınıf oluşturucusu `StringWrapper` dize değerinin nasıl `StringOperationType` paketlendiğini belirleyen bir iç numaralandırma değerini ortaya çıkardığında ortaya çıkan derleyici hatasını gösterilebilir.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Genel türler ve üyeler

İç içe geçmiş türler her zaman en az kendi çevreleyen türü kadar sayıda genel parametreye sahiptir. Bunlar, çevreleyen türdeki genel parametrelere göre konumolarak karşılık gelir. Genel tür, yeni genel parametreler de içerebilir.

İçeren bir türün genel tür parametreleri ile iç içe olan türleri arasındaki ilişki, tek tek dillerin sözdizimi tarafından gizlenmiş olabilir. Aşağıdaki örnekte, genel `Outer<T>` bir tür iki `Inner1A` iç `Inner1B<U>`içe sınıf içerir ve. Her sınıfın `ToString` devraldığı yönteme yapılan <xref:System.Object.ToString%2A?displayProperty=nameWithType>çağrılar, iç içe geçen her sınıfın kendi sınıfının tür parametrelerini içerdiğini gösterir.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Genel tür adları form *adı\`n*kodlanır , *burada* ad \` türü adı, bir karakter literal ve *n* türü nde bildirilen parametrelerin sayısı, ya da iç içe genel türleri için, yeni tanıtılan tür parametrelerinin sayısıdır. Genel tür adlarının bu kodlaması, öncelikle bir kitaplıktaki CLS şikayeti genel türlerine erişmek için yansımayı kullanan geliştiricilerin ilgisini çekmiştir.

Genel bir türe kısıtlamalar uygulanırsa, kısıtlama olarak kullanılan tüm türler de CLS uyumlu olmalıdır. Aşağıdaki örnek, CLS `BaseClass` uyumlu olmayan bir sınıf ve `BaseCollection` tür `BaseClass`parametresi. `BaseClass` Ancak CLS uyumlu olmadığından, derleyici bir uyarı yayar.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Genel bir tür genel bir taban türünden türetilmişse, temel türdeki kısıtlamaların da karşılanmasına engel olabilmesi için kısıtlamaları yeniden beyan etmesi gerekir. Aşağıdaki örnek, herhangi `Number<T>` bir sayısal türü temsil eden bir tanım tanımlar. Ayrıca kayan `FloatingPoint<T>` nokta değerini temsil eden bir sınıf tanımlar. Ancak, kaynak kod derlenemiyor, çünkü `Number<T>` `FloatingPoint<T>`bu kısıtlamayı (T'nin bir değer türü olması gerekir) .

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

Kısıtlama `FloatingPoint<T>` sınıfa eklenirse, örnek başarıyla derlenir.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

Ortak Dil Belirtimi iç içe gelen türler ve korunan üyeler için uygun bir anlık hareket modeli uygular. Açık genel türler, iç içe, korumalı genel bir türbelirli bir anlık içeren imzaları olan alanları veya üyeleri ortaya çıkaramaz. Genel bir taban sınıfının veya arabirimin belirli bir anlık anını genişleten genel olmayan türler, iç içe, korunan genel türün farklı bir anlık anlık bir anını içeren imzalarla alanları veya üyeleri ortaya çıkaramaz.

Aşağıdaki `C1<T>` örnek, genel bir türü `C1(Of T)` (veya Visual Basic'te) `C1<T>.N` ve `C1(Of T).N` korumalı bir sınıfı (veya Visual Basic'te) tanımlar. `C1<T>`iki yöntemi `M1` vardır `M2`ve . Ancak, `M1` C1\<T> (veya) `C1<int>.N` nesnesinden `C1(Of Integer).N`(veya) `C1(Of T)`nesnesini döndürmeye çalıştığından CLS uyumlu değildir. İkinci sınıf, `C2`türetilmiştir `C1<long>` (veya). `C1(Of Long)` İki yöntemi var `M3` `M4`ve. `M3`bir alt sınıftan (veya) `C1<int>.N` `C1(Of Integer).N`nesnesini döndürmeye çalıştığından `C1<long>`CLS uyumlu değildir. Dil derleyicilerin daha da kısıtlayıcı olabileceğini unutmayın. Bu örnekte, Visual Basic derlemeye çalıştığında `M4`bir hata görüntüler.

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Oluşturucular

CLS uyumlu sınıflarda ve yapılardaki kurucular aşağıdaki kurallara uymalıdır:

- Türetilmiş bir sınıfın oluşturucusu, devralınan örnek verilerine erişmeden önce taban sınıfının örnek oluşturucuyu çağırmalıdır. Bu gereksinim, taban sınıf oluşturucuların türetilmiş sınıfları tarafından devralınmaması nedeniyledir. Bu kural, doğrudan devralmayı desteklemeyen yapılar için geçerli değildir.

  Genellikle derleyiciler, aşağıdaki örnekte görüldüğü gibi, bu kuralı CLS uyumluluğundan bağımsız olarak uygular. Bir sınıftan `Doctor` türetilen bir `Person` sınıf oluşturur, `Doctor` ancak sınıf, `Person` devralınan örnek alanlarını başlatmaya sınıf oluşturucusu çağıramaz.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Nesne oluşturucu, nesne oluşturmak dışında çağrılamaz. Ayrıca, bir nesne iki kez başharfe alınamaz. Örneğin, bu ve <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> deserialization yöntemleri <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> gibi yapıcılar aramaması gerektiği anlamına gelir.

<a name="properties"></a>

### <a name="properties"></a>Özellikler

CLS uyumlu türlerdeki özellikler aşağıdaki kurallara uymalıdır:

- Bir özelliğin ayarlayıcısı, bir ayarlayıcısı veya her ikisi de olmalıdır. Bir derlemede, bunlar ayrı yöntemler olarak görünecekleri anlamına gelen özel yöntemler olarak uygulanır (alıcıya `get_` *özellik adı* verilir ve ayarlayıcı özellik `set_` *adıdır)* derlemenin meta verilerinde işaretlenir. `SpecialName` C# ve Visual Basic derleyicileri özniteliği uygulamaya <xref:System.CLSCompliantAttribute> gerek kalmadan bu kuralı otomatik olarak uygular.

- Bir özelliğin türü, özellik getterinin iade türüdür ve ayarlayıcının son bağımsız değişkenidir. Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler başvuru ile özelliğe atanamaz (diğer bir şekilde, bunlar yönetilemez işaretçileri).

- Bir özelliğin hem getter hem de ayarlayıcısı varsa, her ikisi de sanal, hem statik veya her iki örnek olmalıdır. C# ve Visual Basic derleyicileri bu kuralı özellik tanımı sözdizimi aracılığıyla otomatik olarak uygular.

<a name="events"></a>

### <a name="events"></a>Olaylar

Bir olay, adı ve türüne göre tanımlanır. Olay türü, olayı belirtmek için kullanılan bir temsilcidir. Örneğin, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay türü. <xref:System.ResolveEventHandler> Olayın kendisine ek olarak, olay adına dayalı adlara sahip üç yöntem etkinliğin `SpecialName` uygulanmasını sağlar ve derlemenin meta verilerinde olduğu gibi işaretlenir:

- `add_` *EventName*adlı bir olay işleyicisi eklemek için bir yöntem. Örneğin, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay için olay abonelik yöntemi `add_AssemblyResolve`adlandırılır.

- `remove_` *EventName*adlı bir olay işleyicisi kaldırmak için bir yöntem. Örneğin, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayın kaldırma yöntemi adlandırılmış. `remove_AssemblyResolve`

- Olayın oluştuğunu belirten bir yöntem, `raise_` *EventName*adlı .

> [!NOTE]
> Ortak Dil Belirtimi'nin olaylarla ilgili kurallarının çoğu dil derleyicileri tarafından uygulanır ve bileşen geliştiricileri için saydamdır.

Olayı ekleme, kaldırma ve yükseltme yöntemleri aynı erişilebilirlikte olmalıdır. Bunların hepsi statik, örnek veya sanal olmalıdır. Olay ekleme ve kaldırma yöntemlerinin, olay temsilcisi türü olan bir parametresi vardır. Ekleme ve kaldırma yöntemleri nin her ikisi de mevcut olmalı veya her ikisi de bulunmamalıdır.

Aşağıdaki örnek, iki okuma arasındaki sıcaklık `Temperature` değişimi `TemperatureChanged` bir eşik değerine eşit sayılsa veya aşarsa, olayı yükselten CLS uyumlu bir sınıf tanımlar. Sınıf, `Temperature` olay işleyicilerini seçiçle yürütebilmek için bir `raise_TemperatureChanged` metodu açıkça tanımlar.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Aşırı Yüklemeler

Ortak Dil Belirtimi, aşırı yüklü üyelere aşağıdaki gereksinimleri uygular:

- Üyeler, parametrelerin sayısına ve herhangi bir parametrenin türüne göre aşırı yüklenebilir. Arama kuralı, iade türü, yönteme veya parametresine uygulanan özel değiştiriciler ve parametrelerin değer veya referans tarafından geçirilip geçirilemediği, aşırı yükler arasında ayrım yaparken dikkate alınmaz. Örneğin, [Adlandırma kuralları](#naming) bölümünde ki bir kapsamda adların benzersiz olması gereksiniminin kodunu görün.

- Yalnızca özellikler ve yöntemler aşırı yüklenebilir. Alanlar ve olaylar aşırı yüklenemez.

- Genel yöntemler, genel parametrelerinsayısına bağlı olarak aşırı yüklenebilir.

> [!NOTE]
> Ve `op_Explicit` `op_Implicit` işleçler, iade değerinin aşırı yük çözümü için yöntem imzasının bir parçası olarak kabul edilmeme kuralının istisnalarıdır. Bu iki işleç hem parametrelerine hem de getiri değerine göre aşırı yüklenebilir.

<a name="exceptions"></a>

### <a name="exceptions"></a>Özel durumlar

Özel durum nesneleri, <xref:System.Exception?displayProperty=nameWithType> <xref:System.Exception?displayProperty=nameWithType>'den türetilen başka bir türden türemelisiniz. Aşağıdaki örnek, özel durum işleme için özel `ErrorClass` bir sınıf kullanıldığında ortaya çıkan derleyici hatasını göstermektedir.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Bu hatayı düzeltmek `ErrorClass` için sınıfın <xref:System.Exception?displayProperty=nameWithType>.'den devralması gerekir. Buna ek `Message` olarak, özellik geçersiz kılınmalıdır. Aşağıdaki örnek, CLS uyumlu `ErrorClass` bir sınıf tanımlamak için bu hataları düzeltir.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Öznitelikler

In.NET Framework derlemeleri, özel öznitelikleri özel öznitelikleri depolamak ve derlemeler, türler, üyeler ve yöntem parametreleri gibi programlama nesneleri hakkında meta veri almak için genişletilebilir bir mekanizma sağlar. Özel öznitelikler, <xref:System.Attribute?displayProperty=nameWithType> <xref:System.Attribute?displayProperty=nameWithType>'den türetilen bir türden veya türden türemelisiniz.

Aşağıdaki örnek bu kuralı ihlal eder. Bu türetilmiştir olmayan bir `NumericAttribute` sınıf <xref:System.Attribute?displayProperty=nameWithType>tanımlar. Derleyici hatasının yalnızca CLS uyumlu olmayan öznitelik uygulandığında, sınıf tanımlandığında değil, sonucu olduğunu unutmayın.

[!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
[!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]

CLS uyumlu bir özniteliğin oluşturucu suveya özellikleri yalnızca aşağıdaki türleri ortaya çıkarabilir:

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

- Altta yatan <xref:System.Byte>türü , , <xref:System.Int16> <xref:System.Int32>, veya <xref:System.Int64>.

Aşağıdaki örnekte, `DescriptionAttribute` 'den <xref:System.Attribute>türeyen bir sınıf tanımlanır. Sınıf oluşturucu türü bir parametre `Descriptor`vardır, bu nedenle sınıf CLS uyumlu değildir. C# derleyicisinin bir uyarı yayan ancak başarılı bir şekilde derlediğini, Visual Basic derleyicisinin ise ne bir uyarı ne de bir hata yayan bir hata olduğunu unutmayın.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>CLSCompliantAttribute özniteliği

Öznitelik, <xref:System.CLSCompliantAttribute> bir program öğesinin Ortak Dil Belirtimine uyup uymadığını belirtmek için kullanılır. Oluşturucu, <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29> `isCompliant`program öğesinin CLS uyumlu olup olmadığını gösteren tek bir gerekli parametre içerir.

Derleme zamanında derleyici, CLS uyumlu olduğu tahmin edilen uyumlu olmayan öğeleri algılar ve bir uyarı yatar. Derleyici, açıkça uyumsuz olduğu bildirilen türler veya üyeler için uyarı lar yayan değildir.

Bileşen geliştiriciler özniteliği <xref:System.CLSCompliantAttribute> iki şekilde kullanabilir:

- Ortak arabirimin CLS uyumlu bir bileşen ve CLS uyumlu olmayan bölümleri tarafından maruz kalan bölümlerini tanımlamak için. Özellik, belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, kullanımı bu öğelerin .NET Framework'ünü hedefleyen tüm dil ve araçlardan erişilebilir olduğunu garanti eder.

- Bileşen kitaplığın ortak arabiriminin yalnızca CLS uyumlu program öğelerini ortaya çıkarmasını sağlamak için. Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı yayımlar.

> [!WARNING]
> Bazı durumlarda, dil derleyicileri özniteliğin <xref:System.CLSCompliantAttribute> kullanılıp kullanılmadığına bakılmaksızın CLS uyumlu kuralları uygular. Örneğin, bir arabirimde statik bir üye tanımlamak bir CLS kuralını ihlal eder. Bu bağlamda, bir arabirimde (C#) veya `static` `Shared` (Visual Basic'te) bir üye tanımlarsanız, hem C# hem de Visual Basic derleyicileri bir hata iletisi görüntüler ve uygulamayı derlemede başarısız olur.

Öznitelik <xref:System.CLSCompliantAttribute> değeri olan <xref:System.AttributeUsageAttribute> bir öznitelik ile <xref:System.AttributeTargets.All?displayProperty=nameWithType>işaretlenir. Bu değer, özniteliği <xref:System.CLSCompliantAttribute> derlemeler, modüller, türler (sınıflar, yapılar, arabirimler ve temsilciler), tür üyeleri (oluşturucular, yöntemler, özellikler, alanlar ve olaylar), parametreler, genel parametreler ve iade değerleri dahil olmak üzere herhangi bir program öğesine uygulamanızı sağlar. Ancak, uygulamada, özniteliği yalnızca derlemelere, türlere ve tür üyelerine uygulamanız gerekir. Aksi takdirde, derleyiciler özniteliği yoklar ve kitaplığınızın ortak arabiriminde uyumlu olmayan bir parametre, genel parametre veya iade değeriyle karşılaştıklarında derleyici uyarıları oluşturmaya devam ederler.

Özniteliğin <xref:System.CLSCompliantAttribute> değeri, içerdiği program öğeleri tarafından devralınR. Örneğin, bir derleme CLS uyumlu olarak işaretlenmişse, türleri de CLS uyumludur. Bir tür CLS uyumlu olarak işaretlenmişse, iç içe olan türleri ve üyeleri de CLS uyumludur.

Özniteliği içerdiği bir program öğesine uygulayarak <xref:System.CLSCompliantAttribute> devralınan uyumluluğu açıkça geçersiz kılabilirsiniz. Örneğin, özniteliği, <xref:System.CLSCompliantAttribute> uyumlu olmayan `isCompliant` bir `false` derlemede uyumlu olmayan bir türü tanımlamak için bir değerle kullanabilir `isCompliant` ve `true` özniteliği uyumlu olmayan bir derlemede uyumlu bir tür tanımlamak için bir değerle kullanabilirsiniz. Uyumlu olmayan üyeleri uyumlu bir türde de tanımlayabilirsiniz. Ancak, uyumlu olmayan bir tür uyumlu üyeleri olamaz, bu nedenle `isCompliant` uyumlu `true` olmayan bir tür devralma geçersiz kılmak için bir değer ile öznitelik kullanamazsınız.

Bileşenler geliştirirken, derlemenizin, <xref:System.CLSCompliantAttribute> türlerinin ve üyelerinin CLS uyumlu olup olmadığını belirtmek için özniteliği her zaman kullanmanız gerekir.

CLS uyumlu bileşenler oluşturmak için:

1. Montajını <xref:System.CLSCompliantAttribute> CLS uyumlu olarak işaretlemek için kullanın.

2. Derlemede, CLS uyumlu olmayan tüm genel olarak açıklanmış türleri uyumlu olmayan olarak işaretleyin.

3. CLS uyumlu türdeki herkese açık üyeleri uyumlu olmayan olarak işaretleyin.

4. CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlayın.

Tüm uyumlu olmayan türlerinizi ve üyelerinizi başarıyla işaretlediyseniz, derleyiciniz herhangi bir uyumsuzluk uyarısı yaslanmamalıdır. Ancak, hangi üyelerin CLS uyumlu olmadığını belirtmeli ve ürün belgelerinizde CLS uyumlu alternatiflerini listelemelisiniz.

Aşağıdaki örnek, <xref:System.CLSCompliantAttribute> CLS uyumlu olmayan iki üyesi olan bir `CharacterUtilities`CLS uyumlu derleme ve bir tür tanımlamak için özniteliği kullanır. Her iki üye de `CLSCompliant(false)` öznitelik ile etiketlenmiş olduğundan, derleyici hiçbir uyarı üretir. Sınıf ayrıca her iki yöntem için cls uyumlu bir alternatif sağlar. Normalde, CLS uyumlu alternatifler sağlamak için `ToUTF16` yönteme iki aşırı yükleme ekleriz. Ancak, yöntemler iade değerine göre aşırı yüklenemediğinden, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklıdır.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Kitaplık yerine bir uygulama geliştiriyorsanız (diğer bir deyişle, diğer uygulama geliştiricileri tarafından tüketilebilen türleri veya üyeleri ifşa etmiyorsanız), uygulamanızın tükettiği program öğelerinin CLS uyumluluğu yalnızca diliniz bunları desteklemiyorsa ilgi nizi görür. Bu durumda, CLS uyumlu olmayan bir öğekullanmaya çalıştığınızda dil derleyiciniz bir hata oluşturur.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Diller Arası Birlikte Çalışabilirlik

Dil bağımsızlığının birkaç olası anlamı vardır. [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../docs/standard/language-independence-and-language-independent-components.md)makalesinde tartışılan bir anlam, başka bir dilde yazılmış bir uygulamadan bir dilde yazılmış türleri sorunsuz bir şekilde tüketmeyi içerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.

Aşağıdaki örnekte, Iki sınıf içeren Utilities.dll adlı bir sınıf kitaplığı `NumericLib` oluşturarak diller arası birlikte çalışabilirlik ve `StringLib`. Sınıf `NumericLib` C# ile yazılır ve `StringLib` sınıf Visual Basic ile yazılır. Aşağıda `ToTitleCase` sınıfında tek bir üye, `StringLib`, içeren StringUtil.vb için kaynak kodu verilmiştir.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

İki sınıfı tek bir derlemede paketlemek için bunları modüller halinde derlemeniz gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
vbc /t:module StringUtil.vb
```

Visual Basic derleyicisinin komut satırı sözdizimi hakkında daha fazla bilgi için [Komut Satırı'ndan Bina bölümüne](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)bakın.

C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
csc /t:module NumberUtil.cs
```

C# derleyicisinin komut satırı sözdizimi hakkında daha fazla bilgi için [csc.exe ile Komut Satırı Binası'na](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)bakın.

Daha sonra iki modülü derlemek için [Bağlayıcı seçeneklerini](/cpp/build/reference/linker-options) kullanırsınız:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Aşağıdaki örnek daha `NumericLib.NearZero` sonra `StringLib.ToTitleCase` çağırır ve yöntemleri. Hem Visual Basic kodunun hem de C# kodunun her iki sınıftaki yöntemlere erişebildiğini unutmayın.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Visual Basic kodunu derlemek için bu komutu kullanın:

```console
vbc example.vb /r:UtilityLib.dll
```

C# ile derlemek için derleyicinin adını **vbc'den** **csc'ye**değiştirin ve dosya uzantısını .vb.'den .cs'ye değiştirin:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.CLSCompliantAttribute>
