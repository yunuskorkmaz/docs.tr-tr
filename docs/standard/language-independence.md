---
title: Dil bağımsızlığı ve dilden bağımsız bileşenler
description: ".NET ' te C#, C++/CLı, F #, IronPython, VB, Visual COBOL ve PowerShell gibi birçok desteklenen dilden birinde nasıl geliştirme yapabileceğinizi öğrenin."
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 813558299b40e0b90e8047f22b788c8f1419eb5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504660"
---
# <a name="language-independence-and-language-independent-components"></a>Dil bağımsızlığı ve dilden bağımsız bileşenler

.NET dilden bağımsız. Yani, geliştirici olarak C#, F # ve Visual Basic gibi .NET uygulamalarını hedefleyen birçok dilden birinde geliştirme yapabilirsiniz. .NET uygulamaları için geliştirilmiş sınıf kitaplıklarının türlerine ve üyelerine, ilk olarak yazıldığı dili ve özgün dilin kurallarından herhangi birini izlemeniz gerekmeden erişebilirsiniz. Bileşen geliştiricisiyseniz, kendi dilinden bağımsız olarak, bileşeninize herhangi bir .NET uygulaması tarafından erişilebilir.

> [!NOTE]
> Bu makalenin ilk bölümünde dilden bağımsız bileşenler, diğer bir deyişle, herhangi bir dilde yazılmış uygulamalar tarafından tüketilen bileşenler oluşturma işlemi ele alınmaktadır. Ayrıca, birden çok dilde yazılmış kaynak kodundan tek bir bileşen veya uygulama oluşturabilirsiniz; Bu makalenin ikinci bölümünde [Diller arası birlikte çalışabilirlik](#cross-language-interoperability) bölümüne bakın.

Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşimde bulunmak için, nesneler yalnızca tüm diller için ortak olan özellikleri çağıranlar halinde kullanıma sunmalıdır. Bu ortak özellikler kümesi, oluşturulan derlemeler için uygulanan bir dizi kural olan ortak dil belirtimi (CLS) tarafından tanımlanır. Ortak dil belirtimi, [ECMA-335 Standardı: ortak dil altyapısının](https://www.ecma-international.org/publications/standards/Ecma-335.htm), Bölüm ı, yan tümceler 7 ila 11 ' de tanımlanmıştır.

Bileşeniniz Ortak dil belirtimine uyuyorsa, CLS uyumlu olması garantilenir ve CLS 'yi destekleyen herhangi bir programlama dilinde yazılan derlemelerdeki koddan erişilebilir. Kaynak kodunuza [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini uygulayarak, bileşeninizin derleme zamanında ortak dil belirtimine uygun olup olmadığını belirleyebilirsiniz. Daha fazla bilgi için bkz. [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute).

## <a name="cls-compliance-rules"></a>CLS Uyumluluk kuralları

Bu bölümde, CLS uyumlu bir bileşen oluşturmak için kurallar açıklanmaktadır. Kuralların tam bir listesi için, bkz. [ECMA-335 standart: ortak dil altyapısının](https://www.ecma-international.org/publications/standards/Ecma-335.htm)bölüm ı, yan tümcesi 11.

> [!NOTE]
> Ortak dil belirtimi, tüketiciler (CLS uyumlu bir bileşene programlı olarak erişen geliştiriciler), çerçeveler (CLS uyumlu kitaplıklar oluşturmak için bir dil derleyicisi kullanan geliştiriciler) ve Extender 'lar (bir dil derleyicisi veya CLS uyumlu bileşenler oluşturan bir kod ayrıştırıcısı gibi bir araç oluşturan geliştiriciler) için geçerli olduğu için her bir kuralı CLS uyumluluğu için tartışır. Bu makale, çerçeveler için uygulanan kurallara odaklanır. Ancak, Extender 'lara uygulanan kuralların bazılarının, [yansıma. yayma](xref:System.Reflection.Emit)kullanılarak oluşturulan derlemeler için de uygulanabilir olabileceğini unutmayın.

Dilden bağımsız bir bileşen tasarlamak için, yalnızca bileşenin ortak arabirimine CLS uyumluluğu için kuralları uygulamanız gerekir. Özel uygulamanızın belirtimine uyması gerekmez.

> [!IMPORTANT]
> CLS uyumluluğu kuralları yalnızca bileşenin ortak arabirimine uygulanır, özel uygulamasına uygulanmaz.

Örneğin, [bayt](xref:System.Byte) dışındaki IŞARETSIZ tamsayılar CLS uyumlu değildir. `Person`Aşağıdaki örnekteki sınıf `Age` [UInt16](xref:System.UInt16)türünde bir özelliği kullanıma sunduğundan, aşağıdaki kod bir derleyici uyarısı görüntüler.

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

Özelliğin türünü, `Age` `UInt16` CLS uyumlu, 16 bit işaretli bir tamsayı olan [Int16](xref:System.Int16)sürümüne DEĞIŞTIREREK, kişi sınıfını CLS uyumlu hale getirebilirsiniz. Özel alanın türünü değiştirmek zorunda değilsiniz `personAge` .

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

Kitaplığın ortak arabirimi aşağıdakilerden oluşur:

* Ortak sınıfların tanımları.

* Ortak sınıfların genel üyelerinin ve türetilmiş sınıfların erişebileceği üyelerin tanımlarının tanımları (yani, korumalı üyeler).

* Ortak sınıfların ortak yöntemlerinin parametreleri ve dönüş türleri, parametreleri ve türetilmiş sınıflar tarafından erişilebilen yöntemlerin dönüş türleri.

CLS uyumluluğu kuralları aşağıdaki tabloda listelenmiştir. Kuralların metni, telif hakkı 2012 olan [ECMA-335 Standardı: ortak dil altyapısından](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(Ecma International göre) alınır. Bu kurallar hakkında daha ayrıntılı bilgi aşağıdaki bölümlerde bulunur.

Kategori | Bkz. | Kural | Kural numarası
-------- | --- | ---- | -----------
Erişilebilirlik | [Üye erişilebilirliği](#member-accessibility) | Erişilebilirlik ile farklı bir derlemeden devralınan bir yöntemi geçersiz kılmanın dışında, devralınan Yöntemler geçersiz kılınırken erişilebilirlik değiştirilmez `family-or-assembly` . Bu durumda, geçersiz kılma erişilebilirliği olacaktır `family` . | 10
Erişilebilirlik | [Üye erişilebilirliği](#member-accessibility) | Türlerin ve üyelerin görünürlüğü ve erişilebilirliği, üyenin görünür ve erişilebilir olduğu her üyenin İmzasındaki türlerin görünür ve erişilebilir olması gibi olacaktır. Örneğin, kendi derlemesi dışında görünen bir genel yöntem, türü yalnızca derleme içinde görünür olan bir bağımsız değişkene sahip olamaz. Herhangi bir Üyenin imzasında kullanılan bir örneklenmiş genel tür oluşturan türlerin görünürlüğü ve erişilebilirliği, üyenin görünür ve erişilebilir olduğu her durumda görünür ve erişilebilir olur. Örneğin, kendi derlemesi dışında görünen bir Üyenin imzasında bulunan bir örneklenmiş genel tür, türü yalnızca derleme içinde görünür olan genel bir bağımsız değişkene sahip olamaz. | 12
Diziler | [Diziler](#arrays) | Diziler CLS uyumlu bir türe sahip öğeler içermelidir ve dizinin tüm boyutları daha düşük sınırlara sahip olacaktır. Yalnızca bir öğenin dizi olması ve dizinin öğe türü, aşırı yüklemeleri ayırt etmek için gerekli olacaktır. Aşırı yükleme iki veya daha fazla dizi türünü temel alarak, öğe türleri adlandırılmış türler olacaktır. | 16
Öznitelikler | [Öznitelikler](#attributes) | Öznitelikler [System. Attribute](xref:System.Attribute)türünde ya da bundan devralan bir tür olmalıdır. | 41
Öznitelikler | [Öznitelikler](#attributes) | CLS yalnızca özel özniteliklerin kodlamalarının bir alt kümesine izin verir. Bu kodlarda görünen türler (bkz. Partition IV): [System. Type](xref:System.Type), [System. String](xref:System.String), [System. Char](xref:System.Char), [System. Boolean](xref:System.Boolean), [System. Byte](xref:System.Byte), [System. Int16](xref:System.Int16), [System. Int32](xref:System.Int32), [System. Int64](xref:System.Int64), System. [Single](xref:System.Single), [System. Double](xref:System.Double)ve CLS uyumlu bir taban tamsayı türüne göre herhangi bir numaralandırma türü. | 34
Öznitelikler | [Öznitelikler](#attributes) | CLS, herkese açık bir şekilde görünür gerekli değiştiricilere izin vermez (bkz. `modreq` Bölüm II), ancak isteğe bağlı değiştiricilere izin veriyor ( `modopt` , bkz. Bölüm II). | 35
Oluşturucular | [Oluşturucular](#constructors) | Bir nesne Oluşturucusu, devralınan örnek verilerine herhangi bir erişim gerçekleşmeden önce temel sınıfının bazı örnek oluşturucusunu çağırmalıdır. (Bu, oluşturucuların olmaması gereken değer türleri için de geçerlidir.)  | 21
Oluşturucular | [Oluşturucular](#constructors) | Bir nesne Oluşturucusu, bir nesne oluşturmanın parçası hariç çağrılmamalıdır ve bir nesne iki kez başlatılamaz. | 22
Numaralandırmalar | [Numaralandırmalar](#enumerations) | Bir numaralandırmanın temel alınan türü yerleşik bir CLS tamsayı türü olacaktır, alanın adı "value__" ve bu alan işaretlenir `RTSpecialName` . |  7
Numaralandırmalar | [Numaralandırmalar](#enumerations) | [System. FlagsAttribute](xref:System.FlagsAttribute) (Bölüm IV kitaplığı) özel özniteliğinin varlığı veya yokluğu tarafından belirtilen iki farklı tür numaralandırmalar vardır. Biri adlandırılmış tamsayı değerlerini temsil eder; diğeri adlandırılmamış bir değer oluşturmak için birleştirilebilen adlandırılmış bit bayraklarını temsil eder. Öğesinin değeri `enum` belirtilen değerlerle sınırlı değil. |  8
Numaralandırmalar | [Numaralandırmalar](#enumerations) | Sabit listesinin değişmez statik alanları, sabit listesinin kendi türüne sahip olacaktır. |  9
Ekinlikler | [Ekinlikler](#events) | Bir olayı uygulayan yöntemler `SpecialName` meta verilerde işaretlenir. |29
Ekinlikler | [Ekinlikler](#events) | Bir olayın ve erişimcilerinin erişilebilirliği aynı olacaktır. |30
Ekinlikler | [Ekinlikler](#events) | `add` `remove` Bir olay için ve yöntemlerinin her ikisi de mevcut ya da yok olacaktır. |31
Ekinlikler | [Ekinlikler](#events) | `add` `remove` Bir olay için ve yöntemlerinin her biri, türü olay türünü tanımlayan ve [System. Delegate](xref:System.Delegate)'ten türetilebilecek bir parametre alır. |32
Ekinlikler | [Ekinlikler](#events) | Olaylar belirli bir adlandırma düzenine bağlı olacaktır. CLS kuralı 29 ' da başvurulan SpecialName özniteliği, uygun ad karşılaştırmaları içinde yok sayılacak ve tanımlayıcı kurallarına uymalecektir.  |33
Özel durumlar | [Özel durumlar](#exceptions) | Oluşturulan nesneler [System. Exception](xref:System.Exception) veya bundan devralan bir tür olmalıdır. Nonetheless, diğer özel durum türlerinin yayılmasını engellemek için CLS uyumlu yöntemler gerekli değildir. | 40
Genel | [CLS Uyumluluk kuralları](#cls-compliance-rules) | CLS kuralları yalnızca, tanımlayıcı derlemenin dışında erişilebilen veya görülebilen bir türün bölümleri için geçerlidir. | 1
Genel | [CLS Uyumluluk kuralları](#cls-compliance-rules) | CLS olmayan uyumlu türlerin üyeleri CLS uyumlu olarak işaretlenmemelidir. | 2
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | İç içe türler, kapsayan tür olarak en az sayıda genel parametreye sahip olacaktır. İç içe bir türdeki genel parametreler, kapsayan türünün genel parametrelerine konum ile karşılık gelir.  | 42
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Genel bir türün adı, iç içe olmayan türde belirtilen tür parametrelerinin sayısını kodlayıp, yukarıda tanımlanan kurallara göre iç içe geçmiş tür parametrelerinin yeni tanıtılmasıyla belirtilir. | 43
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Genel bir tür, temel türdeki kısıtlamaların veya arabirimlerin genel tür kısıtlamaları tarafından karşılanabileceğini güvence altına almak için yeterli kısıtlamaları yeniden bildirir. | 44
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Genel parametrelerde kısıtlama olarak kullanılan türler, CLS uyumlu olacaktır. | 45
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Bir örneklenmiş genel türdeki üyelerin görünürlük ve erişilebilirliği, bir bütün olarak genel tür bildirimi yerine belirli bir örnek oluşturma kapsamına alınır. Bunun varsayılarak, CLS kuralı 12 ' nin görünürlük ve erişilebilirlik kuralları hala geçerlidir. | 46
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Her soyut veya sanal genel yöntem için, varsayılan bir somut (soyut olmayan) uygulama olacaktır | 47
Arabirimler | [Arabirimler](#interfaces) | CLS uyumlu arabirimler, CLS uyumlu olmayan yöntemlerin uygulanması için tanımı gerektirmez. | 18
Arabirimler | [Arabirimler](#interfaces) | CLS uyumlu arabirimler statik yöntemler tanımlamaz ve alanları tanımlayamazlar. | 19
Üyeler | [Genel olarak tür üyeleri](#type-members-in-general) | Genel statik alanlar ve yöntemler CLS uyumlu değildir. | 36
Üyeler | -- | Bir sabit değer statik değeri, alan başlatma meta verilerinin kullanımı aracılığıyla belirtilir. CLS uyumlu bir sabit değeri, alan başlatma meta verilerinde tam olarak aynı türde (ya da değişmez değer ise) bir değere sahip olmalıdır `enum` . | 13
Üyeler | [Genel olarak tür üyeleri](#type-members-in-general) | Vararg kısıtlaması CLS kapsamında değildir ve CLS tarafından desteklenen tek çağırma kuralı Standart yönetilen çağırma kuralıdır. | 15
Adlandırma kuralları | [Adlandırma kuralları](#naming-conventions) | Derlemeler, [Unicode normalleştirme formlarında](https://unicode.org/reports/tr15/)çevrimiçi olarak kullanılabilir olan ve tanımlayıcılara dahil edilip edilmelerine izin verilen karakter kümesini yöneten Unicode standart 3.0 'ın ek 7 Technical Report 15 ' i izlemelidir. Tanımlayıcılar Unicode normalleştirme biçimi C tarafından tanımlanan kurallı biçimde olacaktır. CLS amacıyla, küçük harfli eşlemelerde (Unicode yerel ayarı duyarsız, bire bir küçük harf eşleştirmelerde belirtildiği gibi) iki tanımlayıcı aynıdır. Diğer bir deyişle, iki tanımlayıcı CLS kapsamında farklı olarak kabul edilmelidir, ancak büyük küçük harf bakımından farklılık gösterir. Ancak, devralınan bir tanımı geçersiz kılmak için CLı, özgün bildirimin kesin kodlamasının kullanılmasını gerektirir. | 4
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | CLS uyumlu bir kapsamda sunulan tüm adlar, adların özdeş ve aşırı yükleme yoluyla çözümlenme dışında, türden bağımsız olacaktır. Diğer bir deyişle, CTS tek bir türün bir yöntem ve bir alan için aynı adı kullanmasına izin veriyorsa, CLS değildir. | 5
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | CTS ayrı imzaların ayırt etmesine izin verdiğinden bağımsız olarak, alanlar ve iç içe türler tanımlayıcı karşılaştırmaya göre birbirinden ayrı olacaktır. Aynı ada (tanımlayıcı karşılaştırmaya göre) sahip Yöntemler, Özellikler ve olaylar, CLS kuralı 39 ' de belirtilmedikçe, yalnızca dönüş türünden daha fazla farklı olacaktır. | 6
Aşırı Yükleme | [Aşırı Yüklemeler](#overloads) | Yalnızca özellikler ve yöntemler aşırı yüklenebilir. | 37
Aşırı Yükleme | [Aşırı Yüklemeler](#overloads) |Özellikler ve yöntemler yalnızca parametrelerinin sayısı ve türleri temel alınarak aşırı yüklenebilir, ve adlı dönüştürme işleçleri, `op_Implicit` `op_Explicit` dönüş türlerine göre de aşırı yüklenebilir. | 38
Aşırı Yükleme | -- | Bir tür içinde belirtilen iki veya daha fazla CLS uyumlu Yöntem aynı ada sahiptir ve belirli bir tür örneklemesiyse, aynı parametre ve dönüş türlerine sahiptirler, tüm bu yöntemler bu tür örneklemelerinden anlam açısından eşdeğerdir. | 48
Özellikler | [Özellikler](#properties) | Bir özelliğin alıcı ve ayarlayıcı yöntemlerini uygulayan yöntemler `SpecialName` meta verilerde işaretlenir. | 24
Özellikler | [Özellikler](#properties) | Bir özelliğin erişimcileri statik, hepsi sanal veya hepsi örnek olmalıdır. | 26
Özellikler | [Özellikler](#properties) | Bir özelliğin türü, alıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türü olacaktır. Özelliğin parametre türleri, alıcı parametrelerinin türleri ve ayarlayıcının son parametresi hariç tüm türleri olacaktır. Bu türlerin hepsi CLS uyumlu olur ve yönetilen işaretçiler olmaz (yani, başvuruya göre geçirilmemelidir). | 27
Özellikler | [Özellikler](#properties) | Özellikler belirli bir adlandırma düzenine bağlı olacaktır. `SpecialName`CLS kuralı 24 ' te başvuruda bulunulan öznitelik, uygun ad karşılaştırmaları içinde yok sayılacak ve tanımlayıcı kurallarına uymalecektir. Bir özelliğin alıcı yöntemi, ayarlayıcı yöntemi veya her ikisi de olmalıdır. | 28
Tür dönüştürme | [Tür dönüştürme](#type-conversion) | Op_Implicit veya op_Explicit sağlandıysa, zorlama sağlamak için alternatif bir yol sağlanmalıdır. | 39
Türler | [Türler ve tür üye imzaları](#types-and-type-member-signatures) | Paketlenmiş değer türleri CLS uyumlu değildir. | 3
Türler | [Türler ve tür üye imzaları](#types-and-type-member-signatures) | Bir imzada görünen tüm türler CLS uyumlu olacaktır. Örneklenmiş genel bir tür oluşturan tüm türler CLS uyumlu olacaktır. | 11
Türler | [Türler ve tür üye imzaları](#types-and-type-member-signatures) | Yazılan başvurular CLS uyumlu değildir. | 14
Türler | [Türler ve tür üye imzaları](#types-and-type-member-signatures) | Yönetilmeyen işaretçi türleri CLS uyumlu değildir. | 17
Türler | [Türler ve tür üye imzaları](#types-and-type-member-signatures) | CLS uyumlu sınıflar, değer türleri ve arabirimler, CLS uyumlu olmayan üyelerin uygulanmasını gerektirmez | 20
Türler | [Türler ve tür üye imzaları](#types-and-type-member-signatures) | [System. Object](xref:System.Object) CLS uyumludur. Diğer CLS uyumlu sınıflar, CLS uyumlu bir sınıftan devralınır. | 23

Alt bölümleri dizine:

* [Türler ve tür üye imzaları](#types-and-type-member-signatures)
* [Adlandırma kuralları](#naming-conventions)
* [Tür dönüştürme](#type-conversion)
* [Diziler](#arrays)
* [Arabirimler](#interfaces)
* [Numaralandırmalar](#enumerations)
* [Genel olarak tür üyeleri](#type-members-in-general)
* [Üye erişilebilirliği](#member-accessibility)
* [Genel türler ve Üyeler](#generic-types-and-members)
* [Oluşturucular](#constructors)
* [Özellikler](#properties)
* [Ekinlikler](#events)
* [Aşırı Yüklemeler](#overloads)
* [Özel durumlar](#exceptions)
* [Öznitelikler](#attributes)

### <a name="types-and-type-member-signatures"></a>Türler ve tür üye imzaları

[System. Object](xref:System.Object) türü CLS uyumludur ve .NET Framework türü sistemindeki tüm nesne türlerinin temel türüdür. .NET Framework devralma örtük olarak (örneğin, [dize](xref:System.String) sınıfı dolaylı olarak `Object` sınıftan devralır) veya açık (örneğin, [Kültürenotfoundexception](xref:System.Globalization.CultureNotFoundException) sınıfı açıkça [özel durum](xref:System.Exception) sınıfından devralınan [ArgumentException](xref:System.ArgumentException) sınıfından devralır. Türetilmiş bir türün CLS uyumlu olması için, taban türünün de CLS uyumlu olması gerekir.

Aşağıdaki örnek, temel türü CLS uyumlu olmayan türetilmiş bir türü gösterir. `Counter`İşaretsiz 32 bitlik bir tamsayıyı sayaç olarak kullanan bir temel sınıf tanımlar. Sınıfı işaretsiz bir tamsayı sarmalayarak sayaç işlevselliği sağladığından, sınıf CLS uyumlu değil olarak işaretlenir. Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter` de CLS uyumlu değildir.

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

Bir yöntemin dönüş türü veya özellik türü de dahil olmak üzere üye imzalarında görünen tüm türler CLS uyumlu olmalıdır. Bunlara ek olarak, genel türler için:

* Bir örneklenmiş genel tür oluşturan tüm türler CLS uyumlu olmalıdır.

* Genel parametrelerde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır.

.NET [ortak tür sistemi](common-type-system.md) , doğrudan ortak dil çalışma zamanı tarafından desteklenen ve bir derlemenin meta verilerinde özel olarak kodlanmış bir dizi yerleşik tür içerir. Bu iç türlerin, aşağıdaki tabloda listelenen türler CLS uyumludur.

CLS uyumlu tür | Description
------------------ | -----------
[Bayt](xref:System.Byte) | 8 bit işaretsiz tamsayı
[Int16](xref:System.Int16) | 16 bit işaretli tamsayı
[Int32](xref:System.Int32) | 32-bit işaretli tamsayı
[Tutulamaz](xref:System.Int64) | 64-bit işaretli tamsayı
[Tek](xref:System.Single) | Tek duyarlıklı kayan nokta değeri
[Çift](xref:System.Double) | Çift duyarlıklı kayan nokta değeri
[Boole](xref:System.Boolean) | doğru veya yanlış değer türü
[Char](xref:System.Char) | UTF-16 kodlu kod birimi
[Kategori](xref:System.Decimal) | Kayan nokta olmayan ondalık sayı
[Serisi](xref:System.IntPtr) | Platform tanımlı boyutun işaretçisi veya işleyicisi
[Dize](xref:System.String) | Sıfır, bir veya daha fazla Char nesnesi koleksiyonu

Aşağıdaki tabloda listelenen iç türler CLS uyumlu değildir.

Uyumlu olmayan tür | Description | CLS uyumlu alternatif
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | 8 bit işaretli tamsayı veri türü | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16 bit işaretsiz tamsayı | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32-bit işaretsiz tamsayı | [Tutulamaz](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64-bit işaretsiz tamsayı | [Int64](xref:System.Int64) (taşma olabilir), [BigInteger](xref:System.Numerics.BigInteger)veya [Double](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | İşaretsiz işaretçi veya tanıtıcı | [Serisi](xref:System.IntPtr)

.NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı CLS uyumlu olmayan diğer türleri içerebilir; Örneğin:

* Paketlenmiş değer türleri. Aşağıdaki C# örneği, adında ortak bir özelliği olan bir sınıf oluşturur `int*` `Value` . Bir `int*` paketlenmiş değer türü olduğundan, derleyici onu CLS uyumlu değil olarak işaretler.

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

* Bir nesneye başvuru ve bir tür başvurusu içeren özel yapılar olan yazılı başvurular.

Bir tür CLS uyumlu değilse, [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini değerine sahip bir *ısuyumlu* parametresiyle uygulamanız gerekir `false` . Daha fazla bilgi için [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute) bölümüne bakın.

Aşağıdaki örnek, bir yöntem imzasında ve genel tür örnek oluşturmada CLS uyumluluğu sorununu göstermektedir. `InvoiceItem` [UInt32](xref:System.UInt32)türünde bir özelliği olan bir sınıfı, [null atanabilir](xref:System.Nullable%601)türünde bir özelliği ve ve türünde parametreleri olan bir oluşturucuyu tanımlar `UInt32` `Nullable(Of UInt32)` . Bu örneği derlemeye çalıştığınızda dört derleyici uyarısı alırsınız.

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

Derleyici uyarılarını ortadan kaldırmak için, ortak arabirimdeki CLS uyumlu olmayan türleri `InvoiceItem` uyumlu türler ile değiştirin:

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

Listelenen belirli türlere ek olarak, bazı tür kategorileri CLS uyumlu değildir. Bunlar, yönetilmeyen işaretçi türlerini ve işlev işaretçisi türlerini içerir. Aşağıdaki örnek bir derleyici uyarısı oluşturur çünkü bir tamsayılar dizisi oluşturmak için bir tamsayı işaretçisi kullanır.

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

CLS uyumlu soyut sınıflar (yani, C# dilinde olarak işaretlenen sınıflar `abstract` ) için, sınıfın tüm üyeleri de CLS uyumlu olmalıdır.

### <a name="naming-conventions"></a>Adlandırma kuralları

Bazı programlama dilleri büyük/küçük harf duyarsız olduğundan, tanımlayıcılar (ad alanları, türler ve Üyeler adları gibi) büyük/küçük harf bakımından farklı olmalıdır. Küçük harfler aynı ise, iki tanımlayıcı eşit kabul edilir. Aşağıdaki C# örneği, ve olmak üzere iki ortak sınıfı tanımlar `Person` `person` . Yalnızca büyük/küçük harf bakımından farklı olduğundan, C# derleyicisi bunları CLS uyumlu değil olarak işaretler.

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

Ad alanları, türler ve üyelerin adları gibi programlama Dil tanımlayıcıları, [Unicode standardına](https://unicode.org/reports/tr15/)uygun olmalıdır. Bunun anlamı:

* Bir tanımlayıcının ilk karakteri herhangi bir Unicode büyük harf, küçük harf, başlık harf harf, değiştirici harf, diğer harf veya harf numarası olabilir. Unicode karakter kategorileri hakkında daha fazla bilgi için bkz. [System. Globalization. UnicodeCategory](xref:System.Globalization.UnicodeCategory) sabit listesi.

* Sonraki karakterler, ilk karakter olarak kategorilerden herhangi birinden olabilir ve Aralık olmayan işaretleri, boşluk birleştirme işaretlerini, ondalık sayıları, bağlayıcı noktalama işaretlerini ve biçimlendirme kodlarını da içerebilir.

Tanımlayıcıları karşılaştırmadan önce, tek bir karakter birden çok UTF-16 kodlu kod birimi ile temsil edilebilmesi için biçimlendirme kodlarını filtrelemeniz ve tanımlayıcıları Unicode normalleştirme biçimi C 'ye dönüştürmeniz gerekir. Unicode normalleştirme biçimi C 'de aynı kod birimlerini üreten karakter dizileri CLS uyumlu değildir. Aşağıdaki örnek, `Å` ANGSTROM işareti (u + 212B) karakterini içeren adlı özelliği ve `Å` LATIN büyük harf a 'Yı yukarıdaki halka (u + 00C5) karakteriyle oluşan ikinci bir özelliği tanımlar. C# derleyicisi, kaynak kodu CLS uyumlu değil olarak işaretler.

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

Belirli bir kapsamdaki üye adları (derleme içindeki ad alanları, bir ad alanı içindeki türler veya bir tür içindeki Üyeler), aşırı yükleme yoluyla çözümlenen adlar dışında benzersiz olmalıdır. Bu gereksinim, bir kapsamdaki birden çok üyenin farklı üye türleri oldukları sürece (örneğin, bir yöntem ve biri bir alandır) aynı adlara sahip olmasını sağlayan ortak tür sisteminden daha sıkı bir yöntemdir. Özellikle, tür üyeleri için:

* Alanlar ve iç içe türler yalnızca ada göre ayırt edilir.

* Aynı ada sahip Yöntemler, Özellikler ve olaylar, yalnızca dönüş türünden daha fazla farklı olmalıdır.

Aşağıdaki örnekte, üye adlarının kapsamları dahilinde benzersiz olması gereken gereksinim gösterilmektedir. Adında dört üye içeren adlı bir sınıfı tanımlar `Converter` `Conversion` . Üç yöntem ve biri bir özelliktir. Bir parametre içeren Yöntem `Int64` benzersiz olarak adlandırılır, ancak `Int32` dönüş değeri bir üyenin imzasının bir parçası olarak değerlendirilmediğinden parametre ile iki yöntem değildir. `Conversion`Özellikler, aşırı yüklenmiş yöntemlerle aynı ada sahip olmadığından, bu gereksinimi da ihlal ediyor.

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

Tek dillerde benzersiz anahtar sözcükler bulunur, bu nedenle ortak dil çalışma zamanını hedefleyen dillerin, anahtar sözcüklerle birlikte bulunan tanımlayıcılara (tür adları gibi) başvurmak için bazı mekanizmalar de sağlaması gerekir. Örneğin, `case` hem C# hem de Visual Basic bir anahtar sözcüktür. Ancak, aşağıdaki Visual Basic örnek, `case` `case` açma ve kapatma küme ayraçlarını kullanarak anahtar sözcükten adlı bir sınıfın ayırt edebilmesini sağlar. Aksi takdirde, örnek hata iletisi üretir, "anahtar sözcüğü tanımlayıcı olarak geçerli değildir" ve derleme başarısız olur.

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

Aşağıdaki C# örneği, `case` Language anahtar sözcüğünden tanımlayıcıyı ayırt etmek için @ sembolünü kullanarak sınıfın örneğini oluşturabilir. Bu olmadan, C# derleyicisi iki hata iletisi görüntüler, "tür bekleniyor" ve "geçersiz ifade terimi ' Case '."

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

Ortak dil belirtimi iki dönüştürme işlecini tanımlar:

* `op_Implicit`, veri veya duyarlık kaybına neden olmayan genişletme dönüştürmeleri için kullanılır. Örneğin, [Decimal](xref:System.Decimal) yapısı `op_Implicit` Integral türlerinin ve [char](xref:System.Char) değerlerinin değerlerini değerlere dönüştürmek için aşırı yüklenmiş bir işleç içerir `Decimal` .

* `op_Explicit`, büyüklük kaybı ile sonuçlanabilecek dönüştürmeleri daraltmak için kullanılır (bir değer, daha küçük bir aralığa sahip bir değere dönüştürülür) veya duyarlığına sahiptir. Örneğin, `Decimal` Yapı `op_Explicit` [çift](xref:System.Double) ve [tek](xref:System.Single) değerleri ' a dönüştürmek için `Decimal` ve `Decimal` değerlerini tamsayı değerlerine,, ve değerine dönüştürmek için aşırı yüklenmiş bir işleç içerir `Double` `Single` `Char` .

Ancak, tüm diller operatör aşırı yüklemesini veya özel işleçlerin tanımını desteklemez. Bu dönüştürme işleçlerini uygulamayı seçerseniz, dönüştürmeyi gerçekleştirmek için alternatif bir yol da sağlamanız gerekir. `From`Xxx ve `To` XXX yöntemleri sağlamanızı öneririz.

Aşağıdaki örnek, CLS uyumlu örtük ve açık dönüştürmeleri tanımlar. `UDouble`İmzalı çift duyarlıklı, kayan noktalı bir sayıyı temsil eden bir sınıf oluşturur. ' Dan `UDouble` `Double` `UDouble` `Single` , `Double` ' a `UDouble` ve ' `Single` `UDouble` a kadar açık dönüşümlere örtülü dönüşümler sağlar. Ayrıca `ToDouble` , örtük dönüştürme işlecine alternatif olarak bir yöntemi ve `ToSingle` ,, `FromDouble` ve `FromSingle` yöntemlerini açık dönüştürme işleçleri alternatifleri olarak tanımlar.

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

CLS uyumlu diziler aşağıdaki kurallara uyar:

* Bir dizinin tüm boyutlarının alt sınırı sıfır olmalıdır. Aşağıdaki örnek, bir alt sınırı olan CLS uyumlu olmayan bir dizi oluşturur. [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği varlığına rağmen, derleyici yöntemi tarafından döndürülen dizinin `Numbers.GetTenPrimes` CLS uyumlu olmadığını algılamaz.

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

* Tüm dizi öğeleri CLS uyumlu türlerden oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan diziler döndüren iki yöntemi tanımlar. İlki [UInt32](xref:System.UInt32) değerlerinin bir dizisini döndürür. İkincisi, [Int32](xref:System.Int32) ve değerleri Içeren bir [nesne](xref:System.Object) dizisi döndürür `UInt32` . Derleyici, türü nedeniyle ilk diziyi uyumsuz olarak tanımlasa da `UInt32` , ikinci DIZININ CLS uyumlu olmayan öğeleri içerdiğini tanıyamaz.

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

* Dizi parametrelerine sahip yöntemler için aşırı yükleme çözümlemesi, diziler oldukları olguyu ve öğe türlerini temel alır. Bu nedenle, aşırı yüklenmiş bir yöntemin aşağıdaki tanımı `GetSquares` CLS uyumludur.

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

CLS uyumlu arabirimler özellikleri, olayları ve sanal yöntemleri (uygulama içermeyen yöntemler) tanımlayabilir. CLS uyumlu bir arabirim aşağıdakilerden birini içeremez:

* Statik yöntemler veya statik alanlar. Bir arabirimde statik üye tanımlarsanız C# derleyicisi derleyici hataları oluşturur.

* Alanını. C# a derleyici, bir arabirimde alan tanımlarsanız derleyici hataları oluşturur.

* CLS uyumlu olmayan yöntemler. Örneğin, aşağıdaki arabirim tanımı, `INumber.GetUnsigned` CLS uyumlu olmayan olarak işaretlenen bir yöntemini içerir. Bu örnek bir derleyici uyarısı oluşturur.

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

  Bu kural nedeniyle, CLS uyumlu olmayan üyeleri uygulamak için CLS uyumlu türler gerekli değildir. CLS uyumlu bir çerçeve CLS uyumlu olmayan bir arabirim uygulayan bir sınıfı kullanıma sunuyorsa, CLS uyumlu olmayan tüm üyelerin somut uygulamalarını da sağlamalıdır.

CLS uyumlu dil derleyicileri Ayrıca, bir sınıfın birden fazla arabirimde aynı ada ve imzaya sahip ayrı üye uygulamaları sağlamasına izin vermelidir. C#, benzer adlandırılmış yöntemlerin farklı uygulamalarını sağlamak için açık arabirim uygulamalarını destekler. Aşağıdaki örnek, `Temperature` `ICelsius` ve `IFahrenheit` arabirimlerini açık arabirim uygulamaları olarak uygulayan bir sınıf tanımlayarak bu senaryoyu göstermektedir.

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

CLS uyumlu numaralandırmalar aşağıdaki kurallara uymalıdır:

* Sabit listesinin temel alınan türü, bir iç CLS uyumlu tamsayı ([byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)veya [Int64](xref:System.Int64)) olmalıdır. Örneğin, aşağıdaki kod, temel türü [UInt32](xref:System.UInt32) olan ve bir derleyici uyarısı oluşturan bir sabit listesi tanımlamaya çalışır.

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

* Sabit listesi türü, özniteliğiyle işaretlenmiş adlı tek bir örnek alanına sahip olmalıdır `Value__` `FieldAttributes.RTSpecialName` . Bu, alan değerine örtülü olarak başvuru yapmanızı sağlar.

* Sabit listesi, türleri numaralandırmanın türüyle eşleşen değişmez static alanları içerir. Örneğin, `State` ve değerlerini içeren bir sabit listesi tanımlarsanız `State.On` `State.Off` `State.On` ve `State.Off` türü olan değişmez değer statik alanlardır `State` .

* İki tür numaralandırma vardır:

  * Birbirini dışlayan, adlandırılmış tamsayı değerleri kümesini temsil eden bir sabit listesi. Bu tür bir numaralandırma [System. FlagsAttribute](xref:System.FlagsAttribute) özel özniteliğinin yokluğuna göre belirtilir.

  * Adlandırılmamış bir değer oluşturmak için birleştirebileceğiniz bir bit bayrakları kümesini temsil eden bir sabit listesi. Bu tür bir numaralandırma [System. FlagsAttribute](xref:System.FlagsAttribute) özel özniteliğinin varlığına göre belirtilir.

Daha fazla bilgi için bkz. [enum](xref:System.Enum) yapısına yönelik belgeler.

* Bir numaralandırmanın değeri, belirtilen değerlerinin aralığıyla sınırlı değildir. Diğer bir deyişle, bir Numaralandırmadaki değer aralığı, temel alınan değerinin aralığıdır. `Enum.IsDefined`Yöntemini, belirtilen değerin bir numaralandırma üyesi olup olmadığını anlamak için kullanabilirsiniz.

### <a name="type-members-in-general"></a>Genel olarak tür üyeleri

Ortak dil belirtimi, tüm alanlara ve yöntemlere belirli bir sınıfın üyeleri olarak erişilmesini gerektirir. Bu nedenle, genel statik alanlar ve Yöntemler (yani, statik alanlar veya bir türden ayrı tanımlanmış yöntemler) CLS uyumlu değildir. Kaynak kodunuza genel bir alan veya yöntem eklemeyi denerseniz, C# derleyicisi bir derleyici hatası oluşturur.

Ortak dil belirtimi yalnızca standart yönetilen çağırma kuralını destekler. Anahtar sözcükle işaretlenmiş bağımsız değişken listeleriyle yönetilmeyen çağırma kurallarını ve yöntemlerini desteklemez `varargs` . Standart yönetilen çağırma kuralıyla uyumlu olan değişken bağımsız değişken listeleri için, [ParamArrayAttribute](xref:System.ParamArrayAttribute) `params` C# ' deki anahtar sözcüğü ve `ParamArray` Visual Basic anahtar sözcüğü gibi, ParamArrayAttribute özniteliğini veya bağımsız dilin uygulamasını kullanın.

### <a name="member-accessibility"></a>Üye erişilebilirliği

Devralınan bir üyenin geçersiz kılınması, o üyenin erişilebilirliğini değiştiremez. Örneğin, bir temel sınıftaki ortak bir yöntem türetilmiş bir sınıftaki özel bir yöntem tarafından geçersiz kılınamaz. Bir özel durum vardır: bir `protected internal` derlemede (C# ' ta) veya `Protected Friend` (Visual Basic), farklı bir derlemedeki bir tür tarafından geçersiz kılınan bir derlemede üye.  Bu durumda, geçersiz kılma erişilebilirliği olur `Protected` .

Aşağıdaki örnek, [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği olarak ayarlandığında oluşturulan hatayı gösterir `true` ve `Person` ' dan türetilmiş bir sınıf olan, `Animal` `Species` özelliğin erişilebilirliğini public iken Private olarak değiştirmeye çalışır. Bunun erişilebilirliği ortak olarak değiştirilirse örnek başarıyla derlenir.

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

Üyenin İmzasındaki türlere, bu üyeye her erişilebilir her seferinde erişilebilir olması gerekir. Örneğin, bu, ortak bir üyenin türü Private, protected veya internal olan bir parametre içeremeyeceği anlamına gelir. Aşağıdaki örnek, bir `StringWrapper` sınıf Oluşturucusu bir `StringOperationType` dize değerinin nasıl sarmalanması gerektiğini belirleyen bir iç sabit listesi değeri ortaya çıkardığı zaman sonuç veren derleyici hatasını gösterir.

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

### <a name="generic-types-and-members"></a>Genel türler ve Üyeler

İç içe türler her zaman kapsayan türü olarak en az sayıda genel parametre içermelidir. Bu, kapsayan türdeki genel parametrelere konuma göre karşılık gelir. Genel tür de yeni genel parametreler içerebilir.

Kapsayan bir türün genel tür parametreleri ve iç içe geçmiş türleri arasındaki ilişki, tek dillerin sözdizimi tarafından gizlenebilir. Aşağıdaki örnekte, genel bir tür `Outer<T>` iki iç içe sınıf içerir `Inner1A` ve `Inner1B<U>` . `ToString`Her sınıfın devraldığı yöntemine yapılan çağrılar, `Object.ToString` her iç içe yerleştirilmiş sınıfın kapsayan sınıfının tür parametrelerini içerdiğini gösterir.

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

Genel tür adları, '*n*' de, *adın* *tür adı olduğu*, *`* bir karakter sabit değeri olduğu ve *n* tür üzerinde belirtilen parametre sayısı veya iç içe genel türler için yeni tanıtılan tür parametrelerinin sayısı olarak kodlanır. Genel tür adlarının bu kodlaması, bir kitaplıktaki CLS uyumlu Genel türlere erişmek için yansıma kullanan geliştiricilere yöneliktir.

Kısıtlamalar genel bir türe uygulanırsa, kısıtlama olarak kullanılan her türlü tür de CLS uyumlu olmalıdır. Aşağıdaki örnek, `BaseClass` CLS uyumlu olmayan adlı bir sınıfı ve tür parametresi türünden türetmelidir adlı bir genel sınıfı tanımlar `BaseCollection` `BaseClass` . Ancak, `BaseClass` CLS uyumlu olmadığından, derleyici bir uyarı yayar.

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

Genel bir tür genel bir temel türden türetildiyse, temel türdeki kısıtlamaların da karşılanmasını garanti edebilmesi için herhangi bir kısıtlamayı yeniden bildirmelidir. Aşağıdaki örnek, herhangi bir `Number<T>` sayısal türü temsil eden bir tanımlar. Ayrıca `FloatingPoint<T>` , kayan nokta değerini temsil eden bir sınıfı tanımlar. Ancak, üzerinde kısıtlama uygulanmadığından kaynak kodu derlenemiyor `Number<T>` (Bu T bir değer türü olmalıdır) `FloatingPoint<T>` .

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

Kısıtlama sınıfa eklenirse, örnek başarıyla derlenir `FloatingPoint<T>` .

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

Ortak dil belirtimi, iç içe türler ve korumalı üyeler için bir örnek oluşturma modeli uygular. Açık genel türler, iç içe geçmiş, korunan genel bir türün belirli bir örneğini içeren imzalara sahip alanları veya üyeleri gösteremez. Genel bir temel sınıfın veya arabirimin belirli bir örneğini genişleten genel olmayan türler, iç içe geçmiş, korunan genel bir türün farklı bir örneğini içeren imzalara sahip alanları veya üyeleri gösteremez.

Aşağıdaki örnek genel bir türü, `C1<T>` ve korumalı bir sınıfı tanımlar `C1<T>.N` . `C1<T>`iki yönteme sahiptir `M1` ve `M2` . Ancak, `M1` öğesinden bir nesne döndürmeye çalıştığı IÇIN CLS uyumlu değildir `C1<int>.N` `C1<T>` . İkinci bir sınıf, `C2` öğesinden türetilir `C1<long>` . İki yöntemi vardır `M3` ve `M4` . `M3`, `C1<int>.N` öğesinin bir alt sınıfından bir nesne döndürmeye çalıştığı IÇIN CLS uyumlu değildir `C1<long>` . Dil derleyicileri daha da kısıtlayıcı olabilir. Bu örnekte, derlemeyi denediğinde Visual Basic bir hata görüntüler `M4` .

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

CLS uyumlu sınıfların ve yapıların içindeki oluşturucular şu kurallara uymalıdır:

* Türetilmiş bir sınıfın Oluşturucusu, devralınan örnek verilerine erişmeden önce temel sınıfının örnek oluşturucusunu çağırmalıdır. Bu gereksinim, temel sınıf oluşturucularının türetilmiş sınıfları tarafından devralınmasından kaynaklanır. Bu kural, doğrudan devralmayı desteklemeyen yapılar için geçerlidir.

  Genellikle, aşağıdaki örnekte gösterildiği gibi, derleyiciler Bu kuralı CLS uyumluluğuna bağımsız olarak uygular. `Doctor`Bir sınıftan türetilmiş bir sınıf oluşturur `Person` , ancak `Doctor` sınıfın `Person` devralınan örnek alanlarını başlatmak için sınıf oluşturucusunu çağırması başarısız olur.

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

* Nesne Oluşturucusu bir nesne oluşturmak hariç çağrılamaz. Ayrıca, bir nesne iki kez başlatılamaz. Örneğin, bu, `Object.MemberwiseClone` oluşturucuları çağırmamalıdır anlamına gelir.

### <a name="properties"></a>Özellikler

CLS uyumlu türlerdeki özellikler aşağıdaki kurallara uymalıdır:

* Özelliğin bir ayarlayıcı, alıcı veya her ikisi de olmalıdır. Bir derlemede, bunlar özel yöntemler olarak uygulanır, yani ayrı yöntemler olarak (alıcı `get` \_ *PropertyName* ve ayarlayıcı, PropertyName olarak adlandırılır `set` \_ *propertyname*) `SpecialName` derlemenin meta verilerinde olarak işaretlenir. C# derleyicisi, özniteliği uygulamaya gerek olmadan bu kuralı otomatik olarak uygular <xref:System.CLSCompliantAttribute> .

* Özelliğin türü, özellik alıcısının dönüş türü ve ayarlayıcının son bağımsız değişkenidir. Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler başvuruya göre özelliğe atanamaz (yani, yönetilen işaretçiler olamaz).

* Bir özelliğin hem alıcı hem de ayarlayıcı varsa, her ikisi de sanal, hem statik hem de her iki örnek olmalıdır. C# derleyicisi otomatik olarak bu kuralı özellik tanımı sözdizimi üzerinden zorlar.

### <a name="events"></a>Ekinlikler

Bir olay, adı ve türü ile tanımlanır. Olay türü, olayı göstermek için kullanılan bir temsilcisidir. Örneğin, `DbConnection.StateChange` olay türündedir `StateChangeEventHandler` . Olayın kendisinin yanı sıra, olay adına göre adlara sahip üç yöntem olayın uygulamasını sağlar ve `SpecialName` derlemenin meta verilerinde olarak işaretlenir:

* _ EventName adlı bir olay işleyicisi ekleme yöntemi `add` .*EventName* Örneğin, olay için olay aboneliği yöntemi `DbConnection.StateChange` adlandırılır `add_StateChange` .

* _ EventName adlı bir olay işleyicisini kaldırma yöntemi `remove` .*EventName* Örneğin, olay için kaldırma yöntemi `DbConnection.StateChange` olarak adlandırılır `remove_StateChange` .

* EventName adlı olayın oluştuğunu belirten bir yöntem `raise` \_ *EventName*.

> [!NOTE]
> Ortak dil belirtiminin olayları ile ilgili kuralları, dil derleyicileri tarafından uygulanır ve bileşen geliştiricileri için saydamdır.

Olayı ekleme, kaldırma ve oluşturma yöntemleri aynı erişilebilirliği içermelidir. Bunların hepsi de statik, örnek veya sanal olması gerekir. Bir olayı ekleme ve kaldırma yöntemleri, türü olay temsilci türü olan bir parametreye sahiptir. Add ve Remove yöntemlerinin her ikisi de bulunmalıdır ya da her ikisi de olmamalıdır.

Aşağıdaki örnek, `Temperature` `TemperatureChanged` iki readsler arasındaki sıcaklık değişikliği bir eşik değerini eşitse veya aştığında bir olayı başlatan adlı CLS uyumlu bir sınıfı tanımlar. `Temperature`Sınıfı açıkça `raise_TemperatureChanged` olay işleyicilerini yürütebilmesi için bir yöntemi tanımlar.

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

Ortak dil belirtimi, aşırı yüklenmiş üyelere aşağıdaki gereksinimleri uygular:

* Üyeler, parametrelerin sayısına ve herhangi bir parametre türüne göre aşırı yüklenebilir. Çağırma kuralı, dönüş türü, yönteme veya parametresine uygulanan özel değiştiriciler, bir değere veya başvuruya göre geçirilen parametrelerin, aşırı yüklemeler arasında ayrım yaparken dikkate alınıp alınmayacağını belirtir. Bir örnek için, [adlandırma kuralları](#naming-conventions) bölümündeki bir kapsam içinde adların benzersiz olması gerekliliğe ilişkin koda bakın.

* Yalnızca özellikler ve yöntemler aşırı yüklenebilir. Alanlar ve olaylar aşırı yüklenemez.

* Genel yöntemler, genel parametrelerinin sayısına bağlı olarak aşırı yüklenebilir.

> [!NOTE]
> `op_Explicit`Ve `op_Implicit` işleçleri, geri yükleme çözümlemesi için bir yöntem imzasının bir parçası olarak kabul edilen bir kural için özel durumlardır. Bu iki işleç, parametreleri ve dönüş değerleri temel alınarak aşırı yüklenebilir.

### <a name="exceptions"></a>Özel durumlar

Özel durum nesnelerinin [sistem. Exception](xref:System.Exception) 'dan veya öğesinden türetilmiş başka bir türden türetilmesi gerekir `System.Exception` . Aşağıdaki örnek, özel bir sınıfı `ErrorClass` özel durum işleme için kullanıldığında oluşan derleyici hatasını gösterir.

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

Bu hatayı düzeltmek için, `ErrorClass` sınıfın öğesinden devralması gerekir `System.Exception` . Ayrıca, Ileti özelliği geçersiz kılınmalıdır. Aşağıdaki örnek, CLS uyumlu bir sınıf tanımlamak için bu hataları düzeltir `ErrorClass` .

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

Özel öznitelikler, özel öznitelikleri depolamak ve derlemeler, türler, Üyeler ve Yöntem parametreleri gibi programlama nesneleri hakkındaki meta verileri almak için genişletilebilir bir mekanizma sağlar. Özel öznitelikler [System. Attribute](xref:System.Attribute) veya öğesinden türetilmiş bir türden türetilmelidir `System.Attribute` .

Aşağıdaki örnek bu kuralı ihlal ediyor. Sınıfından `NumericAttribute` türetilmeyen bir sınıfı tanımlar `System.Attribute` . Derleyici hatası, sınıf tanımlandığında değil, yalnızca CLS uyumlu olmayan öznitelik uygulandığında oluşur.

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

CLS uyumlu bir özniteliğin Oluşturucusu veya özellikleri yalnızca aşağıdaki türleri açığa alabilir:

* [Boole](xref:System.Boolean)

* [Bayt](xref:System.Byte)

* [Char](xref:System.Char)

* [Çift](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Tutulamaz](xref:System.Int64)

* [Tek](xref:System.Single)

* [Dize](xref:System.String)

* [Tür](xref:System.Type)

* Temel türü,, veya olan herhangi bir numaralandırma türü `Byte` `Int16` `Int32` `Int64` .

Aşağıdaki örnek, `DescriptionAttribute` [özniteliğinden](xref:System.Attribute)türetilen bir sınıfı tanımlar. Sınıf oluşturucusunun türünde bir parametresi vardır, bu `Descriptor` yüzden sınıf CLS uyumlu değildir. C# derleyicisi bir uyarı yayar ancak başarıyla derlenir.

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

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği, bir program öğesinin ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)`Oluşturucu, program ÖĞESININ CLS uyumlu olup olmadığını belirten, *ısuyumlu*tek bir gerekli parametre içerir.

Derleme zamanında derleyici, CLS uyumlu olarak kabul edilen uyumlu olmayan öğeleri algılar ve bir uyarı gönderir. Derleyici, açıkça uyumsuz olacak şekilde bildirilmeyen türler veya Üyeler için uyarıları göstermez.

Bileşen geliştiricileri, `CLSCompliantAttribute` özniteliğini iki şekilde kullanabilir:

* CLS uyumlu olan ve CLS uyumlu olmayan parçalar içeren bir bileşen tarafından açığa çıkarılan ortak arabirimin parçalarını tanımlamak için. Özniteliği belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, bu öğelerin .NET Framework hedef olan tüm diller ve araçlardan erişilebilir olmasını güvence altına alır.

* Bileşen kitaplığının ortak arabiriminin yalnızca CLS uyumlu program öğelerini kullanıma sunduğundan emin olmak için. Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı vermez.

> [!WARNING]
> Bazı durumlarda, dil derleyicileri, özniteliğin kullanılıp kullanılmadığına bakılmaksızın CLS uyumlu kuralları uygular `CLSCompliantAttribute` . Örneğin, `*static` bir arabirimde bir üyenin TANıMLANMASı CLS kuralını ihlal ediyor. Ancak, `*static` bir arabirimde bir üye tanımlarsanız, C# derleyicisi bir hata iletisi görüntüler ve uygulamayı derlemez.

`CLSCompliantAttribute`Özniteliği değeri olan bir [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) özniteliğiyle işaretlenir `AttributeTargets.All` . Bu değer, `CLSCompliantAttribute` özniteliği derlemeler, modüller, türler (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), tür üyeleri (oluşturucular, Yöntemler, özellikler, alanlar ve olaylar), parametreler, genel parametreler ve dönüş değerleri dahil olmak üzere herhangi bir program öğesine uygulamanıza olanak tanır. Ancak, uygulamada, özniteliğini yalnızca derlemeler, türler ve tür üyelerine uygulamanız gerekir. Aksi takdirde, derleyiciler özniteliği yoksayar ve kitaplığınızın ortak arabirimindeki uyumlu olmayan bir parametre, genel parametre veya dönüş değeri ile karşılaştığında Derleyici uyarıları oluşturmaya devam eder.

`CLSCompliantAttribute`Özniteliğin değeri kapsanan program öğeleri tarafından devralınır. Örneğin, bir derleme CLS uyumlu olarak işaretlenmişse, türleri de CLS uyumludur. Bir tür CLS uyumlu olarak işaretlenmişse, iç içe geçmiş türleri ve üyeleri de CLS uyumludur.

`CLSCompliantAttribute`Dahil edilen bir program öğesine özniteliğini uygulayarak devralınan uyumluluğu açıkça geçersiz kılabilirsiniz. Örneğin, uyumlu bir `CLSCompliantAttribute` derlemede uyumlu olmayan bir tür tanımlamak Için *ısuyumlu* değeri olan özniteliğini kullanabilirsiniz `false` ve uyumlu olmayan bir derlemede uyumlu bir tür tanımlamak için bir *ısuyumlu* değeri ile özniteliğini kullanabilirsiniz `true` . Uyumlu olmayan üyeleri, uyumlu bir türde de tanımlayabilirsiniz. Ancak, uyumlu olmayan bir tür uyumlu üyelere sahip olamaz, bu yüzden uyumsuz bir türden devralmayı geçersiz kılmak için *ısuyumlu* değeri olan özniteliği kullanamazsınız `true` .

Bileşenleri geliştirirken, `CLSCompliantAttribute` derlemenizin, türlerinin ve ÜYELERININ CLS uyumlu olup olmadığını belirtmek için her zaman özniteliğini kullanmanız gerekir.

CLS uyumlu bileşenler oluşturmak için:

1. `CLSCompliantAttribute`DERLEMENIZI CLS uyumlu olarak işaretlemek için öğesini kullanın.

2. Derlemede, CLS uyumlu olmayan, genel olarak sunulan herhangi bir türü, uyumsuz olarak işaretleyin.

3. CLS uyumlu türlerde herkese açık olan tüm üyeleri uyumlu değil olarak işaretleyin.

4. CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlar.

Uyumlu olmayan tüm türlerini ve üyelerini başarıyla işaretlediyseniz, derleyicisinde uyumsuz olmayan uyarılar sunulmamalıdır. Ancak, hangi üyelerin CLS uyumlu olmadığını ve ürün belgelerinizde CLS uyumlu alternatiflerini listelemeyeceğini belirtmeniz gerekir.

Aşağıdaki örnek, CLS `CLSCompliantAttribute` uyumlu bir derlemeyi ve `CharacterUtilities` , CLS uyumlu olmayan iki üyeye sahip bir türünü tanımlamak için özniteliğini kullanır. Her iki üye de özniteliğiyle etiketlendiği `CLSCompliant(false)` için derleyici hiçbir uyarı üretmez. Sınıfı, her iki yöntem için de CLS uyumlu bir alternatif sağlar. Normalde, `ToUTF16` CLS uyumlu alternatifler sağlamak için metoda yalnızca iki aşırı yükleme ekleyeceğiz. Ancak, dönüş değerine göre Yöntemler aşırı yüklenemez, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklıdır.

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

Bir kitaplık yerine bir uygulama geliştiriyorsanız (yani, diğer uygulama geliştiricileri tarafından tüketilen türleri veya üyeleri açığa çıkarmadıysanız), uygulamanızın kullandığı program öğelerinin CLS uyumluluğu yalnızca dilinizin bu işlemleri desteklememesi durumunda ilgilenmektedir. Bu durumda, CLS uyumlu olmayan bir öğeyi kullanmaya çalıştığınızda dil derleyicinizin bir hata üretecektir.

## <a name="cross-language-interoperability"></a>Diller arası birlikte çalışabilirlik

Dil bağımsızlığının birkaç olası anlamı vardır. Bir anlamı, başka bir dilde yazılmış bir uygulamadan bir dilde yazılmış türleri sorunsuz bir şekilde kullanmayı içerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.

Aşağıdaki örnek, iki sınıf içeren Utilities. dll adlı bir sınıf kitaplığı oluşturarak platformlar arası birlikte çalışabilirliği gösterir `NumericLib` ve `StringLib` . `NumericLib`Sınıfı C# dilinde yazılır ve `StringLib` sınıf Visual Basic yazılır. `StringUtil.vb`Bu, sınıfının sınıfında tek bir üye içeren kaynak kodu `ToTitleCase` `StringLib` .

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

İki sınıfı tek bir derlemede paketlemek için, bunları modüller halinde derlemeniz gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
vbc /t:module StringUtil.vb
```

C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```console
csc /t:module NumberUtil.cs
```

Daha sonra, iki modülü bir derlemede derlemek için bağlantı aracını (LINK. exe) kullanabilirsiniz:

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Aşağıdaki örnek `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemlerini çağırır. Hem Visual Basic kodu hem de C# kodu, her iki sınıftaki yöntemlere erişebilir.

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

C# ile derlemek için, derleyicinin adını vbc 'den CSC 'ye değiştirin ve dosya uzantısını. vb iken. cs olarak değiştirin:

```console
csc example.cs /r:UtilityLib.dll
```
