---
title: Sabit listesi türleri C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3573959a1e10b475a9867631767de5d10a08b9ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969771"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="53215-102">Sabit listesi türleriC# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="53215-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="53215-103">Bir sabit listesi türü (numaralandırma veya sabit listesi olarak da adlandırılır), bir değişkene atanabilecek adlandırılmış integral sabitleri kümesini tanımlamak için etkili bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="53215-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="53215-104">Örneğin, değeri haftanın gününü temsil edecek bir değişken tanımlamanız gerektiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="53215-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="53215-105">Bu değişkenin her zaman depolayabileceği yedi anlamlı değer vardır.</span><span class="sxs-lookup"><span data-stu-id="53215-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="53215-106">Bu değerleri tanımlamak için, [enum](../language-reference/keywords/enum.md) anahtar sözcüğü kullanılarak bildirilebilecek bir numaralandırma türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="53215-107">Varsayılan olarak, numaralandırıcıdaki her öğenin temel alınan türü [int](../language-reference/builtin-types/integral-numeric-types.md)'tir. Önceki örnekte gösterildiği gibi, iki nokta üst üste kullanarak başka bir integral sayısal türü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-107">By default the underlying type of each element in the enum is [int](../language-reference/builtin-types/integral-numeric-types.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="53215-108">Olası türlerin tam listesi için bkz. [enum (C# başvuru)](../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="53215-108">For a full list of possible types, see [enum (C# Reference)](../language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="53215-109">Aşağıdaki örnekte gösterildiği gibi temel alınan türe atama yaparak temeldeki sayısal değerleri doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

<span data-ttu-id="53215-110">Sayısal bir tür yerine bir sabit listesi kullanmanın avantajları aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="53215-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="53215-111">Değişken için hangi değerlerin geçerli olduğunu açıkça istemci kodu için belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="53215-112">Visual Studio 'da, IntelliSense tanımlı değerleri listeler.</span><span class="sxs-lookup"><span data-stu-id="53215-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="53215-113">Numaralandırıcı listesindeki öğeler için değer belirtmeyin, değerler otomatik olarak 1 ' den artırılır.</span><span class="sxs-lookup"><span data-stu-id="53215-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="53215-114">Önceki örnekte, `Day.Sunday` 0 değerine sahiptir, `Day.Monday` 1 değeri vardır ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="53215-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="53215-115">Yeni bir `Day` nesnesi oluşturduğunuzda, açıkça bir değer atamadıysanız varsayılan değeri `Day.Sunday` (0) olur.</span><span class="sxs-lookup"><span data-stu-id="53215-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="53215-116">Bir sabit listesi oluşturduğunuzda, en mantıksal varsayılan değeri seçin ve sıfıra bir değer verin.</span><span class="sxs-lookup"><span data-stu-id="53215-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="53215-117">Bu, tüm Numaralandırmaların, oluşturulduklarında açıkça bir değer atamadığı takdirde, bu varsayılan değere sahip olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="53215-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="53215-118">Değişken `meetingDay` `Day`tür ise (açık bir atama olmadan), yalnızca `Day`tarafından tanımlanan değerlerden birini atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="53215-119">Toplantı günü değişirse, `meetingDay``Day` yeni bir değer atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="53215-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="53215-120">`meetingDay`için herhangi bir rastgele tamsayı değeri atamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="53215-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="53215-121">Örneğin, bu kod satırı bir hata oluşturmaz: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="53215-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="53215-122">Ancak, örtük beklentide bir numaralandırma değişkeninin yalnızca enum tarafından tanımlanan değerlerden birini tutacağından bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="53215-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="53215-123">Sabit listesi türünde bir değişkene rastgele bir değer atamak için, hatalara yönelik yüksek riskli bir hata ortaya çıkaracak.</span><span class="sxs-lookup"><span data-stu-id="53215-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="53215-124">Bir numaralandırma türünün Numaralandırıcı listesindeki öğelere herhangi bir değer atayabilir ve hesaplanan değerleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="53215-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="53215-125">Bit bayrakları olarak numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="53215-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="53215-126">Bir numaralandırma türü örneğini, Numaralandırıcı listesinde tanımlanan değerlerin herhangi bir birleşimini depolamak üzere bir numaralandırma türü örneği sağlayan bit bayraklarını tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="53215-127">(Tabii ki, bazı birleşimler program kodunuzda anlamlı veya izin verilebilir olmayabilir.)</span><span class="sxs-lookup"><span data-stu-id="53215-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="53215-128"><xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliğini uygulayarak ve değerleri uygun şekilde tanımlayarak, `AND`, `OR`, `NOT` ve `XOR` bit düzeyinde işlemler gerçekleştirilmeleri için bir bit bayrakları numaralandırması oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="53215-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="53215-129">Bir bit bayrakları numaralandırmasında, "hiçbir bayrak ayarlanmadı" anlamına gelen değeri sıfır olan adlandırılmış sabiti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53215-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="53215-130">"Bayrak ayarlanmamışsa" bir değere sıfır değeri vermeyin.</span><span class="sxs-lookup"><span data-stu-id="53215-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="53215-131">Aşağıdaki örnekte, `Days`adlı `Day` numaralandırmasının başka bir sürümü tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="53215-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="53215-132">`Days` `Flags` özniteliğine sahiptir ve her değere 2 ' nin sonraki daha yüksek gücüne atanır.</span><span class="sxs-lookup"><span data-stu-id="53215-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="53215-133">Bu, değeri `Days.Tuesday | Days.Thursday`olan `Days` bir değişken oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="53215-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="53215-134">Bir numaralandırıcıda bayrak ayarlamak için aşağıdaki örnekte gösterildiği gibi bit düzeyinde `OR` işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="53215-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="53215-135">Belirli bir bayrağın ayarlanmış olup olmadığını anlamak için aşağıdaki örnekte gösterildiği gibi bit düzeyinde `AND` işlem kullanın:</span><span class="sxs-lookup"><span data-stu-id="53215-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="53215-136"><xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliğiyle numaralandırma türlerini tanımlarken göz önünde bulundurmanız gerekenler hakkında daha fazla bilgi için, bkz. <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53215-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="53215-137">Enum değerlerini bulma ve işlemek için System. Enum yöntemlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="53215-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="53215-138">Tüm numaralandırmalar <xref:System.Enum?displayProperty=nameWithType> türünün örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="53215-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="53215-139"><xref:System.Enum?displayProperty=nameWithType>yeni sınıflar türetemezsiniz, ancak kendi yöntemlerini kullanarak bir numaralandırma örneğindeki değerleri hakkında bilgi bulabilir ve bunları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="53215-140">Daha fazla bilgi için bkz. <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53215-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="53215-141">Ayrıca, bir uzantı yöntemi kullanarak bir numaralandırma için yeni bir yöntem oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53215-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="53215-142">Daha fazla bilgi için bkz. [bir numaralandırma için yeni bir yöntem oluşturma](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="53215-142">For more information, see [How to create a new method for an enumeration](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53215-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53215-143">See also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>
- [<span data-ttu-id="53215-144">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="53215-144">C# Programming Guide</span></span>](./index.md)
- [<span data-ttu-id="53215-145">enum</span><span class="sxs-lookup"><span data-stu-id="53215-145">enum</span></span>](../language-reference/keywords/enum.md)
