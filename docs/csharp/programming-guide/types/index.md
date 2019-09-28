---
title: Türler- C# Programlama Kılavuzu
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
ms.openlocfilehash: a5ccd0e9e0e3e5bedad06a619be115c362b38e0d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392159"
---
# <a name="types-c-programming-guide"></a>Türler (C# Programlama Kılavuzu)

## <a name="types-variables-and-values"></a>Türler, değişkenler ve değerler

C#türü kesin belirlenmiş bir dildir. Her değişken ve sabitin, bir değeri değerlendiren her ifadeyi olduğu gibi bir türü vardır. Her yöntem imzası her giriş parametresi ve dönüş değeri için bir tür belirtir. .NET sınıf kitaplığı, dosya sistemi, ağ bağlantıları, koleksiyon ve nesne dizileri ve tarihler gibi çok çeşitli mantıksal yapıları temsil eden daha karmaşık türler ve yerleşik sayısal türlerin bir kümesini tanımlar. Tipik C# bir program, sınıf kitaplığından türleri ve programın sorunlu etki alanına özgü kavramları modelleyebilir Kullanıcı tanımlı türleri kullanır.

Bir tür içinde depolanan bilgiler şunları içerebilir:

- Türün bir değişkeninin gerektirdiği depolama alanı.

- Temsil ettiği maksimum ve en düşük değerler.

- İçerdiği Üyeler (Yöntemler, alanlar, olaylar vb.).

- Devraldığı temel tür.

- Değişkenlere yönelik belleğin çalışma zamanında ayrılabileceği konum.

- İzin verilen işlem türleri.

Derleyici, kodunuzda gerçekleştirilen tüm işlemlerin *tür açısından güvenli*olduğundan emin olmak için tür bilgilerini kullanır. Örneğin, [int](../../language-reference/builtin-types/integral-numeric-types.md)türünde bir değişken bildirirseniz, derleyici değişkeni toplama ve çıkarma işlemlerinde kullanmanıza izin verir. [Bool](../../language-reference/keywords/bool.md)türünde bir değişkende aynı işlemleri gerçekleştirmeye çalışırsanız, derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> C ve C++ geliştiricilerle, [bool](../../language-reference/keywords/bool.md) 'un C# [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürülebilir olmadığına dikkat edin.

Derleyici, tür bilgilerini yürütülebilir dosyaya meta veriler olarak katıştırır. Ortak dil çalışma zamanı (CLR), bellek ayırdığı ve geri kazanır daha fazla güvence altına almak için çalışma zamanında bu meta verileri kullanır.

### <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türleri belirtme

Bir programda bir değişken veya sabit belirttiğinizde, onun türünü belirtmeniz veya [var](../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak derleyicinin türü saymasına izin vermelisiniz. Aşağıdaki örnek, hem yerleşik sayısal türler hem de Kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimlerini gösterir:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Yöntem parametrelerinin türleri ve dönüş değerleri Yöntem imzasında belirtilmiştir. Aşağıdaki imza, giriş bağımsız değişkeni olarak bir [int](../../language-reference/builtin-types/integral-numeric-types.md) gerektiren ve bir dize döndüren bir yöntemi gösterir:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Bir değişken oluşturulduktan sonra, yeni bir türle yeniden bildirilemez ve belirtilen türle uyumlu olmayan bir değer atanamaz. Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) bildiremez ve bunu [true](../../language-reference/keywords/true-literal.md)Boolean değeri atayabilirsiniz. Ancak, değerler başka türlere dönüştürülebilir (örneğin, yeni değişkenlere atandığında veya yöntem bağımsız değişkenleri olarak geçirildiğinde). Veri kaybına neden olmayan bir *tür dönüştürmesi* , derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme, kaynak kodda bir *tür dönüştürme* gerektirir.

