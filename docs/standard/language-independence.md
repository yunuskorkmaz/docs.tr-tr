---
title: Dil bağımsızlığı ve dilden bağımsız bileşenler
description: C#, C++/CLI, F#, IronPython, VB, Visual COBOL ve PowerShell gibi .NET'te desteklenen birçok dilden birinde nasıl geliştirebileceğinizi öğrenin.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 03751fa3758c239cb9eea5fe826dff66c1c1605b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249584"
---
# <a name="language-independence-and-language-independent-components"></a>Dil bağımsızlığı ve dilden bağımsız bileşenler

.NET dilden bağımsızdır. Bu, bir geliştirici olarak C#, F#ve Visual Basic gibi .NET uygulamalarını hedefleyen birçok dilden birinde geliştirebileceğiniz anlamına gelir. .NET uygulamaları için geliştirilen sınıf kitaplıklarının türlerine ve üyelerine, orijinal dilin kurallarını izlemeden ve dilin yazıldığı dili bilmek zorunda kalmadan erişebilirsiniz. Bileşen geliştiricisiyseniz, bileşeninize dili ne olursa olsun herhangi bir .NET uygulaması erişebilir.

> [!NOTE]
> Bu makalenin bu ilk bölümünde, dilden bağımsız bileşenler - yani herhangi bir dilde yazılmış uygulamalar tarafından tüketilebilen bileşenler oluşturma yı tartışır. Ayrıca, birden çok dilde yazılmış kaynak kodundan tek bir bileşen veya uygulama oluşturabilirsiniz; bu makalenin ikinci bölümünde [Çapraz Diller Arası Birlikte çalışabilirlik](#cross-language-interoperability) bölümüne bakın.

Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşimde kalmak için, nesnelerin arayanlara yalnızca tüm dillerde ortak olan bu özellikleri ortaya çıkarmaları gerekir. Bu yaygın özellik kümesi, oluşturulan derlemeler için geçerli olan bir kural kümesi olan Ortak Dil Belirtimi (CLS) tarafından tanımlanır. Ortak Dil Belirtimi Bölüm I, Clauses 7 ile 11 [ECMA-335 Standart: Ortak Dil Altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm)tanımlanır.

Bileşeniniz Ortak Dil Belirtimi'ne uygunsa, CLS uyumlu olduğu garanti edilir ve CLS'yi destekleyen herhangi bir programlama dilinde yazılmış derlemelerde koddan erişilebilir. [ClSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini kaynak kodunuza uygulayarak bileşeninizin derleme zamanında Ortak Dil Belirtimine uygun olup olmadığını belirleyebilirsiniz. Daha fazla bilgi için [CLSCompliant Attribute özniteliğine](#the-clscompliantattribute-attribute)bakın.

Bu makalede:

* [CLS uyumluluk kuralları](#cls-compliance-rules)

  * [Üye imzatürleri ve türleri](#types-and-type-member-signatures)

  * [Adlandırma kuralları](#naming-conventions)

  * [Tür dönüştürme](#type-conversion)

  * [Diziler](#arrays)

  * [Arabirimler](#interfaces)

  * [Numaralandırma](#enumerations)

  * [Genel olarak tip üyeleri](#type-members-in-general)

  * [Üye erişilebilirliği](#member-accessibility)

  * [Genel türler ve üyeler](#generic-types-and-members)

  * [Oluşturucular](#constructors)

  * [Özellikler](#properties)

  * [Olaylar](#events)

  * [Aşırı Yüklemeler](#overloads)

  * [Özel durumlar](#exceptions)

  * [Öznitelikler](#attributes)

* [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute)

* [Diller Arası Birlikte Çalışabilirlik](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>CLS uyumluluk kuralları

Bu bölümde CLS uyumlu bir bileşen oluşturma kuralları tartışılmaktadır. Kuralların tam listesi için, [ECMA-335 Standardının](https://www.ecma-international.org/publications/standards/Ecma-335.htm)Bölüm I, Madde 11: Ortak Dil Altyapısı'na bakın.

> [!NOTE]
> Ortak Dil Belirtimi, tüketiciler (CLS uyumlu bir bileşene programlı olarak erişen geliştiriciler), çerçeveler (oluşturmak için bir dil derleyicisi kullanan geliştiriciler) için geçerli olduğu için CLS uyumluluğu için her kuralı tartışır CLS uyumlu kitaplıklar ve genişleticiler (dil derleyicisi veya CLS uyumlu bileşenler oluşturan bir kod aracı gibi bir araç oluşturan geliştiriciler). Bu makalede, çerçeveler için geçerli olarak kurallar üzerinde duruluyor. Ancak, genişleticiler için geçerli olan bazı kuralların [Reflection.Emit](xref:System.Reflection.Emit)kullanılarak oluşturulan derlemeler için de geçerli olabileceğini unutmayın.

Dilden bağımsız bir bileşen tasarlamak için CLS uyumluluğu kurallarını bileşeninizin ortak arabirimine uygulamanız gerekir. Özel uygulamanız belirtime uymak zorunda değildir.

> [!IMPORTANT]
> CLS uyumluluğu için kurallar, özel uygulaması için değil, yalnızca bir bileşenin ortak arabirimi için geçerlidir.

Örneğin, [Byte](xref:System.Byte) dışındaki imzasız tümerler CLS uyumlu değildir. Aşağıdaki `Person` örnekteki sınıf `Age` [UInt16](xref:System.UInt16)türüözelliğini ortaya çıkardığından, aşağıdaki kod derleyici uyarısı görüntüler.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

ClS uyumlu, 16 bit imzalı bir `Age` tamsayı `UInt16` olan [Int16](xref:System.Int16)özelliğinin türünü değiştirerek Kişi sınıfı CLS uyumlu hale getirebilirsiniz. Özel `personAge` alanın türünü değiştirmeniz gerekmez.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

Bir kitaplığın ortak arabirimi aşağıdakilerden oluşur:

* Ortak sınıfların tanımları.

* Ortak sınıfların genel üyelerinin tanımları ve türemiş sınıflara erişilebilen üyelerin tanımları (diğer bir şekilde korunan üyeler).

* Genel sınıfların ortak yöntemlerinin parametreleri ve dönüş türleri ile türemiş sınıflar için erişilebilir parametreler ve dönüş yöntemleri.

CLS uyumluluk kuralları aşağıdaki tabloda listelenmiştir. Kuralların metni [ECMA-335 Standardı: Ortak Dil Altyapısından,](https://www.ecma-international.org/publications/standards/Ecma-335.htm)Telif Hakkı 2012 Ecma International tarafından aynen alınmıştır. Bu kurallar hakkında daha ayrıntılı bilgi aşağıdaki bölümlerde yer aldı.

Kategori | Bkz. | Kural | Kural Numarası
-------- | --- | ---- | -----------
Erişilebilirlik | [Üye erişilebilirliği](#member-accessibility) | Erişilebilirlik, erişilebilirlik `family-or-assembly`ile farklı bir derlemeden devralınan bir yöntemi geçersiz kılmak dışında, devralınan yöntemleri geçersiz kılarak erişilebilirlik değiştirilemez. Bu durumda, geçersiz kılma erişilebilirlik `family`olacaktır. | 10
Erişilebilirlik | [Üye erişilebilirliği](#member-accessibility) | Türlerin ve üyelerin görünürlüğü ve erişilebilirliği, herhangi bir üyenin imzasındaki türlerin görünür ve erişilebilir olması durumunda görünür ve erişilebilir olacaktır. Örneğin, derlemesi dışında görünen genel bir yöntem, türü yalnızca derleme içinde görünen bir bağımsız değişkene sahip olmayacaktır. Herhangi bir üyenin imzasında kullanılan anlık genel bir türü oluşturan türlerin görünürlüğü ve erişilebilirliği, üyenin kendisi görünür ve erişilebilir olduğunda görünür ve erişilebilir olacaktır. Örneğin, derlemesi dışında görünen bir üyenin imzasında bulunan anlık genel bir tür, türü yalnızca derleme içinde görünen genel bir bağımsız değişkene sahip olmayacaktır. | 12
Diziler | [Diziler](#arrays) | Diziler CLS uyumlu türe sahip öğelere sahip olacak ve dizinin tüm boyutları sıfır ın alt sınırlarına sahip olacaktır. Yalnızca bir öğenin bir dizi olması ve dizinin öğe türüaşırı yüklemeleri ayırt etmek için gerekli olacaktır. Aşırı yükleme iki veya daha fazla dizi türüne dayandığında eleman türleri türleri adlandırılacaktır. | 16
Öznitelikler | [Öznitelikler](#attributes) | Öznitelikler, [System.Attribute](xref:System.Attribute)türünden veya ondan devralan bir türden olacaktır. | 41
Öznitelikler | [Öznitelikler](#attributes) | CLS yalnızca özel özniteliklerin kodlamalarının bir alt kümesine izin verir. Bu kodlamalar görünecek tek türleri (Bölüm IV bakınız): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), ve cls uyumlu baz tamsayı türüne dayalı herhangi bir numaralandırma türü. | 34
Öznitelikler | [Öznitelikler](#attributes) | CLS, genel olarak görünür olarak görülebilen gerekli değiştiricilere izin vermez (,`modreq`Bkz. Bölüm II), ancak isteğe bağlı değiştiricilere izin verir (`modopt`, Bölüm II'ye bakınız) anlamaz. | 35
Oluşturucular | [Oluşturucular](#constructors) | Bir nesne oluşturucu, devralınan örnek verilerine herhangi bir erişim oluşmadan önce taban sınıfının bazı örnek oluşturucularını çağırır. (Bu, oluşturucuları olmayan değer türleri için geçerli değildir.)  | 21
Oluşturucular | [Oluşturucular](#constructors) | Bir nesne oluşturucu, bir nesnenin oluşturulmasının bir parçası dışında çağrılmayacaktır ve bir nesne iki kez başharfe batılamaz. | 22
Numaralandırmalar | [Numaralandırma](#enumerations) | Bir enum un altında yatan türü dahili CLS tamsayı türü olacak, alanın adı "value__" olacak `RTSpecialName`ve bu alan işaretlenecektir. |  7
Numaralandırmalar | [Numaralandırma](#enumerations) | [System.FlagsAttribute](xref:System.FlagsAttribute) (Bkz. Bölüm IV Kitaplığı) özel özniteliğinin varlığı veya yokluğuyla gösterilen iki farklı enum türü vardır. Biri adlandırılmış veyasededeğerleri temsil eder; diğeri, adsız bir değer oluşturmak için biraraya getirilebilen adlandırılmış bit bayraklarını temsil eder. A `enum` değeri belirtilen değerlerle sınırlı değildir. |  8
Numaralandırmalar | [Numaralandırma](#enumerations) | Bir enumun gerçek statik alanları, enumun kendi türüne sahip olacaktır. |  9
Olaylar | [Olaylar](#events) | Bir olayı uygulayan yöntemler meta `SpecialName` verilerde işaretlenir. |29
Olaylar | [Olaylar](#events) | Bir olayın ve onun erişenegelenlerinin erişilebilirliği aynı olacaktır. |30
Olaylar | [Olaylar](#events) | Bir `add` `remove` olayın yöntemleri ve yöntemleri hem mevcut hem de yok olacaktır. |31
Olaylar | [Olaylar](#events) | Bir `add` `remove` olayın ve yöntemlerin her biri, etkinliğin türünü tanımlayan ve [System.Delegate'den](xref:System.Delegate)türetilecek bir parametre alır. |32
Olaylar | [Olaylar](#events) | Olaylar belirli bir adlandırma desenine uygun olacaktır. CLS kural 29'da belirtilen SpecialName özniteliği, uygun ad karşılaştırmalarında yoksayılır ve tanımlayıcı kurallarına uyar.  |33
Özel durumlar | [Özel durumlar](#exceptions) | Atılan nesneler [System.Exception](xref:System.Exception) türünden veya ondan devralan bir türden olacaktır. Bununla birlikte, CLS uyumlu yöntemler, diğer özel durum türlerinin yayılmasını engellemek için gerekli değildir. | 40
Genel | [CLS uyumluluk kuralları](#cls-compliance-rules) | CLS kuralları yalnızca tanımlayıcı derlemenin dışında erişilebilen veya görülebilen bir türdeki parçalar için geçerlidir. | 1
Genel | [CLS uyumluluk kuralları](#cls-compliance-rules) | CLS uyumlu olmayan türlerin üyeleri CLS uyumlu olarak işaretlenmeyecek. | 2
Genel Türler | [Genel türler ve üyeler](#generic-types-and-members) | İç içe geçmiş türler, en az çevreleyen tür kadar sayıda genel parametreye sahip olacaktır. İç içe bir türdeki genel parametreler, kendi çevreleyen türündeki genel parametrelere göre konuma göre karşılık gelir.  | 42
Genel Türler | [Genel türler ve üyeler](#generic-types-and-members) | Genel bir türün adı, iç içe geçmemiş türde beyan edilen veya iç içe geçen türe yeni getirilen tür parametrelerinin sayısını yukarıda açıklanan kurallara göre kodlar. | 43
Genel Türler | [Genel türler ve üyeler](#generic-types-and-members) | Genel bir tür, temel türdeki kısıtlamaların veya arabirimlerin genel tür kısıtlamaları tarafından karşılanacağını garanti etmek için yeterli kısıtlamaları yeniden beyan eder. | 44
Genel Türler | [Genel türler ve üyeler](#generic-types-and-members) | Genel parametrelerde kısıtlama olarak kullanılan türler CLS uyumlu olacaktır. | 45
Genel Türler | [Genel türler ve üyeler](#generic-types-and-members) | Üyelerin (iç içe gelişmiş türler dahil) anlık genel bir türdeki görünürlüğü ve erişilebilirliği, genel tür bildiriminin bir bütün olarak yerine belirli anlık olarak kapsamı olarak kabul edilecektir. Bunu varsayarsak, CLS kural 12'nin görünürlük ve erişilebilirlik kuralları hala geçerlidir. | 46
Genel Türler | [Genel türler ve üyeler](#generic-types-and-members) | Her soyut veya sanal genel yöntem için varsayılan bir somut (soyut olmayan) uygulama | 47
Arabirimler | [Arabirimler](#interfaces) | CLS uyumlu arabirimler, bunları uygulamak için CLS uyumlu olmayan yöntemlerin tanımlanmasını gerektirmez. | 18
Arabirimler | [Arabirimler](#interfaces) | CLS uyumlu arabirimler statik yöntemleri tanımlamaz ve alanları tanımlamaz. | 19
Üyeler | [Genel olarak tip üyeleri](#type-members-in-general) | Genel statik alanlar ve yöntemler CLS uyumlu değildir. | 36
Üyeler | -- | Bir literal statik değeri alan başlatma meta verilerinin kullanımı ile belirtilir. CLS uyumlu bir literal, alan başlatma meta verilerinde tam olarak literal (veya temel türde, eğer bu gerçek `enum`bir gerçek se) ile aynı türde belirtilen bir değere sahip olmalıdır. | 13
Üyeler | [Genel olarak tip üyeleri](#type-members-in-general) | Vararg kısıtlaması CLS'nin bir parçası değildir ve CLS tarafından desteklenen tek çağrı sözleşmesi standart yönetilen arama kuralıdır. | 15
Adlandırma kuralları | [Adlandırma kuralları](#naming-conventions) | Derlemeler, Unicode Standard3.0'ın Teknik Raporu'nun 15'inci ekini izleyerek, [Unicode Normalizasyon Formlarında](https://www.unicode.org/unicode/reports/tr15/tr15-18.html)çevrimiçi olarak bulunan tanımlayıcılara başlamasına ve dahil edilmesine izin verilen karakter kümesini yönetecektir. Tanımlayıcılar, Unicode Normalizasyon Formu C ile tanımlanan kanonik formatta olacaktır. CLS amaçları için, küçük harf eşlemeleri (Unicode yerel duyarsız, bire bir küçük harf eşlemeleri tarafından belirtildiği gibi) aynıysa iki tanımlayıcı aynıdır. Diğer bir deyişle, iki tanımlayıcının CLS altında farklı kabul edilmesi için, sadece kendi durumunda daha farklı olacaktır. Ancak, devralınan bir tanımı geçersiz kılmak için CLI, özgün bildirimin kesin kodlamasının kullanılmasını gerektirir. | 4
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | CLS uyumlu bir kapsamda tanıtılan tüm adlar, adların aynı olduğu ve aşırı yükleme yoluyla çözüldüğü durumlar dışında farklı türde bağımsız olacaktır. Diğer bir zamanda, CTS tek bir türün bir yöntem ve alan için aynı adı kullanmasına izin verirken, CLS bunu yapmaz. | 5
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | CtS farklı imzaların ayırt edilmesine izin vermesine rağmen, alanlar ve iç içe doğru türler yalnızca tanımlayıcı karşılaştırmasına göre ayrı olacaktır. Aynı ada sahip yöntemler, özellikler ve olaylar (tanımlayıcı karşılaştırmasına göre) CLS Kural 39'da belirtilenler dışında, dönüş türünden daha fazlasına göre farklılık gösterir | 6
Aşırı Yükleme | [Aşırı Yüklemeler](#overloads) | Yalnızca özellikler ve yöntemler aşırı yüklenebilir. | 37
Aşırı Yükleme | [Aşırı Yüklemeler](#overloads) |Özellikler ve yöntemler, yalnızca parametrelerinin sayısına ve türlerine göre, `op_Implicit` `op_Explicit`adlandırılmış dönüştürme işleçleri dışında ve dönüş türlerine göre aşırı yüklenebilecek aşırı yüklenebilir. | 38
Aşırı Yükleme | -- | Bir türde bildirilen iki veya daha fazla CLS uyumlu yöntem aynı ada sahipse ve belirli bir tür anlık yineleme kümesi için aynı parametre ve dönüş türlerine sahipse, tüm bu yöntemler bu tür anlık belirlemelerde anlamsal olarak eşdeğer olacaktır. | 48
Özellikler | [Özellikler](#properties) | Bir özelliğin alıcı ve ayarlayıcı yöntemlerini uygulayan `SpecialName` yöntemler meta verilerde işaretlenir. | 24
Özellikler | [Özellikler](#properties) | Bir mülkün erişime girenlerin tümü statik, tümü sanal veya örnek olacaktır. | 26
Özellikler | [Özellikler](#properties) | Bir özelliğin türü, ayarlayıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türü olacaktır. Özelliğin parametrelerinin türleri, ayarlayıcının parametrelerinin türleri ve ayarlayıcının son parametresi dışında tüm parametrelerin türleri olacaktır. Bu türlerin tümü CLS uyumlu olacaktır ve yönetilmeyecektir (diğer bir şekilde referans la geçirilmeyecektir). | 27
Özellikler | [Özellikler](#properties) | Özellikler belirli bir adlandırma desenine bağlıdır. `SpecialName` CLS kural 24'te belirtilen öznitelik, uygun ad karşılaştırmalarında yoksayılır ve tanımlayıcı kurallarına uyar. Bir özellik bir getter yöntemi, bir ayarlayıcı yöntemi veya her ikisi de olacaktır. | 28
Tür dönüştürme | [Tür dönüştürme](#type-conversion) | op_Implicit veya op_Explicit sağlanmışsa, zorlamayı sağlamak için alternatif bir araç sağlanacaktır. | 39
Türler | [Üye imzatürleri ve türleri](#types-and-type-member-signatures) | Kutulu değer türleri CLS uyumlu değildir. | 3
Türler | [Üye imzatürleri ve türleri](#types-and-type-member-signatures) | İmzada görünen tüm türler CLS uyumlu olacaktır. Anlık genel bir tür oluşturan tüm türler CLS uyumlu olacaktır. | 11
Türler | [Üye imzatürleri ve türleri](#types-and-type-member-signatures) | Yazılan başvurular CLS uyumlu değildir. | 14
Türler | [Üye imzatürleri ve türleri](#types-and-type-member-signatures) | Yönetilmeyen işaretçi türleri CLS uyumlu değildir. | 17
Türler | [Üye imzatürleri ve türleri](#types-and-type-member-signatures) | CLS uyumlu sınıflar, değer türleri ve arayüzler, CLS uyumlu olmayan üyelerin uygulanmasını gerektirmez | 20
Türler | [Üye imzatürleri ve türleri](#types-and-type-member-signatures) | [System.Object](xref:System.Object) CLS uyumludur. CLS uyumlu diğer herhangi bir sınıf, CLS uyumlu bir sınıftan devralınacaktır. | 23

### <a name="types-and-type-member-signatures"></a>Üye imzatürleri ve türleri

[System.Object](xref:System.Object) türü CLS uyumludur ve .NET Framework türü sistemindeki tüm nesne türlerinin temel türüdür. .NET Framework'deki devralma ya örtülüdür (örneğin, [String](xref:System.String) sınıfı `Object` örtük olarak sınıftan devralır) veya açık (örneğin, [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) sınıfı, [Özel Durum](xref:System.Exception) sınıfından açıkça devralan Bağımsız [Durum](xref:System.ArgumentException) sınıfından açıkça devralır. Türetilen bir türün CLS uyumlu olabilmesi için, taban türü de CLS uyumlu olmalıdır.

Aşağıdaki örnekte, taban türü CLS uyumlu olmayan türetilmiş bir tür gösterilmektedir. İmzasız 32 `Counter` bit tamsayı kullanan bir taban sınıfı sayaç olarak tanımlar. Sınıf imzasız bir karşıcıyı sararak sayaç işlevselliği sağladığından, sınıf CLS uyumlu olmayan olarak işaretlenir. Sonuç olarak, türetilmiş `NonZeroCounter`bir sınıf, CLS uyumlu değildir.

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

Bir yöntemin dönüş türü veya özellik türü de dahil olmak üzere üye imzalarda görünen tüm türler CLS uyumlu olmalıdır. Buna ek olarak, genel türleri için:

* Anında genel bir tür oluşturan tüm türler CLS uyumlu olmalıdır.

* Genel parametrelerde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır.

.NET [ortak tür sistemi,](common-type-system.md) ortak dil çalışma zamanı tarafından doğrudan desteklenen ve bir derlemenin meta verilerinde özel olarak kodlanan bir dizi yerleşik türleri içerir. Bu içsel türlerden, aşağıdaki tabloda listelenen türleri CLS uyumludur.

CLS uyumlu tip | Açıklama
------------------ | -----------
[Bayt](xref:System.Byte) | 8 bit imzasız tümseci
[Int16](xref:System.Int16) | 16 bit imzalı tümseci
[Int32](xref:System.Int32) | 32 bit imzalı tümseci
[Int64](xref:System.Int64) | 64 bit imzalı tümseci
[Tek](xref:System.Single) | Tek hassas kayan nokta değeri
[Çift](xref:System.Double) | Çift duyarlıklı kayan nokta değeri
[Boole](xref:System.Boolean) | doğru veya yanlış değer türü
[Char](xref:System.Char) | UTF-16 kodlanmış kod birimi
[On -da -lık](xref:System.Decimal) | Kayan olmayan nokta ondalık sayı
[ıntptr](xref:System.IntPtr) | Platform tanımlı bir boyutun işaretçisi veya tutamacı
[Dize](xref:System.String) | Sıfır, bir veya daha fazla Char nesnesinin toplanması

Aşağıdaki tabloda listelenen içsel türleri CLS uyumlu değildir.

Uyumlu olmayan tür | Açıklama | CLS uyumlu alternatif
------------------ | ----------- | -------------------------
[Sbyte](xref:System.SByte) | 8 bit imzalı imzalı veri türü | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16 bit imzasız tümseci | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32 bit imzasız tümseci | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64 bit imzasız tümseci | [Int64](xref:System.Int64) (taşabilir), [BigInteger](xref:System.Numerics.BigInteger)veya [Çift](xref:System.Double)
[Uıntptr](xref:System.UIntPtr) | İmzasız işaretçi veya tanıtıcı | [ıntptr](xref:System.IntPtr)

.NET Framework Class Kitaplığı veya başka bir sınıf kitaplığı CLS uyumlu olmayan diğer türleri içerebilir; örneğin:

* Kutulu değer türleri. Aşağıdaki C# örneği, * adlı `int` `Value`türde bir ortak özelliği olan bir sınıf oluşturur. `int`* kutulu bir değer türü olduğundan, derleyici onu CLS uyumlu olmayan olarak işaretler.

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* Bir nesneye ve bir türe başvuru içeren özel yapılar olan yazılı başvurular.

Bir tür CLS uyumlu değilse, [CLSCompliant Attribute özniteliğini](xref:System.CLSCompliantAttribute) bir değeri `false` olan bir *isCompliant* parametresi ile uygulamalısınız. Daha fazla bilgi için [CLSCompliant Attribute öznitelik](#the-clscompliantattribute-attribute) bölümüne bakın.

Aşağıdaki örnekte, bir yöntem imzasında ve genel tür anında cls uyumluluğu sorunu gösteriş göstermektedir. Bu türü `InvoiceItem` [UInt32](xref:System.UInt32)özelliği olan bir sınıf tanımlar, türü Nullable bir özelliği [(UInt32)](xref:System.Nullable%601)ve `UInt32` `Nullable(Of UInt32)`türü parametreleri ile bir yapıcı ve . Bu örneği derlemeye çalıştığınızda dört derleyici uyarısı alırsınız.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

Derleyici uyarılarını ortadan kaldırmak `InvoiceItem` için, genel arabirimdeki CLS uyumlu olmayan türleri uyumlu türlerle değiştirin:

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

Listelenen belirli türlere ek olarak, bazı tür kategorileri CLS uyumlu değildir. Bunlar, yönetilmeyen işaretçi türleri ve işlev işaretçisi türlerini içerir. Aşağıdaki örnek, bir tamsayı dizisi oluşturmak için bir tamsayı işaretçisi kullandığından derleyici uyarısı oluşturur.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

CLS uyumlu soyut sınıflar için (diğer `abstract` bir deyişle, c#olarak işaretlenmiş sınıflar), sınıfın tüm üyeleri de CLS uyumlu olmalıdır.

### <a name="naming-conventions"></a>Adlandırma kuralları

Bazı programlama dilleri büyük/küçük harf duyarlı olduğundan, tanımlayıcılar (ad alanlarının adları, türleri ve üyeleri gibi) büyük/küçük harften daha fazla farklılık gösterir. Küçük eşlemeleri aynıysa, iki tanımlayıcı eşdeğer olarak kabul edilir. Aşağıdaki C# örneği iki ortak `Person` sınıf `person`tanımlar ve . Yalnızca duruma göre farklılık gösterirler, C# derleyicisi bunları CLS uyumlu değil olarak işaretler.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

Ad alanları, türleri ve üyeleri gibi programlama dili tanımlayıcıları [Unicode Standart 3.0, Teknik Rapor 15, Ek 7'ye](https://www.unicode.org/reports/tr15/tr15-18.html)uygun olmalıdır. Bu şu anlama gelir:

* Bir tanımlayıcının ilk karakteri herhangi bir Unicode büyük harf, küçük harf, başlık büyük harf, değiştirici mektup, diğer harf veya harf numarası olabilir. Unicode karakter kategorileri hakkında bilgi için [System.Globalization.UnicodeKategori](xref:System.Globalization.UnicodeCategory) numaralandırma'ya bakın.

* Sonraki karakterler ilk karakter olarak kategorilerden herhangi birinden olabilir ve aralık olmayan işaretleri, işaretleri birleştirme aralığı, ondalık sayılar, bağlayıcı noktalama işaretleri ve biçimlendirme kodlarını da içerebilir.

Tanımlayıcıları karşılaştırmadan önce, biçimlendirme kodlarını filtrelemeniz ve tanımlayıcıları Unicode Normalization Form C'ye dönüştürmeniz gerekir, çünkü tek bir karakter birden çok UTF-16 kodlanmış kod birimi tarafından temsil edilebilir. Unicode Normalization Form C'de aynı kod birimlerini oluşturan karakter dizileri CLS uyumlu değildir. Aşağıdaki örnek, ANGSTROM `Å`SIGN (U+212B) karakterinden oluşan bir özellik ve `Å` LATIN BÜYÜK HARFLİ A RING YU (U+00C5) karakterinden oluşan ikinci bir özelliği tanımlar. C# derleyicisi kaynak kodunu CLS uyumlu olmayan olarak işaretler.

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

Belirli bir kapsamdaki üye adları (derlemedeki ad alanları, ad alanı içindeki türler veya bir tür içindeki üyeler gibi) aşırı yükleme yoluyla çözülen adlar dışında benzersiz olmalıdır. Bu gereksinim, farklı türde üye oldukları sürece kapsam daki birden çok üyenin aynı adlara sahip olmasını sağlayan ortak tür sisteminden daha sıkıdır (örneğin, biri bir yöntem, diğeri bir alandır). Özellikle, tür üyeleri için:

* Alanlar ve iç içe türler tek başına adıyla ayırt edilir.

* Aynı ada sahip yöntemler, özellikler ve olaylar, dönüş türünden daha fazla olmalıdır.

Aşağıdaki örnek, üye adların kendi kapsamları içinde benzersiz olması gereksinimini göstermektedir. Adı geçen dört `Converter` üyeyi içeren `Conversion`bir sınıf tanımlar. Üçü yöntem, biri de bir özellik. Parametre `Int64` içeren yöntem benzersiz adlandırılmış, ancak parametreli `Int32` iki yöntem değildir, çünkü iade değeri üyenin imzasının bir parçası olarak kabul edilmez. Özellikler `Conversion` aşırı yüklenen yöntemlerle aynı ada sahip olamayacağından, özellik de bu gereksinimi ihlal eder.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

Tek tek diller benzersiz anahtar kelimeler içerir, bu nedenle ortak dil çalışma zamanını hedefleyen diller, anahtar kelimelerle çakışan tanımlayıcılara (tür adları gibi) başvurmak için bazı mekanizmalar da sağlamalıdır. Örneğin, `case` hem C# hem de Visual Basic'te kullanılan bir anahtar kelimedir. Ancak, aşağıdaki Visual Basic örneği, açılış ve kapanış `case` ayraçlarını kullanarak `case` anahtar kelimeden adlı bir sınıfı ayrıştırabilir. Aksi takdirde, örnek hata iletisi üretir, "Anahtar kelime tanımlayıcı olarak geçerli değildir" ve derlemek için başarısız.

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

Aşağıdaki C# örneği, tanımlayıcıyı `case` dil anahtar kelimesinden ayrıştırmak için @ simgesini kullanarak sınıfı anında atabiliyor. Bu olmadan, C# derleyicisi iki hata iletisi görüntüler: "Bekleneni yazın" ve "Geçersiz ifade terimi 'büyük/küçük harf'."

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a>Tür dönüştürme

Ortak Dil Belirtimi iki dönüşüm işleci tanımlar:

* `op_Implicit`, veri veya kesinlik kaybına neden olmayan dönüşümleri genişletmek için kullanılır. Örneğin, [Ondalık](xref:System.Decimal) yapı, integral `op_Implicit` türlerinin ve [Char](xref:System.Char) değerlerinin değerlerini `Decimal` değerlere dönüştürmek için aşırı yüklü bir işleç içerir.

* `op_Explicit`, büyüklük kaybına neden olabilecek dönüşümleri daraltmak için kullanılır (bir değer daha küçük aralıklı bir değere dönüştürülür) veya kesinlik. Örneğin, `Decimal` [yapı, Çift](xref:System.Double) ve [Tek](xref:System.Single) değerleri integral değerlerine `Decimal` dönüştürmek `Decimal` ve değerleri `Double`integral `Single`değerlere dönüştürmek için aşırı yüklü `Char` `op_Explicit` bir işleç içerir, ve .

Ancak, tüm diller operatörün aşırı yüklenmesi veya özel işleçlerin tanımını desteklemez. Bu dönüşüm işleçlerini uygulamayı seçerseniz, dönüşümü gerçekleştirmek için alternatif bir yol da sağlamanız gerekir. Xxx ve `To`Xxx `From`yöntemlerini sağlamanızı öneririz.

Aşağıdaki örnek, CLS uyumlu örtülü ve açık dönüşümleri tanımlar. İmzalanmış çift `UDouble` duyarlıklı, kayan nokta numarasını temsil eden bir sınıf oluşturur. `UDouble` Örtülü dönüşümleri, `Double` açık dönüşümlerden `UDouble` `Single`, `Double` `UDouble` `Single` ve . `UDouble` Ayrıca, `ToDouble` bir yöntemi örtülü dönüştürme işlecine alternatif `ToSingle` `FromDouble`olarak `FromSingle` tanımlar ve açık dönüştürme işleçlerine alternatif olarak , ve yöntemleri tanımlar.

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a>Diziler

CLS uyumlu diziler aşağıdaki kurallara uygundur:

* Bir dizinin tüm boyutları sıfırın alt sınırı olmalıdır. Aşağıdaki örnek, daha düşük bir sınıra sahip CLS uyumlu olmayan bir dizi oluşturur. [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği nin varlığına rağmen, derleyici `Numbers.GetTenPrimes` yöntem tarafından döndürülen dizi CLS uyumlu olmadığını algılamaz unutmayın.

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* Tüm dizi öğeleri CLS uyumlu türlerden oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan dizileri döndüren iki yöntem tanımlar. İlk [uint32](xref:System.UInt32) değerleri bir dizi döndürür. İkinci, [Int32](xref:System.Int32) ve `UInt32` değerleri içeren bir [Nesne](xref:System.Object) dizisini döndürür. Derleyici, türü nedeniyle ilk diziyi uyumlu `UInt32` olmayan olarak tanımlasa da, ikinci dizinin CLS uyumlu olmayan öğeler içerdiğini fark edememektedir.

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* Dizi parametreleri olan yöntemler için aşırı yükleme çözünürlüğü, dizi olmaları ve eleman türüne dayanır. Bu nedenle, aşırı yüklü `GetSquares` bir yöntemin aşağıdaki tanımı CLS uyumludur.

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a>Arabirimler

CLS uyumlu arabirimler özellikleri, olayları ve sanal yöntemleri (uygulama olmadan yöntemler) tanımlayabilir. CLS uyumlu bir arabirim aşağıdakilerden herhangi biri olamaz:

* Statik yöntemler veya statik alanlar. Bir arabirimde statik bir üye tanımlarsanız C# derleyicisi derleyici hataları oluşturur.

* Alanları. C# derleyicisi, arabirimdeki bir alanı tanımlarsanız derleyici hataları oluşturur.

* CLS uyumlu olmayan yöntemler. Örneğin, aşağıdaki arabirim tanımı, `INumber.GetUnsigned`CLS uyumlu olmayan olarak işaretlenmiş bir yöntem içerir. Bu örnek derleyici uyarısı oluşturur.

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  Bu kural nedeniyle, CLS uyumlu olmayan üyeleri uygulamak için CLS uyumlu türleri gerekmez. CLS uyumlu bir çerçeve, CLS uyumlu olmayan bir arabirim uygulayan bir sınıfı ortaya çıkarırsa, CLS uyumlu olmayan tüm üyelerin somut uygulamalarını da sağlamalıdır.

CLS uyumlu dil derleyicileri, bir sınıfın birden çok arabirimde aynı ad ve imzaya sahip üyelerin ayrı uygulamalarını sağlamasına da izin vermelidir. C# aynı adlı yöntemlerin farklı uygulamaları sağlamak için açık arabirim uygulamalarını destekler. Aşağıdaki örnek, açık arabirim uygulamaları `Temperature` olarak ve `ICelsius` `IFahrenheit` arabirimleri uygulayan bir sınıf tanımlayarak bu senaryoyu göstermektedir.

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a>Numaralandırmalar

CLS uyumlu sayısallaştırmalar aşağıdaki kurallara uymalıdır:

* Numaralandırmanın altında yatan tip içsel BIR CLS uyumlu bir toplam[(Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), veya [Int64](xref:System.Int64)) olmalıdır. Örneğin, aşağıdaki kod, temel türü [UInt32](xref:System.UInt32) olan bir numaralandırma tanımlamaya çalışır ve derleyici uyarısı oluşturur.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* Bir numaralandırma türü öznitelik ile `Value__` `FieldAttributes.RTSpecialName` işaretlenmiş tek bir örnek alanı adlı olmalıdır. Bu, alan değerini dolaylı olarak referans almanızı sağlar.

* Numaralandırma, türleri numaralandırmanın kendisiyle eşleşen gerçek statik alanları içerir. Örneğin, `State` `State.On` bir numaralandırma ve `State.Off`, her `State.On` `State.Off` ikisi de türü `State`.

* İki tür sayısallaştırma vardır:

  * Birbirini dışlayan, tamsayı değerleri kümesini temsil eden numaralandırma. Bu tür numaralandırma [System.FlagsAttribute](xref:System.FlagsAttribute) özel özniteliği yokluğu ile gösterilir.

  * Adsız bir değer oluşturmak için biraraya getirebilen bit bayrakları kümesini temsil eden numaralandırma. Bu tür numaralandırma [System.FlagsAttribute](xref:System.FlagsAttribute) özel özniteliği varlığı ile gösterilir.

Daha fazla bilgi için [Enum](xref:System.Enum) yapısıiçin belgelere bakın.

* Numaralandırmanın değeri, belirtilen değerlerin aralığıyla sınırlı değildir. Başka bir deyişle, numaralandırmadaki değer aralığı, temel değerinin aralığıdır. Belirtilen değerin `Enum.IsDefined` numaralandırmanın bir üyesi olup olmadığını belirlemek için yöntemi kullanabilirsiniz.

### <a name="type-members-in-general"></a>Genel olarak tip üyeleri

Ortak Dil Belirtimi, tüm alanların ve yöntemlerin belirli bir sınıfın üyesi olarak erişilmesini gerektirir. Bu nedenle, genel statik alanlar ve yöntemler (diğer bir şekilde statik alanlar veya bir tür dışında tanımlanan yöntemler) CLS uyumlu değildir. Kaynak kodunuza genel bir alan veya yöntem eklemeye çalışırsanız, C# derleyicisi bir derleyici hatası oluşturur.

Ortak Dil Belirtimi yalnızca standart yönetilen arama kuralını destekler. `varargs` Anahtar kelimeyle işaretlenmiş değişken bağımsız değişken listeleriyle yönetilmeyen çağrı kurallarını ve yöntemlerini desteklemez. Standart yönetilen arama kuralıyla uyumlu değişken bağımsız değişken listeleri [için, ParamArrayAttribute](xref:System.ParamArrayAttribute) özniteliğini veya `params` C#'daki anahtar `ParamArray` kelime ve Visual Basic'teki anahtar sözcük gibi tek tek dilin uygulamasını kullanın.

### <a name="member-accessibility"></a>Üye erişilebilirliği

Devralınan bir üyenin geçersiz kılınması, bu üyenin erişilebilirliğini değiştiremez. Örneğin, taban sınıftaki ortak yöntem, türemiş bir sınıftaki özel bir yöntem tarafından geçersiz kılınamaz. Bir istisna vardır: `protected internal` (C#' `Protected Friend` da) veya (Visual Basic'te) üye, farklı bir derlemedeki bir tür tarafından geçersiz kılınan bir derlemede.  Bu durumda, geçersiz kılmanın `Protected`erişilebilirliği.

Aşağıdaki örnek, [CLSCompliant Attribute özniteliği](xref:System.CLSCompliantAttribute) ayarlandığında `true`oluşturulan hatayı göstermektedir `Person`ve türetilen bir `Animal`sınıf olan , `Species` özelliğin erişilebilirliğini ortaktan özele değiştirmeye çalışır. Erişilebilirliği genel olarak değiştirilirse, örnek başarıyla derlenir.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

Bir üyenin imzasındaki türlere, bu üyeye erişilebildiğinde erişilebiliyor olmalıdır. Örneğin, bu, ortak bir üyenin türü özel, korumalı veya dahili bir parametre içeremeyeceği anlamına gelir. Aşağıdaki örnekte, bir sınıf oluşturucusu `StringWrapper` dize değerinin nasıl `StringOperationType` paketlendiğini belirleyen bir iç numaralandırma değerini ortaya çıkardığında ortaya çıkan derleyici hatasını gösterilebilir.

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a>Genel türler ve üyeler

İç içe geçmiş türler her zaman en az kendi çevreleyen türü kadar sayıda genel parametreye sahiptir. Bunlar, çevreleyen türdeki genel parametrelere göre konumolarak karşılık gelir. Genel tür, yeni genel parametreler de içerebilir.

İçeren bir türün genel tür parametreleri ile iç içe olan türleri arasındaki ilişki, tek tek dillerin sözdizimi tarafından gizlenmiş olabilir. Aşağıdaki örnekte, genel `Outer<T>` bir tür iki `Inner1A` iç `Inner1B<U>`içe sınıf içerir ve. Her sınıfın `ToString` devraldığı yönteme yapılan `Object.ToString`çağrılar, iç içe geçen her sınıfın kendi sınıfının tür parametrelerini içerdiğini gösterir.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

Genel tür adları form *adı*'*n*, *burada ad* türü *`* adı, bir karakter literal ve *n* türü üzerinde bildirilen parametrelerin sayısı veya iç içe genel türleri için, yeni tanıtılan tür parametrelerinin sayısı kodlanır. Genel tür adlarının bu kodlaması, öncelikle bir kitaplıktaki CLS şikayeti genel türlerine erişmek için yansımayı kullanan geliştiricilerin ilgisini çekmiştir.

Genel bir türe kısıtlamalar uygulanırsa, kısıtlama olarak kullanılan tüm türler de CLS uyumlu olmalıdır. Aşağıdaki örnek, CLS `BaseClass` uyumlu olmayan bir sınıf ve `BaseCollection` tür `BaseClass`parametresi. `BaseClass` Ancak CLS uyumlu olmadığından, derleyici bir uyarı yayar.

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

Genel bir tür genel bir taban türünden türetilmişse, temel türdeki kısıtlamaların da karşılanmasına engel olabilmesi için kısıtlamaları yeniden beyan etmesi gerekir. Aşağıdaki örnek, herhangi `Number<T>` bir sayısal türü temsil eden bir tanım tanımlar. Ayrıca kayan `FloatingPoint<T>` nokta değerini temsil eden bir sınıf tanımlar. Ancak, kaynak kod derlenemiyor, çünkü `Number<T>` `FloatingPoint<T>`bu kısıtlamayı (T'nin bir değer türü olması gerekir) .

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

Kısıtlama `FloatingPoint<T>` sınıfa eklenirse, örnek başarıyla derlenir.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

Ortak Dil Belirtimi iç içe gelen türler ve korunan üyeler için uygun bir anlık hareket modeli uygular. Açık genel türler, iç içe, korumalı genel bir türbelirli bir anlık içeren imzaları olan alanları veya üyeleri ortaya çıkaramaz. Genel bir taban sınıfının veya arabirimin belirli bir anlık anını genişleten genel olmayan türler, iç içe, korunan genel türün farklı bir anlık anlık bir anını içeren imzalarla alanları veya üyeleri ortaya çıkaramaz.

Aşağıdaki örnek, `C1<T>`genel bir türü ve korumalı `C1<T>.N`bir sınıfı tanımlar. `C1<T>`iki yöntemi `M1` vardır `M2`ve . Ancak, `M1` bir `C1<int>.N` nesneyi ' den döndürmeye çalıştığından `C1<T>`CLS uyumlu değildir İkinci sınıf, `C2` `C1<long>`türetilmiştir. İki yöntemi var `M3` `M4`ve. `M3`bir `C1<int>.N` nesneyi bir alt sınıftan döndürmeye çalıştığından `C1<long>`CLS uyumlu değildir. Dil derleyicilerin daha da kısıtlayıcı olabileceğini unutmayın. Bu örnekte, Visual Basic derlemeye çalıştığında `M4`bir hata görüntüler.

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a>Oluşturucular

CLS uyumlu sınıflarda ve yapılardaki kurucular aşağıdaki kurallara uymalıdır:

* Türetilmiş bir sınıfın oluşturucusu, devralınan örnek verilerine erişmeden önce taban sınıfının örnek oluşturucuyu çağırmalıdır. Bu gereksinim, taban sınıf oluşturucuların türetilmiş sınıfları tarafından devralınmaması nedeniyledir. Bu kural, doğrudan devralmayı desteklemeyen yapılar için geçerli değildir.

  Genellikle derleyiciler, aşağıdaki örnekte görüldüğü gibi, bu kuralı CLS uyumluluğundan bağımsız olarak uygular. Bir sınıftan `Doctor` türetilen bir `Person` sınıf oluşturur, `Doctor` ancak sınıf, `Person` devralınan örnek alanlarını başlatmaya sınıf oluşturucusu çağıramaz.

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* Nesne oluşturucu, nesne oluşturmak dışında çağrılamaz. Ayrıca, bir nesne iki kez başharfe alınamaz. Örneğin, bu yapıcılar `Object.MemberwiseClone` çağırmamak gerektiği anlamına gelir.

### <a name="properties"></a>Özellikler

CLS uyumlu türlerdeki özellikler aşağıdaki kurallara uymalıdır:

* Bir özelliğin ayarlayıcısı, bir ayarlayıcısı veya her ikisi de olmalıdır. Bir derlemede, bunlar ayrı yöntemler olarak görünecekleri anlamına gelen özel yöntemler olarak `get` \_uygulanır (alıcıya özellik *adı* verilir ve ayarlayıcı özellik `set` \_ *adıdır)* derlemenin meta verilerinde işaretlenir. `SpecialName` C# derleyicisi özniteliği uygulamaya <xref:System.CLSCompliantAttribute> gerek kalmadan bu kuralı otomatik olarak uygular.

* Bir özelliğin türü, özellik getterinin iade türüdür ve ayarlayıcının son bağımsız değişkenidir. Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler başvuru ile özelliğe atanamaz (diğer bir şekilde, bunlar yönetilemez işaretçileri).

* Bir özelliğin hem getter hem de ayarlayıcısı varsa, her ikisi de sanal, hem statik veya her iki örnek olmalıdır. C# derleyicisi bu kuralı özellik tanımı sözdizimi aracılığıyla otomatik olarak uygular.

### <a name="events"></a>Olaylar

Bir olay, adı ve türüne göre tanımlanır. Olay türü, olayı belirtmek için kullanılan bir temsilcidir. Örneğin, `DbConnection.StateChange` olay türü. `StateChangeEventHandler` Olayın kendisine ek olarak, olay adına dayalı adlara sahip üç yöntem etkinliğin `SpecialName` uygulanmasını sağlar ve derlemenin meta verilerinde olduğu gibi işaretlenir:

* _ `add`*EventName*adlı bir olay işleyicisi ekleme yöntemi. Örneğin, `DbConnection.StateChange` olay için olay abonelik yöntemi `add_StateChange`adlandırılır.

* _ `remove`*EventName*adlı bir olay işleyicisi kaldırmak için bir yöntem . Örneğin, `DbConnection.StateChange` olayın kaldırma yöntemi adlandırılmış. `remove_StateChange`

* Olayın oluştuğunu belirten bir yöntem, `raise` \_ *EventName*adlı .

> [!NOTE]
> Ortak Dil Belirtimi'nin olaylarla ilgili kurallarının çoğu dil derleyicileri tarafından uygulanır ve bileşen geliştiricileri için saydamdır.

Olayı ekleme, kaldırma ve yükseltme yöntemleri aynı erişilebilirlikte olmalıdır. Bunların hepsi statik, örnek veya sanal olmalıdır. Olay ekleme ve kaldırma yöntemlerinin, olay temsilcisi türü olan bir parametresi vardır. Ekleme ve kaldırma yöntemleri nin her ikisi de mevcut olmalı veya her ikisi de bulunmamalıdır.

Aşağıdaki örnek, iki okuma arasındaki sıcaklık `Temperature` değişimi `TemperatureChanged` bir eşik değerine eşit sayılsa veya aşarsa, olayı yükselten CLS uyumlu bir sınıf tanımlar. Sınıf, `Temperature` olay işleyicilerini seçiçle yürütebilmek için bir `raise_TemperatureChanged` metodu açıkça tanımlar.

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a>Aşırı Yüklemeler

Ortak Dil Belirtimi, aşırı yüklü üyelere aşağıdaki gereksinimleri uygular:

* Üyeler, parametrelerin sayısına ve herhangi bir parametrenin türüne göre aşırı yüklenebilir. Arama kuralı, iade türü, yönteme veya parametresine uygulanan özel değiştiriciler ve parametrelerin değer veya referans tarafından geçirilip geçirilemediği, aşırı yükler arasında ayrım yaparken dikkate alınmaz. Örneğin, [Adlandırma kuralları](#naming-conventions) bölümünde ki bir kapsamda adların benzersiz olması gereksiniminin kodunu görün.

* Yalnızca özellikler ve yöntemler aşırı yüklenebilir. Alanlar ve olaylar aşırı yüklenemez.

* Genel yöntemler, genel parametrelerinsayısına bağlı olarak aşırı yüklenebilir.

> [!NOTE]
> Ve `op_Explicit` `op_Implicit` işleçler, iade değerinin aşırı yük çözümü için yöntem imzasının bir parçası olarak kabul edilmeme kuralının istisnalarıdır. Bu iki işleç hem parametrelerine hem de getiri değerine göre aşırı yüklenebilir.

### <a name="exceptions"></a>Özel durumlar

Özel durum nesneleri [System.Exception'dan](xref:System.Exception) veya türetilen `System.Exception`başka bir türden türemelidir. Aşağıdaki örnek, özel durum işleme için özel `ErrorClass` bir sınıf kullanıldığında ortaya çıkan derleyici hatasını göstermektedir.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

Bu hatayı düzeltmek `ErrorClass` için sınıfın `System.Exception`.'den devralması gerekir. Ayrıca, İleti özelliği geçersiz kılınmalıdır. Aşağıdaki örnek, CLS uyumlu `ErrorClass` bir sınıf tanımlamak için bu hataları düzeltir.

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a>Öznitelikler

In.NET Framework derlemeleri, özel öznitelikleri özel öznitelikleri depolamak ve derlemeler, türler, üyeler ve yöntem parametreleri gibi programlama nesneleri hakkında meta veri almak için genişletilebilir bir mekanizma sağlar. Özel öznitelikler [System.Attribute'ten](xref:System.Attribute) veya `System.Attribute`türetilen bir türden türemelidir.

Aşağıdaki örnek bu kuralı ihlal eder. Bu türetilmiştir olmayan bir `NumericAttribute` sınıf `System.Attribute`tanımlar. Derleyici hatasının yalnızca CLS uyumlu olmayan öznitelik uygulandığında, sınıf tanımlandığında değil, sonucu olduğunu unutmayın.

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

CLS uyumlu bir özniteliğin oluşturucu suveya özellikleri yalnızca aşağıdaki türleri ortaya çıkarabilir:

* [Boole](xref:System.Boolean)

* [Bayt](xref:System.Byte)

* [Char](xref:System.Char)

* [Çift](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Tek](xref:System.Single)

* [Dize](xref:System.String)

* [Tür](xref:System.Type)

* Altta yatan `Byte`türü , , `Int16` `Int32`, veya `Int64`.

Aşağıdaki örnek, `DescriptionAttribute` [Atnitelik'ten](xref:System.Attribute)türeyen bir sınıf tanımlar. Sınıf oluşturucu türü bir parametre `Descriptor`vardır, bu nedenle sınıf CLS uyumlu değildir. C# derleyicisinin bir uyarı yayan ancak başarılı bir şekilde derlediğini unutmayın.

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a>CLSCompliantAttribute özniteliği

[CLSCompliantAttribute özniteliği,](xref:System.CLSCompliantAttribute) bir program öğesinin Ortak Dil Belirtimine uyup uymadığını belirtmek için kullanılır. Oluşturucu, `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` program öğesinin CLS uyumlu olup olmadığını gösteren tek bir gerekli parametre, *isCompliant*içerir.

Derleme zamanında derleyici, CLS uyumlu olduğu tahmin edilen uyumlu olmayan öğeleri algılar ve bir uyarı yatar. Derleyici, açıkça uyumsuz olduğu bildirilen türler veya üyeler için uyarı lar yayan değildir.

Bileşen geliştiriciler özniteliği `CLSCompliantAttribute` iki şekilde kullanabilir:

* Ortak arabirimin CLS uyumlu bir bileşen ve CLS uyumlu olmayan bölümleri tarafından maruz kalan bölümlerini tanımlamak için. Özellik, belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, kullanımı bu öğelerin .NET Framework'ünü hedefleyen tüm dil ve araçlardan erişilebilir olduğunu garanti eder.

* Bileşen kitaplığın ortak arabiriminin yalnızca CLS uyumlu program öğelerini ortaya çıkarmasını sağlamak için. Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı yayımlar.

> [!WARNING]
> Bazı durumlarda, dil derleyicileri özniteliğin `CLSCompliantAttribute` kullanılıp kullanılmadığına bakılmaksızın CLS uyumlu kuralları uygular. Örneğin, bir arabirimde bir `*static` üyetanımlamak bir CLS kuralını ihlal eder. Ancak, bir arabirimde bir `*static` üye tanımlarsanız, C# derleyicisi bir hata iletisi görüntüler ve uygulamayı derlemede başarısız olur.

Öznitelik, `CLSCompliantAttribute` değeri . [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) `AttributeTargets.All` Bu değer, özniteliği `CLSCompliantAttribute` derlemeler, modüller, türler (sınıflar, yapılar, arabirimler ve temsilciler), tür üyeleri (oluşturucular, yöntemler, özellikler, alanlar ve olaylar), parametreler, genel parametreler ve iade değerleri dahil olmak üzere herhangi bir program öğesine uygulamanızı sağlar. Ancak, uygulamada, özniteliği yalnızca derlemelere, türlere ve tür üyelerine uygulamanız gerekir. Aksi takdirde, derleyiciler özniteliği yoklar ve kitaplığınızın ortak arabiriminde uyumlu olmayan bir parametre, genel parametre veya iade değeriyle karşılaştıklarında derleyici uyarıları oluşturmaya devam ederler.

Özniteliğin `CLSCompliantAttribute` değeri, içerdiği program öğeleri tarafından devralınR. Örneğin, bir derleme CLS uyumlu olarak işaretlenmişse, türleri de CLS uyumludur. Bir tür CLS uyumlu olarak işaretlenmişse, iç içe olan türleri ve üyeleri de CLS uyumludur.

Özniteliği içerdiği bir program öğesine uygulayarak `CLSCompliantAttribute` devralınan uyumluluğu açıkça geçersiz kılabilirsiniz. Örneğin, uyumlu olmayan `CLSCompliantAttribute` bir derlemede uyumlu olmayan `false` bir türü tanımlamak için *isCompliant* değerine sahip özniteliği kullanabilir *isCompliant* ve uyumlu `true` olmayan bir derlemede uyumlu bir türü tanımlamak için uyumlu bir değere sahip özniteliği kullanabilirsiniz. Uyumlu olmayan üyeleri uyumlu bir türde de tanımlayabilirsiniz. Ancak, uyumlu olmayan bir tür uyumlu üyeleri olamaz, bu nedenle uyumlu olmayan `true` bir tür devralma geçersiz kılmak için bir *isCompliant* değeri ile özniteliği kullanamazsınız.

Bileşenler geliştirirken, derlemenizin, `CLSCompliantAttribute` türlerinin ve üyelerinin CLS uyumlu olup olmadığını belirtmek için özniteliği her zaman kullanmanız gerekir.

CLS uyumlu bileşenler oluşturmak için:

1. Montajını `CLSCompliantAttribute` CLS uyumlu olarak işaretlemek için kullanın.

2. Derlemede, CLS uyumlu olmayan tüm genel olarak açıklanmış türleri uyumlu olmayan olarak işaretleyin.

3. CLS uyumlu türdeki herkese açık üyeleri uyumlu olmayan olarak işaretleyin.

4. CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlayın.

Tüm uyumlu olmayan türlerinizi ve üyelerinizi başarıyla işaretlediyseniz, derleyiciniz herhangi bir uyumsuzluk uyarısı yaslanmamalıdır. Ancak, hangi üyelerin CLS uyumlu olmadığını belirtmeli ve ürün belgelerinizde CLS uyumlu alternatiflerini listelemelisiniz.

Aşağıdaki örnek, `CLSCompliantAttribute` CLS uyumlu olmayan iki üyesi olan bir `CharacterUtilities`CLS uyumlu derleme ve bir tür tanımlamak için özniteliği kullanır. Her iki üye de `CLSCompliant(false)` öznitelik ile etiketlenmiş olduğundan, derleyici hiçbir uyarı üretir. Sınıf ayrıca her iki yöntem için cls uyumlu bir alternatif sağlar. Normalde, CLS uyumlu alternatifler sağlamak için `ToUTF16` yönteme iki aşırı yükleme ekleriz. Ancak, yöntemler iade değerine göre aşırı yüklenemediğinden, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklıdır.

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

Kitaplık yerine bir uygulama geliştiriyorsanız (diğer bir deyişle, diğer uygulama geliştiricileri tarafından tüketilebilen türleri veya üyeleri ifşa etmiyorsanız), uygulamanızın tükettiği program öğelerinin CLS uyumluluğu yalnızca diliniz bunları desteklemiyorsa ilgi nizi çekebilir . Bu durumda, CLS uyumlu olmayan bir öğekullanmaya çalıştığınızda dil derleyiciniz bir hata oluşturur.

## <a name="cross-language-interoperability"></a>Diller Arası Birlikte Çalışabilirlik

Dil bağımsızlığının birkaç olası anlamı vardır. Bir anlam, başka bir dilde yazılmış bir uygulamadan bir dilde yazılmış türleri sorunsuz bir şekilde tüketmeiçerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.

Aşağıdaki örnekte, Iki sınıf içeren Utilities.dll adlı bir sınıf kitaplığı `NumericLib` oluşturarak diller arası birlikte çalışabilirlik ve `StringLib`. Sınıf `NumericLib` C# ile yazılır ve `StringLib` sınıf Visual Basic ile yazılır. Burada, sınıfında `StringUtil.vb` `ToTitleCase` `StringLib` tek bir üye içeren kaynak kodu vebu kod vardır.

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

İki sınıfı tek bir derlemede paketlemek için bunları modüller halinde derlemeniz gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
vbc /t:module StringUtil.vb
```

C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
csc /t:module NumberUtil.cs
```

Daha sonra iki modülü derlemek için Bağlantı aracını (Link.exe) kullanırsınız:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Aşağıdaki örnek daha `NumericLib.NearZero` sonra `StringLib.ToTitleCase` çağırır ve yöntemleri. Hem Visual Basic kodunun hem de C# kodunun her iki sınıftaki yöntemlere erişebildiğini unutmayın.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

Visual Basic kodunu derlemek için bu komutu kullanın:

```console
vbc example.vb /r:UtilityLib.dll
```

C# ile derlemek için derleyicinin adını vbc'den csc'ye değiştirin ve dosya uzantısını .vb.'den .cs'ye değiştirin:

```console
csc example.cs /r:UtilityLib.dll
```
