---
title: Türleri - C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: 23aae1a41a19689bd5ad4e29f19c8cff704e742c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709695"
---
# <a name="types-c-programming-guide"></a>Türler (C# Programlama Kılavuzu)

## <a name="types-variables-and-values"></a>Türler, değişkenler ve değerleri

C# bir türü kesin belirlenmiş dildir. Bir değere Değerlenen her ifadenin gibi her değişken ve sabit bir türü vardır. Her yöntem imzası bir tür için her giriş parametresi ve dönüş değeri belirtir. .NET sınıf kitaplığı bir yerleşik sayısal türler ve bunun yanı sıra çok çeşitli dosya sistemi, ağ bağlantıları, koleksiyonlar ve diziler nesneleri ve tarihler gibi mantıksal yapıları temsil eden daha karmaşık türleri kümesi tanımlar. Tipik bir C# programı sınıf kitaplığından alınan türleri aynı zamanda programın sorun etki alanına özgü kavramları modelleyen kullanıcı tanımlı türler kullanır.

Bir tür içinde depolanan bilgiler aşağıdakileri içerebilir:

- Bir tür değişkeninin gerektirdiği depolama alanı.

- Temsil edebileceği maksimum ve minimum değerler.

- İçerdiği üyeler (yöntemler, alanlar, olaylar vb.).

- Devraldığı taban türü.

- Değişkenler için belleğin çalışma zamanında burada ayrılacak konumu.

- İzin verilen işlem türleri.

Derleyici, kodunuzda gerçekleştirilen tüm işlemler olduğundan emin olmak için tür bilgilerini kullanır. *denkliği*. Örneğin, türünde bir değişken bildirirseniz [int](../../../csharp/language-reference/keywords/int.md), derleyici değişkeni buna ek olarak kullanmanızı ve çıkarma işlemleri sağlar. Türünde bir değişkende aynı işlemleri gerçekleştirmeyi denerseniz [bool](../../../csharp/language-reference/keywords/bool.md), aşağıdaki örnekte gösterildiği gibi derleyici bir hata oluşturur:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> C ve C++ geliştiricileri seçeneğinde bu C# ' ta [bool](../../../csharp/language-reference/keywords/bool.md) öğesine dönüştürülebilir değildir [int](../../../csharp/language-reference/keywords/int.md).

Derleyicinin tür bilgisini yürütülebilir dosya meta veri olarak gömer. Ortak dil çalışma zamanı (CLR) ayırır ve belleği geri kazanır, daha fazla tür güvenliği sağlamak için çalışma zamanında bu meta verileri kullanır.

### <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türleri belirtme

Ne zaman bir değişken bildirdiğinizde veya sabit bir program, türünü belirtmeniz veya kullanın [var](../../../csharp/language-reference/keywords/var.md) anahtar sözcüğünü kullanarak derleyicinin türü sağlar. Aşağıdaki örnek, hem yerleşik sayısal türler hem de kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimlerini gösterir:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Yöntem parametreleri ve dönüş değerlerinin türleri Yöntem imzasında belirtilir. Aşağıdaki imza gerektiren bir yöntemi gösterir bir [int](../../../csharp/language-reference/keywords/int.md) giriş bağımsız değişkeni olarak bir dize döndürür:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Bir değişken bildirildikten sonra yeni bir türle yeniden bildirilemez ve bildirilen türle uyumlu olmayan bir değer atanamaz. Örneğin, bildiremezsiniz bir [int](../../../csharp/language-reference/keywords/int.md) Boolean değerini atayın [true](../../../csharp/language-reference/keywords/true-literal.md). Ancak, değerler örneğin yeni değişkenlere eklendiklerinde veya yöntem bağımsız değişkenleri olarak geçtiklerinde diğer türlere dönüştürülebilir. A *tür dönüştürme* , yoksa veri kaybına neden olmayan derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme gerektiren bir *atama* kaynak kodunda.

