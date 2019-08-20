---
title: enum anahtar sözcüğü C# -başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: fb11fb1a81b8407e2585e32d4217e08a75ea19b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605824"
---
# <a name="enum-c-reference"></a><span data-ttu-id="eebd2-102">enum (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eebd2-102">enum (C# Reference)</span></span>

<span data-ttu-id="eebd2-103">`enum` Anahtar sözcüğü, Numaralandırıcı listesi olarak adlandırılan bir adlandırılmış sabitler kümesinden oluşan ayrı bir tür olan sabit listesini bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eebd2-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="eebd2-104">Genellikle, ad alanındaki tüm sınıfların eşit kolaylık olmadan erişebilmesi için doğrudan bir ad alanı içinde bir numaralandırma tanımlamanız en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="eebd2-105">Ancak, bir numaralandırma bir sınıf veya yapı içinde de iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="eebd2-106">Varsayılan olarak, ilk Numaralandırıcı 0 değerine sahiptir ve art arda her bir Numaralandırıcı değeri 1 artırılır.</span><span class="sxs-lookup"><span data-stu-id="eebd2-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="eebd2-107">Örneğin, aşağıdaki `Sat` numaralandırmada,,, vb. `Sun` olur. `Mon` `0` `1` `2`</span><span class="sxs-lookup"><span data-stu-id="eebd2-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="eebd2-108">Numaralandırıcılar, aşağıdaki örnekte gösterildiği gibi varsayılan değerleri geçersiz kılmak için başlatıcıları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="eebd2-109">Bu numaralandırmada, öğelerin sırası `1` `0`yerine başlangıç olarak zorlanır.</span><span class="sxs-lookup"><span data-stu-id="eebd2-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="eebd2-110">Ancak, 0 değeri olan bir sabit kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="eebd2-111">Daha fazla bilgi için bkz. [numaralandırma türleri](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="eebd2-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="eebd2-112">Her numaralandırma türünün bir temel türü vardır ve bu her türlü [integral sayısal tür](../builtin-types/integral-numeric-types.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="eebd2-113">[Char](char.md) türü bir sabit listesinin temel alınan türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="eebd2-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="eebd2-114">Enumeration öğelerinin temel alınan varsayılan türü [int](../builtin-types/integral-numeric-types.md)'tir. [Byte](../builtin-types/integral-numeric-types.md)gibi başka bir integral türünün bir sabit listesini bildirmek için, aşağıdaki örnekte gösterildiği gibi, tanımlayıcıdan sonra türün ardından bir iki nokta üst üste kullanın.</span><span class="sxs-lookup"><span data-stu-id="eebd2-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="eebd2-115">Sabit listesi türünün değişkenine, temel alınan türün aralığında herhangi bir değer atanabilir; değerler, adlandırılmış sabitler ile sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="eebd2-116">Varsayılan değeri `enum E` , ifadesi `(E)0`tarafından üretilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="eebd2-117">Numaralandırıcı, adında boşluk içeremez.</span><span class="sxs-lookup"><span data-stu-id="eebd2-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="eebd2-118">Temel alınan tür, her Numaralandırıcı için ne kadar depolama ayrılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="eebd2-119">Ancak, `enum` türden bir integral türüne dönüştürmek için açık bir dönüştürme gerekir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="eebd2-120">Örneğin, aşağıdaki ifade, ' den `Sun` `enum` ' a dönüştürmek `int`için bir cast kullanarak, numaralandırıcıyı [int](../builtin-types/integral-numeric-types.md) türünde bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="eebd2-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="eebd2-121">Bit düzeyinde <xref:System.FlagsAttribute?displayProperty=nameWithType> `OR` işlemle birleştirilebilecek öğeleri içeren bir sabit listesi için uyguladığınızda, özniteliği bazı araçlarla kullanıldığında öğesinin `enum` davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="eebd2-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="eebd2-122"><xref:System.Console> Sınıf yöntemleri ve ifade değerlendiricisi gibi araçları kullandığınızda bu değişiklikleri fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eebd2-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="eebd2-123">(Bkz. üçüncü örnek.)</span><span class="sxs-lookup"><span data-stu-id="eebd2-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="eebd2-124">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="eebd2-124">Robust programming</span></span>

<span data-ttu-id="eebd2-125">Her türlü Sabitte olduğu gibi, bir numaralandırmanın tek tek değerlerine yapılan tüm başvurular, derleme zamanında sayısal değişmez değerlere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="eebd2-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="eebd2-126">Bu, [sabitler](../../programming-guide/classes-and-structs/constants.md)bölümünde açıklandığı gibi olası sürüm oluşturma sorunları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="eebd2-127">Yeni Numaralandırmaların yeni sürümlerine ek değerler atama veya yeni sürümde enum üyelerinin değerlerini değiştirme, bağımlı kaynak kodu sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="eebd2-128">Numaralandırma değerleri genellikle [Switch](switch.md) deyimlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eebd2-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="eebd2-129">`enum` Türe ek öğeler eklendiyse, switch ifadesinin varsayılan bölümü beklenmedik şekilde seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="eebd2-130">Diğer geliştiriciler kodunuzu kullanıyorsa, herhangi bir `enum` türe yeni öğe eklenirse kodun nasıl tepki vermesi hakkında yönergeler sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="eebd2-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="eebd2-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="eebd2-131">Example</span></span>

<span data-ttu-id="eebd2-132">Aşağıdaki örnekte, bir sabit listesi `Day`bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="eebd2-133">İki Numaralandırıcı açıkça tam sayıya dönüştürülür ve tamsayı değişkenlerine atanır.</span><span class="sxs-lookup"><span data-stu-id="eebd2-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="eebd2-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="eebd2-134">Example</span></span>

<span data-ttu-id="eebd2-135">Aşağıdaki örnekte, üyeleri türünde `enum` `long`olan bir öğesini bildirmek için temel tür seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eebd2-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="eebd2-136">Numaralandırmanın `long`temel alınan türü olsa da, sabit listesi üyelerinin bir tür dönüştürme kullanılarak açıkça türe `long` dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="eebd2-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="eebd2-137">Example</span></span>

<span data-ttu-id="eebd2-138">Aşağıdaki kod örneği, bir <xref:System.FlagsAttribute?displayProperty=nameWithType> `enum` bildirimde özniteliğin kullanımını ve etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eebd2-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="eebd2-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eebd2-139">Comments</span></span>

<span data-ttu-id="eebd2-140">' I kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="eebd2-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="eebd2-141">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="eebd2-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eebd2-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eebd2-142">See also</span></span>

- [<span data-ttu-id="eebd2-143">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="eebd2-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eebd2-144">Sabit Listesi Türleri</span><span class="sxs-lookup"><span data-stu-id="eebd2-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="eebd2-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="eebd2-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eebd2-146">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="eebd2-146">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="eebd2-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="eebd2-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="eebd2-148">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="eebd2-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="eebd2-149">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="eebd2-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="eebd2-150">Sabit Listesi adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="eebd2-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
