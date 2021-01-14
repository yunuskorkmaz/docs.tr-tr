---
title: Türler-C# Programlama Kılavuzu
description: C# programlamasında yerleşik türler, özel türler, değer türleri ve başvuru türleri gibi türler hakkında bilgi edinin.
ms.date: 11/19/2020
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
ms.openlocfilehash: 6a1a5b230e427a4991162a702245f1a87352784d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190253"
---
# <a name="types-c-programming-guide"></a>Türler (C# Programlama Kılavuzu)

## <a name="types-variables-and-values"></a>Türler, değişkenler ve değerler

C# türü kesin belirlenmiş bir dildir. Her değişken ve sabitin, bir değeri değerlendiren her ifadeyi olduğu gibi bir türü vardır. Her yöntem bildiriminde, her giriş parametresi ve dönüş değeri için bir ad, parametre sayısı ve tür ve tür (değer, başvuru veya çıkış) belirtilir. .NET sınıf kitaplığı, dosya sistemi, ağ bağlantıları, koleksiyon ve nesne dizileri ve tarihler gibi çok çeşitli mantıksal yapıları temsil eden yerleşik sayısal türler ve daha karmaşık türler kümesini tanımlar. Tipik bir C# programı, sınıf kitaplığından türleri ve programın sorunlu etki alanına özgü kavramları modeleden Kullanıcı tanımlı türleri kullanır.

Bir tür içinde depolanan bilgiler aşağıdaki öğeleri içerebilir:

- Türün bir değişkeninin gerektirdiği depolama alanı.
- Temsil ettiği maksimum ve en düşük değerler.
- İçerdiği Üyeler (Yöntemler, alanlar, olaylar vb.).
- Devraldığı temel tür.
- Uyguladığı Arabirim (ler).
- Değişkenlere yönelik belleğin çalışma zamanında ayrılabileceği konum.
- İzin verilen işlem türleri.

Derleyici, kodunuzda gerçekleştirilen tüm işlemlerin *tür açısından güvenli* olduğundan emin olmak için tür bilgilerini kullanır. Örneğin, [int](../../language-reference/builtin-types/integral-numeric-types.md)türünde bir değişken bildirirseniz, derleyici değişkeni toplama ve çıkarma işlemlerinde kullanmanıza izin verir. [Bool](../../language-reference/builtin-types/bool.md)türünde bir değişkende aynı işlemleri gerçekleştirmeye çalışırsanız, derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:

:::code language="csharp" source="snippets/index/Program.cs" id="TypeSafeExample":::

> [!NOTE]
> C ve C++ geliştiricileri, C# ' ta [bool](../../language-reference/builtin-types/bool.md) ' ın [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürülebilir olmadığına dikkat edin.

Derleyici, tür bilgilerini yürütülebilir dosyaya meta veriler olarak katıştırır. Ortak dil çalışma zamanı (CLR), bellek ayırdığı ve geri kazanır daha fazla güvence altına almak için çalışma zamanında bu meta verileri kullanır.

### <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerinde türleri belirtme

Bir programda bir değişken veya sabit belirttiğinizde, onun türünü belirtmeniz veya [var](../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak derleyicinin türü saymasına izin vermelisiniz. Aşağıdaki örnek, hem yerleşik sayısal türler hem de Kullanıcı tanımlı karmaşık türler kullanan bazı değişken bildirimlerini gösterir:

:::code language="csharp" source="snippets/index/Program.cs" id="Declarations":::

Yöntem parametrelerinin türleri ve dönüş değerleri yöntem bildiriminde belirtilmiştir. Aşağıdaki imza, giriş bağımsız değişkeni olarak bir [int](../../language-reference/builtin-types/integral-numeric-types.md) gerektiren ve bir dize döndüren bir yöntemi gösterir:

:::code language="csharp" source="snippets/index/Program.cs" id="GetName":::

Bir değişken bildirdikten sonra, bunu yeni bir türle yeniden bildiremezsiniz ve kendisine ait bir değer, belirtilen türle uyumlu olmayan bir değer atayamazsınız. Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) bildiremez ve bunu Boolean değeri atayabilirsiniz `true` . Ancak, değerler başka türlere dönüştürülebilir, örneğin, yeni değişkenlere atandıklarında veya yöntem bağımsız değişkenleri olarak geçirildiğinde. Veri kaybına neden olmayan bir *tür dönüştürme* , derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme, kaynak kodda bir *tür dönüştürme* gerektirir.

