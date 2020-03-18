---
title: Türleri - C# Programlama Kılavuzu
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
ms.openlocfilehash: 2fec7b5c36173bf4a99b35cc2bf9e3ca26354a11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399744"
---
# <a name="types-c-programming-guide"></a>Türler (C# Programlama Kılavuzu)

## <a name="types-variables-and-values"></a>Türleri, değişkenleri ve değerleri

C# güçlü bir şekilde yazılan bir dildir. Her değişken ve sabit, bir değere değer biçen her ifade gibi bir türü vardır. Her yöntem imzası, her giriş parametresi ve iade değeri için bir tür belirtir. .NET sınıf kitaplığı, dosya sistemi, ağ bağlantıları, koleksiyonlar ve nesne dizileri ve tarihler gibi çok çeşitli mantıksal yapıları temsil eden yerleşik sayısal türlerin yanı sıra daha karmaşık türleri tanımlar. Tipik bir C# programı, sınıf kitaplığından gelen türlerin yanı sıra programın sorunlu etki alanına özgü kavramları modelleyen kullanıcı tanımlı türleri kullanır.

Bir türde depolanan bilgiler aşağıdakileri içerebilir:

- Türünün bir değişkeninin gerektirdiği depolama alanı.

- Temsil edebileceği maksimum ve minimum değerler.

- İçerdiği üyeler (yöntemler, alanlar, olaylar vb.)

- Devraldığı temel türü.

- Değişkenler için belleğin çalışma zamanında ayrılacağı konum.

- İzin verilen işlem türleri.

Derleyici, kodunuzda gerçekleştirilen tüm işlemlerin *tür güvenli*olduğundan emin olmak için tür bilgilerini kullanır. Örneğin, tür [int](../../language-reference/builtin-types/integral-numeric-types.md)bir değişken bildirirseniz, derleyici ek ve çıkarma işlemlerinde değişken kullanmanıza olanak sağlar. Aynı işlemleri tür [bool](../../language-reference/builtin-types/bool.md)değişkeninde gerçekleştirmeye çalışırsanız, derleyici aşağıdaki örnekte gösterildiği gibi bir hata oluşturur:

