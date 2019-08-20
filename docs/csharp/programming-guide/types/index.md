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
ms.openlocfilehash: 422613a9016efb55c299f24c50cd2eec6c2c1069
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588407"
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

C#tamsayılar, kayan nokta değerleri, Boole ifadeleri, metin karakterleri, ondalık değerler ve diğer veri türlerini temsil etmek için standart bir yerleşik sayısal türler kümesi sağlar. Ayrıca yerleşik `string` ve `object` türler vardır. Bunlar, herhangi bir C# programda kullanabilmeniz için kullanılabilir. Yerleşik türler hakkında daha fazla bilgi için bkz. [Yerleşik türler Için başvuru tabloları](../../language-reference/keywords/built-in-types-table.md).

## <a name="custom-types"></a>Özel türler

Kendi özel türlerinizi oluşturmak için [struct](../../language-reference/keywords/struct.md), [Class](../../language-reference/keywords/class.md), [Interface](../../language-reference/keywords/interface.md)ve [enum](../../language-reference/keywords/enum.md) yapılarını kullanırsınız. .NET sınıf kitaplığı, Microsoft tarafından kendi uygulamalarınızda kullanabileceğiniz özel türlerin bir koleksiyonudur. Varsayılan olarak, sınıf kitaplığındaki en sık kullanılan türler her C# programda kullanılabilir. Diğerleri yalnızca tanımlandıkları derlemeye açıkça bir proje başvurusu eklediğinizde kullanılabilir hale gelir. Derleyicinin derlemeye bir başvurusu olduktan sonra, kaynak kodda o derlemede belirtilen türlerin değişkenlerini (ve sabitleri) bildirebilirsiniz. Daha fazla bilgi için bkz. [.NET sınıf kitaplığı](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET 'teki tür sistemi hakkında iki temel noktayı anlamak önemlidir:

