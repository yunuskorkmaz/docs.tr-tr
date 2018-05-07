---
title: Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- value types [C#]
- reference types [C#]
- types [C#]
- C# language, data types
- common type system [C#]
- data types [C#]
- C# language, types
- strong typing [C#]
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
ms.openlocfilehash: 15f3a774255923aba83f15700540369040c02dcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="types-c-programming-guide"></a>Türler (C# Programlama Kılavuzu)
## <a name="types-variables-and-values"></a>Türleri, değişkenler ve değerleri  
 C# bir kesin türü belirtilmiş bir dildir. Bir değer veren her ifade yaptığı gibi her değişken ve sabit bir türe sahip. Her yöntem imzası her giriş parametre ve dönüş değeri için bir türünü belirtir. .NET sınıf kitaplığı çok çeşitli dosya sistemi, ağ bağlantıları, koleksiyonları ve nesneleri ve tarihleri dizileri gibi mantıksal yapıları temsil eden daha karmaşık türlerin yanı sıra yerleşik sayısal türler kümesini tanımlar. Tipik bir C# programı sınıf kitaplığı türlerinden yanı sıra kullanıcı tanımlı türler, programın sorunu etki alanına özgü kavramları modeli kullanır.  
  
 Bir tür depolanan bilgileri aşağıdakileri içerebilir:  
  
-   Türünde bir değişken gerektirir depolama alanı.  
  
-   Temsil edebilir maksimum ve minimum değerler.  
  
-   İçerdiği üyeler (yöntemler, alanları, olayları ve benzeri).  
  
-   Öğesinden devralınan temel türü.  
  
-   Çalışma zamanında değişkenleri için bellek burada ayrılır konumu.  
  
-   İzin verilen işlem türleri.  
  
 Derleyici türü bilgileri kodunuzdaki tüm işlemler olduğundan emin olmak için kullanır. *denkliği*. Örneğin, türünde bir değişken bildirirseniz [int](../../../csharp/language-reference/keywords/int.md), değişkeni ayrıca kullanmanızı ve çıkarma işlemleri derleyici sağlar. Bir değişken türü bu aynı işlemleri gerçekleştirmek deneyin [bool](../../../csharp/language-reference/keywords/bool.md), derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:  
  
 [!code-csharp[csProgGuideTypes#42](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  C ve C++ geliştiriciler, fark, C# ' ta [bool](../../../csharp/language-reference/keywords/bool.md) parametresinin [int](../../../csharp/language-reference/keywords/int.md).  
  
 Derleyici yürütülebilir dosyasına türü bilgisini meta veri olarak katıştırır. Ortak dil çalışma zamanı (CLR) ayırır ve bellek kaldırsa daha fazla tür güvenliği güvence altına almak için çalışma zamanında meta verilerin kullanır.  
  
### <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türlerini belirtme  
 Ne zaman bir değişken bildirme veya sabit bir programda türünü belirtin veya kullanmak [var](../../../csharp/language-reference/keywords/var.md) türü Infer derleyici izin vermek için anahtar sözcüğü. Aşağıdaki örnek, yerleşik sayısal türler ve kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimleri gösterir:  
  
 [!code-csharp[csProgGuideTypes#36](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_2.cs)]  
  
 Yöntem parametreleri ve dönüş değerleri türlerini yöntemi imzada belirtilir. Aşağıdaki imzası gerektiren bir yöntemi gösterir bir [int](../../../csharp/language-reference/keywords/int.md) giriş bağımsız değişken olarak ve bir dize döndürür:  
  
 [!code-csharp[csProgGuideTypes#35](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_3.cs)]  
  
 Bir değişken bildirildikten sonra yeni bir türüyle yeniden bildirilen olamaz ve onun bildirilen türü ile uyumlu olmayan bir değer atanamaz. Örneğin, bildiremezsiniz bir [int](../../../csharp/language-reference/keywords/int.md) ve bir Boolean değeri atamak [doğru](../../../csharp/language-reference/keywords/true-literal.md). Ancak, örneğin yeni değişkenlere atanan veya yöntem bağımsız değişken olarak geçirilen diğer türleri için değerleri dönüştürülebilir. A *yazın dönüştürme* o mu neden veri kaybı derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden bir dönüştürme gerektiren bir *cast* kaynak kodundaki.  
  
 Daha fazla bilgi için bkz: [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="built-in-types"></a>Yerleşik türler  
 C# tamsayı, kayan nokta değerleri, Boole ifadeleri, metin karakterler, ondalık değerleri temsil etmek için yerleşik sayısal türler ve diğer veri türleri standart kümesi sağlar. Ayrıca vardır yerleşik `string` ve `object` türleri. Bu, tüm C# programında kullanmanız için kullanılabilir. Yerleşik türleri hakkında daha fazla bilgi için bkz: [türler için başvuru tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Özel türler  
 Kullandığınız [yapısı](../../../csharp/language-reference/keywords/struct.md), [sınıfı](../../../csharp/language-reference/keywords/class.md), [arabirimi](../../../csharp/language-reference/keywords/interface.md), ve [enum](../../../csharp/language-reference/keywords/enum.md) yapıları kendi özel türleri oluşturmak için. .NET sınıf kitaplığı kendisi, kendi uygulamalarında kullanabileceğiniz Microsoft tarafından sağlanan özel türler koleksiyonudur. Varsayılan olarak, en sık kullanılan türleri sınıf kitaplığı'nda tüm C# programı içinde kullanılabilir. Yalnızca açıkça tanımlanmış derleme proje başvurusu eklediğinizde diğerleri kullanılabilir hale gelir. Derleyici derlemesine başvuru sahip olduktan sonra değişkenlerin (ve sabitleri) türleri bu derleme kaynak kodunda bildirilen bildirebilirsiniz. Daha fazla bilgi için bkz: [.NET sınıf kitaplığı](../../../standard/class-library-overview.md).  
  
## <a name="the-common-type-system"></a>Ortak tür sistemi  
 İki temel noktaları .NET türü sistemde hakkında anlamak önemlidir:  
  
-   Devralma ilkesini destekler. Türler adlı diğer türlerinden türetmek *temel türleri*. Türetilmiş bir tür (bazı sınırlamalarla birlikte) yöntemler, özellikler ve diğer temel türün üyeleri devralır. Temel türü sırayla çalışması türetilmiş bir tür devralma hiyerarşisi içinde her iki temel tür üyeleri devralır başka türü, türetilen. Yerleşik sayısal türler gibi dahil tüm türleri <xref:System.Int32?displayProperty=nameWithType> (C# anahtar sözcüğü: [int](../../../csharp/language-reference/keywords/int.md)), türetilen sonuçta tek taban türünden olduğu <xref:System.Object?displayProperty=nameWithType> (C# anahtar sözcüğü: [nesne](../../../csharp/language-reference/keywords/object.md)). Bu birleşik türü hiyerarşi adı verilen [ortak tür sistemi](../../../standard/base-types/common-type-system.md) (CTS). C# devralma hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
-   Her türde CTS olarak tanımlanan bir *değer türü* veya *başvuru türüne*. Bu, .NET sınıf kitaplığı'nda tüm özel türler ve ayrıca kendi kullanıcı tanımlı türler içerir. Kullanarak tanımladığınız türleri [yapısı](../../../csharp/language-reference/keywords/struct.md) anahtar değer türleri; tüm yerleşik sayısal türler `structs`. Kullanarak tanımladığınız türleri [sınıfı](../../../csharp/language-reference/keywords/class.md) bir anahtar sözcüktür başvuru türleri. Başvuru türleri ve değer türleri farklı derleme zamanı kurallar ve farklı bir çalışma zamanı davranışı sahiptir.  
  
 Aşağıdaki çizimde CTS değer türleri ve başvuru türleri arasındaki ilişkiyi gösterir.  
  
 ![Değer türleri ve başvuru türleri](../../../csharp/programming-guide/types/media/valuetypescts.png "ValueTypesCTS")  
Değer türleri ve CTS türlerinde başvuru  
  
> [!NOTE]
>  En yaygın olarak kullanılan türleri tüm düzenlenir olduğunu görebilirsiniz <xref:System> ad alanı. Ancak, bir değer olup hiçbir ilişki içinde bir tür içeriyordu ad alanına sahip türü veya reference türü.  
  
### <a name="value-types"></a>Değer Türleri  
 Değer türleri türetilen <xref:System.ValueType?displayProperty=nameWithType>, den türetilen <xref:System.Object?displayProperty=nameWithType>. Öğesinden türetilen türler <xref:System.ValueType?displayProperty=nameWithType> CLR özel davranışa sahiptir. Değer türü değişkenleri bellek satır değişkeni bildirilmiş herhangi bir bağlamı içinde ayrılır başka bir deyişle, bunların değerleri doğrudan içerir. Ayrı yığın ayırma veya değer türü değişkenleri için atık toplama yükünü yoktur.  
  
 Değer türleri iki kategorisi vardır: [yapısı](../../../csharp/language-reference/keywords/struct.md) ve [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Yerleşik sayısal yapıları türleridir ve sahip oldukları özellikleri ve yöntemleri erişebilirsiniz:  
  
```csharp  
// Static method on type Byte.  
byte b = Byte.MaxValue;  
```  
  
 Ancak bildirme ve basit olmayan türler değilmiş gibi değerler atayabilirsiniz:  
  
```csharp  
byte num = 0xA;  
int i = 5;  
char c = 'Z';  
```  
  
 Değer türleri *korumalı*, yani, örneğin, bir türünden türetilemez <xref:System.Int32?displayProperty=nameWithType>, ve yapı yalnızca devralınan çünkü herhangi bir kullanıcı tanımlı sınıf veya yapı devralmak için yapı tanımlayamazsınız <xref:System.ValueType?displayProperty=nameWithType> . Ancak, yapı bir veya daha fazla arabirimleri uygulayabilir. Bir arabirim türü bir yapı türüne çevirebilirsiniz; Bu neden olan bir *kutulama* yapısı içinde bir başvuru türü nesnesi yönetilen yığında kaydırma işlemi. Kutulama işlemleri gerçekleşmesi gereken bir yönteme bir değer türü geçirdiğinizde bir <xref:System.Object?displayProperty=nameWithType> giriş parametresi olarak. Daha fazla bilgi için bkz: [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
 Kullandığınız [yapısı](../../../csharp/language-reference/keywords/struct.md) kendi özel değer türleri oluşturmak için anahtar sözcüğü. Genellikle, yapı kapsayıcı olarak bir dizi ilgili değişkenler için aşağıdaki örnekte gösterildiği gibi kullanılır:  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_4.cs)]  
  
 Yapılar hakkında daha fazla bilgi için bkz: [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md). .NET içinde değer türleri hakkında daha fazla bilgi için bkz: [değer türleri](../../../csharp/language-reference/keywords/value-types.md).  
  
 Değer türleri diğer kategori [enum](../../../csharp/language-reference/keywords/enum.md). Enum adlandırılmış tamsayı sabitleri kümesini tanımlar. Örneğin, <xref:System.IO.FileMode?displayProperty=nameWithType> numaralandırma .NET sınıf kitaplığı'nda nasıl bir dosyanın açılması belirtin sabit tamsayılar adlı bir kümesini içerir. Aşağıdaki örnekte gösterildiği gibi tanımlanır:  
 
 [!code-csharp[csProgGuideTypes#44](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_5.cs)]  
  
 `System.IO.FileMode.Create` Sabiti 2 değerine sahip. Ancak, adı için kaynak kodu okuma insanlar çok daha anlamlı ve, nedenden dolayı numaralandırmalar yerine sabit değişmez değer numaralarını kullanmak en iyisidir. Daha fazla bilgi için bkz. <xref:System.IO.FileMode?displayProperty=nameWithType>.  
  
 Tüm numaralandırmaları devralınmalıdır <xref:System.Enum?displayProperty=nameWithType>, devralan <xref:System.ValueType?displayProperty=nameWithType>. Yapılar için geçerli olan tüm kurallar numaralandırmalar için de geçerlidir. Numaralandırmalar hakkında daha fazla bilgi için bkz: [Numaralandırma türleri](../../../csharp/programming-guide/enumeration-types.md).  
  
### <a name="reference-types"></a>Başvuru Türleri  
 Olarak tanımlanan bir tür bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [temsilci](../../../csharp/language-reference/keywords/delegate.md), dizi veya [arabirimi](../../../csharp/language-reference/keywords/interface.md) olan bir *başvuru türüne*. Ne zaman bildirdiğiniz başvuru türünde bir değişken, çalışma zamanında değişken değeri içeren [null](../../../csharp/language-reference/keywords/null.md) açıkça kullanarak bir nesne oluşturma kadar [yeni](../../../csharp/language-reference/keywords/new.md) işleci veya daha eski bir nesne atama başka bir yerde kullanılarak oluşturulan `new`, aşağıdaki örnekte gösterildiği gibi:
  
```csharp  
MyClass mc = new MyClass();  
MyClass mc2 = mc;  
```  
   Bunu uygulayan bir sınıf nesnesi ile birlikte bir arabirim başlatılması gerekir. Varsa `MyClass` uygulayan `IMyInterface`, örneğini oluşturduğunuz `IMyInterface` aşağıdaki örnekte gösterildiği gibi:  
  
```csharp  
IMyInterface iface = new MyClass();  
```  
  
 Nesne oluşturulduğunda, bellek yönetilen yığında ayrılan ve yalnızca bir nesnenin konumunu başvuru değişkeni içerir. Yönetilen yığın türlerinde gerektiren ek yükü bunlar ayırırken hem olarak adlandırılıyor CLR otomatik bellek yönetimi işlevselliğini tarafından talep edilen zaman *çöp toplama*. Ancak, atık toplama ayrıca getirilmiş ve çoğu senaryoda, bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için bkz: [otomatik bellek yönetimi](../../../standard/automatic-memory-management.md).  
  
 Değer türleri öğelerini olsa bile, tüm diziler başvuru türleridir. Diziler örtük olarak türetilen <xref:System.Array?displayProperty=nameWithType> sınıfı, ancak bildirme ve bunları C# tarafından sağlanan Basitleştirilmiş söz dizimi ile aşağıdaki örnekte gösterildiği gibi kullanın:  
  
 [!code-csharp[csProgGuideTypes#45](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_6.cs)]  
  
 Başvuru türleri devralma tam destek sağlar. Bir sınıf oluşturduğunuzda, herhangi bir arabirim veya olarak tanımlanmamış sınıfı devralabilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md), ve diğer sınıflar, sınıfından devralınır ve sanal yöntemleri geçersiz kılın. Kendi sınıflarınızı oluşturma hakkında daha fazla bilgi için bkz: [sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md). Devralma ve sanal yöntemleri hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="types-of-literal-values"></a>Değişmez değer türleri  
 C# ' ta değişmez değerler derleyiciden bir türü alır. Sayı sonuna bir harf ekleyerek tamsayısal bir hazır değer nasıl yazılmalıdır belirtebilirsiniz. Örneğin, 4.56 değeri float ele alınması gerektiğini belirtmek için bir "f" veya "F" sayıdan sonra sonuna: `4.56f`. Harfi yok eklenirse derleyici değişmez değeri için bir tür Infer. İçindeki tek tek türler için başvuru sayfaları hakkında türleri belirtilebilir harf öneklerle daha fazla bilgi için bkz: [değer türleri](../../../csharp/language-reference/keywords/value-types.md).  
  
 Değişmez değerler yazılan ve tüm türleri sonuçta türetilen olduğundan gelen <xref:System.Object?displayProperty=nameWithType>, yazma ve aşağıdaki gibi kod derleme:  
  
 [!code-csharp[csProgGuideTypes#37](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_7.cs)]  
  
## <a name="generic-types"></a>Genel türler  
 Bir veya daha fazla ile bir türü bildirilebilir *tür parametrelerindeki* , gerçek tür için bir yer tutucu olarak hizmet verir ( *somut türü*) türünün bir örneğini oluşturduğunda, istemci kodu sağlayacaktır. Bu tür türleri olarak adlandırılır *genel türler*. Örneğin, .NET türü <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , kural tarafından adı verilen bir tür parametresi sahip *T*. Türünün bir örneği oluşturduğunuzda, bu liste, örneğin, dize içerir nesnelerin türünü belirtin:  
 
```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```
 Tür parametresi kullanımını her öğeye Dönüştür gerek kalmadan herhangi bir türde öğe tutmak için aynı sınıfı yeniden mümkün kılar [nesne](../../../csharp/language-reference/keywords/object.md). Genel koleksiyon sınıfları çağrılır *kesin türü belirtilmiş koleksiyonları* derleyici koleksiyonun öğelerini belirli türünü bilir ve neden olabilir, derleme zamanı IF sırasında bir hata olduğundan, örneğin, bir tamsayı eklemeyideneyin`stringList` önceki örnekte nesnesi. Daha fazla bilgi için bkz: [genel türler](../../../csharp/programming-guide/generics/index.md).  
  
## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Örtük türleri, anonim türler ve boş değer atanabilir türler  
 Daha önce belirtildiği gibi örtük olarak yerel bir değişken (ancak sınıf üyeleri) kullanarak yazabilirsiniz [var](../../../csharp/language-reference/keywords/var.md) anahtar sözcüğü. Değişkeni derleme zamanında hala bir türü alır, ancak türü derleyici tarafından sağlanır. Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Bazı durumlarda depolamak veya yöntemi sınırları dışında geçirmek istemediğiniz ilgili değerleri basit kümeleri için adlandırılmış bir türü oluşturmak uygun değildir. Oluşturabileceğiniz *anonim türler* bu amaç için. Daha fazla bilgi için bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Sıradan değer türleri değerine sahip olamaz [null](../../../csharp/language-reference/keywords/null.md). Ancak, boş değer atanabilen değer türleri affixing tarafından oluşturabileceğiniz bir `?` türü sonra. Örneğin, `int?` olan bir `int` değerini de alabilir türü [null](../../../csharp/language-reference/keywords/null.md). CTS boş değer atanabilir türler genel yapı türünün örnekleridir <xref:System.Nullable%601?displayProperty=nameWithType>. Boş değer atanabilir türler için ve sayısal değerleri null olabilir veritabanlarından veri geçirilirken özellikle yararlıdır. Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Kutulama ve Kutudan Çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
  
-   [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
  
-   [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
  
-   [Genel Türler](../../../csharp/programming-guide/generics/index.md)  

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [XML Veri Türlerini Dönüştürme](../../../standard/data/xml/conversion-of-xml-data-types.md)  
 [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)