Daha fazla bilgi için [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Yerleşik türler

C# Standart tamsayılar, kayan nokta değerleri, Boolean ifadeler, metin karakterleri, ondalık değerleri temsil etmek için yerleşik sayısal türler ve diğer veri türleri kümesi sağlar. Ayrıca vardır yerleşik `string` ve `object` türleri. Bunlar, bir C# programında kullanabilmeniz için kullanılabilir. Yerleşik türler hakkında daha fazla bilgi için bkz. [türler için başvuru tabloları](../../../csharp/language-reference/keywords/reference-tables-for-types.md).

## <a name="custom-types"></a>Özel türler

Kullandığınız [yapı](../../../csharp/language-reference/keywords/struct.md), [sınıfı](../../../csharp/language-reference/keywords/class.md), [arabirimi](../../../csharp/language-reference/keywords/interface.md), ve [enum](../../../csharp/language-reference/keywords/enum.md) yapılar, kendi özel türlerinizi oluşturmak için. .NET sınıf kitaplığının kendisi, uygulamalarınızda kullanabileceğiniz Microsoft tarafından sağlanan özel türler koleksiyonudur. Varsayılan olarak, Sınıf Kitaplığı'nda en sık kullanılan türleri bir C# programı içinde kullanılabilir. Diğerleri yalnızca açıkça tanımlanmış derlemenin bir proje başvurusu eklediğinizde kullanılabilir. Derleyici derlemesine bir başvuru olduğunda, değişkenler (ve sabitler) türlerinin derlemeye kaynak kodunda bildirilen bildirebilir. Daha fazla bilgi için [.NET sınıf kitaplığı](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET içindeki tür sisteminde iki temel noktanın anlaşılması önemlidir:

- Bu devralma ilkesini destekler. Türleri olarak adlandırılan diğer türlerden türetilebilir *taban türler*. Türetilmiş bir tür, yöntemleri, özellikleri ve diğer temel türün üyelerini (bazı sınırlamalarla birlikte) devralır. Temel tür sırayla durumda türetilmiş tür devralma hiyerarşisinde her iki taban türün üyelerini devralan başka bir türden türeyebilir. Gibi yerleşik sayısal türler dahil olmak üzere tüm türleri <xref:System.Int32?displayProperty=nameWithType> (C# anahtar sözcüğünü: [int](../../../csharp/language-reference/keywords/int.md)), türetilen sonuçta tek temel türünden olduğu <xref:System.Object?displayProperty=nameWithType> (C# anahtar sözcüğünü: [nesne](../../../csharp/language-reference/keywords/object.md)). Bu birleşik tür hiyerarşisine adlı [ortak tür sistemi](../../../standard/base-types/common-type-system.md) (CTS). C# içinde devralma hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).

- Cts'deki her tür olarak tanımlanan bir *değer türü* veya *başvuru türüne*. Bu, .NET sınıf kitaplığı'nda tüm özel türleri ve ayrıca kendi kullanıcı tanımlı türler içerir. Kullanarak tanımladığınız türler [yapı](../../../csharp/language-reference/keywords/struct.md) anahtar değer türleri; tüm yerleşik sayısal türler `structs`. Kullanarak tanımladığınız türler [sınıfı](../../../csharp/language-reference/keywords/class.md) anahtar sözcüğü olan başvuru türleri. Başvuru türleri ve değer türleri farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışı sahiptir.

Aşağıdaki çizim CTS'deki değer türleri ve başvuru türleri arasındaki ilişkiyi gösterir.

Aşağıdaki görüntüde CTS'deki değer türleri ve başvuru türleri gösterilmektedir:

![Gösterir CTS değer türleri ve başvuru türleri ekran görüntüsü.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> Sık kullanılan türlerinin tümünün olduğunu gördüğünüz <xref:System> ad alanı. Ancak türü içeren ad alanı için bir değer olup ilgisi yoktur türü veya başvuru türü.

### <a name="value-types"></a>Değer Türleri

Değer türleri <xref:System.ValueType?displayProperty=nameWithType>, öğesinden türetildiğini <xref:System.Object?displayProperty=nameWithType>. Öğesinden türetilen türler <xref:System.ValueType?displayProperty=nameWithType> CLR içinde özel davranışa sahiptir. Değer türü değişkenler doğrudan değerlerini, değişkenin bildirildiği hangi bağlamda satır içi bellek tahsis edildiği anlamına gelir içerir. Ayrı yığın atama veya değer türü değişkenler çöp toplama taşması yoktur.

Değer türlerinin iki kategorisi vardır: [yapı](../../../csharp/language-reference/keywords/struct.md) ve [enum](../../../csharp/language-reference/keywords/enum.md).

Yerleşik sayısal türler yapı birimleridir ve özellikleri ve yöntemleri erişebileceğiniz sahiptirler:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Ancak bildirmek ve bunların basit toplama olmayan türlermiş gibi bunlara değer atayamazsınız:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Değer türleri *korumalı*, yani, örneğin, bir türden türetilemez <xref:System.Int32?displayProperty=nameWithType>, ve bir yapı yalnızca kaynağından devralabileceğinden bir kullanıcı tanımlı sınıf veya yapıdan devralacak bir yapı tanımlayamazsınız <xref:System.ValueType?displayProperty=nameWithType> . Ancak, bir yapının bir veya daha fazla arabirim uygulayabilir. Bir yapı türünü uygulayan herhangi bir arabirim türüne çevirebilirsiniz; Bu neden olan bir *kutulama* yönetilen yığında struct bir başvuru türü nesnesi içine sarmak için işlemi. Kutulama işlemleri, bir değer türü alan bir yönteme geçirdiğinizde meydana bir <xref:System.Object?displayProperty=nameWithType> veya herhangi bir arabirim türü giriş parametresi olarak. Daha fazla bilgi için [kutulama ve kutudan çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md).

Kullandığınız [yapı](../../../csharp/language-reference/keywords/struct.md) kendi özel değer türlerinizi oluşturmak için anahtar sözcüğü. Genellikle, bir yapının bir kapsayıcı gibi küçük bir ilişkili değişken kümesi için aşağıdaki örnekte gösterildiği gibi kullanılır:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Yapılar hakkında daha fazla bilgi için bkz. [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md). .NET içindeki değer türleri hakkında daha fazla bilgi için bkz. [değer türleri](../../../csharp/language-reference/keywords/value-types.md).

Değer türlerinin diğer kategorisi [enum](../../../csharp/language-reference/keywords/enum.md). Bir numaralandırma, adlandırılmış tam sayı sabitler kümesini tanımlar. Örneğin, <xref:System.IO.FileMode?displayProperty=nameWithType> numaralandırma .NET sınıf kitaplığı'nda adlandırılmış bir dosyanın nasıl açılacağını belirten sabit tamsayı Seti içerir. Aşağıdaki örnekte gösterildiği gibi tanımlanır:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

`System.IO.FileMode.Create` Sabitinin değeri 2'dir. Ancak, ad, kaynak kodu okuyanlar için daha anlamlı olur ve bu nedenle sabit ve değişmez sayılar yerine numaralandırmalar kullanılması daha iyidir. Daha fazla bilgi için bkz. <xref:System.IO.FileMode?displayProperty=nameWithType>.

Tüm numaralandırmalar devralınacak <xref:System.Enum?displayProperty=nameWithType>, işlevinden devralan <xref:System.ValueType?displayProperty=nameWithType>. Yapılar için geçerli olan tüm kurallar numaralandırmalar için de geçerlidir. Numaralandırmalar hakkında daha fazla bilgi için bkz. [Numaralandırma türleri](../../../csharp/programming-guide/enumeration-types.md).

### <a name="reference-types"></a>Başvuru Türleri

Olarak tanımlanan bir tür bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [temsilci](../../../csharp/language-reference/keywords/delegate.md), dizi veya [arabirimi](../../../csharp/language-reference/keywords/interface.md) olduğu bir *başvuru türüne*. Bir değişken bildirdiğinizde başvuru türü, çalışma zamanında değişken değeri içeren [null](../../../csharp/language-reference/keywords/null.md) açıkça kullanarak bir nesne oluşturma kadar [yeni](../../../csharp/language-reference/keywords/new.md) işleci veya olan bir nesne atama başka bir yerde kullanılarak oluşturulan `new`, aşağıdaki örnekte gösterildiği gibi:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Bir arabirim, kendisini uygulayan bir sınıf nesnesiyle birlikte başlatılmalıdır. Varsa `MyClass` uygulayan `IMyInterface`, örneğini oluşturduğunuz `IMyInterface` aşağıdaki örnekte gösterildiği gibi:

```csharp
IMyInterface iface = new MyClass();
```

Nesne oluşturulduğunda bellek yönetilen yığında ayrılır ve değişken yalnızca nesne konumu bir başvuru tutar. Yönetilen yığındaki türler ayrıldıkları zaman hem olarak da bilinen CLR'nin otomatik bellek yönetimi işlevinin tarafından talep edilen zaman ek yükü gerektirir *çöp toplama*. Ancak, çöp toplama yüksek oranda iyileştirilmiştir ve çoğu senaryoda, bir performans sorununa neden olmaz. Çöp toplama hakkında daha fazla bilgi için bkz: [otomatik bellek yönetimi](../../../standard/automatic-memory-management.md).

Öğeleri değer türleri olsa bile, tüm diziler başvuru türleridir. Diziler dolaylı olarak türetilen <xref:System.Array?displayProperty=nameWithType> sınıfı, ancak bildirme ve bunları C# tarafından sağlanan Basitleştirilmiş sözdizimi ile aşağıdaki örnekte gösterildiği gibi kullanın:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Başvuru türleri devralmayı tam olarak destekler. Bir sınıf oluşturduğunuz zaman, herhangi bir arabirim veya tanımlanmamış sınıfı devralabilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md), ve diğer sınıflar, sizin sınıfınızdan miras ve sanal yöntemlerinizi geçersiz kılabilir. Kendi sınıflarınızı nasıl oluşturabileceğiniz hakkında daha fazla bilgi için bkz. [sınıfları ve yapıları](../../../csharp/programming-guide/classes-and-structs/index.md). Devralma ve sanal yöntemler hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Değişmez değer türleri

C# dilinde değişmez değerler derleyiciden bir tür alır. Sayı sonuna bir harf ekleyerek sayısal değişmez değerin nasıl yazılacağını belirtebilirsiniz. Örneğin, 4.56 değerinin kaydırma olarak ele alınması gerektiğini belirtmek için bir "f" veya "F" sayı sonra Ekle: `4.56f`. Hiçbir harf eklenirse, derleyici değişmez değer için bir tür olarak çıkarımlar. Hangi belirtilebilen türler harf sonekleri daha fazla bilgi için her bir türe ilişkin başvuru sayfalarına bakın [değer türleri](../../../csharp/language-reference/keywords/value-types.md).

Değişmez değerler olduğu ve tüm türler nihai olarak türetmek için gelen <xref:System.Object?displayProperty=nameWithType>, yazabilir ve aşağıdaki gibi kodu derleyin:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Genel türler

Bir türü bir veya daha fazla bildirilmiş *tür parametrelerindeki* gerçek tür için bir yer tutucu olarak hizmet veren ( *somut tür*) türün bir örneğini oluşturduğunda, istemci kodunun sağlayacağı. Bu türler olarak adlandırılır *genel türler*. Örneğin, .NET türü <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> gereği adı verilen bir tür parametresine sahip *T*. Bir türün örneğini oluşturduğunuzda dize listesi yer alacak nesnelerin türünü belirtin:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Tür parametresinin kullanımı, her öğesine dönüştürmek zorunda kalmadan herhangi bir türde öğe için aynı sınıf yeniden mümkün kılar [nesne](../../../csharp/language-reference/keywords/object.md). Genel koleksiyon sınıflarına çağrılır *kesin olarak belirtilmiş koleksiyonlar* derleyici koleksiyonun öğelerinin belirli tür bilir ve derleme sırasında bir hata gönderebilirsiniz olduğundan, örneğin, bir tamsayı içineklemeyideneyin`stringList` önceki örnekte nesne. Daha fazla bilgi için [genel türler](../../../csharp/programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Örtülü türler, anonim türler ve boş değer atanabilir türler

Daha önce belirtildiği gibi örtük olarak yerel bir değişken (ancak sınıf üyeleri olmamak) kullanarak yazabilirsiniz [var](../../../csharp/language-reference/keywords/var.md) anahtar sözcüğü. Değişken derleme zamanında hala bir türü alır, ancak türü derleyici tarafından sağlanır. Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).

Bazı durumlarda, bu depolamak veya yöntemi sınırları dışında geçirmek istemediğiniz ilgili değer kümeleri için adlandırılmış bir tür oluşturmak çok kullanışsız olur. Oluşturabileceğiniz *anonim türler* bu amaç için. Daha fazla bilgi için [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).

Sıradan değer türleri değerine sahip [null](../../../csharp/language-reference/keywords/null.md). Ancak, boş değer atanabilen değer türleri ekleyerek oluşturabileceğiniz bir `?` türden sonra. Örneğin, `int?` olduğu bir `int` değeri de olabilir bir tür [null](../../../csharp/language-reference/keywords/null.md). CTS içinde boş değer atanabilir türler genel yapı türünün örnekleridir <xref:System.Nullable%601?displayProperty=nameWithType>. Boş değer atanabilir türler için ve veritabanlarına sayı değerleri null olabilir veri geçirirken özellikle kullanışlıdır. Daha fazla bilgi için [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).

## <a name="related-sections"></a>İlgili Bölümler

Daha fazla bilgi için aşağıdaki konulara bakın:

- [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)

- [Kutulama ve Kutudan Çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md)

- [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)

- [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)

- [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)

- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)

- [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

- [Genel Türler](../../../csharp/programming-guide/generics/index.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [XML Veri Türlerini Dönüştürme](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)