Daha fazla bilgi için bkz. [atama ve tür dönüştürmeleri](./casting-and-type-conversions.md).

## <a name="built-in-types"></a>Yerleşik türler

C#, tamsayıları, kayan nokta değerlerini, Boole ifadelerini, metin karakterlerini, ondalık değerleri ve diğer veri türlerini temsil etmek için standart bir yerleşik türler kümesi sağlar. Ayrıca yerleşik `string` ve `object` türler vardır. Bu türler, herhangi bir C# programında kullanabileceğiniz şekilde kullanılabilir. Yerleşik türlerin tam listesi için bkz. [Yerleşik türler](../../language-reference/builtin-types/built-in-types.md).

## <a name="custom-types"></a>Özel türler

Kendi özel türlerinizi oluşturmak için [struct](../../language-reference/builtin-types/struct.md), [Class](../../language-reference/keywords/class.md), [Interface](../../language-reference/keywords/interface.md)ve [enum](../../language-reference/builtin-types/enum.md) yapılarını kullanırsınız. .NET sınıf kitaplığı, Microsoft tarafından kendi uygulamalarınızda kullanabileceğiniz özel türlerin bir koleksiyonudur. Varsayılan olarak, sınıf kitaplığındaki en sık kullanılan türler, herhangi bir C# programında kullanılabilir. Diğerleri yalnızca tanımlandıkları derlemeye açıkça bir proje başvurusu eklediğinizde kullanılabilir hale gelir. Derleyicinin derlemeye bir başvurusu olduktan sonra, kaynak kodda o derlemede belirtilen türlerin değişkenlerini (ve sabitleri) bildirebilirsiniz. Daha fazla bilgi için bkz. [.NET sınıf kitaplığı](../../../standard/class-library-overview.md).

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET 'teki tür sistemi hakkında iki temel noktayı anlamak önemlidir:

- Devralma ilkesini destekler. Türler, *temel türler* olarak adlandırılan diğer türlerden türetilebilir. Türetilmiş tür, yöntemleri, özellikleri ve temel türün diğer üyelerini devralır (bazı kısıtlamalarla). Temel tür başka bir türden türetebilir, bu durumda türetilmiş tür, devralma hiyerarşisindeki her iki temel türün üyelerini devralır. (C# anahtar sözcüğü: int) gibi yerleşik sayısal türler dahil olmak üzere tüm türler, <xref:System.Int32?displayProperty=nameWithType> sonuçta [](../../language-reference/builtin-types/integral-numeric-types.md) <xref:System.Object?displayProperty=nameWithType> (c# anahtar sözcüğü: [nesnesi](../../language-reference/builtin-types/reference-types.md)) tek bir temel türden türetilir. Bu Birleşik tür hiyerarşisine [ortak tür sistemi](../../../standard/base-types/common-type-system.md) (Cts) denir. C# ' de devralma hakkında daha fazla bilgi için bkz. [Devralma](../classes-and-structs/inheritance.md).
- CTS içindeki her tür, bir *değer türü* veya bir *başvuru türü* olarak tanımlanır. Bu türler, .NET sınıf kitaplığı 'ndaki tüm özel türleri ve ayrıca kendi Kullanıcı tanımlı türlerinizi içerir. [Struct](../../language-reference/builtin-types/struct.md) anahtar sözcüğünü kullanarak tanımladığınız türler değer türleridir; Tüm yerleşik sayısal türler `structs` . [Sınıf](../../language-reference/keywords/class.md) anahtar sözcüğünü kullanarak tanımladığınız türler başvuru türleridir. Başvuru türleri ve değer türlerinde farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışları vardır.

Aşağıdaki çizimde, CTS 'deki değer türleri ve başvuru türleri arasındaki ilişki gösterilmektedir.

![CTS değer türlerini ve başvuru türlerini gösteren ekran görüntüsü.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> En yaygın olarak kullanılan türlerin <xref:System> ad alanında düzenlendiğini görebilirsiniz. Ancak, bir türün bulunduğu ad alanının, bir değer türü veya başvuru türü olup olmadığı bir ilişkisi yoktur.

### <a name="value-types"></a>Değer türleri

Değer türleri öğesinden türetilir <xref:System.ValueType?displayProperty=nameWithType> , öğesinden türetilir <xref:System.Object?displayProperty=nameWithType> . Öğesinden türetilen türlerin <xref:System.ValueType?displayProperty=nameWithType> clr 'de özel davranışı vardır. Değer türü değişkenleri doğrudan değerlerini içerir, bu da belleğin, değişkenin bildirildiği bağlamda satır içi olarak ayrıldığı anlamına gelir. Değer türü değişkenler için ayrı yığın ayırma veya çöp toplama ek yükü yoktur.

Değer türlerinin iki kategorisi vardır: [struct](../../language-reference/builtin-types/struct.md) ve [enum](../../language-reference/builtin-types/enum.md).

Yerleşik sayısal türler yapı birimleridir ve erişebileceğiniz alanlar ve yöntemlere sahiptirler:

:::code language="csharp" source="snippets/index/Program.cs" id="ConstantByte":::

Ancak bunları, basit olmayan türler gibi, bunlara değerler bildirir ve atarsınız:

:::code language="csharp" source="snippets/index/Program.cs" id="NonAggregateTypes":::

Değer türleri *Sealed* olur, bu, örneğin herhangi bir değer türünden bir tür türetimeyeceğiniz anlamına gelir <xref:System.Int32?displayProperty=nameWithType> . Bir struct yalnızca öğesinden devraldığı için, Kullanıcı tanımlı bir sınıftan veya yapıdan devralacak bir struct tanımlayamazsınız <xref:System.ValueType?displayProperty=nameWithType> . Ancak, bir struct bir veya daha fazla arabirim uygulayabilir. Yapı türünü, uygulayan herhangi bir arabirim türüne çevirebilirsiniz; Bu atama, bir *paketleme* işleminin yapıyı yönetilen yığında bir başvuru türü nesnesinin içine sarmasına neden olur. Paketleme işlemleri, bir değer türünü bir <xref:System.Object?displayProperty=nameWithType> veya herhangi bir arabirim türünü giriş parametresi olarak alan bir yönteme geçirdiğinizde oluşur. Daha fazla bilgi için bkz. [kutulama ve kutudan](./boxing-and-unboxing.md)çıkarma.

Kendi özel değer türlerinizi oluşturmak için [struct](../../language-reference/builtin-types/struct.md) anahtar sözcüğünü kullanırsınız. Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi küçük bir ilgili değişkenler kümesi için kapsayıcı olarak kullanılır:

:::code language="csharp" source="snippets/index/Program.cs" id="Coords":::

Yapılar hakkında daha fazla bilgi için bkz. [yapı türleri](../../language-reference/builtin-types/struct.md). Değer türleri hakkında daha fazla bilgi için bkz. [değer türleri](../../language-reference/builtin-types/value-types.md).

Değer türlerinin diğer kategorisi [sabit listesi](../../language-reference/builtin-types/enum.md)' dir. Enum, adlandırılmış integral sabitleri kümesini tanımlar. Örneğin, <xref:System.IO.FileMode?displayProperty=nameWithType> .NET sınıf kitaplığındaki sabit listesi, bir dosyanın nasıl açılacağını belirten adlandırılmış sabit tamsayılar kümesi içerir. Aşağıdaki örnekte gösterildiği gibi tanımlanmıştır:

:::code language="csharp" source="snippets/index/Program.cs" id="EnumFileMode":::

`System.IO.FileMode.Create`Sabitin değeri 2 ' dir. Ancak, ad, kaynak kodu okuyan insanlar için çok daha anlamlı olur ve bu nedenle sabit değişmez sayılar yerine Numaralandırmaların kullanılması daha iyidir. Daha fazla bilgi için bkz. <xref:System.IO.FileMode?displayProperty=nameWithType>.

Tüm numaralandırmalar öğesinden <xref:System.Enum?displayProperty=nameWithType> devralan öğesinden devralır <xref:System.ValueType?displayProperty=nameWithType> . Yapılar için uygulanan tüm kurallar, numaralandırmalar için de geçerlidir. Numaralandırmalar hakkında daha fazla bilgi için bkz. [numaralandırma türleri](../../language-reference/builtin-types/enum.md).

### <a name="reference-types"></a>Başvuru türleri

[Class](../../language-reference/keywords/class.md), [Delegate](../../language-reference/builtin-types/reference-types.md), array veya [Interface](../../language-reference/keywords/interface.md) olarak tanımlanan bir tür, bir *başvuru türüdür*. Çalışma zamanında, bir başvuru türü değişkeni bildirdiğinizde, [New](../../language-reference/operators/new-operator.md) işlecini kullanarak açıkça bir nesne oluşturana veya onu [](../../language-reference/keywords/null.md) `new` Aşağıdaki örnekte gösterildiği gibi kullanılarak başka bir yerde oluşturulmuş bir nesne atayarak, değişken null değerini içerir:

:::code language="csharp" source="snippets/index/Program.cs" id="DeclarationAndAssignment":::

Bir arabirim, kendisini uygulayan bir sınıf nesnesiyle birlikte başlatılmalıdır. `MyClass`Uygularsa `IMyInterface` , `IMyInterface` Aşağıdaki örnekte gösterildiği gibi bir örneği oluşturursunuz:

:::code language="csharp" source="snippets/index/Program.cs" id="InterfaceDeclaration":::

Nesne oluşturulduğunda, bellek yönetilen yığında ayrılır ve değişken yalnızca nesnenin konumuna bir başvuru içerir. Yönetilen yığında bulunan türler, her ikisi de ayrıldıklarında ve *çöp toplama* olarak bilinen clr 'nin otomatik bellek yönetimi işlevselliği tarafından geri kazanıyorsa ek yük gerektirir. Ancak çöp toplama da yüksek oranda iyileştirilmiştir ve çoğu senaryoda bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için bkz. [Otomatik bellek yönetimi](../../../standard/automatic-memory-management.md).

Tüm diziler, öğeleri değer türleri olsa bile başvuru türlerdir. Diziler sınıfından dolaylı olarak türetilir <xref:System.Array?displayProperty=nameWithType> , ancak aşağıdaki örnekte gösterildiği gibi bunları C# tarafından verilen Basitleştirilmiş sözdizimi ile bildirir ve kullanabilirsiniz:

:::code language="csharp" source="snippets/index/Program.cs" id="ArrayDeclaration":::

Başvuru türleri devralmayı tamamen destekler. Bir sınıf oluşturduğunuzda, [korumalı](../../language-reference/keywords/sealed.md)olarak tanımlanmayan diğer bir arabirim veya sınıftan kalıtımla alabilir ve diğer sınıflar sınıfınızdan devralınabilir ve sanal yöntemlerinizi geçersiz kılabilir. Kendi sınıflarınızı oluşturma hakkında daha fazla bilgi için bkz. [sınıflar ve yapılar](../classes-and-structs/index.md). Devralma ve sanal yöntemler hakkında daha fazla bilgi için bkz. [Devralma](../classes-and-structs/inheritance.md).

## <a name="types-of-literal-values"></a>Değişmez değer türleri

C# ' de, değişmez değerler derleyicisinden bir tür alır. Sayının sonuna bir harf ekleyerek sayısal bir sabit değerin nasıl yazılması gerektiğini belirtebilirsiniz. Örneğin, 4,56 değerinin bir float olarak değerlendirilip değerlendirilmeyeceğini belirtmek için, sayıdan sonra bir "f" veya "F" ekleyin: `4.56f` . Hiçbir harf eklenyoksa, derleyici değişmez değer için bir tür çıkarması olur. Hangi türlerin harf sonekleriyle belirtibileceği hakkında daha fazla bilgi için bkz. [Integral sayısal türleri](../../language-reference/builtin-types/integral-numeric-types.md) ve [kayan nokta sayısal türleri](../../language-reference/builtin-types/floating-point-numeric-types.md).

Değişmez değerler yazıldığı ve tüm türler sonunda öğesinden türetilmediği <xref:System.Object?displayProperty=nameWithType> için aşağıdaki kod gibi bir kod yazabilir ve derleyebilirsiniz:

:::code language="csharp" source="snippets/index/Program.cs" id="ConvertTypes":::

## <a name="generic-types"></a>Genel türler

Bir tür, istemci kodunun türün bir örneğini oluşturduğunda sağladığı gerçek tür ( *somut tür*) için yer tutucu olarak görev yapan bir veya daha fazla *tür parametresiyle* bildirilemez. Bu tür türler *Genel türler* olarak adlandırılır. Örneğin, .NET türü, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> kuralına göre bir tür parametresine sahiptir.  Türün bir örneğini oluşturduğunuzda, listenin içereceği nesnelerin türünü (örneğin, dize) belirtirsiniz:

:::code language="csharp" source="snippets/index/Program.cs" id="GenericType":::

Tür parametresinin kullanımı, her öğeyi [nesneye](../../language-reference/builtin-types/reference-types.md)dönüştürmek zorunda kalmadan her türlü öğe türünü tutmak için aynı sınıfı yeniden kullanmayı mümkün kılar. Derleyici, koleksiyon öğelerinin belirli türünü bildiğinden ve derleme zamanında bir hata, örneğin, önceki örnekteki nesnesine bir tamsayı eklemeye çalışırsanız, genel koleksiyon sınıfları *kesin türü belirtilmiş koleksiyonlar* olarak adlandırılır `stringList` . Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Örtük türler, anonim türler ve null yapılabilir değer türleri

Daha önce belirtildiği gibi, [var](../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak yerel bir değişkeni (sınıf üyelerini değil) örtük olarak yazabilirsiniz. Değişken hala derleme zamanında bir tür alır, ancak tür derleyici tarafından sağlanır. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).

Metot sınırlarını depolamayı veya dışına geçirmemenizi istemediğiniz ilgili değerlerin basit kümeleri için adlandırılmış bir tür oluşturmak kullanışlı olabilir. Bu amaçla *anonim türler* oluşturabilirsiniz. Daha fazla bilgi için bkz. [anonim türler](../classes-and-structs/anonymous-types.md).

Sıradan değer türlerinin değeri [null](../../language-reference/keywords/null.md)olamaz. Ancak, türden sonra bir ekleyerek null olabilen değer türleri oluşturabilirsiniz `?` . Örneğin, `int?` `int` [null](../../language-reference/keywords/null.md)değeri de olan bir türdür. Null yapılabilir değer türleri, genel yapı türünün örnekleridir <xref:System.Nullable%601?displayProperty=nameWithType> . Null olabilen değer türleri, genellikle sayısal değerlerin null olabileceği veritabanlarına ve veritabanlarından veri geçirirken faydalıdır. Daha fazla bilgi için bkz. [Nullable değer türleri](../../language-reference/builtin-types/nullable-value-types.md).

## <a name="compile-time-type-and-runtime-type"></a>Derleme zamanı türü ve çalışma zamanı türü

Bir değişken farklı derleme zamanı ve çalışma zamanı türlerine sahip olabilir. *Derleme zamanı türü* , kaynak koddaki değişkenin bildirildiği veya Çıkarsanan türüdür. *Çalışma zamanı türü* , bu değişken tarafından başvurulan örneğin türüdür. Genellikle, bu iki tür aşağıdaki örnekte olduğu gibi aynıdır:

:::code language="csharp" source="snippets/index/Program.cs" id="CompileTimeType":::

Diğer durumlarda, aşağıdaki iki örnekte gösterildiği gibi, derleme zamanı türü farklıdır:

:::code language="csharp" source="snippets/index/Program.cs" id="RuntimeTypes":::

Yukarıdaki örneklerde, çalışma zamanı türü bir ' dır `string` . Derleme zamanı türü `object` ilk satırda ve `IEnumerable<char>` ikinci olarak.

İki tür bir değişken için farklıysa, derleme zamanı türü ve çalışma zamanı türünün ne zaman uygulanacağını anlamak önemlidir. Derleme zamanı türü, derleyici tarafından gerçekleştirilen tüm eylemleri belirler. Bu derleyici eylemleri Yöntem çağrı çözümü, aşırı yükleme çözümlemesi ve kullanılabilir örtük ve açık yayınları içerir. Çalışma zamanı türü çalışma zamanında çözümlenen tüm eylemleri belirler. Bu çalışma zamanı eylemleri, sanal yöntem çağrılarını, değerlendirme `is` ve `switch` ifadeleri ve diğer tür testi API 'lerini dağıtma 'yı içerir. Kodunuzun türlerle nasıl etkileşime gireceğini daha iyi anlamak için hangi eylemin hangi türe uygulanacağını tanıyın.

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

- [Atama ve Tür Dönüşümleri](./casting-and-type-conversions.md)
- [Kutulama ve Kutudan Çıkarma](./boxing-and-unboxing.md)
- [Tür dinamiği kullanma](./using-type-dynamic.md)
- [Değer türleri](../../language-reference/builtin-types/value-types.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)
- [Anonim Türler](../classes-and-structs/anonymous-types.md)
- [Genel Türler](../generics/index.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [XML Veri Türlerini Dönüştürme](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [Integral türleri](../../language-reference/builtin-types/integral-numeric-types.md)
