---
title: Dil bağımsızlığı ve dilden bağımsız bileşenler
description: '.NET, C#, C + gibi birçok desteklenen dilde birinde nasıl geliştirebileceğinizi öğrenin +/ CLI, F #, IronPython, VB, Visual COBOL ve PowerShell.'
keywords: .NET, .NET core
author: dotnet-bot
ms.author: dotnetcontent
ms.date: 07/22/2016
ms.topic: article
dev_langs:
- csharp
- vb
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2745bc67c926f50c28f5fdfb122ee94a85f020ec
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="language-independence-and-language-independent-components"></a>Dil bağımsızlığı ve dilden bağımsız bileşenler

.NET bağımsız dilidir. Bu, geliştirici olarak size C#, F # ve Visual Basic gibi .NET uygulamalarında hedef birçok dilde birinde geliştirebilirsiniz, anlamına gelir. Türleri ve sınıf kitaplıkları için .NET uygulamaları, bunlar ilk olarak yazılmış dili bilmenize gerek kalmadan ve özgün dil kuralları birini izleyin gerek kalmadan geliştirilen üyeleri erişebilir. Bileşen geliştiriciyseniz bileşeniniz dili bağımsız olarak herhangi bir .NET uygulama tarafından erişilebilir.

> [!NOTE]
> Bu makalede bu ilk kısmı dilden bağımsız bileşenler - diğer bir deyişle, herhangi bir dilde yazılan uygulamaları tarafından kullanılabilecek bileşenler oluşturma açıklanır. Çeşitli dillerde yazılmış kaynak koddan tek bir bileşen ya uygulaması oluşturabilirsiniz; bkz: [diller arası birlikte çalışabilirlik](#cross-language-interoperability) ikinci bölümü, bu makalenin. 

Tam olarak herhangi bir dilde yazılmış diğer nesnelerle etkileşim kurmak için nesneleri, tüm diller için ortak olan özellikleri arayanlara kullanıma gerekir. Bu ortak bir özellikler kümesi ortak dil belirtimi (CLS tarafından), hangi oluşturulmuş derlemeler için geçerli bir kurallar kümesidir tanımlanır. Ortak dil belirtimi bölüm ı yan tümceleri 7 11 /'ile tanımlanan [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm). 

Bileşeniniz ortak dil belirtimi uyuyorsa, CLS uyumlu olması garanti ve CLS destekleyen tüm programlama dilinde yazılmıştır derlemelerde koddan erişilebilir. Bileşeniniz ortak dil belirtimi derleme zamanında uygulayarak uyup uymadığını belirleyebilirsiniz [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği için kaynak kodu. Daha fazla bilgi için bkz: [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute).

Bu makalede:

* [CLS uyumluluk kuralları](#cls-compliance-rules)

    * [Türleri ve türü üye imzaları](#types-and-type-member-signatures)

    * [Adlandırma kuralları](#naming-conventions)
    
    * [Tür dönüştürmeleri](#type-conversion)
    
    * [Diziler](#arrays)
    
    * [Arabirimler](#interfaces)
    
    * [Sabit Listeleri](#enumerations)
    
    * [Genel üyeleri yazın](#type-members-in-general)
    
    * [Üye erişilebilirlik](#member-accessibility)
    
    * [Genel türler ve üyeleri](#generic-types-and-members)
    
    * [Oluşturucular](#constructors)
    
    * [Özellikler](#properties)
    
    * [Olaylar](#events)
    
    * [Overloads](#overloads)
    
    * [Özel Durumlar](#exceptions)
    
    * [Öznitelikler](#attributes)
    
* [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute)

* [Diller arası birlikte çalışabilirlik](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a>CLS uyumluluk kuralları

Bu bölümde, CLS uyumlu bir bileşen oluşturmak için kurallar açıklanmaktadır. Bölüm ı yan tümcesi 11 / kuralları tam bir listesi için bkz [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> Çerçeveler (dil derleyici oluşturmak için kullandığınız geliştiriciler tüketicilere CLS uyumlu bir bileşen program aracılığıyla erişme (geliştiriciler) uygularken ortak dil belirtimi CLS uyumluluğu için her bir kural açıklanır. CLS-compliant kitaplıklar) ve Extender'larının (dil derleyici veya CLS uyumlu bileşenleri oluşturan bir kod ayrıştırıcı gibi bir araç oluşturan geliştiriciler). Çerçeveler için uygularken bu makalede kurallarında odaklanır. Ancak, bazı Extender'larının için geçerli olan kurallar da kullanılarak oluşturulan derlemeleri uygulayabilir Not [Reflection.Emit](xref:System.Reflection.Emit). 

Dilden bağımsızdır bir bileşen tasarlamak için yalnızca, bileşenin ortak arabirim CLS uyumluluğu için kurallar uygulama gerekir. Özel uygulamanızı belirtimine uygun olarak yok. 

> [!IMPORTANT]
> CLS uyumluluğu için kurallar, yalnızca kendi özel uygulama için bir bileşenin ortak arabirimi uygulanır. 

Örneğin, tamsayılar dışında imzasız [bayt](xref:System.Byte) CLS uyumlu değildir. Çünkü `Person` sınıfı aşağıdaki örnekte sunar bir `Age` türündeki özelliği [UInt16](xref:System.UInt16), aşağıdaki kod derleyici uyarısı görüntüler.

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

CLS uyumlu kişi sınıfı türünü değiştirerek yapabilirsiniz `Age` özelliğinden `UInt16` için [Int16](xref:System.Int16), CLS uyumlu, 16 bit işaretli tamsayıyı olduğu. Özel türünü değiştirmek zorunda değilsiniz `personAge` alan. 

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

* Ortak sınıfları tanımlar.

* Ortak sınıflar ortak üyeleri ve türetilen sınıflar (diğer bir deyişle, korumalı üyeleri) erişilebilir üyelerinin tanımları tanımları. 

* Parametreler ve genel yöntemlerin ortak sınıflar, parametreler ve dönüş türleri ve yöntemleri türetilmiş sınıflara erişilebilir dönüş türü. 

CLS uyumluluğu için kuralları aşağıdaki tabloda listelenmiştir. Kurallar metin alanından verbatim alınır [ECMA-335 standart: ortak dil altyapısı](https://www.ecma-international.org/publications/standards/Ecma-335.htm), telif hakkı 2012 Ecma uluslararası tarafından olduğu. Aşağıdaki bölümlerde bu kuralları hakkında daha ayrıntılı bilgi bulunamadı. 

Kategori | Bkz.  | Kural | Kural numarası
-------- | --- | ---- | -----------
Erişilebilirlik | [Üye erişilebilirlik](#member-accessibility) | Erişilebilirlik değil değiştirilmesi geçersiz kılma ne zaman bir yöntemini geçersiz kılma farklı bir derlemeden erişilebilirliği devralınan dışında yöntemleri, devralınan zaman `family-or-assembly`. Bu durumda, geçersiz kılma erişilebilirlik sahip `family`. | 10
Erişilebilirlik | [Üye erişilebilirlik](#member-accessibility) | Üye görünür ve erişilebilir olduğunda imza türlerinde herhangi bir üyenin görünür ve erişilebilir olacaktır, görünürlük ve erişilebilirlik türleri ve üyeleri olacaktır. Örneğin, kendi derlemenin dışından görülebilir genel bir yöntem türü yalnızca derlemede görünür olan bir bağımsız değişken sahip. Üye görünür ve erişilebilir olduğunda görünürlük ve herhangi bir üyenin imzada kullanılan bir oluşturulmuş genel tür oluşturma türlerinin erişilebilirlik görünür ve erişilebilir olacaktır. Örneğin, bir oluşturulmuş genel tür imzada mevcut kendi derlemenin dışından görünür bir üyenin türü yalnızca derlemede görünür olan genel bir bağımsız değişken sahip. | 12
Diziler | [Diziler](#arrays) | Diziler CLS uyumlu bir türü olan öğeleri sahip ve tüm boyutlar dizinin alt sınırlarını sıfır sahip. Yalnızca bir dizi ve dizi öğesi türü bir öğedir olgu aşırı arasında ayrım yapmak için gerekli. Ne zaman aşırı yüklemesi iki dayalı olan veya daha fazla dizi öğesi türleri türleri adlı. | 16
Öznitelikler | [Öznitelikler](#attributes) | Öznitelik türü olacaktır [System.Attribute'un](xref:System.Attribute), veya ondan devralan bir tür. | 41
Öznitelikler | [Öznitelikler](#attributes) | CLS yalnızca bir alt kümesini özel özniteliklerin Kodlamalar izin verir. (Bölüm IV bakın) bu Kodlamalar görünür yalnızca türleri şunlardır: [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [ System.Single](xref:System.Single), [System.Double](xref:System.Double), ve herhangi bir numaralandırma türü CLS uyumlu bir temel tamsayı türünde dayanır. | 34
Öznitelikler | [Öznitelikler](#attributes) | CLS herkese görünür gerekli değiştiricileri izin verme (`modreq`, Bölüm II bakın), isteğe bağlı değiştiricileri izin vermez ancak (`modopt`, Bölüm II bakın) anlamadığı. | 35
Oluşturucular | [Oluşturucular](#constructors) | Devralınan örnek veriler için herhangi bir erişim oluşmadan önce bir nesne oluşturucusu bazı örnek oluşturucusu olduğu temel sınıfın çağrısı. (Bu oluşturucular olmak zorunda değildir değer türleri için geçerli değildir.)  | 21
Oluşturucular | [Oluşturucular](#constructors) | Bir nesne Oluşturucusu dışındaki bir nesnenin oluşturmanın bir parçası çağrılması değil ve bir nesne iki kez başlatılmamış. | 22
Numaralandırmalar | [Sabit Listeleri](#enumerations) | Enum temel türü bir yerleşik CLS tamsayı türü olacaktır, alanın adını "value__" olacaktır ve bu alan işaretli `RTSpecialName`. |  7
Numaralandırmalar | [Sabit Listeleri](#enumerations) | Varlığı veya yokluğuna göre tarafından gösterilen Numaralandırmaların iki farklı tür vardır [System.FlagsAttribute](xref:System.FlagsAttribute) (bkz. Bölüm IV kitaplık) özel bir öznitelik. Bir adlandırılmış tamsayı değerlerini temsil eder; diğer temsil adsız bir değer üretmek için birleştirilmiş bir bit bayrakları adlı. Değeri bir `enum` belirtilen değerlere sınırlı değildir. |  8
Numaralandırmalar | [Sabit Listeleri](#enumerations) | Bir numaralandırma sabit değeri statik alanları ve enum türüne sahip. |  9
Olaylar | [Olaylar](#events) | Bir olay uygulamak yöntemleri olarak işaretlenmiş `SpecialName` meta veriler. |29
Olaylar | [Olaylar](#events) | Bir olay ve onun erişimciler erişilebilirlik aynı olacaktır. |30
Olaylar | [Olaylar](#events) | `add` Ve `remove` yöntemleri bir olay ya da her ikisini de gelecektir için mevcut olmalı veya belirtilmemelidir. |31
Olaylar | [Olaylar](#events) | `add` Ve `remove` yöntemleri bir olay her bir parametre türü alan için olay türünü tanımlar ve bu türetilen [System.Delegate](xref:System.Delegate). |32
Olaylar | [Olaylar](#events) | Olaylar, belirli bir adlandırma deseni uyması. CLS kural 29 başvurulan SpecialName özniteliği uygun adı karşılaştırmaları göz ardı ve tanımlayıcı kurallarına.  |33
Özel Durumlar | [Özel Durumlar](#exceptions) | Oluşturulan nesnelerin türü olacaktır [System.Exception](xref:System.Exception) veya ondan devralan bir tür. Öte yandan, CLS uyumlu yöntemlerini diğer tür özel durumlar yayılmasını engellemek için gerekli değildir. | 40
Genel | [CLS uyumluluk kuralları](#cls-compliance-rules) | CLS kuralları erişilebilir veya görünür outsideof tanımlama derleme olan yalnızca parçaları türü için geçerlidir. | 1.
Genel | [CLS uyumluluk kuralları](#cls-compliance-rules) | CLS dışı uyumlu türleri üyeleri CLS uyumlu olarak işaretlenmemiş. | 2
Genel Türler | [Genel türler ve üyeleri](#generic-types-and-members) | İç içe geçmiş türler en az sayıda genel parametreler kendilerini kapsayan türle sahip. Genel bir iç içe geçmiş tür parametrelerinde kapsayan türü genel parametreler konuma göre karşılık gelir.  | 42
Genel Türler | [Genel türler ve üyeleri](#generic-types-and-members) | Genel bir tür adı olmayan iç içe geçmiş türünde bildirilen ya da yeni yukarıda tanımlanan kurallarına göre iç içe yoksa türe giriş türü parametre sayısı kodlayın. | 43
Genel Türler | [Genel türler ve üyeleri](#generic-types-and-members) | Genel bir tür kısıtlamalar temel türü veya arabirimleri tarafından genel tür kısıtlamaları getirilmez güvence altına almak için yeterli kısıtlamaları redeclare. | 44
Genel Türler | [Genel türler ve üyeleri](#generic-types-and-members) | Genel parametreler üzerinde kısıtlamalar olarak kullanılan türleri kendilerini CLS uyumlu olacaktır. | 45
Genel Türler | [Genel türler ve üyeleri](#generic-types-and-members) | Görünürlük ve bir oluşturulmuş genel tür üyeleri (iç içe geçmiş türler dahil) erişilebilirliğini bir bütün olarak genel tür bildirimi yerine belirli örneklemesi Kapsamınızın dikkate. Bu varsayıldığında, CLS kuralının 12 görünürlük ve erişilebilirlik kuralları hala geçerlidir. | 46
Genel Türler | [Genel türler ve üyeleri](#generic-types-and-members) | Her soyut veya sanal genel yönteminde var olacaktır varsayılan somut (soyut) uygulama | 47
Arabirimler | [Arabirimler](#interfaces) | Bunları uygulamak için CLS uyumlu arabirimleri CLS olmayan compliantmethods tanımını gerektirmeyecek. | 18
Arabirimler | [Arabirimler](#interfaces) | CLS uyumlu arabirimlerde statik yöntemler tanımlamak değil ya da alanları tanımla. | 19
Üyeler | [Genel üyeleri yazın](#type-members-in-general) | Genel statik alanları ve yöntemleri CLS uyumlu değildir. | 36
Üyeler | -- | Değişmez değer statik değerini alan başlatma meta veri kullanımı ile belirtilir. CLS uyumlu bir sabit değişmez değeri olarak tam olarak aynı türde alan başlatma meta verilerinde belirtilmiş bir değere sahip olmalıdır (veya bu değişmez değeri ise, temel türde bir `enum`). | 13
Üyeler | [Genel üyeleri yazın](#type-members-in-general) | Vararg kısıtlaması CLS parçası değildir ve yalnızca çağırma kuralı CLS tarafından desteklenen standart çağırma yönetiliyor. | 15
Adlandırma kuralları | [Adlandırma kuralları](#naming-conventions) | Derlemeleri eki 7, teknik rapor 15 başlatmak ve tanımlayıcılarının, kullanılabilir adresindeki çevrimiçi dahil edilmesi için izin verilen karakter kümesini yöneten Unicode Standard3.0 izleyin [Unicode normalleştirme formları](http://www.unicode.org/unicode/reports/tr15/tr15-18.html). Tanımlayıcıları Unicode normalleştirme Form c tarafından tanımlanan kurallı biçimde olacaktır CLS amacıyla iki tanımlayıcılara aynı küçük eşlemelerini (Unicode yerel duyarsız, bire bir küçük harf eşlemeleri tarafından belirtildiği şekilde) aynı olması durumunda. Diğer bir deyişle, CLS altında farklı olarak kabul edilmesi iki tanımlayıcıları için bunların birden fazla yalnızca kendi durumda farklı. Ancak, devralınan bir tanımı geçersiz kılmak için CLI özgün bildirimi kesin kodlama kullanılabilir gerektirir. | 4
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | Tüm adları CLS uyumlu bir kapsamda sunulan ayrı bağımsız tür adları aynı ve aşırı yükleme aracılığıyla çözümlenmiş nerede dışında tutulamaz. CTS sağlar, ancak bir yöntem ve bir alan için aynı adı kullanmak tek bir türü diğer bir deyişle, CLS desteklemez. | 5
Aşırı Yükleme | [Adlandırma kuralları](#naming-conventions) | Alanlar ve iç içe geçmiş türler tarafından tanımlayıcı karşılaştırma tek başına farklı olacaktır, ayırt edici olarak ayrı imzaları eventhough CTS sağlar. Yöntemler, özellikler ve (tanımlayıcı karşılaştırma tarafından) aynı ada sahip olayları dönüş türüne göre çok daha fazlası farklı dışındaki CLS kural 39 belirtildiği gibi | 6
Aşırı Yükleme | [Overloads](#overloads) | Yalnızca özelliklerini ve yöntemlerini aşırı yüklenmiş. | 37
Aşırı Yükleme | [Overloads](#overloads) |Özellikleri ve yöntemleri aşırı yüklenebilir yalnızca sayısı ve türleri adlı dönüşüm işleçleri dışında kendi parametreleri temel `op_Implicit` ve `op_Explicit`, kendi dönüş türüne bağlı olarak, aynı zamanda aşırı yüklenebilir. | 38
Aşırı Yükleme | -- | İki veya daha fazla CLS uyumlu yöntemler tür tarafından bildirilen aynı sistemine sahip, türü örneklemesi, belirli bir dizi için aynı parametre ve dönüş türleri, sonra bu yöntemler bu tür örneklemesi anlam olarak eşdeğer olacaktır. | 48
Özellikler | [Özellikler](#properties) | Bir özelliğin'Set ' yordamı yöntemleri uygulamak yöntemleri olarak işaretlenmiş `SpecialName` meta veriler. | 24
Özellikler | [Özellikler](#properties) | Bir özelliğin erişimciler tüm statik olacaktır, tüm sanal veya tüm örneği olmalıdır. | 26
Özellikler | [Özellikler](#properties) | Bir özelliğin türünü alıcı dönüş türü ve kurucu son bağımsız değişkeni tür olacaktır. Özelliğin parametre türlerini alıcı ve tüm türleri parametreleri ancak kurucu son parametre türleri olacaktır. Tüm bu tür CLS uyumlu olacaktır ve yönetilen işaretçileri tutulamaz (diğer bir deyişle, başvuruya göre geçirilmesi değil). | 27
Özellikler | [Özellikler](#properties) | Özellikler, belirli bir adlandırma deseni uyması. `SpecialName` CLS kural 24 başvuruda bulunulan öznitelik uygun adı karşılaştırmaları göz ardı ve tanımlayıcı kurallarına. Özellik alıcısı yöntemi, ayarlayıcı yöntemi veya ikisine birden sahip. | 28
Tür dönüştürmeleri | [Tür dönüştürmeleri](#type-conversion) | Op_Implicit veya op_Explicit sağlanırsa, zorlama sağlama alternatif bir yol sağlanan. | 39
Türler | [Türleri ve türü üye imzaları](#types-and-type-member-signatures) | Paketlenmiş değer türleri CLS uyumlu değildir. | 3
Türler | [Türleri ve türü üye imzaları](#types-and-type-member-signatures) | İmza görünen tüm türleri CLS uyumlu olacaktır. Bir oluşturulmuş genel tür oluşturma tüm türleri CLS uyumlu olacaktır. | 11
Türler | [Türleri ve türü üye imzaları](#types-and-type-member-signatures) | Belirlenmiş başvurular CLS uyumlu değildir. | 14
Türler | [Türleri ve türü üye imzaları](#types-and-type-member-signatures) | Yönetilmeyen işaretçi türleri CLS uyumlu değildir. | 17
Türler | [Türleri ve türü üye imzaları](#types-and-type-member-signatures) | CLS uyumlu sınıfları, değer türleri ve arabirimleri CLS uyumlu olmayan üyeler uyarlamasını gerektirmeyecek | 20
Türler | [Türleri ve türü üye imzaları](#types-and-type-member-signatures) | [System.Object](xref:System.Object) CLS uyumlu değil. CLS uyumlu herhangi bir sınıf CLS uyumlu bir sınıftan devralınan. | 23

### <a name="types-and-type-member-signatures"></a>Türleri ve türü üye imzaları

[System.Object](xref:System.Object) türü CLS uyumlu olduğundan ve .NET Framework türü sistemindeki tüm nesne türlerini taban türü değil. .NET Framework'teki devralma olduğu ya da örtük (örneğin, [dize](xref:System.String) örtük olarak sınıfının devraldığı `Object` sınıfı) veya açık (örneğin, [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) sınıf açıkça devralır [ArgumentException](xref:System.ArgumentException) açıkça devraldığı sınıfı [özel durum](xref:System.Exception) sınıfı. CLS uyumlu olacak şekilde türetilen tür için temel türü de CLS uyumlu olmalıdır. 

Aşağıdaki örnek, temel türü CLS uyumlu olmayan türetilmiş bir tür gösterir. Bir taban tanımlar `Counter` işaretsiz bir 32 bit tamsayı sayacı olarak kullanan sınıfı. Sınıfı, bir işaretsiz tamsayı kaydırma tarafından sayaç işlevselliği sağladığından, sınıf-CLS uyumlu olmayan olarak işaretlenir. Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter`, ayrıca CLS uyumlu değil. 

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

Bir yöntemin dönüş türü veya bir özellik türü de dahil olmak üzere üye imzalarında görünür tüm türleri CLS ile uyumlu olması gerekir. Ayrıca, genel türleri için: 

* Oluşturulan genel bir tür oluşturan tüm türleri CLS ile uyumlu olması gerekir.

* Genel parametreler üzerinde kısıtlamalar olarak kullanılan tüm türleri CLS ile uyumlu olması gerekir. 

.NET [ortak tür sistemi](common-type-system.md) bir derlemenin meta verilerde doğrudan ortak dil çalışma zamanı tarafından desteklenir ve özel olarak kodlanmış yerleşik türler içerir. İç bu tür, aşağıdaki tabloda listelenen CLS uyumlu türleridir. 


CLS uyumlu türü | Açıklama
------------------ | -----------
[Bayt](xref:System.Byte) | 8 bit işaretsiz tamsayıyı 
[Int16](xref:System.Int16) | 16 bit işaretli tamsayıyı 
[Int32](xref:System.Int32) | 32 bit işaretli tamsayıyı 
[Int64](xref:System.Int64) | 64 bit işaretli tamsayıyı
[Tek](xref:System.Single) | Tek duyarlıklı kayan noktalı değeri
[Çift](xref:System.Double) | Çift duyarlıklı kayan noktalı değeri
[Boole değeri](xref:System.Boolean) | TRUE veya false değeri türü 
[char](xref:System.Char) | UTF-16 kodlu kod birimi
[Ondalık](xref:System.Decimal) | Olmayan kayan noktalı ondalık sayı
[IntPtr](xref:System.IntPtr) | İşaretçi veya platform tarafından tanımlanan bir boyut tanıtıcısı
[Dize](xref:System.String) | Sıfır, bir veya daha fazla karakter nesneleri koleksiyonu 
 
Aşağıdaki tabloda listelenen iç türleri CLS uyumlu değil.


Uyumlu türü | Açıklama | CLS uyumlu alternatifi
------------------ | ----------- | -------------------------
[SByte](xref:System.SByte) | 8 bit işaretli tamsayıyı veri türü | [Int16](xref:System.Int16)
[UInt16](xref:System.UInt16) | 16 bit işaretsiz tamsayıyı | [Int32](xref:System.Int32)
[UInt32](xref:System.UInt32) | 32 bit işaretsiz tamsayıyı | [Int64](xref:System.Int64)
[UInt64](xref:System.UInt64) | 64 bit işaretsiz tamsayıyı | [Int64](xref:System.Int64) (taşma), [BigInteger](xref:System.Numerics.BigInteger), veya [çift](xref:System.Double)
[UIntPtr](xref:System.UIntPtr) | İmzasız işaretçi veya tanıtıcısı | [IntPtr](xref:System.IntPtr)
 
 .NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı CLS ile uyumlu olmayan diğer türleri içerebilir; Örneğin: 
 
 * Paketlenmiş değer türleri. Aşağıdaki C# örnek türünde ortak bir özelliği olan bir sınıfı oluşturur `int`* adlı `Value`. Çünkü bir `int`* paketlenmiş değer türü derleyici-CLS uyumlu olmayan olarak işaretler.

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

* Bir nesneye başvuru ve türüne bir başvuru içeren özel yapılar belirlenmiş başvurular.

Bir tür CLS ile uyumlu değilse, uygulamalıdır [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) ile öznitelik bir *isCompliant* parametre değeriyle `false` ona. Daha fazla bilgi için bkz: [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute) bölümü.  

Aşağıdaki örnek, CLS uyumluluğu yöntem imzası ve genel tür oluşturmada sorun gösterilmektedir. Tanımladığı bir `InvoiceItem` türünde bir özellik sınıfıyla [UInt32](xref:System.UInt32), türünde bir özellik [null atanabilir, (UInt32)](xref:System.Nullable%601)hem de türünde parametrelere sahip bir oluşturucu `UInt32` ve `Nullable(Of UInt32)`. Bu örneği derlemek çalıştığınızda dört derleyici uyarıları alın.

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

Derleyici uyarılarını kaldırmak için CLS uyumlu olmayan türler yerini `InvoiceItem` uyumlu türleri olan ortak arabirim:

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

Listelenen belirli türlerine ek olarak bazı kategorileri türlerinin CLS uyumlu değildir. Bu, yönetilmeyen işaretçi türleri ve işlev işaretçisi türleri içerir. Aşağıdaki örnek, dizisi oluşturmak için bir işaretçi bir tamsayıya kullandığından derleyici uyarısı oluşturur. 

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

CLS uyumlu için soyut sınıflar (diğer bir deyişle, sınıflar olarak işaretlenmiş `abstract` C#), sınıfın tüm üyelerini de CLS ile uyumlu olması gerekir. 

### <a name="naming-conventions"></a>Adlandırma kuralları

Bazı programlama dilleri büyük/küçük harfe duyarsızdır olduğundan (örneğin, ad alanlarını, türleri ve üyeleri adları) tanımlayıcılar örnekten daha fazla farklı olmalıdır. İki tanımlayıcı küçük eşlemelerini aynıysa eşdeğer olarak değerlendiriliyor. Aşağıdaki C# örnek iki ortak sınıf tanımlar `Person` ve `person`. Yalnızca örneğe göre farklılık gösterdiğinden, C# Derleyici bunları değil CLS uyumlu işaretler. 

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

Ad alanlarını, türleri ve üyeleri, adları gibi Dil tanımlayıcıları programlama gerekir uygun [Unicode standart 3.0, teknik rapor 15, eki 7](https://www.unicode.org/reports/tr15/tr15-18.html). Bunun anlamı:

* İlk karakteri bir tanımlayıcı olarak herhangi bir Unicode büyük harf, küçük harf, büyük/küçük harf başlık, değiştiricisi, diğer mektup olması veya numarası harf. Unicode karakter kategorileri hakkında daha fazla bilgi için bkz: [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) numaralandırması. 

* Sonraki karakterler kategorileri hiçbirini ilk karakter olarak olabilir ve aralık birleştirme işaretleri, ondalık sayılar, bağlayıcı noktalama işaretleri ve biçimlendirme kodları aralıksız işaretlerini de içerir. 

Tanımlayıcıları karşılaştırmak önce biçimlendirme veya kodları filtre ve tek bir karakter birden çok UTF-16 kodlu kod birimler tarafından temsil edilebilir bulunduğundan Unicode normalleştirme Form C tanımlayıcıları dönüştürülemiyor. Unicode normalleştirme Form C aynı kodu birimlerinde üretmek karakter sıralarının CLS uyumlu değildir. Aşağıdaki örnek adlı bir özelliğini tanımlar `Å`ANGSTROM işareti (U + 212B) karakterinin oluşur ve ikinci bir özelliğe adlı `Å` LATIN büyük harf A ile HALKASI YUKARIDA (U + 00 C 5) karakterinin oluşur. C# Derleyici kaynak kodu CLS uyumlu olmayan olarak işaretler.

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

Üye adlarının (örneğin, ad alanları bir ad alanı içindeki tür veya üye türünde bir derleme içinde) belirli bir kapsam içinde dışında aşırı yükleme aracılığıyla çözülür adları benzersiz olmalıdır. Bu gereksinim, farklı türde üye olduğu sürece, aynı adlara sahip bir kapsamı içinde birden çok üye sağlar ortak tür sistemi daha daha sıkı (örneğin, bir yöntem biridir ve bir alan biridir). Tür üyeleri için özel olarak: 

* Alanlar ve iç içe geçmiş türler adıyla ayırt edilir. 

* Yöntemler, özellikler ve aynı ada sahip olayları birden fazla yalnızca dönüş türüne göre farklı olmalıdır. 

Aşağıdaki örnek üye adlarını kendi kapsamı içinde benzersiz olmalıdır gereksinim gösterilmektedir. Adlı bir sınıf tanımlar `Converter` adlı dört üyeleri içeren `Conversion`. Üç yöntemlerdir ve bir özelliktir. İçeren yöntemi bir `Int64` parametresi benzersiz olarak adlandırılır, ancak iki yöntemle bir `Int32` parametresi değildir, çünkü dönüş değeri bir üyenin imza bir parçası olarak kabul edilmez. `Conversion` Özelliği özelliklerin aşırı yüklenmiş yöntemler adıyla aynı olduğundan bu gereksinim ayrıca ihlal. 

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

Dilleri hedefleyen ortak dil çalışma zamanı da anahtar sözcükler ile çakıştığı tanımlayıcıları (gibi tür adları) başvuran için bazı mekanizma sağlamanız gerekir benzersiz anahtar sözcükler, tek tek dilleri içerir. Örneğin, `case` hem C# ve Visual Basic bir anahtar sözcüktür. Ancak, aşağıdaki Visual Basic örnek adlı bir sınıf belirsizliğini ortadan kaldırmak mümkün `case` gelen `case` açma ve küme ayraçları kapatma kullanarak anahtar sözcüğü. Aksi takdirde, örnek "Anahtar sözcüğü bir tanımlayıcı olarak geçerli değil" hata iletisi oluşturmak ve bu derlemek başarısız. 

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

Aşağıdaki C# örnek örneği yapabiliyor `case` kullanarak sınıfı @ simgesinden dil anahtar sözcüğünü tanımlayıcıdan belirsizliğini ortadan kaldırmak için. Bu olmadan, C# Derleyici iki hata iletileri, "Tür bekleniyor" ve "geçersiz ifade terimi 'case'." görüntüler 

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

### <a name="type-conversion"></a>Tür dönüştürmeleri

Ortak dil belirtimi iki dönüşüm işleçleri tanımlar:

* `op_Implicit`, hangi veri veya duyarlık kaybına neden değil dönüşümleri için kullanılır. Örneğin, [ondalık](xref:System.Decimal) yapısı içeren bir aşırı yüklenmiş `op_Implicit` tam sayı türleri değerini dönüştürmek için işleci ve [Char](xref:System.Char) değerler `Decimal` değerleri. 

* `op_Explicit`, hangi daraltma (daha küçük bir aralık sahip bir değer için bir değer dönüştürülen) büyüklük veya duyarlık kaybına yol açabilir dönüşümleri için kullanılır. Örneğin, `Decimal` yapısı içeren bir aşırı yüklenmiş `op_Explicit` dönüştürmek için işleci [çift](xref:System.Double) ve [tek](xref:System.Single) değerler `Decimal` ve dönüştürmek için `Decimal` değerler tam sayı değerleri `Double`, `Single`, ve `Char`. 

Ancak, tüm diller İşleç aşırı yüklemesi ya da özel işleçleri tanımını desteklemez. Bu dönüşüm işleçleri uygulamak isterseniz dönüştürme gerçekleştirmek için alternatif bir yöntem sağlaması gerekir. Sağlamanızı öneririz `From`Xxx ve `To`Xxx yöntemleri. 

Aşağıdaki örnek, CLS uyumlu örtük ve açık dönüştürmeler tanımlar. Oluşturduğu bir `UDouble` imzalı çift duyarlıklı, kayan noktalı sayıyı temsil eden sınıf. Örtük dönüşümler sağlayan `UDouble` için `Double` ve açık dönüştürmeler `UDouble` için `Single`, `Double` için `UDouble`, ve `Single` için `UDouble`. Ayrıca tanımlayan bir `ToDouble` örtük dönüşüm işleci alternatif olarak yöntemi ve `ToSingle`, `FromDouble`, ve `FromSingle` açık dönüşüm işleçleri alternatifleri olarak yöntemler. 

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

CLS uyumlu diziler aşağıdaki kurallara uygun: 

* Bir dizinin tüm boyutları alt sınırı sıfır olmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan bir dizi alt sınır bir oluşturur. Unutmayın, varlığını rağmen [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği derleyici algılamazsa tarafından döndürülen dizi `Numbers.GetTenPrimes` yöntem CLS uyumlu değildir. 

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

* Tüm dizi öğeleri CLS uyumlu türleri oluşmalıdır. Aşağıdaki örnek, CLS uyumlu olmayan dizileri döndürür iki yöntemleri tanımlar. İlk bir dizi döndürür [UInt32](xref:System.UInt32) değerleri. İkinci döndürür bir [nesne](xref:System.Object) içeren bir dizi [Int32](xref:System.Int32) ve `UInt32` değerleri. İlk dizi uyumsuz olarak nedeniyle derleyici tanımlasa da, `UInt32` türü, başarısız ikinci dizi CLS uyumlu olmayan öğeler içeriyor tanımadığı. 

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

* Dizi parametrelerine sahip yöntemleri için aşırı yükleme çözünürlüğü diziler oldukları dayanarak açık nedeni olduğunu ve bunların öğe türü bilinmiyor. Bu nedenle, aşırı yüklenmiş bir aşağıdaki tanımını `GetSquares` yöntem CLS uyumlu değil. 

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

CLS uyumlu arabirimleri özellikleri, olayları ve sanal yöntemler (uygulaması yöntemleriyle) tanımlayabilirsiniz. CLS uyumlu bir arabirim aşağıdakilerden herhangi birini içeremez: 

* Statik yöntemler veya statik alanları. Bir arabirim, statik bir üyenin tanımlarsanız, C# Derleyici generatse derleyici hataları. 

* Alanlar. Bir alan bir arabirim tanımlarsanız, C# acompiler derleyici hataları oluşturur.

* CLS uyumlu olmayan yöntemleri. Örneğin, aşağıdaki arabirim tanımı bir yöntem içerir `INumber.GetUnsigned`, yani olarak-CLS uyumlu olmayan olarak işaretlenmiş. Bu örnek derleyici uyarısı oluşturur. 

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

  Bu kural nedeniyle CLS uyumlu türleri CLS uyumlu olmayan üyeler uygulamak için gerekli değildir. CLS dışı uyumlu arabirimini uygulayan bir sınıf CLS uyumlu bir çerçeve kullanıma, CLS uyumlu olmayan tüm üyelerin somut uygulamaları da sağlamalıdır. 

CLS uyumlu dil derleyicileri aynı ad ve imza birden çok arabirimlerde sahip üyeler ayrı uygulamalarını için bir sınıf de izin vermeniz gerekir. C# aynı adlı yöntemlerin farklı uygulamaları sağlamak için açık arabirim uygulamaları destekler. Aşağıdaki örnekte, tanımlayarak bu senaryo gösterilmektedir bir `Temperature` uygulayan sınıf `ICelsius` ve `IFahrenheit` arabirimleri açık arabirim uygulamaları olarak. 

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

CLS uyumlu numaralandırmalar bu kurallara uymalıdır: 

* Temel alınan numaralandırması iç CLS uyumlu Tamsayı türünde olmalıdır ([bayt](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), veya [Int64](xref:System.Int64)). Örneğin, temel alınan türü olan bir numaralandırma tanımlamak aşağıdaki kodu çalışır [UInt32](xref:System.UInt32) ve derleyici uyarısı oluşturur. 

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

* Bir numaralandırma türü adlı tek örnek alanı olmalıdır `Value__` ile işaretlenmiş `FieldAttributes.RTSpecialName` özniteliği. Bu alan değeri örtük olarak başvuru sağlar. 

* Numaralandırma, türü numaralandırma türüyle eşleşen değişmez değer statik alanları içerir. Örneğin, tanımladığınız bir `State` değerlerle numaralandırma `State.On` ve `State.Off`, `State.On` ve `State.Off` türü olan iki değişmez değer statik alanları `State`. 

* Numaralandırmalar iki tür vardır: 
    
    * Birbirini dışlayan kümesini temsil eden numaralandırma adlı tamsayı değerleri. Bu numaralandırma türü yokluğu tarafından gösterilen [System.FlagsAttribute](xref:System.FlagsAttribute) özel öznitelik.
    
    * Adsız bir değer üretmek için birleştirebilirsiniz bit bayrakları kümesini temsil eden bir numaralandırması. Bu numaralandırma türü varlığını tarafından gösterilen [System.FlagsAttribute](xref:System.FlagsAttribute) özel öznitelik.
    
 Daha fazla bilgi için belgelerine bakın [Enum](xref:System.Enum) yapısı. 

* Numaralandırma değeri, belirtilen değer aralığı için sınırlı değildir. Diğer bir deyişle, numaralandırma değerlerinin aralığını temel değerini aralığıdır. Kullanabileceğiniz `Enum.IsDefined` belirtilen bir değeri bir numaralandırma üyesi olup olmadığının yöntemi. 

### <a name="type-members-in-general"></a>Genel üyeleri yazın

Ortak dil belirtimi, tüm alanları ve belirli bir sınıfın bir üyesi olarak erişilecek yöntemleri gerektirir. Bu nedenle, genel statik alanları ve yöntemleri (diğer bir deyişle, statik alanları veya dışında bir türü tanımlanmadı yöntemleri) CLS uyumlu değildir. Genel alan veya yöntem kaynak kodunuzda eklemeye çalışırsanız, C# Derleyici derleyici hatası oluşturur. 

Yalnızca standart çağırma yönetilen ortak dil belirtimi destekler. Yönetilmeyen çağırma kurallarını desteklemez ve değişken bağımsız değişken listeleri yöntemleriyle işaretlenmiş `varargs` anahtar sözcüğü. Standart yönetilen çağırma kuralı ile uyumlu olan değişken bağımsız değişken listeleri için kullanmak [ParamArrayAttribute](xref:System.ParamArrayAttribute) özniteliği ya da tek tek dil uygulaması gibi `params` C# anahtar sözcüğü ve `ParamArray` Visual Basic anahtar sözcüğü. 

### <a name="member-accessibility"></a>Üye erişilebilirlik

Devralınmış bir üyeyi geçersiz kılma bu üyede erişilebilirliğini değiştiremezsiniz. Örneğin, bir taban sınıf ortak yönteminde, türetilmiş bir sınıf içinde özel bir yöntem tarafından değiştirilemiyor. Bir istisna vardır: bir `protected internal` (C# ' ta) veya `Protected Friend` (Visual Basic'te) farklı bir derlemedeki bir türe göre geçersiz bir derleme üyesi.  Bu durumda, geçersiz kılma erişilebilirliğini olduğu `Protected`. 

Aşağıdaki örnek hata gösterilmektedir oluşturulan [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği `true`, ve `Person`, hangi bir sınıfın türetildiği `Animal`, değiştirmeye çalışırsa erişilebilirliğini `Species` ortak özelliğinden özel. Kendi erişilebilirlik ortak olarak değiştirilirse örnek başarıyla derler. 

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

Bu üye erişilebilir olduğunda imza türlerinde üyenin erişilebilir olması gerekir. Örneğin, bu ortak üyesi özel, korumalı veya dahili türü olan bir parametre içeremez anlamına gelir. Aşağıdaki örnek sonuçları derleyici hatası gösterilmektedir, bir `StringWrapper` sınıfı oluşturucusu kullanıma sunan bir iç `StringOperationType` bir dize değeri nasıl alınmalı belirler numaralandırma değeri. 

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

### <a name="generic-types-and-members"></a>Genel türler ve üyeleri

İç içe geçmiş türler, kendilerini kapsayan türle her zaman en az sayıda genel parametrelere sahip. Bunlar, kendilerini kapsayan türle genel parametreler konuma göre karşılık gelir. Genel tür yeni genel parametreler de içerir. 

Genel tür parametreleri içeren bir türde ve iç içe geçmiş türler arasındaki ilişki tek tek dilleri sözdizimi tarafından gizlenmiş olabilir. Aşağıdaki örnekte, genel bir tür `Outer<T>` iki iç içe geçmiş sınıflar içeren `Inner1A` ve `Inner1B<U>`. Çağrıları `ToString` her sınıfının devraldığı yöntemi `Object.ToString`, her iç içe geçmiş sınıf kapsayan sınıfı tür parametrelerini içerdiğini gösterir. 

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

Genel tür adları biçiminde kodlanmış *adı*'*n*, burada *adı* tür adı *`* bir karakter değişmez değeri değil ve *n* türünde bildirilen parametrelerin sayısı veya genel iç içe geçmiş için türleri, yeni sunulan türü parametre sayısı. Bu genel tür adları CLS uyumlu bir Kitaplığı'nda genel türler erişmek için yansıma kullanan geliştiriciler öncelikle ilgisini kodlamadır. 

Bir genel kısıtlamalar uyguladıysanız kısıtlamaları da CLS ile uyumlu olması gerektiği kullanılan türleri yazın. Aşağıdaki örnek adlı bir sınıf tanımlar `BaseClass` yani değil CLS ile uyumlu ve adlı genel bir sınıf `BaseCollection` , tür parametresi öğesinden türetilmelidir `BaseClass`. Ancak çünkü `BaseClass` CLS uyumlu olmayan bir uyarı derleyicisi yayar. 

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

Genel bir tür genel bir temel türden türetilmiş, böylece temel türü kısıtlamaları da karşılanır garanti edebilir kısıtlamalar redeclare gerekir. Aşağıdaki örnek tanımlayan bir `Number<T>` herhangi bir sayısal tür temsil edebilir. Ayrıca tanımlayan bir `FloatingPoint<T>` kayan temsil eden sınıf noktası değeri. Bu kısıtlama geçerli değildir çünkü ancak, Kaynak Kodu derlemek başarısız `Number<T>` (T değeri türü olması gerekir) için `FloatingPoint<T>`.

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

Kısıtlama eklenirse, örnek başarıyla derlenen `FloatingPoint<T>` sınıfı.

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

Ortak dil belirtimi, iç içe geçmiş türler için koruyucu örneklemesi başına modeli uygular ve korumalı üyeler. Açık genel türler alanları veya iç içe geçmiş, korumalı bir genel türü belirli bir örnek oluşturma içeren imzaları üyeleriyle gösteremez. Belirli bir örnek oluşturma genel temel sınıf veya arabirim genişletmek olmayan genel türleri, alanlar veya iç içe geçmiş, korumalı bir genel türü farklı bir örnek oluşturma içeren imzaları üyeleriyle gösteremez.

Aşağıdaki örnek, genel bir tür tanımlar `C1<T>`ve korumalı bir sınıf `C1<T>.N`. `C1<T>` iki yöntemi vardır `M1` ve `M2`. Ancak, `M1` döndürmeye çalışır CLS uyumlu olmadığından bir `C1<int>.N` nesnesinin `C1<T>`. İkinci sınıfı `C2`, türetildiği `C1<long>`. İki yöntemi vardır `M3` ve `M4`. `M3` döndürmeye çalışır CLS uyumlu olmadığından bir `C1<int>.N` öğesinin bir alt nesne `C1<long>`. Dil derleyicileri daha kısıtlayıcı olabileceğini unutmayın. Derlemeye çalıştığında bu örnekte, Visual Basic hata görüntüler. `M4`. 

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

CLS uyumlu sınıfları ve yapıları oluşturucular bu kurallara uymalıdır: 

* Devralınan örnek veri erişim izni vermeden önce türetilmiş bir sınıf oluşturucusunun olduğu temel sınıfın örneği oluşturucusu çağırmanız gerekir. Taban sınıf oluşturucular kendi türetilmiş sınıflar tarafından devralınır değil due için bu gereksinim olabilir. Bu kural doğrudan devralma desteklemeyen yapıları için geçerli değildir. 

  Genellikle, bu kural aşağıdaki örnekte gösterildiği gibi CLS uyumluluğu bağımsız olarak derleyicileri uygulayın. Oluşturduğu bir `Doctor` türetilmiş sınıf bir `Person` sınıfı, ancak `Doctor` sınıfı başarısız çağırmak `Person` devralınan örneği alanları başlatmak için sınıf oluşturucu. 

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
    
* Bir nesne oluşturucusu, nesneyi oluşturmak için dışında çağrılamaz. Ayrıca, bir nesne iki kez başlatılamaz. Örneğin, bunun anlamı `Object.MemberwiseClone` oluşturucular çağırmalısınız değil.  

### <a name="properties"></a>Özellikler

CLS uyumlu türleri özelliklerinde bu kurallara uymalıdır:

* Özellik ayarlayıcı, bir alıcı ya da her ikisini de olması gerekir. Derlemede, bu özel yöntemleri, ayrı yöntemleri olarak görünürler yani uygulanır (alıcı adlı `get` \_ *propertyname* ve kurucu `set*\_*propertyname*) marked as `SpecialName' ın derlemenin meta veriler. Bu kural uygulamak için otomatik olarak gerek kalmadan C# Derleyici zorlar [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği. 

* Bir özelliğin özellik alıcısı dönüş türü ve kurucu son bağımsız değişkeni türüdür. Bu tür CLS uyumlu olması gerekir ve bağımsız değişkenler atanamaz özelliğine başvuruya göre (diğer bir deyişle, bunlar yönetilen işaretçileri olamaz). 

* Bir özelliği hem alıcı hem de ayarlayıcı varsa, bunlar hem de sanal olmalıdır hem statik ya da her iki örneği. C# derleyici otomatik olarak bu kural özellik tanımı sözdizimi aracılığıyla zorlar. 

### <a name="events"></a>Olaylar

Bir olay adını ve türünü tarafından tanımlanır. Olay türü olay göstermek için kullanılan bir temsilcisidir. Örneğin, `DbConnection.StateChange` olay türüdür `StateChangeEventHandler`. Olayın kendisi, ek olarak, üç yöntem olay adına göre adlarıyla olayın uygulamasını sağlamak ve olarak işaretlenmiş `SpecialName` derlemenin meta verilerini de: 

* Adlı bir olay işleyicisi eklemek için bir yöntem `add`_*EventName*. Örneğin, abonelik için olay yöntemi `DbConnection.StateChange` olay adlandırılan `add_StateChange`. 

* Adlı bir olay işleyicisi kaldırmak için bir yöntem `remove`_*EventName*. Örneğin, temizleme yöntemi için `DbConnection.StateChange` olay adlandırılan `remove_StateChange`.

* Olay oluştu, belirten yöntemi adlı `raise`_*EventName*. 

> [!NOTE]
> Ortak dil belirtimi'nın kuralları olayları ile ilgili çoğu dil derleyicileri tarafından uygulanan ve Bileşen geliştiriciler için saydamdır. 

Eklemek için yöntemleri, kaldırma ve olayı tetiklenmeden aynı erişilebilirlik olması gerekir. Bunlar ayrıca tüm statik olmalıdır örneği veya sanal. İçin yöntemler ekleme ve kaldırma bir olay türü olay temsilci türü olan bir parametre vardır. Add ve remove yöntemlerini hem de mevcut olmalıdır veya her ikisi de yok. 

Aşağıdaki örnek adlı CLS uyumlu bir sınıfı tanımlar `Temperature` olayını bir `TemperatureChanged` iki okumalar arasında sıcaklık değişikliği değerine eşit veya eşik değeri, olay. `Temperature` Sınıfı açıkça tanımlayan bir `raise_TemperatureChanged` yöntemi olan olay işleyicileri seçmeli olarak çalıştırabilirsiniz.

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

Ortak dil belirtimi aşırı yüklenmiş üyeler aşağıdaki gereksinimleri getirir: 

* Üyeleri parametrelerin sayısı ve herhangi bir parametre türünü temel alan aşırı yüklenmiş. Çağırma kuralı, dönüş türü, özel değiştiricileri yöntemi veya onun parametresi uygulanır ve parametreleri değere veya başvuruya göre geçirilir dikkate alınmaz zaman overloads arasında ayrım yapma. Adları gereksinim bir kapsam içinde benzersiz olmalıdır, bir örnek için kodu görmek [adlandırma kuralları](#naming-conventions) bölümü. 

* Yalnızca özelliklerini ve yöntemlerini aşırı yüklenmiş. Alanlar ve olayları aşırı yüklenemez. 

* Genel yöntemler genel parametrelerini sayısına göre aşırı yüklenmiş. 

> [!NOTE]
>`op_Explicit` Ve `op_Implicit` işleçleri aşırı yükleme çözünürlüğü için bir yöntem imzası parçası değeri dikkate alınmaz döndüren kural istisnalar mevcuttur. Bu iki işleç parametrelerini ve dönüş değerlerine göre aşırı yüklenmiş. 

### <a name="exceptions"></a>Özel Durumlar

Özel durum nesneleri öğesinden türetilmelidir [System.Exception](xref:System.Exception) veya başka bir türden türetilmiş `System.Exception`. Aşağıdaki örnek adlı özel bir sınıf sonuçlara derleyici hatası gösterilmektedir `ErrorClass` özel durum işleme için kullanılır.

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

Bu hatayı düzeltmek için `ErrorClass` sınıfı öğesinden devralmalıdır `System.Exception`. Ayrıca, ileti özelliği geçersiz kılınmalıdır. Aşağıdaki örnek tanımlamak için bu hataları düzeltir bir `ErrorClass` CLS uyumlu sınıfı.  

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

In.NET Framework derlemeleri özel öznitelikler özel öznitelikleri depolamak ve derlemeler, türleri, üyeleri ve yöntem parametreleri gibi nesneler programlama hakkındaki meta verilerini alma için genişletilebilir bir mekanizma sağlar. Özel öznitelikler öğesinden türetilmelidir [System.Attribute'un](xref:System.Attribute) veya türetilmiş bir türden `System.Attribute`.

Aşağıdaki örnek, bu kural ihlal ediyor. Bunu tanımlayan bir `NumericAttribute` türünden türemez sınıfı `System.Attribute`. Derleyici Hatası sınıfı tanımlanmadığında yalnızca zaman CLS uyumlu olmayan özniteliği, uygulanan sonuçları unutmayın. 

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

Oluşturucunun ya da CLS uyumlu bir özniteliğin özelliklerini yalnızca şu türleri getirebilir:

* [Boole değeri](xref:System.Boolean)

* [Bayt](xref:System.Byte)

* [char](xref:System.Char)

* [Çift](xref:System.Double)

* [Int16](xref:System.Int16)

* [Int32](xref:System.Int32)

* [Int64](xref:System.Int64)

* [Tek](xref:System.Single)

* [Dize](xref:System.String)

* [Türü](xref:System.Type)

* Temel alınan türü olan herhangi bir numaralandırma türü `Byte`, `Int16`, `Int32`, veya `Int64`. 

Aşağıdaki örnek tanımlayan bir `DescriptionAttribute` öğesinden türetilen sınıf [özniteliği](xref:System.Attribute). Türünde bir parametre sınıfı kurucusunun `Descriptor`, bu sınıf CLS uyumlu değil. C# Derleyici bir uyarı gösterir ancak başarıyla derlenen unutmayın. 

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

[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) öznitelik, bir program öğesi ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır. `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Oluşturucusu içeren tek bir gerekli parametre *isCompliant*, bir program öğesi CLS ile uyumlu olup olmadığını gösterir. 

Derleme zamanında derleyici CLS ile uyumlu olması için varsayılan ve bir uyarı yayar uyumlu olmayan öğeler algılar. Derleyici uyarıları türler veya uyumlu olması için açıkça bildirilen üyeler için yayma değil. 

Bileşen geliştiricileri kullanabilir `CLSCompliantAttribute` öznitelik iki yolla: 

* CLS uyumlu bir bileşen tarafından kullanıma sunulan ortak arabirimi bölümlerini ve CLS uyumlu olmayan bölümleri tanımlamak için. Kullanımı öznitelik belirli programın öğeleri CLS ile uyumlu işaretlemek için kullanıldığında, bu öğeleri tüm diller ve .NET Framework hedefleyen Araçlar menüsünden erişilebilir olduğunu güvence altına alır. 

* Bileşen kitaplığın ortak arabirim, CLS uyumlu program öğelerini oluşturduğuna emin olmak için. Öğeleri CLS ile uyumlu değilse, derleyicileri genellikle bir uyarı verecek.

> [!WARNING]
> Bazı durumlarda, dil derleyicileri mi bakılmaksızın CLS uyumlu kuralları zorla `CLSCompliantAttribute` özniteliği kullanılır. Örneğin, tanımlayan bir `*static` bir arabirim üye CLS kuralını ihlal ediyor. Ancak, tanımlarsanız bir `*static` bir arabirim üye, C# Derleyici bir hata iletisi ile başarısız uygulama derlemek için görüntüler.

`CLSCompliantAttribute` Özniteliği ile işaretlenmiş bir [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) değerine sahip öznitelik `AttributeTargets.All`. Bu değer uygulamanıza imkan sağlayan `CLSCompliantAttribute` özniteliği derlemeler, modüller de dahil olmak üzere herhangi bir program öğesi için türleri (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), üyeleri (Oluşturucular, yöntemler, özellikler, alanları ve olaylar), yazın Parametreler, genel parametreler ve dönüş değerleri. Bununla birlikte, pratikte, öznitelik yalnızca derlemeler, türleri ve tür üyeleri uygulamalıdır. Aksi takdirde derleyicileri öznitelik yoksay ve her genel parametresi, uyumlu olmayan bir parametre karşılaştığınız veya dönüş değeri kitaplığınızın ortak arabiriminde derleyici uyarıları oluşturmaya devam.  

Değeri `CLSCompliantAttribute` özniteliği kapsanan program öğeleri tarafından devralınır. Bir derlemeyi CLS ile uyumlu işaretlenmişse, örneğin, türlerinden ayrıca CLS uyumlu değildir. Bir tür CLS ile uyumlu işaretlenmişse, kendi iç içe geçmiş türler ve üyeleri ayrıca CLS uyumlu değildir. 

Devralınan uyumluluk uygulayarak açıkça geçersiz kılabilirsiniz `CLSCompliantAttribute` özniteliği kapsanan bir program öğesi için. Örneğin, kullanabileceğiniz `CLSCompliantAttribute` ile öznitelik bir *isCompliant* değerini `false` uyumlu bir derleme ve, uyumlu olmayan bir tür tanımlamak için öznitelik kullanabilirsiniz bir *isComplian*değerini `true` uyumlu bir türü uyumlu olmayan bir derlemede tanımlamak için. Ayrıca, uyumlu bir türü uyumlu olmayan üyeler tanımlayabilirsiniz. Ancak, dolayısıyla özniteliğiyle kullanamaz uyumlu üyeler uyumlu olmayan bir türü olamaz bir *isCompliant* değerini `true` uyumlu olmayan türünden devralma geçersiz kılmak için. 

Bileşenleri geliştirirken, her zaman kullanmalısınız `CLSCompliantAttribute` derlemenizi, kendi türleri ve üyeleri CLS ile uyumlu olup olmadığını belirtmek için öznitelik. 

CLS uyumlu bileşenleri oluşturmak için: 

1. Kullanım `CLSCompliantAttribute` Derleme CLS uyumlu olarak işaretlemek için.

2. CLS uyumlu olarak uyumlu olmayan derlemesindeki genel olarak sunulan türler işaretleyin. 

3. CLS uyumlu türleri uyumsuz olarak genel kullanıma sunulan tüm üyelerinde işaretleyin. 

4. CLS uyumlu alternatifi CLS uyumlu olmayan üyeler için sağlar. 

Tüm uyumlu olmayan türleri ve üyeleri başarıyla işaretlediyseniz, derleyici hiçbir uyumsuzluk uyarıları yayma değil. Ancak, hangi üyeleri CLS uyumlu değildir ve bunların CLS uyumlu alternatifleri, ürün belgelerinde listesinde belirtmeniz gerekir. 

Aşağıdaki örnek kullanır `CLSCompliantAttribute` CLS uyumlu bir derleme ve bir tür tanımlamak için öznitelik `CharacterUtilities`, iki CLS uyumlu olmayan üyeler içeriyor. Her iki üyeleri ile etiketlenir çünkü `CLSCompliant(false)` özniteliği, derleyici hiçbir uyarılar üretir. Sınıf, CLS uyumlu alternatifi için iki yöntem de sağlar. Normalde, biz yalnızca iki aşırı eklediğiniz `ToUTF16` yöntem CLS uyumlu alternatifleri sağlayın. Ancak, dönüş değerini temel yöntemlerini aşırı yüklenemez olduğundan, uyumlu olmayan yöntemleri adlarından adları CLS uyumlu yöntemlerin farklıdır.  

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

Varsa (diğer bir deyişle, türler veya diğer uygulama geliştiriciler tarafından kullanılan üyeler gösterme değil ise) bir kitaplık yerine bir uygulama geliştirdiğiniz, uygulamanızı tüketen program öğelerin CLS uyumluluğu ilgi yalnızca dilinizi bunları desteklemiyorsa . Bu durumda, CLS uyumlu olmayan bir öğe kullanmaya çalıştığınızda, dil derleyici bir hata oluşturur. 

## <a name="cross-language-interoperability"></a>Diller Arası Birlikte Çalışabilirlik

Dil bağımsızlığının birkaç olası anlamı vardır. Sorunsuz bir şekilde başka bir dilde bir uygulamadan bir dilinde yazılmış türlerini kullanan bir anlam içerir. Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir. 

Aşağıdaki örnekte, iki sınıf içerir Utilities.dll adlı bir sınıf kitaplığı oluşturarak diller arası birlikte çalışabilirlik gösterilmektedir `NumericLib` ve `StringLib`. `NumericLib` Sınıfı yazılır C# ' ta ve `StringLib` sınıfı, Visual Basic'te yazılır. Kaynak kodu işte `StringUtil.vb`, tek bir üyeyi içeren `ToTitleCase`, kendi `StringLib` sınıfı.

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

Tek bir derleme iki sınıflarda paketlemek için modüllerine derlemesi gerekir. Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın: 

```
vbc /t:module StringUtil.vb 
```

C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:

```
csc /t:module NumberUtil.cs
```

Bir derlemeye iki modülleri derlemek için bağlantı aracını (Link.exe) kullanın: 

```
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

Aşağıdaki örnek daha sonra çağırır `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemleri. Visual Basic kodu ve C# kodu her iki sınıfları yöntemleri erişebilir olduğuna dikkat edin.

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

C# ile derlemek için csc için vbc derleyici adını değiştirmek ve dosya uzantısını .cs için .vb değiştirin:

```
csc example.cs /r:UtilityLib.dll
```

