---
title: Dil bağımsızlığı ve dilden bağımsız bileşenler
description: Nasıl birçok desteklenen .NET dillerinde biriyle gibi geliştirebileceğinizi öğrenin C#, C + +/ CLI, F#, IronPython, VB, Visual COBOL ve PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 9e63b16106f69ec35b7713ffc1a28e2cfb19d2d9
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203658"
---
# <a name="language-independence-and-language-independent-components"></a>Dil bağımsızlığı ve dilden bağımsız bileşenler

.NET bağımsız bir dildir. Bu bir geliştirici olarak, birinde gibi .NET uygulamaları hedefleyen birçok dilde geliştirebileceğiniz anlamına gelir C#, F#ve Visual Basic. Türler ve üyeler sınıf kitaplığı için .NET uygulamaları, bunlar ilk olarak yazılmış dili bilmek zorunda kalmadan ve herhangi bir özgün dil kuralları izlemeye gerek kalmadan olmadan geliştirilen erişebilirsiniz. Bileşen geliştiricisiyseniz, diline bakılmaksızın herhangi bir .NET uygulama bileşeniniz erişebilir.

> [!NOTE]
> Bu ilk kısmı bu makalede, dilden bağımsız bileşenler - diğer bir deyişle, herhangi bir dilde yazılmış uygulamalar tarafından tüketilebilecek bileşenlerin oluşturulması açıklanmaktadır. Birden çok dilde yazılmış kaynak kodundan tek bileşen veya uygulama da oluşturabilirsiniz; bkz: [diller arası birlikte çalışabilirlik](#cross-language-interoperability) ikinci bölümündeki bu makalede. 

Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşim kurmayı nesneleri arayanlara tüm diller için ortak olan özellikleri göstermesi gerekir. Bu ortak özellikler kümesi, oluşturulmuş derlemeler için uygulanan bir kurallar kümesi olan ortak dil belirtimi (CLS ile), tanımlanır. Ortak dil belirtimi bölüm ı, yan tümceler 7 ila 11'de tanımlanan [ECMA-335 standardı: Ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm). 

Bileşeniniz ortak dil belirtimi için uyuyorsa, CLS uyumlu olması sağlanır ve CLS destekleyen programlama diliyle yazılmış derlemedeki koddan erişilebilir. Bileşeniniz ortak dil belirtimi için derleme zamanında uygulayarak uyup uymadığını belirleyebilirsiniz [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini kaynak kodunuza. Daha fazla bilgi için [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute).

Bu makalede:

* [CLS uyumluluğu kuralları](#cls-compliance-rules)

    * [Türler ve tür üyesi imzaları](#types-and-type-member-signatures)

    * [Adlandırma kuralları](#naming-conventions)
    
    * [Tür dönüştürme](#type-conversion)
    
    * [Diziler](#arrays)
    
    * [Arabirimler](#interfaces)
    
    * [Sabit Listeleri](#enumerations)
    
    * [Genel olarak tür üyeleri](#type-members-in-general)
    
    * [Üye erişilebilirliği](#member-accessibility)
    
    * [Genel türler ve Üyeler](#generic-types-and-members)
    
    * [Oluşturucular](#constructors)
    
    * [Özellikler](#properties)
    
    * [Olaylar](#events)
    
    * [Overloads](#overloads)
    
    * [Özel Durumlar](#exceptions)
    
    * [Öznitelikler](#attributes)
    
* [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute)

* [Diller arası birlikte çalışabilirlik](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>CLS uyumluluğu kuralları

Bu bölüm, CLS uyumlu bileşen oluşturma kurallarını anlatır. Kuralları tam listesi için bölüm ı, madde 11'ine bakın [ECMA-335 standardı: Ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Çerçeveler (oluşturmak için bir dil derleyicisi kullanan geliştiriciler tüketiciler (CLS uyumlu bir bileşen programlı olarak erişen geliştiriciler), geçerli olduğundan ortak dil belirtimi CLS uyumuyla ilgili her kuralı açıklanır. CLS-compliant kitaplıkları) ve Genişleticileri (bir dil derleyicisi veya CLS uyumlu bileşenler oluşturan kod ayrıştırıcısı gibi bir araç oluşturan geliştiriciler). Bu makale, çerçeveler için geçerli olarak kurallarında odaklanır. Ancak, Genişleticiler için geçerli kurallar bazıları da kullanılarak oluşturulan derlemelere uygulanabileceğini unutmayın [Reflection.Emit](xref:System.Reflection.Emit). 

Dilden bağımsız bir bileşen tasarlamak için yalnızca CLS kurallarını bileşeninizin genel arabirimine uygulamanız gerekir. Özel uygulamanızın belirtime uygun gerekmez. 

> [!IMPORTANT]
> CLS uyumluluğu kuralları yalnızca bileşenin özel uygulaması için bir bileşenin genel arabirimi uygulanır. 

Örneğin, dışındaki imzalanmamış tamsayılar [bayt](xref:System.Byte) CLS uyumlu değildir. Çünkü `Person` sınıfı aşağıdaki örnekte gösterir bir `Age` türünün özelliği [UInt16](xref:System.UInt16), aşağıdaki kod bir derleyici uyarısı görüntüler.

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

CLS uyumlu kişi sınıf türünü değiştirerek yapabileceğiniz `Age` özelliğinden `UInt16` için [Int16](xref:System.Int16), CLS uyumlu, 16 bit işaretli bir tamsayı olduğu. Özel türünü değiştirmek zorunda değilsiniz `personAge` alan. 

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

Kitaplığın Genel arabirimi aşağıdakilerden oluşur:

* Ortak sınıfların tanımları.

* Ortak sınıfların ortak üyelerinin ve üyelerin erişilebilir türetilmiş sınıflar (yani, korumalı üyeler) tanımları tanımları. 

* Parametreleri ve ortak sınıfların ve parametreleri genel yöntemlerin dönüş türleri ve türetilen sınıflar için erişilebilir yöntemlerin dönüş türleri. 

CLS uyumluluğu kuralları, aşağıdaki tabloda listelenmiştir. Metin kuralları ndan alınmıştır [ECMA-335 standardı: Ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm), Ecma International telif hakkı 2012 olduğu. Aşağıdaki bölümlerde bu kurallar hakkında daha ayrıntılı bilgi bulunur. 

Kategori | Bkz.  | Kural | Kural numarası
-------- | --- | ---- | -----------
Erişilebilirlik | [Üye erişilebilirliği](#member-accessibility) | Devralınan dışında olduğunda bir yöntemini geçersiz kılma farklı bir derlemeden devralınan yöntemi geçersiz kılma erişilebilirlik değiştirilmemelidir `family-or-assembly`. Bu durumda geçersiz kılma erişilebilirlik olmalıdır `family`. | 10
Erişilebilirlik | [Üye erişilebilirliği](#member-accessibility) | Görünürlük ve erişilebilirliği türleri ve üyeleri üye bizzat görünür ve erişilebilir olduğunda herhangi bir üyenin İmzasındaki türler görünür ve erişilebilir olmasını olacaktır. Örneğin, kendi derlemesi dışında görülebilir bir genel yöntem türü yalnızca derleme içinde görünür olan bir bağımsız değişkene sahip olamaz. Üye bizzat görünür ve erişilebilir olduğunda görünürlük ve erişilebilirliği herhangi bir üyenin imzasında kullanılan örneklenmiş bir genel tür oluşturan türlerin görünür ve erişilebilir olmalıdır. Örneğin, örneklenmiş bir genel tür imzasında bulunan kendi derlemesi dışında görülebilir bir üyenin, türü yalnızca derleme içinde görünür olan bir genel bağımsız değişkene sahip olamaz. | 12
Diziler | [Diziler](#arrays) | Diziler CLS uyumlu türü olan öğeleri olmalıdır ve tüm boyutlar dizinin alt sınırı sıfır olmalıdır. Yalnızca bir dizi ve dizinin öğe türü bir öğedir olgu aşırı yükler arasında ayrım yapmak için gerekli. Ne zaman aşırı yükleme iki alan ya da daha fazla dizi öğesi türleri türleri adlı. | 16
Öznitelikler | [Öznitelikler](#attributes) | Öznitelikleri türü olacaktır [System.Attribute](xref:System.Attribute), ya da bundan devralan bir tür. | 41
Öznitelikler | [Öznitelikler](#attributes) | CLS yalnızca bir özel özniteliklerin kodlamalarının alt kümesine izin verir. (Bkz. Bölüm IV) bu kodlamalarda görünmesi gereken türleri yalnızca şunlardır: [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [ System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), ve herhangi bir numaralandırma türü CLS uyumlu temel tamsayı türüne göre. | 34
Öznitelikler | [Öznitelikler](#attributes) | CLS ortak olarak görünür gerekli değiştiricilere izin vermiyor (`modreq`, bkz. Bölüm II), isteğe bağlı değiştiricilere izin vermez ancak (`modopt`, bkz. Bölüm II) anlamadığı. | 35
Oluşturucular | [Oluşturucular](#constructors) | Devralınan örnek verilerine herhangi bir erişim oluşmadan önce nesne Oluşturucu, temel sınıfının bazı örnek oluşturucusu oluşturucularını çağırmalıdır (Bu oluşturuculara sahip olmak zorunda olmayan değer türleri için geçerli değildir.)  | 21
Oluşturucular | [Oluşturucular](#constructors) | Nesne Oluşturucu dışında bir nesnenin oluşturmanın bir parçası çağrılmamalıdır ve nesne iki kez başlatılmamış. | 22
Numaralandırmalar | [Sabit Listeleri](#enumerations) | Temel bir enum türü yerleşik bir CLS tamsayı türü olacaktır, alanın adı "value__" olacaktır ve bu alanın işaretlenmesi `RTSpecialName`. |  7
Numaralandırmalar | [Sabit Listeleri](#enumerations) | Bir varlığı veya yokluğu ile gösterilen iki ayrı türü vardır [System.FlagsAttribute](xref:System.FlagsAttribute) (bkz: bölüm IV kitaplığı) özel öznitelik. Biri, adlandırılmış tamsayı değerlerini temsil eder; diğer temsil eder, adlandırılmamış değer üretmek için birleştirilebilen bit bayrakları adı. Değerini bir `enum` belirtilen değerlerle sınırlı değildir. |  8
Numaralandırmalar | [Sabit Listeleri](#enumerations) | Bir enumun değişmez statik alanları numaralandırma türüne sahip olamaz. |  9
Olaylar | [Olaylar](#events) | Bir olay uygulayan yöntemler olarak işaretlenmeyecektir `SpecialName` meta verilerinde. |29
Olaylar | [Olaylar](#events) | Bir olay ve onun erişimcilerinin erişilebilirliği aynı olacaktır. |30
Olaylar | [Olaylar](#events) | `add` Ve `remove` yöntemleri için bir olay ya da her ikisini de gelecektir mevcut olmalı veya olmamalıdır. |31
Olaylar | [Olaylar](#events) | `add` Ve `remove` yöntemleri bir olay her bir parametre türü almalı olay türünü tanımlar ve öğesinden türetilmelidir [System.Delegate](xref:System.Delegate). |32
Olaylar | [Olaylar](#events) | Olaylar, belirli bir adlandırma desenine uymalıdır. CLS kural 29 başvurulan SpecialName özniteliği uygun ad karşılaştırmalarında yoksayılmalı ve tanımlayıcı kurallarına uymalıdır.  |33
Özel Durumlar | [Özel Durumlar](#exceptions) | Oluşan nesneler, türü olacaktır [System.Exception](xref:System.Exception) veya ondan devralınan bir türde. Öte yandan, CLS uyumlu yöntemler diğer tür özel durumların yayılmasını engellemek için gerekli değildir. | 40
Genel | [CLS uyumluluğu kuralları](#cls-compliance-rules) | CLS kuralları erişilebilir veya görünebilir tanımlanan derlemenin yalnızca bu bölümleri türü için geçerlidir. | 1.
Genel | [CLS uyumluluğu kuralları](#cls-compliance-rules) | CLS olmayan uyumlu türlerin üyeleri CLS uyumlu olarak işaretlenmeyecektir. | 2
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | İç içe geçmiş türler en az kadar genel parametresi kapsayan tür olmalıdır. İç içe bir türde genel parametreler kapsayan türdeki genel parametrelere konuma göre karşılık gelir.  | 42
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Genel bir tür adını iç içe olmayan türde bildirilen veya yukarıda tanımlanan kurallara göre iç içe türü için yeni sunulan tür parametrelerinin sayısı kodlayın. | 43
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Genel tür, genel tür kısıtlamaları tarafından temel türü veya arabirim kısıtlama getirilmez garanti edecek yeterli kısıtlamaları yeniden bildirmek. | 44
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Genel parametreler üzerinde kısıtlama olarak kullanılan türler kendilerini CLS uyumlu olmalıdır. | 45
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Görünürlük ve erişilebilirliği (iç içe türler dahil) oluşturulmuş bir genel türde üyelerin bir bütün olarak genel tür bildirimi yerine belirli bir örnek Kapsamınızın göz önünde bulundurulmalıdır. Bu varsayılırsa, CLS kuralı 12 görünürlük ve erişilebilirlik kuralları hala geçerlidir. | 46
Genel Türler | [Genel türler ve Üyeler](#generic-types-and-members) | Her Özet veya sanal genel yöntem için olmalıdır varsayılan bir somut (soyut olmayan) uygulama | 47
Arabirimler | [Arabirimler](#interfaces) | CLS uyumlu arabirimler CLS olmayan duyar tanımına uygulamak için gerektirmez. | 18
Arabirimler | [Arabirimler](#interfaces) | CLS uyumlu arabirimler statik yöntemleri tanımlamak değil ya da alanlarını tanımlarlar. | 19
Üyeler | [Genel olarak tür üyeleri](#type-members-in-general) | Genel statik alanlar ve yöntemler CLS uyumlu değildir. | 36
Üyeler | -- | Bir değişmez statik değeri, alan başlatma meta verileri kullanılarak belirtilir. CLS uyumlu bir hazır değer değişmez değer olarak tam olarak aynı türde olan alan başlatma meta verilerinde belirtilen bir değeri olmalıdır (veya hazır bilgi ise temel türdeki bir `enum`). | 13
Üyeler | [Genel olarak tür üyeleri](#type-members-in-general) | Vararg kısıtlaması CLS'nin parçası değildir ve CSL tarafından desteklenen tek çağırma kuralı, standart yönetimli çağırma kuralıdır olduğu. | 15
Adlandırma kuralları | [Adlandırma kuralları](#naming-conventions) | Derlemeleri Annex 7, teknik rapor 15, başlatmak ve tanımlayıcıları, kullanılabilir adresindeki çevrimiçi eklenmesi için izin verilen karakter kümesini yöneten Unicode Standard3.0 izleyin [Unicode normalleştirme formları](https://www.unicode.org/unicode/reports/tr15/tr15-18.html). Tanımlayıcıları Unicode normalleştirme Form c tarafından tanımlanan kurallı biçimde olmalıdır CLS amacıyla, iki tanımlayıcı aynı harfli eşlemeler (Unicode yerel ayara duyarlı, bire bir küçük harf eşlemeler tarafından belirtildiği şekilde) aynı olması durumunda. Diğer bir deyişle, iki tanımlayıcı CLS altında farklı kabul edilmesi için daha çok, farklı olacaktır. Ancak, devralınan bir tanımı geçersiz kılmak için CLI'yı özgün bildirimin kesin kodlama kullanılmasını gerektirir. | 4
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | CLS uyumlu kapsamda sunulan tüm adlar, ayrı bağımsız tür adları aynı ve aşırı yükleme olduğu dışında tutulamaz. CTS sağlar, ancak bir yöntem ve bir alan için aynı adı kullanmak tek bir türü diğer bir deyişle, buna izin vermez. | 5
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | Alanlar ve iç içe geçmiş türler yalnızca tanımlayıcı karşılaştırması ile edilmesine, verse CTS, ayrı imzaların ayırt edici olmasını sağlar. Yöntemler, özellikler ve olaylar (tanımlayıcı karşılaştırmasına göre) aynı ada sahip yalnızca dönüş türüne göre farklı olmalıdır da CLS kuralı 39'da belirtilen hariç | 6
Aşırı Yükleme | [Overloads](#overloads) | Özellikler ve yöntemler aşırı yüklenebilir. | 37
Aşırı Yükleme | [Overloads](#overloads) |Özellikler ve yöntemler aşırı yüklenebilir yalnızca sayı ve dönüştürme işleçleri dışında parametre türleri temel `op_Implicit` ve `op_Explicit`, kendi dönüş türüne bağlı olarak, aynı zamanda aşırı yüklenebilir. | 38
Aşırı Yükleme | -- | İki veya daha fazla CLS uyumlu yöntem bir türde bildirilen varsa aynı ada sahip, belirli bir tür örneklemeleri kümesi için aynı parametre ve dönüş türleri ve ardından bu yöntemlerin tümü, bu tür anlamsal olarak eşdeğer olacaktır. | 48
Özellikler | [Özellikler](#properties) | Bir özelliğin alıcı ve ayarlayıcı yöntemleri uygulayan yöntemler olarak işaretlenmeyecektir `SpecialName` meta verilerinde. | 24
Özellikler | [Özellikler](#properties) | Özelliğin erişimcileri tüm statik olmalıdır, tüm sanal ya da tamamen örnek olmalıdır. | 26
Özellikler | [Özellikler](#properties) | Özellik türü alıcının dönüş türü ve ayarlayıcının son bağımsız değişken türü olmalıdır. Özelliğin parametrelerinin türleri türler alıcı ve tüm tür parametreleri ancak ayarlayıcının son parametre olmalıdır. Tüm bu türler CLS uyumlu olmalıdır ve işaretçileri yönetemezler tutulamaz (diğer bir deyişle, başvuruyla geçirilmemelidir). | 27
Özellikler | [Özellikler](#properties) | Özellikler, belirli bir adlandırma desenine uymalıdır. `SpecialName` CLS kural 24 başvurulan özniteliği uygun ad karşılaştırmalarında yoksayılmalı ve tanımlayıcı kurallarına uymalıdır. Bir özelliğin bir alıcı yöntemi, ayarlayıcı yöntemi veya her ikisi de olmalıdır. | 28
Tür dönüştürme | [Tür dönüştürme](#type-conversion) | Op_Implicit ya da op_Explicit sağlanırsa, alternatif bir yol, zorlama sağlama aracı sağlanacaktır. | 39
Türler | [Türler ve tür üyesi imzaları](#types-and-type-member-signatures) | Paketlenmiş değer türleri CLS uyumlu değildir. | 3
Türler | [Türler ve tür üyesi imzaları](#types-and-type-member-signatures) | Bir imzada görünen tüm türler CLS uyumlu olmalıdır. Örneklenen bir genel türü oluşturan tüm türler CLS uyumlu olmalıdır. | 11
Türler | [Türler ve tür üyesi imzaları](#types-and-type-member-signatures) | Türü belirlenmiş başvurular, CLS uyumlu değildir. | 14
Türler | [Türler ve tür üyesi imzaları](#types-and-type-member-signatures) | Yönetilmeyen işaretçi türleri CLS uyumlu değildir. | 17
Türler | [Türler ve tür üyesi imzaları](#types-and-type-member-signatures) | CLS uyumlu sınıflar, değer türleri ve arabirimler, CLS uyumlu olmayan üyelerinin uygulamasını gerektirmez | 20
Türler | [Türler ve tür üyesi imzaları](#types-and-type-member-signatures) | [System.Object](xref:System.Object) CLS uyumludur. CLS uyumlu herhangi bir sınıf, CLS uyumlu bir sınıftan devralmalıdır. | 23

### <a name="types-and-type-member-signatures"></a>Türler ve tür üyesi imzaları

[System.Object](xref:System.Object) türü CLS uyumlu ve .NET Framework tür sistemindeki tüm nesne türlerinin temel türü değil. .NET Framework'te devralma ya da olan örtülü (örneğin, [dize](xref:System.String) sınıfı örtük olarak devraldığı `Object` sınıfı) ya da açık (örneğin, [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) sınıf açık olarak devralınılır [ArgumentException](xref:System.ArgumentException) açıkça öğesinden devralan sınıf [özel durum](xref:System.Exception) sınıfı. Türetilmiş bir tür CLS uyumlu olacak şekilde bilgi için kendi temel türü de CLS uyumlu olmalıdır. 

Aşağıdaki örnek, temel türü CLS uyumlu değil, türetilmiş bir tür gösterir. Temel tanımlar `Counter` sayaç olarak imzalanmamış bir 32 bitlik tamsayı kullanan sınıf. Sınıfı, bir işaretsiz tamsayıyı kaydırarak sayaç işlevi sağladığından, sınıf CLS uyumlu olmayan olarak işaretlenir. Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter`, ayrıca CLS uyumlu değil. 

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
      return String.Format("{0}). ", ctr);
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
      Return String.Format("{0}). ", ctr)
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

Bir yöntemin dönüş türü veya özellik türü dahil olmak üzere, üye imzalarında görüntülenen tüm türler CLS uyumlu olmalıdır. Ayrıca, genel türler için: 

* Örneklenen bir genel türü oluşturan tüm türler CLS uyumlu olmalıdır.

* Genel parametreler üzerinde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır. 

.NET [ortak tür sistemi](common-type-system.md) bir derlemenin meta verilerde özel olarak kodlanmış, doğrudan ortak dil çalışma zamanı tarafından desteklenen yerleşik türler içerir. Bu gerçek türlerden, aşağıdaki tabloda listelenen türler CLS uyumludur. 


CLS uyumlu türü | Açıklama
------------------ | -----------
[Bayt](xref:System.Byte) | 8 bitlik işaretsiz tamsayı 
[Int16](xref:System.Int16) | 16 bit işaretli tamsayı 
[Int32](xref:System.Int32) | 32 bitlik işaretli tamsayı 
[Int64](xref:System.Int64) | 64-bit işaretli tamsayı
[Tek](xref:System.Single) | Tek duyarlıklı kayan nokta değeri
[çift](xref:System.Double) | Çift duyarlıklı kayan nokta değeri
[Boole değeri](xref:System.Boolean) | TRUE veya false değeri türü 
[Char](xref:System.Char) | UTF-16 kodlu kod birimi
[Ondalık](xref:System.Decimal) | Ondalık sayı olmayan kayan nokta
[IntPtr](xref:System.IntPtr) | İşaretçisi veya tutamacı bir platform tanımlı boyutun
[dize](xref:System.String) | Sıfır, bir veya daha fazla karakter nesne koleksiyonu 
 
Aşağıdaki tabloda listelenen gerçek türler CLS uyumlu değildir.


Uyumsuz tür | Açıklama | CLS uyumlu alternatif
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | 8 bitlik işaretli tamsayı veri türü | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16-bit işaretsiz tamsayı | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32-bit işaretsiz tamsayı | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64-bit işaretsiz tamsayı | [Int64](xref:System.Int64) (taşabilir), [BigInteger](xref:System.Numerics.BigInteger), veya [çift](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | İmzalanmamış işaretçi veya işleç | [IntPtr](xref:System.IntPtr)
 
 .NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı, CLS uyumlu olmayan diğer türleri içerebilir. Örneğin: 
 
 * Paketlenmiş değer türleri. Aşağıdaki C# örnek, bir ortak özellik türü olan bir sınıf oluşturur `int`* adlı `Value`. Çünkü bir `int`* bir kutulanmış değer türü olduğundan Derleyici bunu CLS-uyumlu değil olarak işaretler.

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

* Yazılı başvurular, bir nesneye başvuru ve bir türe başvuru içeren özel bir yapıdır.

Bir tür CLS uyumlu değilse, uygulamalıdır [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini bir *isCompliant* parametre değerini `false` ona. Daha fazla bilgi için [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute) bölümü.  

Aşağıdaki örnek, bir yöntem imzası ve genel tür örneği oluşturmada CLS uyumluluğu sorununu göstermektedir. Tanımladığı bir `InvoiceItem` sınıf türünde bir özellik ile [UInt32](xref:System.UInt32), türünde bir özellik [Nullable'nın (UInt32)](xref:System.Nullable%601)ve tür parametreleri olan bir oluşturucusu `UInt32` ve `Nullable(Of UInt32)`. Bu örneği derlemeye çalıştığınızda, dört derleyici uyarısı alırsınız.

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

Derleyici uyarılarını ortadan kaldırmak için CLS uyumlu olmayan türleri yerine `InvoiceItem` genel arabiriminde:

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

Listelenen belirli türlere ek olarak, bazı türden kategoriler CLS uyumlu değildir. Bunlar, yönetilmeyen işaretçi türleri ve işlev işaretçi türlerini içerir. Aşağıdaki örnek, tamsayı dizisi oluşturmak için bir tamsayı işaretçisi kullandığından bir derleyici uyarısı oluşturur. 

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

```vb
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

CLS uyumlu soyut sınıflar (olarak işaretlenen sınıflar `abstract` içinde C#), sınıfın tüm üyeleri de CLS uyumlu olmalıdır. 

### <a name="naming-conventions"></a>Adlandırma kuralları

Bazı programlama dilleri büyük/küçük harfe duyarsızdır çünkü tanımlayıcılarını (örneğin, ad alanları, türler ve üyeler adları) daha fazla farklı olmalıdır. İki tanımlayıcı küçük eşlemeleri aynı ise eşdeğer olarak kabul edilir. Aşağıdaki C# örneği iki genel sınıfı tanımlar `Person` ve `person`. Bunlar yalnızca büyük küçük harfle farklı olduğundan, C# derleyicisi bunları CLS uyumlu değil işaretler. 

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

Ad alanları, türler ve üyeler, adları gibi Dil tanımlayıcıları programlama uygun olması gerekir [Unicode standartı 3.0, teknik rapor 15, ek 7](https://www.unicode.org/reports/tr15/tr15-18.html). Bunun anlamı:

* Bir tanımlayıcının ilk karakteri olması herhangi bir Unicode büyük harf, küçük harf, başlık biçimindeki harf, değiştirici harf, başka bir harf veya harf numarası. Unicode karakter kategorileri hakkında daha fazla bilgi için bkz: [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) sabit listesi. 

* İzleyen karakterler, ilk karakter olarak kategorilerden birini olabilir ve aralıksız işaretler, aralık birleştirme işaretleri, ondalık sayılar, bağlayıcı noktalamalar ve biçimlendirme kodları da içerebilir. 

Tanımlayıcıları karşılaştırmadan önce biçimlendirme kodlarını filtrelemeniz ve tek bir karakter birden çok UTF-16 kodlu kod birimi tarafından temsil edilebildiğinden tanımlayıcıları Unicode normalleştirme formu C'ye dönüştürmeniz gerekir. Unicode normalleştirme formu C'de aynı kod birimlerini üreten karakter sıraları CLS uyumlu değildir. Aşağıdaki örnek adlı bir özellik tanımlar `Å`ANGSTROM SIGN (U + 212B) karakterinden oluşan oluşur ve adlı ikinci `Å` LATIN CAPITAL LETTER A WITH RING ABOVE (U + 00 C 5) karakterinden oluşan oluşur. C# Derleyici kaynak kodunu CLS uyumlu olmayan olarak işaretler.

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

(Örneğin, bir ad alanı içindeki türleri ya da bir tür içindeki üyelerden bir derleme içinde ad uzayları) belirli bir kapsam içindeki üye adları, aşırı yükleme yoluyla çözülmüş adlar dışında benzersiz olmalıdır. Bu gereksinim kapsamı içinde farklı türde üye oldukları sürece aynı adlara sahip birden çok üye veren ortak tür sistemi, daha fazla katı (örneğin, bir yöntem biridir ve bir alan biridir). Özellikle, tür üyeleri için: 

* Alanlar ve iç içe geçmiş türler yalnızca ad ile ayırt edilir. 

* Yöntemler, özellikler ve aynı ada sahip olaylar birden fazla sadece dönüş türüne göre farklı olmalıdır. 

Aşağıdaki örnek üye adlarının kendi kapsamı içinde benzersiz olması şartını göstermektedir. Adlı bir sınıf tanımlar `Converter` adlı dört üye içeren `Conversion`. Üçü yöntemdir ve birisi bir özelliktir. İçeren yöntemi bir `Int64` parametresi benzersiz olarak adlandırılır, ancak iki yöntemle bir `Int32` parametresi değildir, çünkü dönüş değeri bir üyenin imzasının bir parçası olarak kabul edilmez. `Conversion` Özelliği Özellikler aşırı yüklenmiş yöntemlerle aynı ada sahip olamaz çünkü bu gereksinim, ayrıca ihlal. 

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

Diller ortak dil çalışma zamanını hedefleyen de anahtar sözcükleri ile Birleşen tanımlayıcıları (Tür adları gibi) başvuran bazı mekanizma sağlamanız gerekir tek tek dillerde benzersiz anahtar sözcükler içerir. Örneğin, `case` hem C# ve Visual Basic'te bir anahtar sözcüktür. Ancak, aşağıdaki Visual Basic örnek adlı bir sınıfın belirsizliğini ortadan kaldırabilir, `case` gelen `case` açma ve kapatma küme ayraçlarını kullanarak anahtar sözcüğü. Aksi takdirde, örnek "Anahtar sözcüğü, bir tanımlayıcı olarak geçerli değil" hata iletisini oluşturur ve bu derleme başarısız. 

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

Aşağıdaki C# örnektir örneğini oluşturabilir `case` sınıfı kullanarak @ sembolünü dil anahtar kelimesi tanımlayıcıdan belirsizliğini ortadan kaldırmak için. Bu olmadan, C# derleyicisi iki hata iletisi, "Tür bekleniyor" ve "geçersiz ifade terimi 'case'." görüntülenir 

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

Ortak dil belirtimi iki dönüştürme işleci tanımlar:

* `op_Implicit`, veri veya duyarlık kaybına neden olmayan dönüştürmesi için kullanılır. Örneğin, [ondalık](xref:System.Decimal) yapısı içeren aşırı yüklenmiş bir `op_Implicit` tam sayı türlerinin değerlerini dönüştürmek için işleci ve [Char](xref:System.Char) değerler `Decimal` değerleri. 

* `op_Explicit`, büyüklük (bir değer daha küçük bir aralığı olan bir değere dönüştürülür) veya duyarlık kaybına neden dönüştürmeleri daraltma için kullanılır. Örneğin, `Decimal` yapısı içeren aşırı yüklenmiş bir `op_Explicit` dönüştürme işleci [çift](xref:System.Double) ve [tek](xref:System.Single) değerler `Decimal` ve dönüştürmek için `Decimal` değerler tamsayı değerlerini `Double`, `Single`, ve `Char`. 

Ancak, tüm diller, İşleç aşırı yüklemesi veya özel işleçlerin tanımını desteklemez. Bu dönüştürme işleçlerini uygulamayı seçerseniz dönüştürmeyi gerçekleştirmenin alternatif bir yolu da sağlamanız gerekir. Sağlamanızı öneririz `From`Xxx ve `To`Xxx yöntemleri. 

Aşağıdaki örnek, CLS uyumlu örtülü ve açık dönüştürmeleri tanımlar. Oluşturur bir `UDouble` imzalı çift duyarlıklı, kayan noktalı sayıyı temsil eden sınıf. Örtük dönüştürmelerine sağlayan `UDouble` için `Double` ve açık dönüşümlerse `UDouble` için `Single`, `Double` için `UDouble`, ve `Single` için `UDouble`. Ayrıca tanımlar bir `ToDouble` yöntemi örtülü dönüştürme işlecine bir alternatif olarak ve `ToSingle`, `FromDouble`, ve `FromSingle` açık dönüştürme işleçleri için alternatif yöntemler. 

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

CLS uyumlu diziler şu kurallara uyar: 

* Tüm boyutlar bir dizinin alt sınırı sıfır olmalıdır. Aşağıdaki örnek, bir alt sınırı bir olan CLS uyumlu olmayan bir dizi oluşturur. Unutmayın varlığına rağmen [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği, derleyici tarafından saptanmayan tarafından döndürülen dizinin `Numbers.GetTenPrimes` yöntemi CLS uyumlu değil. 

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

* Tüm dizi öğeleri, CLS uyumlu türlerden oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan bir dizi döndüren iki yöntemi tanımlar. İlk bir dizi döndürür [UInt32](xref:System.UInt32) değerleri. İkinci döndürür bir [nesne](xref:System.Object) içeren bir dizi [Int32](xref:System.Int32) ve `UInt32` değerleri. Derleyici ilk diziyi uyumlu nedeniyle tanımlasa da, `UInt32` türü başarısız ikinci dizinin CLS uyumlu olmayan öğeler içerdiğini anlayamaz. 

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

* Dizi parametreleri olan yöntemler için aşırı yükleme çözünürlüğü olduklarından dayanarak gerçeğine ve kendi öğe türünde ' dir. Bu nedenle, aşırı yüklenmiş bir aşağıdaki tanımını `GetSquares` yöntemi CLS uyumludur. 

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

CLS uyumlu arabirimler, özellikleri, olayları ve sanal yöntemleri (uygulama içermeyen yöntemleri) tanımlayabilir. CLS uyumlu bir arabirim şunlardan herhangi birini içeremez: 

* Statik yöntemler veya static alanlar. C# Derleyici generatse bir arabirimde statik bir üye tanımlarsanız derleyici hataları. 

* Alanları. C# Acompiler bir arabirimde bir alan tanımlarsanız derleyici hataları oluşturur.

* CLS uyumlu olmayan yöntemleri. Örneğin, aşağıdaki arabirim tanımı bir yöntem içerir `INumber.GetUnsigned`, yani olarak CLS uyumlu olmayan olarak işaretlenmiş. Bu örnek, bir derleyici uyarısı oluşturur. 

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

  Bu kural nedeniyle, CLS uyumlu türler CLS uyumlu olmayan üyeleri uygulamak için gerekli değildir. CLS uyumlu bir çerçeve, CLS olmayan uyumlu arabirimi uygulayan bir sınıfı gösterirse, CLS uyumlu olmayan tüm üyelerinin somut uygulamalarını da sağlamanız gerekir. 

CLS uyumlu dil derleyicileri de birden fazla arabirimde aynı ada ve imzaya sahip üyelerin ayrı uygulamalarını sağlamak bir sınıf izin vermeniz gerekir. C#aynı adlı yöntemlerin farklı uygulamalarını sağlamak için açık arabirim uygulamalarını destekler. Aşağıdaki örnek, tanımlayarak bu senaryoyu gösteren bir `Temperature` uygulayan sınıf `ICelsius` ve `IFahrenheit` arabirimlerini açık arabirim uygulamalarını olarak. 

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

CLS uyumlu numaralandırmalar şu kurallara uymalıdır: 

* Sabit listesinin temel alınan türü bir iç CLS uyumlu tamsayı olmalıdır ([bayt](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), veya [Int64](xref:System.Int64)). Aşağıdaki kod gibi temel alınan türü olan bir numaralandırma tanımlamayı dener [UInt32](xref:System.UInt32) ve bir derleyici uyarısı oluşturur. 

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

* Bir numaralandırma türü adlı tek bir örnek alanına sahip olmalıdır `Value__` ile işaretlenmiş `FieldAttributes.RTSpecialName` özniteliği. Bu, alan değerine dolaylı başvuru sağlar. 

* Bir numaralandırma eşleşen türleri numaralandırma türüyle eşleşen değişmez statik alanları içerir. Örneğin, tanımladığınız bir `State` sabit listesi değerleri ile `State.On` ve `State.Off`, `State.On` ve `State.Off` türü olan sabit statik alanlarsa olan `State`. 

* Numaralandırmanın iki türü vardır: 
    
    * Birbirini dışlayan bir dizi adlandırılmış tamsayı değerlerini temsil eden bir sabit listesi. Bu numaralandırma türü yokluğuyla [System.FlagsAttribute](xref:System.FlagsAttribute) özel öznitelik.
    
    * Adlandırılmamış değer üretmek için birleştirilebilen bit bayrakları kümesini temsil eden bir sabit listesi. Bu numaralandırma türü varlığını tarafından belirtilen [System.FlagsAttribute](xref:System.FlagsAttribute) özel öznitelik.
    
 Daha fazla bilgi için belgelerine bakın [Enum](xref:System.Enum) yapısı. 

* Bir numaralandırma değeri, belirtilen değerler aralığıyla sınırlı değildir. Diğer bir deyişle, bir numaralandırmada değerler aralığı kendi temel değer aralığıdır. Kullanabileceğiniz `Enum.IsDefined` bir belirtilen değerin bir numaralandırma üyesi olup olmadığını belirlemek için yöntemi. 

### <a name="type-members-in-general"></a>Genel olarak tür üyeleri

Ortak dil belirtimi, tüm alanlar ve yöntemler, belirli bir sınıfın üyesi olarak erişilmesini gerektirir. Bu nedenle, genel statik alanlar ve yöntemler (diğer bir deyişle, statik alanlar veya bir türden ayrı tanımlanan yöntemler) CLS uyumlu değildir. Genel alan veya yöntem kaynak kodunuzu eklemeye çalışırsanız C# derleyici, bir derleyici hatası oluşturur. 

Ortak dil belirtimi yalnızca standart yönetilen çağırma kuralı destekler. Yönetilmeyen çağırma kurallarını desteklemeyen ve yöntemleri değişken bağımsız değişken listesiyle işaretlenmiş `varargs` anahtar sözcüğü. Standart yönetilen çağırma kuralı ile uyumlu olan değişken bağımsız değişken listeleri için [ParamArrayAttribute](xref:System.ParamArrayAttribute) özniteliği veya tek tek dilin uygulamasını gibi `params` anahtar sözcüğünü C# ve `ParamArray` Visual Basic'teki. 

### <a name="member-accessibility"></a>Üye erişilebilirliği

Devralınmış bir üyeyi geçersiz kılmak o üyenin erişilebilirliğini değiştiremezsiniz. Örneğin, genel bir temel sınıf yöntemi özel bir yöntem türetilmiş bir sınıf tarafından geçersiz kılınamaz. Bir istisna vardır: bir `protected internal` (C# ' de) veya `Protected Friend` (Visual Basic'te) üyesi farklı bir derlemedeki bir türe tarafından geçersiz kılınan bir derlemedeki.  Bu durumda geçersiz kılma erişimi olan `Protected`. 

Hata aşağıdaki örnekte oluşturulan [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği `true`, ve `Person`, bir sınıf, türetilir `Animal`, özele değiştirmeye erişilebilirliği `Species` genel özelliğinden özel. Erişilebilirlik genel olarak değişirse örnek başarıyla derler. 

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

Bir üyenin İmzasındaki türler, üye erişilebilir olduğunda erişilebilir olması gerekir. Örneğin, bu genel bir üyenin, türü özel, korumalı veya iç olan bir parametre içeremez anlamına gelir. Sonuçları derleyici hatası aşağıdaki örnekte, bir `StringWrapper` sınıf oluşturucusu bir iç sunan `StringOperationType` bir dize değerinin nasıl sarılacağını belirleyen sabit listesi değeri. 

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

İç içe geçmiş türler, her zaman kapsayan türü en az sayıda genel parametrelere sahip. Bunlar, kapsayan türdeki genel parametrelere konuma göre karşılık gelir. Genel tür de yeni genel parametreler ekleyebilirsiniz. 

Genel tür parametreleri bir kapsayan tür ile onun iç içe geçmiş türler arasındaki ilişki, tek tek dillerin sözdizimi tarafından gizlenmiş olabilir. Aşağıdaki örnekte, genel tür `Outer<T>` içeren iki iç içe geçmiş sınıflar `Inner1A` ve `Inner1B<U>`. Çağrıları `ToString` her sınıf öğesinden devralan yöntemi `Object.ToString`, iç içe geçmiş sınıf her sınıfın kapsayan sınıf türü parametreleri içerdiğini gösterir. 

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

Genel tür adları biçiminde kodlanır *adı*'*n*burada *adı* tür adıdır *`* bir karakter değişmez değeridir ve *n* türde bildirilen parametre sayısı veya iç içe geçmiş türler için yeni sunulan tür parametrelerinin sayısı. Bu genel tür adları kodlaması öncelikle bir kitaplıktaki CLS uyumlu genel türlere erişmek için yansımayı kullanan geliştiricileri ilgilendirir. 

Bir genel kısıtlamalar uygulanırsa kısıtlamaları de CLS uyumlu olmalıdır olarak kullanılan türler yazın. Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` yani değil CLS uyumlu ve adlı bir genel sınıf `BaseCollection` tür parametresi türetilmesi gereken `BaseClass`. Ancak `BaseClass` CLS uyumlu değilse derleyici bir uyarı gösterir. 

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

Genel bir tür genel bir temel türden türetilirse, temel tür kısıtlamaları da karşılanır karşılanmasını garantileyebilmesi için kısıtlamaları gerekir. Aşağıdaki örnekte tanımlayan bir `Number<T>` herhangi bir sayısal türü temsil edebilir. Ayrıca tanımlar bir `FloatingPoint<T>` sınıfı temsil eder bir kayan nokta değeri. Bu kısıtlama geçerli değildir çünkü Bununla birlikte, Kaynak Kodu derlemek, başarısız `Number<T>` (T bir değer türü olması gerekir) için `FloatingPoint<T>`.

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
// The attempt to comple the example displays the following output:
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
' The attempt to comple the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'    
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

Kısıtlama eklenirse örnek başarıyla derler `FloatingPoint<T>` sınıfı.

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

Ortak dil belirtimi, bir iç içe geçmiş türler için her örnekleme başına koruyucu modeli uygular ve korumalı üyeler. Açık genel türler, belirli bir örneğini oluşturmada iç içe, korunan bir genel tür içeren imzaları olan alanları veya üyeleri gösteremez. Genel temel sınıfı veya arabiriminin belirli bir örneğini genişleten genel olmayan türler, farklı bir örneğini oluşturmada iç içe, korunan bir genel tür içeren imzaları olan alanları veya üyeleri gösteremez.

Aşağıdaki örnek bir genel tür tanımlar `C1<T>`ve korumalı bir sınıf `C1<T>.N`. `C1<T>` iki yönteme sahiptir `M1` ve `M2`. Ancak, `M1` getirmeyi denediğinden CLS uyumlu değil bir `C1<int>.N` nesnesinden `C1<T>`. İkinci bir sınıf `C2`, türetilen `C1<long>`. İki yönteme sahiptir `M3` ve `M4`. `M3` getirmeyi denediğinden CLS uyumlu değil bir `C1<int>.N` öğesinin nesneden `C1<long>`. Dil derleyicileri daha kısıtlayıcı olabileceğine dikkat edin. Derlemeye çalıştığında bu örnekte, Visual Basic bir hata gösterir. `M4`. 

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

CLS uyumlu sınıf ve yapılardaki oluşturucular bu kuralları izlemelidir: 

* Devralınan örnek verilerine erişmeden önce bir oluşturucu türetilmiş bir sınıfın temel sınıfının örnek oluşturucusunu çağırmalıdır. Temel sınıf Kurucularını kendi türetilmiş sınıfları tarafından miras alınmamasından ötürü olabilir, bu gereksinim olmasıdır. Bu kural doğrudan devralmayı desteklemeyen yapılar için geçerli değildir. 

  Genellikle, derleyiciler bu kuralı aşağıdaki örnekte gösterildiği gibi CLS uyumluluğundan bağımsız olarak uygular. Oluşturur bir `Doctor` türetilen sınıf bir `Person` sınıfı, ancak `Doctor` sınıfı başarısız olursa çağrılacak `Person` devralınan örnek alanları başlatmak için sınıfın Oluşturucusu. 

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
    
* Nesne Oluşturucu, nesne oluşturma dışında çağrılamaz. Ayrıca, bir nesne iki kez başlatılamaz. Örneğin, yani `Object.MemberwiseClone` oluşturucular çağırmamalıdır.  

### <a name="properties"></a>Özellikler

CLS uyumlu türlerdeki özellikler şu kurallara uymalıdır:

* Bir özelliğin bir Ayarlayıcısı, alıcısı veya her ikisi de olmalıdır. Bir derlemede, bunlar özel yöntemler olarak deyişle ayrı yöntemler olarak görünür uygulanır (alıcı adlı `get` \_ *propertyname* ayarlayıcı `set` \_ *propertyname*) olarak işaretlenmiş `SpecialName` derlemenin meta verilerinde. C# Derleyici otomatik olarak uygulamak için gerek kalmadan bu kuralı zorlayan <xref:System.CLSCompliantAttribute> özniteliği. 

* Bir özelliğin özellik alıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türüdür. Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler atanamaz özelliği başvuruya göre (diğer bir deyişle, bunlar yönetilen işaretçiler olamaz). 

* Bir özellik hem alıcı hem de ayarlayıcı varsa, bunlar hem de sanal olmalıdır hem statik veya her ikisi de örnek. C# Derleyici otomatik olarak özellik tanımı sözdizimleri aracılığıyla bu kuralı uygular. 

### <a name="events"></a>Olaylar

Bir olay adı ve türüne göre tanımlanır. Olay türü olayı göstermek için kullanılan bir temsilcidir. Örneğin, `DbConnection.StateChange` olay türüdür `StateChangeEventHandler`. Olayın kendisinin yanı sıra, olay adına dayandırılan adlara sahip üç yöntem olayın uygulanmasını sağlar ve olarak işaretlenmiş `SpecialName` derlemenin meta verilerinde: 

* Adlı bir olay işleyicisi eklemek için bir yöntem `add`_*EventName*. Örneğin, olay aboneliği yöntemi için `DbConnection.StateChange` olay adlı `add_StateChange`. 

* Adlı bir olay işleyicisini kaldırma yöntemi `remove`_*EventName*. Örneğin, kaldırma yöntemi `DbConnection.StateChange` olay adlı `remove_StateChange`.

* Adlı olayın oluştuğunu belirten bir yöntem `raise`_*EventName*. 

> [!NOTE]
> Olaylara ilişkin ortak dil belirtimi kurallarının çoğu, dil derleyiciler tarafından uygulanır ve Bileşen geliştiriciler için saydamdır. 

Ekleme yöntemleri, kaldırma ve olayı tetiklenmeden aynı erişilebilirliği olmalıdır. Bunlar ayrıca tümü statik olmalıdır örneği veya sanal. Yöntem ekleme ve kaldırma olay türü olay temsilci türü olan bir parametreye sahip. Ekleme ve kaldırma yöntemlerinin her ikisi de bulunmalıdır veya ikisi de olmamalıdır. 

Aşağıdaki örnekte adlı, CLS uyumlu bir sınıf tanımlar `Temperature` oluşturan bir `TemperatureChanged` iki okuma arasındaki sıcaklık değişikliği değerine eşit veya eşik değeri, olay. `Temperature` Sınıfı açıkça tanımlayan bir `raise_TemperatureChanged` yöntemi olan olay işleyicileri seçmeli olarak çalıştırabilirsiniz.

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

Ortak dil belirtimi, aşırı yüklenmiş üyelerde aşağıdaki gereksinimleri karşılamalıdır: 

* Parametre sayısı ve herhangi bir parametre türüne göre üyeler aşırı yüklenebilir. Çağırma kuralı, dönüş türü özel değiştiriciler yönteme veya parametresine uygulanan ve parametrelerin değere veya başvuruya göre iletilir dikkate alınmaz aşırı yükler arasında ayrım yapılırken. Adları gereksinim bir kapsam içinde benzersiz olmalıdır. Örneğin, kodu görmek [adlandırma kuralları](#naming-conventions) bölümü. 

* Özellikler ve yöntemler aşırı yüklenebilir. Alanlar ve olaylar aşırı yüklenemez. 

* Genel yöntemler, genel parametrelerinin sayısına göre aşırı yüklenebilir. 

> [!NOTE]
>`op_Explicit` Ve `op_Implicit` işleçler şunlardır: değer olarak kabul edilmez aşırı yükleme çözümlemesi için bir yöntem imzasının parçası döndüren kuralının istisnalarıdır. Bu iki işleç hem parametreleri hem de dönüş değerlerine bağlı olarak aşırı yüklenebilir. 

### <a name="exceptions"></a>Özel Durumlar

Özel durum nesneleri türetilmesi gereken [System.Exception](xref:System.Exception) veya başka bir türden türetilmiş `System.Exception`. Aşağıdaki örnekte adlı özel bir sınıf olmadığında ortaya çıkar.%nÇözüm derleyici hatası `ErrorClass` özel durum işleme için kullanılır.

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

Bu hatayı düzeltmek için `ErrorClass` sınıfı devralmalıdır `System.Exception`. Ayrıca, ileti özelliği geçersiz kılınmalıdır. Aşağıdaki örnek tanımlamak için bu hataları düzeltir bir `ErrorClass` CLS uyumlu sınıf.  

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

.NET Framework derlemelerindeki özel öznitelikler özel öznitelikleri depolamak ve programlama derlemeler, türler, üye ve yöntem parametreleri gibi nesneler hakkındaki meta verileri almak için genişletilebilir bir mekanizma sağlar. Özel öznitelikler türetilmesi gereken [System.Attribute](xref:System.Attribute) veya türetilmiş bir türden `System.Attribute`.

Aşağıdaki örnek bu kuralı ihlal ediyor. Tanımladığı bir `NumericAttribute` türünden türemez sınıfı `System.Attribute`. Derleyici Hatası sınıfın tanımlı değil, yalnızca CLS uyumlu olmayan öznitelik, uygulandığında sonuçları verdiğine dikkat edin. 

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

Oluşturucu veya CLS uyumlu bir özniteliğin özellikleri sadece aşağıdaki türleri getirebilir:

* [Boole değeri](xref:System.Boolean)

* [Bayt](xref:System.Byte)

* [Char](xref:System.Char)

* [çift](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Tek](xref:System.Single)

* [dize](xref:System.String)

* [Tür](xref:System.Type)

* Temel alınan türü olan herhangi bir numaralandırma türü `Byte`, `Int16`, `Int32`, veya `Int64`. 

Aşağıdaki örnekte tanımlayan bir `DescriptionAttribute` türetilen sınıf [özniteliği](xref:System.Attribute). Sınıf oluşturucu türünde bir parametreye sahip `Descriptor`, bu nedenle sınıf CLS uyumlu değildir. Unutmayın C# derleyici bir uyarı yaydığına ancak başarıyla derler. 

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

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği bir program öğesinin ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Oluşturucu içeren bir tek gerekli parametresi *isCompliant*, program öğesinin CLS uyumlu olup olmadığını gösterir. 

Derleme zamanında derleyici, CLS uyumlu olduğu varsayılan uyum olmayan ve bir uyarı verir uyumlu olmayan öğeleri algılar. Derleyici, tür veya uyumlu olması için açıkça bildirilen üyeler için uyarı yayımlamaz. 

Bileşen geliştiriciler `CLSCompliantAttribute` özniteliğini iki şekilde: 

* Bir bileşen tarafından açıklanan genel arabirimin CLS uyumlu parçalarını ve CLS uyumlu olmayan parçalarını tanımlamak için. Öznitelik belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, kullanımı bu öğelerin tüm diller ve .NET Framework'ü hedefleyen Araçlar erişilebilir olmasını garanti eder. 

* Bileşen kitaplığının ortak arabiriminin yalnızca CLS uyumlu program öğelerini göstermesini sağlamak için. Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı verir.

> [!WARNING]
> Bazı durumlarda, dil derleyicileri, bağımsız olarak CLS uyumlu kuralları zorunlu `CLSCompliantAttribute` özniteliği kullanılır. Örneğin, tanımlama bir `*static` üye bir arabirimde CLS kuralını ihlal ediyor. Ancak, tanımlarsanız bir `*static` bir arabirim üye C# derleyici bir hata iletisi görüntüler ve uygulamayı derleyemez başarısız olur.

`CLSCompliantAttribute` Özniteliği ile işaretlenmiş bir [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) değerine sahip öznitelik `AttributeTargets.All`. Bu değer, uygulamanıza olanak sağlar. `CLSCompliantAttribute` özniteliği derlemeler, modüller, dahil olmak üzere tüm program öğesi için türler (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), üyeleri (Oluşturucular, yöntemler, özellikler, alanlar ve olaylar), yazın. Parametreler, genel parametreler ve dönüş değerleri. Ancak, uygulamada, özniteliği yalnızca derlemeler, türler ve tür üyeleri uygulamanız gerekir. Aksi takdirde, derleyiciler yoksayar ve karşılaştığınız uyumlu olmayan bir parametre, genel parametre veya dönüş değeri kitaplığınızın ortak arabiriminde her derleyici uyarıları oluşturmaya devam edin.  

Değerini `CLSCompliantAttribute` özniteliği içerdiği program ögeleri tarafından devralınır. Bir derleme CLS uyumlu olarak işaretlenmişse, örneğin, türlerinden de CLS uyumludur. Bir tür CLS uyumlu olarak işaretlenmişse, iç içe geçmiş türleri ve üyeleri de CLS uyumludur. 

Uygulayarak devralınan uyumluluğu açıkça kılabilirsiniz `CLSCompliantAttribute` özniteliği içerdiği program öğesine. Örneğin, kullanabileceğiniz `CLSCompliantAttribute` özniteliğini bir *isCompliant* değerini `false` özniteliği ile uyumlu bir derlemeyi ve, uyumlu olmayan bir tür tanımlamak için kullanabilirsiniz bir *isComplian*değerini `true` uyumlu olmayan bir derlemede uyumlu bir tür tanımlamak için. Uyumlu bir türde uyumlu olmayan üyeler de tanımlayabilirsiniz. Ancak, ile özniteliği kullanamazsınız. Bu nedenle uyumlu olmayan bir türün uyumlu üyeleri olamaz bir *isCompliant* değerini `true` uyumlu olmayan bir türden devralmayı geçersiz kılmak için. 

Bileşenleri geliştirirken her zaman kullanmalısınız `CLSCompliantAttribute` derlemenizin, türlerinin ve üyelerinin CLS uyumlu olup olmadığını belirtmek için özniteliği. 

CLS uyumlu bileşenler oluşturmak için: 

1. Kullanım `CLSCompliantAttribute` Derleme CLS uyumlu olarak işaretlemek için.

2. CLS uyumlu değil olarak uyumlu olmayan derlemedeki genel olarak sunulan türlerini işaretleyin. 

3. Herhangi bir genel olarak sunulan üye CLS uyumlu türlerde uyumlu olmayan olarak işaretleyin. 

4. CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlar. 

Tüm uyumlu olmayan türleri ve üyeleri başarılı bir şekilde işaretlediyseniz, derleyici tüm uyumsuz uyarılarını yayınlamaz. Ancak hangi üyelerin CLS uyumlu değildir ve ürün belgelerinizde bunların CLS uyumlu alternatifler listesinde gösterilmelidir. 

Aşağıdaki örnekte `CLSCompliantAttribute` CLS uyumlu bir derlemeyi ve bir tür tanımlamak için öznitelik `CharacterUtilities`, CLS uyumlu olmayan iki üyesi olan. Her iki üyeleri ile etiketlendiğinden `CLSCompliant(false)` özniteliği, derleyici uyarı üretmez. Sınıfı, her iki yöntem için CLS uyumlu bir alternatif de sağlar. Normalde, iki aşırı yüklemesi için yalnızca ekleriz `ToUTF16` yöntemi CLS uyumlu alternatifler sağlamak için. Ancak, dönüş değerini temel alarak yöntemler aşırı yüklenemez olduğundan, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklı.  

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

Varsa (diğer bir deyişle, türleri ve diğer uygulama geliştiricileri tarafından tüketilebilecek üyeleri göstermiyorsanız) kitaplık yerine bir uygulama geliştiriyorsanız, uygulamanızın kullandığı program öğelerinin CLS uyumluluğu yalnızca diliniz onları desteklemiyorsa ilgi olan . Bu durumda, CLS uyumlu olmayan bir öğe kullanmaya çalıştığınızda dil derleyici bir hata oluşturur. 

## <a name="cross-language-interoperability"></a>Diller Arası Birlikte Çalışabilirlik

Dil bağımsızlığının birkaç olası anlamı vardır. Bir anlamı, sorunsuz bir şekilde başka bir dilde yazılmış bir uygulamadan tek bir dilde yazılmış türleri kullanmayı içerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir. 

Aşağıdaki örnekte, iki sınıf içerir Utilities.dll adlı bir sınıf kitaplığı oluşturarak diller arası birlikte çalışabilirlik gösterilmektedir `NumericLib` ve `StringLib`. `NumericLib` Sınıfı C# ile yazılan ve `StringLib` sınıfı, Visual Basic'te yazılır. Kaynak kodu işte `StringUtil.vb`, tek bir üye içeren `ToTitleCase`, kendi `StringLib` sınıfı.

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

Tek bir derleme için iki sınıf paketlemek için modülleri derlemeniz gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın: 

```
vbc /t:module StringUtil.vb 
```

C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```
csc /t:module NumberUtil.cs
```

Bağlantı aracını (Link.exe) sonra iki modül bir birleştirme dosyasına derlemek için kullanın: 

```
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Aşağıdaki örnek daha sonra çağırır `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemleri. Hem Visual Basic kodunu hem de C# kod hem sınıflarını yöntemlerdeki erişmesi mümkün olduğunu unutmayın.

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

```
vbc example.vb /r:UtilityLib.dll
```

Derlemek için C#, derleyicinin adını vbc csc için değiştirin ve dosya uzantısını .vb yerine .cs olarak değiştirin:

```
csc example.cs /r:UtilityLib.dll
```