- Devralma ilkesini destekler. Türler, *temel türler*olarak adlandırılan diğer türlerden türetilebilir. Türetilmiş tür, yöntemleri, özellikleri ve temel türün diğer üyelerini devralır (bazı kısıtlamalarla). Temel tür başka bir türden türetebilir, bu durumda türetilmiş tür, devralma hiyerarşisindeki her iki temel türün üyelerini devralır. <xref:System.Int32?displayProperty=nameWithType> (C# Anahtar sözcük: [int](../../language-reference/builtin-types/integral-numeric-types.md)) gibi yerleşik sayısal türler dahil olmak üzere tüm türler, sonunda <xref:System.Object?displayProperty=nameWithType> (C# anahtar sözcük: [nesne](../../language-reference/keywords/object.md)) tek bir temel türden türetilir. Bu Birleşik tür hiyerarşisine [ortak tür sistemi](../../../standard/base-types/common-type-system.md) (Cts) denir. ' De C#devralma hakkında daha fazla bilgi için bkz. [Devralma](../classes-and-structs/inheritance.md).

- CTS içindeki her tür, bir *değer türü* veya bir *başvuru türü*olarak tanımlanır. Bu, .NET sınıf kitaplığı 'ndaki tüm özel türleri ve ayrıca kendi Kullanıcı tanımlı türlerinizi içerir. [Struct](../../language-reference/keywords/struct.md) anahtar sözcüğünü kullanarak tanımladığınız türler değer türleridir; Tüm yerleşik sayısal türler `structs`. [Sınıf](../../language-reference/keywords/class.md) anahtar sözcüğünü kullanarak tanımladığınız türler başvuru türleridir. Başvuru türleri ve değer türlerinde farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışları vardır.

Aşağıdaki çizimde, CTS 'deki değer türleri ve başvuru türleri arasındaki ilişki gösterilmektedir.

Aşağıdaki görüntüde, CTS 'deki değer türleri ve başvuru türleri gösterilmektedir:

![CTS değer türlerini ve başvuru türlerini gösteren ekran görüntüsü.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> En yaygın olarak kullanılan türlerin <xref:System> ad alanında düzenlendiğini görebilirsiniz. Ancak, bir türün bulunduğu ad alanının, bir değer türü veya başvuru türü olup olmadığı bir ilişkisi yoktur.

### <a name="value-types"></a>Değer Türleri

Değer türleri <xref:System.ValueType?displayProperty=nameWithType>öğesinden türetilir, öğesinden <xref:System.Object?displayProperty=nameWithType>türetilir. Öğesinden <xref:System.ValueType?displayProperty=nameWithType> türetilen türlerin clr 'de özel davranışı vardır. Değer türü değişkenleri doğrudan değerlerini içerir, bu da belleğin, değişkenin bildirildiği bağlamda satır içi olarak ayrıldığı anlamına gelir. Değer türü değişkenler için ayrı bir yığın ayırma veya çöp toplama ek yükü yoktur.

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

Değer türleri *Sealed*' dir; bu, örneğin, öğesinden <xref:System.Int32?displayProperty=nameWithType>bir tür türetmeyeceğiniz ve bir yapının yalnızca <xref:System.ValueType?displayProperty=nameWithType>devralabileceği şekilde, Kullanıcı tanımlı herhangi bir sınıftan veya yapıdan devralacak bir yapı tanımlayabilmeniz anlamına gelir. Ancak, bir struct bir veya daha fazla arabirim uygulayabilir. Yapı türünü, uygulayan herhangi bir arabirim türüne çevirebilirsiniz; Bu, bir *kutulama* işleminin yapıyı yönetilen yığında bir başvuru türü nesnesinin içine sarmasına neden olur. Paketleme işlemleri, bir değer türünü bir veya herhangi bir <xref:System.Object?displayProperty=nameWithType> arabirim türünü giriş parametresi olarak alan bir yönteme geçirdiğinizde oluşur. Daha fazla bilgi için bkz. [kutulama ve kutudan](./boxing-and-unboxing.md)çıkarma.

Kendi özel değer türlerinizi oluşturmak için [struct](../../language-reference/keywords/struct.md) anahtar sözcüğünü kullanırsınız. Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi küçük bir ilgili değişkenler kümesi için kapsayıcı olarak kullanılır:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Yapılar hakkında daha fazla bilgi için bkz. [yapılar](../classes-and-structs/structs.md). .NET 'teki değer türleri hakkında daha fazla bilgi için bkz. [değer türleri](../../language-reference/keywords/value-types.md).

Değer türlerinin diğer kategorisi [sabit listesi](../../language-reference/keywords/enum.md)' dir. Enum, adlandırılmış integral sabitleri kümesini tanımlar. Örneğin, <xref:System.IO.FileMode?displayProperty=nameWithType> .NET sınıf kitaplığındaki sabit listesi, bir dosyanın nasıl açılacağını belirten adlandırılmış sabit tamsayılar kümesi içerir. Aşağıdaki örnekte gösterildiği gibi tanımlanmıştır:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

`System.IO.FileMode.Create` Sabitin değeri 2 ' dir. Ancak ad, kaynak kodu okuyan insanlar için çok daha anlamlı olur ve bu nedenle sabit değişmez sayılar yerine Numaralandırmaların kullanılması daha iyidir. Daha fazla bilgi için bkz. <xref:System.IO.FileMode?displayProperty=nameWithType>.

Tüm numaralandırmalar öğesinden <xref:System.Enum?displayProperty=nameWithType> <xref:System.ValueType?displayProperty=nameWithType>devralan öğesinden devralır. Yapılar için uygulanan tüm kurallar, numaralandırmalar için de geçerlidir. Numaralandırmalar hakkında daha fazla bilgi için bkz. [numaralandırma türleri](../enumeration-types.md).

### <a name="reference-types"></a>Başvuru Türleri

[Class](../../language-reference/keywords/class.md), [Delegate](../../language-reference/keywords/delegate.md), array veya [Interface](../../language-reference/keywords/interface.md) olarak tanımlanan bir tür, bir *başvuru türüdür*. Çalışma zamanında, bir başvuru türü değişkeni bildirdiğinizde, [New](../../language-reference/operators/new-operator.md) işlecini kullanarak açıkça bir nesne oluşturana veya onu kullanarak `new`başka bir yerde oluşturulmuş bir nesne atayarak, değişken [null](../../language-reference/keywords/null.md) değerini içerir. Aşağıdaki örnekte gösterildiği gibi:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Bir arabirim, kendisini uygulayan bir sınıf nesnesiyle birlikte başlatılmalıdır. Uygularsa `IMyInterface`, aşağıdaki örnekte gösterildiği `IMyInterface` gibi bir örneği oluşturursunuz: `MyClass`

```csharp
IMyInterface iface = new MyClass();
```

Nesne oluşturulduğunda, bellek yönetilen yığında ayrılır ve değişken yalnızca nesnenin konumuna bir başvuru içerir. Yönetilen yığında bulunan türler, her ikisi de ayrıldıklarında ve *çöp toplama*olarak bilinen clr 'nin otomatik bellek yönetimi işlevselliği tarafından geri kazanıyorsa ek yük gerektirir. Ancak çöp toplama da yüksek oranda iyileştirilmiştir ve çoğu senaryoda bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için bkz. [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md).

Tüm diziler, öğeleri değer türleri olsa bile başvuru türlerdir. Diziler <xref:System.Array?displayProperty=nameWithType> sınıfından dolaylı olarak türetilir, ancak aşağıdaki örnekte gösterildiği gibi bunları tarafından C#verilen Basitleştirilmiş sözdizimi ile bildirir ve kullanabilirsiniz:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Başvuru türleri devralmayı tamamen destekler. Bir sınıf oluşturduğunuzda, [korumalı](../../language-reference/keywords/sealed.md)olarak tanımlanmayan diğer bir arabirim veya sınıftan kalıtımla alabilir ve diğer sınıflar sınıfınızdan devralınabilir ve sanal yöntemlerinizi geçersiz kılabilir. Kendi sınıflarınızı oluşturma hakkında daha fazla bilgi için bkz. [sınıflar ve yapılar](../classes-and-structs/index.md). Devralma ve sanal yöntemler hakkında daha fazla bilgi için bkz. [Devralma](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Değişmez değer türleri

' C#De, değişmez değerler derleyicisinden bir tür alır. Sayının sonuna bir harf ekleyerek sayısal bir sabit değerin nasıl yazılması gerektiğini belirtebilirsiniz. Örneğin, 4,56 değerinin bir float olarak değerlendirilip değerlendirilmeyeceğini belirtmek için, sayıdan sonra bir "f" veya "F" ekleyin: `4.56f`. Hiçbir harf eklenyoksa, derleyici değişmez değer için bir tür çıkarması olur. Hangi türlerin harf sonekleriyle belirtibileceği hakkında daha fazla bilgi için bkz. [değer türlerinde](../../language-reference/keywords/value-types.md)bağımsız türler için başvuru sayfaları.

Değişmez değerler yazıldığı ve tüm türler sonunda ' den <xref:System.Object?displayProperty=nameWithType>türettiğinden, aşağıdaki gibi bir kod yazabilir ve derleyebilirsiniz:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Genel Türler

Bir tür, istemci kodunun türün bir örneğini oluşturduğunda sağladığı gerçek tür ( *somut tür*) için yer tutucu olarak görev yapan bir veya daha fazla *tür parametresiyle* bildirilemez. Bu tür türler *Genel türler*olarak adlandırılır. Örneğin, .NET türü <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , kuralına göre bir tür parametresine sahiptir. Türün bir örneğini oluşturduğunuzda, listenin içereceği nesnelerin türünü (örneğin, dize) belirtirsiniz:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Tür parametresinin kullanımı, her öğeyi [nesneye](../../language-reference/keywords/object.md)dönüştürmek zorunda kalmadan her türlü öğe türünü tutmak için aynı sınıfı yeniden kullanmayı mümkün kılar. Derleyici, koleksiyon öğelerinin belirli türünü bildiğinden ve derleme zamanında bir hata yükseltebileceği için, genel koleksiyon sınıfları *kesin türü belirtilmiş koleksiyonlar* olarak adlandırılır. Örneğin, `stringList` önceki örnek. Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Örtük türler, anonim türler ve null yapılabilir türler

Daha önce belirtildiği gibi, [var](../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak yerel bir değişkeni (sınıf üyelerini değil) örtük olarak yazabilirsiniz. Değişken hala derleme zamanında bir tür alır, ancak tür derleyici tarafından sağlanır. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).

Bazı durumlarda, yöntem sınırlarını depolamayı veya geçişi istemediğiniz ilgili değerlerin basit kümeleri için adlandırılmış bir tür oluşturmak uygun değildir. Bu amaçla *anonim türler* oluşturabilirsiniz. Daha fazla bilgi için bkz. [anonim türler](../classes-and-structs/anonymous-types.md).

Sıradan değer türlerinin değeri [null](../../language-reference/keywords/null.md)olamaz. Ancak, türden sonra bir `?` ekleyerek null olabilen değer türleri oluşturabilirsiniz. Örneğin, `int?` [null](../../language-reference/keywords/null.md)değeri de `int` olan bir türdür. CTS 'de, null yapılabilir türler genel yapı türünün <xref:System.Nullable%601?displayProperty=nameWithType>örnekleridir. Null yapılabilir türler, sayısal değerlerin null olabileceği veritabanlarına ve veritabanlarından veri geçirirken özellikle kullanışlıdır. Daha fazla bilgi için bkz. [Nullable türler](../nullable-types/index.md).

## <a name="related-sections"></a>İlgili Bölümler

Daha fazla bilgi için aşağıdaki konulara bakın:

- [Tür Değiştirme ve Tür Dönüştürmeler](./casting-and-type-conversions.md)

- [Kutulama ve Kutudan Çıkarma](./boxing-and-unboxing.md)

- [Tür dinamiği kullanma](./using-type-dynamic.md)

- [Değer Türleri](../../language-reference/keywords/value-types.md)

- [Başvuru Türleri](../../language-reference/keywords/reference-types.md)

- [Sınıflar ve Yapılar](../classes-and-structs/index.md)

- [Anonim Tipler](../classes-and-structs/anonymous-types.md)

- [Genel Türler](../generics/index.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [XML Veri Türlerini Dönüştürme](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Integral türleri](../../language-reference/builtin-types/integral-numeric-types.md)
