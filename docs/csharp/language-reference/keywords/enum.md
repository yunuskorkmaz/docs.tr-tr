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
ms.openlocfilehash: 639a3a01c9c4da13e0212bd0230acbd2af170b25
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428513"
---
# <a name="enum-c-reference"></a><span data-ttu-id="d2b29-102">enum (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d2b29-102">enum (C# Reference)</span></span>

<span data-ttu-id="d2b29-103">`enum` anahtar sözcüğü, Numaralandırıcı listesi olarak adlandırılan bir adlandırılmış sabitler kümesinden oluşan ayrı bir tür olan bir sabit listesi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b29-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="d2b29-104">Genellikle, ad alanındaki tüm sınıfların eşit kolaylık olmadan erişebilmesi için doğrudan bir ad alanı içinde bir numaralandırma tanımlamanız en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="d2b29-105">Ancak, bir numaralandırma bir sınıf veya yapı içinde de iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="d2b29-106">Varsayılan olarak, ilk Numaralandırıcı 0 değerine sahiptir ve art arda her bir Numaralandırıcı değeri 1 artırılır.</span><span class="sxs-lookup"><span data-stu-id="d2b29-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="d2b29-107">Örneğin, aşağıdaki numaralandırmada `Sat` `0`, `Sun` `1`, `Mon` `2`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="d2b29-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="d2b29-108">Numaralandırıcılar, aşağıdaki örnekte gösterildiği gibi varsayılan değerleri geçersiz kılmak için başlatıcıları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="d2b29-109">Bu numaralandırmada, öğelerin sırası `0`yerine `1` başlatmaya zorlanır.</span><span class="sxs-lookup"><span data-stu-id="d2b29-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="d2b29-110">Ancak, 0 değeri olan bir sabit kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="d2b29-111">Daha fazla bilgi için bkz. [numaralandırma türleri](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="d2b29-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="d2b29-112">Her numaralandırma türünün bir temel türü vardır ve bu her türlü [integral sayısal tür](../builtin-types/integral-numeric-types.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="d2b29-113">[Char](../builtin-types/char.md) türü bir sabit listesinin temel alınan türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="d2b29-113">The [char](../builtin-types/char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="d2b29-114">Enumeration öğelerinin temel alınan varsayılan türü [int](../builtin-types/integral-numeric-types.md)'tir. [Byte](../builtin-types/integral-numeric-types.md)gibi başka bir integral türünün bir sabit listesini bildirmek için, aşağıdaki örnekte gösterildiği gibi, tanımlayıcıdan sonra türün ardından bir iki nokta üst üste kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2b29-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="d2b29-115">Sabit listesi türünün değişkenine, temel alınan türün aralığında herhangi bir değer atanabilir; değerler, adlandırılmış sabitler ile sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="d2b29-116">`enum E` varsayılan değeri, ifade `(E)0`tarafından üretilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b29-117">Numaralandırıcı, adında boşluk içeremez.</span><span class="sxs-lookup"><span data-stu-id="d2b29-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="d2b29-118">Temel alınan tür, her Numaralandırıcı için ne kadar depolama ayrılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="d2b29-119">Ancak, `enum` türünden integral türüne dönüştürmek için açık bir dönüştürme gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="d2b29-120">Örneğin, aşağıdaki ifade, `enum` `int`'e dönüştürmek için bir cast kullanarak, Numaralandırıcı `Sun` [int](../builtin-types/integral-numeric-types.md) türünde bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="d2b29-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="d2b29-121">Bit düzeyinde `OR` işlemle birleştirilebilecek öğeleri içeren bir numaralandırmaya <xref:System.FlagsAttribute?displayProperty=nameWithType> uyguladığınızda, öznitelik bazı araçlarla kullanıldığında `enum` davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="d2b29-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="d2b29-122"><xref:System.Console> sınıfı yöntemleri ve Ifade Değerlendiricisi gibi araçları kullandığınızda bu değişiklikleri fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2b29-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="d2b29-123">(Bkz. üçüncü örnek.)</span><span class="sxs-lookup"><span data-stu-id="d2b29-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="d2b29-124">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="d2b29-124">Robust programming</span></span>

<span data-ttu-id="d2b29-125">Her türlü Sabitte olduğu gibi, bir numaralandırmanın tek tek değerlerine yapılan tüm başvurular, derleme zamanında sayısal değişmez değerlere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d2b29-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="d2b29-126">Bu, [sabitler](../../programming-guide/classes-and-structs/constants.md)bölümünde açıklandığı gibi olası sürüm oluşturma sorunları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="d2b29-127">Yeni Numaralandırmaların yeni sürümlerine ek değerler atama veya yeni sürümde enum üyelerinin değerlerini değiştirme, bağımlı kaynak kodu sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="d2b29-128">Numaralandırma değerleri genellikle [Switch](switch.md) deyimlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b29-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="d2b29-129">`enum` türüne ek öğeler eklendiyse, switch ifadesinin varsayılan bölümü beklenmedik şekilde seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="d2b29-130">Diğer geliştiriciler kodunuzu kullanıyorsa, yeni öğeler `enum` türlerine eklenirse kodun nasıl tepki vermesi hakkında yönergeler sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d2b29-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="d2b29-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2b29-131">Example</span></span>

<span data-ttu-id="d2b29-132">Aşağıdaki örnekte, `Day`bir sabit listesi bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="d2b29-133">İki Numaralandırıcı açıkça tam sayıya dönüştürülür ve tamsayı değişkenlerine atanır.</span><span class="sxs-lookup"><span data-stu-id="d2b29-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="d2b29-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2b29-134">Example</span></span>

<span data-ttu-id="d2b29-135">Aşağıdaki örnekte, üyeleri `long`türünde olan bir `enum` bildirmek için temel tür seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2b29-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="d2b29-136">Sabit listesinin temel alınan türü `long`olsa da, numaralandırma üyelerinin bir cast kullanılarak `long` türüne açıkça dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="d2b29-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2b29-137">Example</span></span>

<span data-ttu-id="d2b29-138">Aşağıdaki kod örneği, `enum` bildiriminde <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliğinin kullanımını ve etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2b29-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="d2b29-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2b29-139">Comments</span></span>

<span data-ttu-id="d2b29-140">`Flags`kaldırırsanız, örnek aşağıdaki değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d2b29-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="d2b29-141">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d2b29-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d2b29-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2b29-142">See also</span></span>

- [<span data-ttu-id="d2b29-143">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="d2b29-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d2b29-144">Sabit Listesi Türleri</span><span class="sxs-lookup"><span data-stu-id="d2b29-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="d2b29-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d2b29-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d2b29-146">Integral türleri</span><span class="sxs-lookup"><span data-stu-id="d2b29-146">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="d2b29-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="d2b29-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="d2b29-148">Sabit Listesi adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d2b29-148">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