[!code-csharp[csProgGuideTypes#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#42)]

> [!NOTE]
> C ve C++ geliştiricileri, C#'da [bool'un](../../language-reference/builtin-types/bool.md) [int'e](../../language-reference/builtin-types/integral-numeric-types.md)dönüştürülemez olduğuna dikkat edin.

Derleyici, tür bilgilerini yürütülebilir dosyaya meta veri olarak yerzetir. Ortak dil çalışma süresi (CLR), bellek tahsis ettiğinde ve geri aldığında tür güvenliğini daha da garanti etmek için bu meta verileri çalışma zamanında kullanır.

### <a name="specifying-types-in-variable-declarations"></a>Değişken bildirimlerde türleri belirtme

Bir programda bir değişken veya sabit beyan ettiğinizde, derleyicinin türü çıkarmasına izin vermek için türünü belirtmeniz veya [var](../../language-reference/keywords/var.md) anahtar sözcükünü kullanmanız gerekir. Aşağıdaki örnek, hem yerleşik sayısal türleri hem de karmaşık kullanıcı tanımlı türleri kullanan bazı değişken bildirimleri gösterir:

[!code-csharp[csProgGuideTypes#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#36)]

Yöntem imzasında yöntem parametreleri ve iade değerleri belirtilir. Aşağıdaki imza, giriş bağımsız değişkeni olarak bir [int](../../language-reference/builtin-types/integral-numeric-types.md) gerektiren bir yöntemi gösterir ve bir dize döndürür:

[!code-csharp[csProgGuideTypes#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#35)]

Bir değişken beyan edildikten sonra, yeni bir türle yeniden bildirilemez ve beyan edilen türüyle uyumlu olmayan bir değer atanamaz. Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) bildiremez ve sonra bir Boolean `true`değeri atayabilirsiniz. Ancak, değerler, örneğin yeni değişkenlere atandığında veya yöntem bağımsız değişkenleri olarak geçirildiğinde diğer türlere dönüştürülebilir. Veri kaybına neden olmayan bir *tür dönüştürme* derleyici tarafından otomatik olarak gerçekleştirilir. Veri kaybına neden olabilecek bir dönüştürme, kaynak kodunda bir *döküm* gerektirir.

Daha fazla bilgi için [bkz.](./casting-and-type-conversions.md)

## <a name="built-in-types"></a>Yerleşik türler

C#, tamsayılar, kayan nokta değerleri, Boolean ifadeleri, metin karakterleri, ondalık değerler ve diğer veri türlerini temsil edecek standart bir yerleşik sayısal türleri kümesi sağlar. Ayrıca yerleşik `string` ve `object` türleri vardır. Bunlar herhangi bir C# programında kullanabileceğiniz bir programdır. Yerleşik türlerin tam listesi için Yerleşik [türleri'ne](../../language-reference/builtin-types/built-in-types.md)bakın.

## <a name="custom-types"></a>Özel türleri

Kendi özel türleri oluşturmak için [yapı,](../../language-reference/builtin-types/struct.md) [sınıf,](../../language-reference/keywords/class.md) [arayüz](../../language-reference/keywords/interface.md)ve [enum](../../language-reference/builtin-types/enum.md) yapıları kullanın. .NET sınıf kitaplığı, Microsoft tarafından sağlanan ve kendi uygulamalarınızda kullanabileceğiniz özel türler topluluğudur. Varsayılan olarak, sınıf kitaplığında en sık kullanılan türler herhangi bir C# programında kullanılabilir. Diğerleri yalnızca tanımlandıkları derlemeye açıkça bir proje başvurusu eklediğinizde kullanılabilir hale gelir. Derleyici derlemeye bir başvuru yaptıktan sonra, bu derlemede bildirilen türlerin değişkenlerini (ve sabitlerini) kaynak kodunda bildirebilirsiniz. Daha fazla bilgi için [bkz.](../../../standard/class-library-overview.md)

## <a name="the-common-type-system"></a>Ortak tür sistemi

.NET'teki tip sistemi ile ilgili iki temel noktayı anlamak önemlidir:

- Miras ilkesini destekler. Türleri, *temel türleri*olarak adlandırılan diğer türlerden türetilebilir. Türetilen tür , yöntemleri, özellikleri ve temel türün diğer üyelerini (bazı kısıtlamalarla) devralır. Taban türü sırayla başka bir türden türetilebilir ve bu durumda türemiş tür, devralma hiyerarşisinde her iki temel türün üyelerini devralır. (C# anahtar kelimesi: [int](../../language-reference/builtin-types/integral-numeric-types.md)), sonuçta tek bir taban türünden <xref:System.Object?displayProperty=nameWithType> (C# anahtar kelimesi: [nesne)](../../language-reference/builtin-types/reference-types.md)gibi yerleşik sayısal türler de dahil olmak üzere tüm türler. <xref:System.Int32?displayProperty=nameWithType> Bu birleşik tür hiyerarşisi [Ortak Tür Sistemi](../../../standard/base-types/common-type-system.md) (CTS) olarak adlandırılır. C#'daki kalıtım hakkında daha fazla bilgi için [bkz.](../classes-and-structs/inheritance.md)

- CTS'deki her tür bir *değer türü* veya *başvuru türü*olarak tanımlanır. Bu, .NET sınıf kitaplığındaki tüm özel türleri ve aynı zamanda kendi kullanıcı tanımlı türlerinizi içerir. [Yapı](../../language-reference/builtin-types/struct.md) anahtar sözcüklerini kullanarak tanımladığınız türler değer türleridir; tüm yerleşik sayısal türleri vardır. `structs` [Sınıf](../../language-reference/keywords/class.md) anahtar sözcük kullanarak tanımladığınız türler başvuru türleridir. Başvuru türleri ve değer türleri farklı derleme zamanı kuralları ve farklı çalışma zamanı davranışı vardır.

Aşağıdaki resimde CTS değer türleri ve başvuru türleri arasındaki ilişki gösterilmektedir.

Aşağıdaki resimde CTS'deki değer türleri ve başvuru türleri gösterilmektedir:

![CTS değer türlerini ve başvuru türlerini gösteren ekran görüntüsü.](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> En sık kullanılan türlerin hepsinin ad alanında düzenlendiğini <xref:System> görebilirsiniz. Ancak, bir türün bulunduğu ad alanının değer türü mü yoksa başvuru türü mü olduğuyla bir ilgisi yoktur.

### <a name="value-types"></a>Değer türleri

Değer türleri, <xref:System.ValueType?displayProperty=nameWithType>'den <xref:System.Object?displayProperty=nameWithType>türeyen. CLR'de <xref:System.ValueType?displayProperty=nameWithType> özel davranıştan tür egelen türler. Değer türü değişkenleri doğrudan kendi değerlerini içerir, bu da belleğin değişkenin beyan edildiği bağlamda satır satır ait olduğu anlamına gelir. Değer türü değişkenler için ayrı bir yığın ayırma veya çöp toplama yükü yoktur.

Değer türleri iki kategori vardır: [struct](../../language-reference/builtin-types/struct.md) ve [num.](../../language-reference/builtin-types/enum.md)

Yerleşik sayısal türleri yapıtlarıdır ve bunlara erişebileceğiniz özellikler ve yöntemler vardır:

```csharp
// Static method on type byte.
byte b = byte.MaxValue;
```

Ancak, değerleri basit toplu olmayan türlergibi beyan ve atayabilirsiniz:

```csharp
byte num = 0xA;
int i = 5;
char c = 'Z';
```

Değer türleri *mühürlür,* bu da örneğin, bir tür <xref:System.Int32?displayProperty=nameWithType>elde edemeyeceğiniz anlamına gelir ve bir yapı yalnızca . <xref:System.ValueType?displayProperty=nameWithType> Ancak, bir yapı bir veya daha fazla arabirim uygulayabilir. Uyguladığı herhangi bir arabirim türüne bir yapı türü atabilirsiniz; bu, bir *kutulama* işleminin yönetilen yığındaki bir başvuru türü nesnesinin içine sarar. Bir değer türünü giriş parametresi olarak bir <xref:System.Object?displayProperty=nameWithType> veya herhangi bir arabirim türünü alan bir yönteme geçtiğinızda kutulama işlemleri oluşur. Daha fazla bilgi [için, Kutulama ve Unboxing](./boxing-and-unboxing.md)bakın.

Kendi özel değer türlerinizi oluşturmak için [yapı](../../language-reference/builtin-types/struct.md) anahtar sözcük kullanırsınız. Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi, ilgili değişkenlerin küçük bir dizi için kapsayıcı olarak kullanılır:

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

Yapıları hakkında daha fazla bilgi için [Yapı türlerine](../../language-reference/builtin-types/struct.md)bakın. Değer türleri hakkında daha fazla bilgi için [Bkz. Değer türleri.](../../language-reference/builtin-types/value-types.md)

Değer türlerinin diğer kategorisi [enum'](../../language-reference/builtin-types/enum.md)dur. Enum, adlandırılmış integral sabitleri kümesini tanımlar. Örneğin, .NET sınıf kitaplığındaki numaralandırma, <xref:System.IO.FileMode?displayProperty=nameWithType> bir dosyanın nasıl açıldığını belirten bir dizi adlandırılmış sabit tamsayı kümesi içerir. Aşağıdaki örnekte gösterildiği gibi tanımlanır:

[!code-csharp[csProgGuideTypes#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#44)]

Sabitin `System.IO.FileMode.Create` değeri 2'dir. Ancak, adı insanlar kaynak kodu okuma için çok daha anlamlı, ve bu nedenle sabit edebi sayılar yerine numaralandırma kullanmak daha iyidir. Daha fazla bilgi için bkz. <xref:System.IO.FileMode?displayProperty=nameWithType>.

Tüm enums <xref:System.Enum?displayProperty=nameWithType>miras , hangi <xref:System.ValueType?displayProperty=nameWithType>devralır . Structs için geçerli tüm kurallar da enums için geçerlidir. Numaralandırma hakkında daha fazla bilgi için [numaralandırma türlerine](../../language-reference/builtin-types/enum.md)bakın.

### <a name="reference-types"></a>Başvuru türleri

[Sınıf,](../../language-reference/keywords/class.md) [temsilci,](../../language-reference/builtin-types/reference-types.md)dizi veya [arabirim](../../language-reference/keywords/interface.md) olarak tanımlanan bir *tür bir başvuru türüdür.* Çalışma zamanında, bir başvuru türünün değişkenini beyan ettiğinizde, değişken, [yeni](../../language-reference/operators/new-operator.md) işleci kullanarak bir nesneyi açıkça oluşturana veya aşağıdaki örnekte gösterildiği gibi `new`başka bir yerde kullanılarak oluşturulan bir nesneyi atayıncaya kadar [null](../../language-reference/keywords/null.md) değerini içerir:

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

Arabirim, onu uygulayan bir sınıf nesnesi ile birlikte başharflere geçirilmelidir. Uygularsa, `MyClass` `IMyInterface`aşağıdaki örnekte `IMyInterface` gösterildiği gibi bir örnek oluşturursunuz:

```csharp
IMyInterface iface = new MyClass();
```

Nesne oluşturulduğunda, bellek yönetilen yığına ayrılır ve değişken yalnızca nesnenin konumuna bir başvuru tutar. Yönetilen yığındaki türler, hem ayrıldıklarında hem de *çöp toplama*olarak bilinen CLR'nin otomatik bellek yönetimi işlevi tarafından geri alındıklarında ek yükü gerektirir. Ancak, çöp toplama da son derece iyi duruma getirilmiş ve çoğu senaryoda bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için [Otomatik Bellek Yönetimi'ne](../../../standard/automatic-memory-management.md)bakın.

Tüm diziler, öğeleri değer türleri olsa bile başvuru türleridir. Diziler örtük olarak <xref:System.Array?displayProperty=nameWithType> sınıftan türemiştir, ancak bunları aşağıdaki örnekte gösterildiği gibi C# tarafından sağlanan basitleştirilmiş sözdizimi ile beyan eder ve kullanırsınız:

[!code-csharp[csProgGuideTypes#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#45)]

Başvuru türleri kalıtımı tam olarak destekler. Bir sınıf oluşturduğunuzda, [mühürlü](../../language-reference/keywords/sealed.md)olarak tanımlanmayan başka bir arabirim den veya sınıftan devralabilir ve diğer sınıflar sınıfınızdan devralabilir ve sanal yöntemlerinizi geçersiz kılabilir. Kendi sınıflarınızı nasıl oluşturabilirsiniz hakkında daha fazla bilgi için [Sınıflar ve Structs'a](../classes-and-structs/index.md)bakın. Devralma ve sanal yöntemler hakkında daha fazla bilgi için [bkz.](../classes-and-structs/inheritance.md)

## <a name="types-of-literal-values"></a>Gerçek değer türleri

C#'da, edebi değerler derleyiciden bir tür alır. Sayısal bir edebi yazın nasıl sayının sonuna bir harf ekleyerek belirtebilirsiniz. Örneğin, 4.56 değerinin float olarak ele alınması gerektiğini belirtmek için, numaradan sonra "f" `4.56f`veya "F" ekine: . Hiçbir harf eklenmezse, derleyici gerçek harf için bir tür çıkaracaktır. Harf sonekleriyle hangi türlerin belirtilebileceği hakkında daha fazla bilgi için, [İntegral sayısal türleri](../../language-reference/builtin-types/integral-numeric-types.md) ve [Kayan nokta sayısal türlerine](../../language-reference/builtin-types/floating-point-numeric-types.md)bakın.

Literals yazıldığı ve tüm türleri sonuçta türetilmiştir <xref:System.Object?displayProperty=nameWithType>çünkü, aşağıdaki gibi kod yazmak ve derlemek:

[!code-csharp[csProgGuideTypes#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#37)]

## <a name="generic-types"></a>Genel türler

Bir tür, istemci kodunun türün bir örneğini oluşturduğunda sağlayacağı gerçek tür *(somut tür)* için yer tutucu olarak hizmet veren bir veya daha fazla *tür parametresiyle* bildirilebilir. Bu tür *türler genel türleri*denir. Örneğin, .NET türünde, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> kuralla *T*adı verilen bir tür parametresi vardır. Türbir örneğini oluşturduğunuzda, listenin içereceği nesnelerin türünü( örneğin, dizeyi) belirtirsiniz:

```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```

Tür parametresinin kullanılması, her öğeyi [nesneye](../../language-reference/builtin-types/reference-types.md)dönüştürmek zorunda kalmadan, her tür öğeyi tutmak için aynı sınıfı yeniden kullanmayı mümkün kılar. Derleyici koleksiyonun öğelerinin belirli türünü bildiğinden ve örneğin önceki örnekteki `stringList` nesneye bir arastım eklemeye çalışırsanız derleme zamanında hata kaldırabileceğinden, genel koleksiyon sınıfları güçlü şekilde yazılan *koleksiyonlar* olarak adlandırılır. Daha fazla bilgi için [Genel Bilgiler'e](../generics/index.md)bakın.

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>Örtük türler, anonim türleri ve nullable değer türleri

Daha önce belirtildiği gibi, [var](../../language-reference/keywords/var.md) anahtar sözcük kullanarak örtülü olarak yerel bir değişken (ancak sınıf üyeleri değil) yazabilirsiniz. Değişken hala derleme zamanında bir tür alır, ancak tür derleyici tarafından sağlanır. Daha fazla bilgi için [bkz.](../classes-and-structs/implicitly-typed-local-variables.md)

Bazı durumlarda, depolamak veya yöntem sınırları dışında geçmek niyetinde olmadığınız ilgili değerlerin basit kümeleri için adlandırılmış bir tür oluşturmak sakıncalıdır. Bu amaçla *anonim türleri* oluşturabilirsiniz. Daha fazla bilgi için [Bkz. Anonim Türler.](../classes-and-structs/anonymous-types.md)

Olağan değer türlerinin [null](../../language-reference/keywords/null.md)değeri olamaz. Ancak, bir `?` türünden sonra yapıştırarak geçersiz değer türleri oluşturabilirsiniz. Örneğin, `int?` aynı `int` zamanda değeri [null](../../language-reference/keywords/null.md)olabilir bir türüdür. Nullable değer türleri genel yapı türü <xref:System.Nullable%601?displayProperty=nameWithType>örnekleridir. Sayısal değerlerin null olabileceği veritabanlarına ve veritabanlarından veri aktarırken, nullable değer türleri özellikle yararlıdır. Daha fazla bilgi için [Nullable değer türlerine](../../language-reference/builtin-types/nullable-value-types.md)bakın.

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Tür Değiştirme ve Tür Dönüştürmeler](./casting-and-type-conversions.md)

- [Kutulama ve Kutudan Çıkarma](./boxing-and-unboxing.md)

- [Tür dinamiği kullanma](./using-type-dynamic.md)

- [Değer Türleri](../../language-reference/builtin-types/value-types.md)

- [Referans Türleri](../../language-reference/keywords/reference-types.md)

- [Sınıflar ve Structs](../classes-and-structs/index.md)

- [Anonim Türler](../classes-and-structs/anonymous-types.md)

- [Genel Türler](../generics/index.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [XML Veri Türlerini Dönüştürme](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [İntegral tipleri](../../language-reference/builtin-types/integral-numeric-types.md)