Daha fazla bilgi için bkz. [atama ve tür dönüştürmeleri](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Yerleşik türler

C#tamsayılar, kayan nokta değerleri, Boole ifadeleri, metin karakterleri, ondalık değerler ve diğer veri türlerini temsil etmek için standart bir yerleşik sayısal türler kümesi sağlar. Ayrıca yerleşik `string` ve `object` türleri vardır. Bunlar, herhangi bir C# programda kullanabilmeniz için kullanılabilir. Yerleşik türler hakkında daha fazla bilgi için bkz. [Yerleşik türler Için başvuru tabloları](../../language-reference/keywords/built-in-types-table.md).

## <a name="custom-types"></a>Özel türler

Kendi özel türlerinizi oluşturmak için [struct](../../language-reference/keywords/struct.md), [Class](../../language-reference/keywords/class.md), [Interface](../../language-reference/keywords/interface.md)ve [enum](../../language-reference/keywords/enum.md) yapılarını kullanırsınız. .NET sınıf kitaplığı, Microsoft tarafından kendi uygulamalarınızda kullanabileceğiniz özel türlerin bir koleksiyonudur. Varsayılan olarak, sınıf kitaplığındaki en sık kullanılan türler her C# programda kullanılabilir. Diğerleri yalnızca tanımlandıkları derlemeye açıkça bir proje başvurusu eklediğinizde kullanılabilir hale gelir. Derleyicinin derlemeye bir başvurusu olduktan sonra, kaynak kodda o derlemede belirtilen türlerin değişkenlerini (ve sabitleri) bildirebilirsiniz. Daha fazla bilgi için bkz. [.NET sınıf kitaplığı](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET 'teki tür sistemi hakkında iki temel noktayı anlamak önemlidir:

- Devralma ilkesini destekler. Türler, *temel türler*olarak adlandırılan diğer türlerden türetilebilir. Türetilmiş tür, yöntemleri, özellikleri ve temel türün diğer üyelerini devralır (bazı kısıtlamalarla). Temel tür başka bir türden türetebilir, bu durumda türetilmiş tür, devralma hiyerarşisindeki her iki temel türün üyelerini devralır. @No__t-C# 0 (anahtar sözcük: [int](../../language-reference/builtin-types/integral-numeric-types.md)) gibi yerleşik sayısal türler dahil olmak üzere tüm türler, sonunda <xref:System.Object?displayProperty=nameWithType> (C# anahtar sözcük: [nesne](../../language-reference/keywords/object.md)) olan tek bir temel türden türetilir. Bu Birleşik tür hiyerarşisine [ortak tür sistemi](../../../standard/base-types/common-type-system.md) (Cts) denir. ' De C#devralma hakkında daha fazla bilgi için bkz. [Devralma](../classes-and-structs/inheritance.md).

- CTS içindeki her tür, bir *değer türü* veya bir *başvuru türü*olarak tanımlanır. Bu, .NET sınıf kitaplığı 'ndaki tüm özel türleri ve ayrıca kendi Kullanıcı tanımlı türlerinizi içerir. [Struct](../../language-reference/keywords/struct.md) anahtar sözcüğünü kullanarak tanımladığınız türler değer türleridir; Tüm yerleşik sayısal türler `structs` ' dir. [Sınıf](../../language-reference/keywords/class.md) anahtar sözcüğünü kullanarak tanımladığınız türler başvuru türleridir. Başvuru türleri ve değer türlerinde farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışları vardır.

Aşağıdaki çizimde, CTS 'deki değer türleri ve başvuru türleri arasındaki ilişki gösterilmektedir.

Aşağıdaki görüntüde, CTS 'deki değer türleri ve başvuru türleri gösterilmektedir:

![CTS değer türlerini ve başvuru türlerini gösteren ekran görüntüsü.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> En yaygın olarak kullanılan türlerin <xref:System> ad alanında düzenlendiğini görebilirsiniz. Ancak, bir türün bulunduğu ad alanının, bir değer türü veya başvuru türü olup olmadığı bir ilişkisi yoktur.

### <a name="value-types"></a>Değer türleri

Değer türleri, <xref:System.Object?displayProperty=nameWithType> ' den türetilen <xref:System.ValueType?displayProperty=nameWithType> ' dan türetilir. @No__t-0 ' dan türetilen türlerin CLR 'de özel davranışı vardır. Değer türü değişkenleri doğrudan değerlerini içerir, bu da belleğin, değişkenin bildirildiği bağlamda satır içi olarak ayrıldığı anlamına gelir. Değer türü değişkenler için ayrı bir yığın ayırma veya çöp toplama ek yükü yoktur.

Değer türlerinin iki kategorisi vardır: [struct](../../language-reference/keywords/struct.md) ve [enum](../../language-reference/keywords/enum.md).

Yerleşik sayısal türler yapı birimleridir ve erişebileceğiniz özelliklere ve yöntemlere sahiptirler:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Ancak bunları, basit olmayan türler gibi bu değerlere bildirir ve bunlara atanır:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Değer türleri *Sealed*olur, yani örneğin, <xref:System.Int32?displayProperty=nameWithType> ' den bir tür türetilemez ve bir yapı yalnızca <xref:System.ValueType?displayProperty=nameWithType> ' den devralabileceği için Kullanıcı tanımlı herhangi bir sınıftan veya yapıdan devralacak bir yapı tanımlayamazsınız. Ancak, bir struct bir veya daha fazla arabirim uygulayabilir. Yapı türünü, uygulayan herhangi bir arabirim türüne çevirebilirsiniz; Bu, bir *kutulama* işleminin yapıyı yönetilen yığında bir başvuru türü nesnesinin içine sarmasına neden olur. Kutulama işlemleri, bir değer türünü <xref:System.Object?displayProperty=nameWithType> veya herhangi bir arabirim türünü giriş parametresi olarak alan bir yönteme geçirdiğinizde oluşur. Daha fazla bilgi için bkz. [kutulama ve kutudan](./boxing-and-unboxing.md)çıkarma.

Kendi özel değer türlerinizi oluşturmak için [struct](../../language-reference/keywords/struct.md) anahtar sözcüğünü kullanırsınız. Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi küçük bir ilgili değişkenler kümesi için kapsayıcı olarak kullanılır:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Yapılar hakkında daha fazla bilgi için bkz. [yapılar](../classes-and-structs/structs.md). .NET 'teki değer türleri hakkında daha fazla bilgi için bkz. [değer türleri](../../language-reference/keywords/value-types.md).

Değer türlerinin diğer kategorisi [sabit listesi](../../language-reference/keywords/enum.md)' dir. Enum, adlandırılmış integral sabitleri kümesini tanımlar. Örneğin, .NET sınıf kitaplığındaki <xref:System.IO.FileMode?displayProperty=nameWithType> numaralandırması, bir dosyanın nasıl açılacağını belirten adlandırılmış sabit tamsayılar kümesi içerir. Aşağıdaki örnekte gösterildiği gibi tanımlanmıştır:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

@No__t-0 sabiti 2 değerine sahiptir. Ancak ad, kaynak kodu okuyan insanlar için çok daha anlamlı olur ve bu nedenle sabit değişmez sayılar yerine Numaralandırmaların kullanılması daha iyidir. Daha fazla bilgi için bkz. <xref:System.IO.FileMode?displayProperty=nameWithType>.

Tüm numaralandırmalar, <xref:System.ValueType?displayProperty=nameWithType> ' den devralan <xref:System.Enum?displayProperty=nameWithType> ' dan devralır. Yapılar için uygulanan tüm kurallar, numaralandırmalar için de geçerlidir. Numaralandırmalar hakkında daha fazla bilgi için bkz. [numaralandırma türleri](../enumeration-types.md).

### <a name="reference-types"></a>Başvuru türleri

[Class](../../language-reference/keywords/class.md), [Delegate](../../language-reference/keywords/delegate.md), array veya [Interface](../../language-reference/keywords/interface.md) olarak tanımlanan bir tür, bir *başvuru türüdür*. Çalışma zamanında, bir başvuru türünde bir değişken bildirdiğinizde, [New](../../language-reference/operators/new-operator.md) işlecini kullanarak açıkça bir nesne [oluşturana veya](../../language-reference/keywords/null.md) bir nesneyi başka bir @no__t yerde oluşturulmuş bir nesne (örneğin, Aşağıdaki örnek:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Bir arabirim, kendisini uygulayan bir sınıf nesnesiyle birlikte başlatılmalıdır. @No__t-0 `IMyInterface` ' i uygularsa, aşağıdaki örnekte gösterildiği gibi bir `IMyInterface` örneği oluşturursunuz:

```csharp
IMyInterface iface = new MyClass();
```

Nesne oluşturulduğunda, bellek yönetilen yığında ayrılır ve değişken yalnızca nesnenin konumuna bir başvuru içerir. Yönetilen yığında bulunan türler, her ikisi de ayrıldıklarında ve *çöp toplama*olarak bilinen clr 'nin otomatik bellek yönetimi işlevselliği tarafından geri kazanıyorsa ek yük gerektirir. Ancak çöp toplama da yüksek oranda iyileştirilmiştir ve çoğu senaryoda bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için bkz. [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md).

Tüm diziler, öğeleri değer türleri olsa bile başvuru türlerdir. Diziler, <xref:System.Array?displayProperty=nameWithType> sınıfından dolaylı olarak türetilir, ancak aşağıdaki örnekte gösterildiği gibi bunları tarafından C#verilen Basitleştirilmiş sözdizimi ile bildirir ve kullanabilirsiniz:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Başvuru türleri devralmayı tamamen destekler. Bir sınıf oluşturduğunuzda, [korumalı](../../language-reference/keywords/sealed.md)olarak tanımlanmayan diğer bir arabirim veya sınıftan kalıtımla alabilir ve diğer sınıflar sınıfınızdan devralınabilir ve sanal yöntemlerinizi geçersiz kılabilir. Kendi sınıflarınızı oluşturma hakkında daha fazla bilgi için bkz. [sınıflar ve yapılar](../classes-and-structs/index.md). Devralma ve sanal yöntemler hakkında daha fazla bilgi için bkz. [Devralma](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Değişmez değer türleri

' C#De, değişmez değerler derleyicisinden bir tür alır. Sayının sonuna bir harf ekleyerek sayısal bir sabit değerin nasıl yazılması gerektiğini belirtebilirsiniz. Örneğin, 4,56 değerinin bir float olarak değerlendirilip değerlendirilmeyeceğini belirtmek için, sayının sonuna bir "f" veya "F" ekleyin: `4.56f`. Hiçbir harf eklenyoksa, derleyici değişmez değer için bir tür çıkarması olur. Hangi türlerin harf sonekleriyle belirtibileceği hakkında daha fazla bilgi için bkz. [değer türlerinde](../../language-reference/keywords/value-types.md)bağımsız türler için başvuru sayfaları.

Değişmez değerler yazıldığı ve tüm türlerin sonunda <xref:System.Object?displayProperty=nameWithType> ' dan türetiğinden, aşağıdaki gibi bir kod yazabilir ve derleyebilirsiniz:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Genel türler

Bir tür, istemci kodunun türün bir örneğini oluşturduğunda sağladığı gerçek tür ( *somut tür*) için yer tutucu olarak görev yapan bir veya daha fazla *tür parametresiyle* bildirilemez. Bu tür türler *Genel türler*olarak adlandırılır. Örneğin, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .NET türü, kuralına göre bir tür parametresine *sahiptir.* Türün bir örneğini oluşturduğunuzda, listenin içereceği nesnelerin türünü (örneğin, dize) belirtirsiniz:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Tür parametresinin kullanımı, her öğeyi [nesneye](../../language-reference/keywords/object.md)dönüştürmek zorunda kalmadan her türlü öğe türünü tutmak için aynı sınıfı yeniden kullanmayı mümkün kılar. Derleyici, koleksiyon öğelerinin belirli türünü bildiğinden ve derleme zamanında bir hata tetikleyebildiğinden, genel koleksiyon sınıfları *kesin türü belirtilmiş koleksiyonlar* olarak adlandırılır ve örneğin, bu durumda `stringList` nesnesine bir tamsayı eklemeye çalışırsanız önceki örnek. Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Örtük türler, anonim türler ve null yapılabilir değer türleri

Daha önce belirtildiği gibi, [var](../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak yerel bir değişkeni (sınıf üyelerini değil) örtük olarak yazabilirsiniz. Değişken hala derleme zamanında bir tür alır, ancak tür derleyici tarafından sağlanır. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).

Bazı durumlarda, yöntem sınırlarını depolamayı veya geçişi istemediğiniz ilgili değerlerin basit kümeleri için adlandırılmış bir tür oluşturmak uygun değildir. Bu amaçla *anonim türler* oluşturabilirsiniz. Daha fazla bilgi için bkz. [anonim türler](../classes-and-structs/anonymous-types.md).

Sıradan değer türlerinin değeri [null](../../language-reference/keywords/null.md)olamaz. Ancak, türden sonra `?` ' ı birleştirerek null yapılabilir değer türleri oluşturabilirsiniz. Örneğin, `int?`, [null](../../language-reference/keywords/null.md)değeri de olan bir `int` türüdür. Null yapılabilir değer türleri, <xref:System.Nullable%601?displayProperty=nameWithType> genel yapı türünün örnekleridir. Null olabilen değer türleri, genellikle sayısal değerlerin null olabileceği veritabanlarına ve veritabanlarından veri geçirirken faydalıdır. Daha fazla bilgi için bkz. [Nullable değer türleri](../nullable-types/index.md).

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için aşağıdaki konulara bakın:

- [Tür Değiştirme ve Tür Dönüştürmeler](./casting-and-type-conversions.md)

- [Kutulama ve Kutudan Çıkarma](./boxing-and-unboxing.md)

- [Tür dinamiği kullanma](./using-type-dynamic.md)

- [Değer Türleri](../../language-reference/keywords/value-types.md)

- [Başvuru Türleri](../../language-reference/keywords/reference-types.md)

- [Sınıflar ve Yapılar](../classes-and-structs/index.md)

- [Anonim Tipler](../classes-and-structs/anonymous-types.md)

- [Genel Türler](../generics/index.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [XML Veri Türlerini Dönüştürme](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Integral türleri](../../language-reference/builtin-types/integral-numeric-types.md)
