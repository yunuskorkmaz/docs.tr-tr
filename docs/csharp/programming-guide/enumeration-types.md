---
title: "Numaralandırma türleri (C# programlama Kılavuzu)"
ms.date: 09/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13ec7d5d2a44cddb2b7f440c8d811c2e4060d432
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="66aa2-102">Numaralandırma türleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="66aa2-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="66aa2-103">(Ayrıca bir sabit listesi veya bir enum adlı) bir numaralandırma türü bir değişkene atanabilir adlandırılmış tamsayı sabitleri kümesini tanımlamak için etkili bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="66aa2-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="66aa2-104">Örneğin, değeri haftanın gününü temsil edecek bir değişkeni tanımlamak olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="66aa2-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="66aa2-105">Bu değişken her zamankinden depolayacak yalnızca yedi anlamlı değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="66aa2-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="66aa2-106">Bu değerleri tanımlamak için kullanarak bildirilmiş bir numaralandırma türü kullanabilirsiniz [enum](../../csharp/language-reference/keywords/enum.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="66aa2-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="66aa2-107">Varsayılan olarak temel alınan her bir öğesinde enum türünde [int](../../csharp/language-reference/keywords/int.md). Önceki örnekte gösterildiği gibi iki nokta kullanarak başka bir tam sayı sayısal tür belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66aa2-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="66aa2-108">Olası türlerinin tam listesi için bkz: [enum (C# Başvurusu)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="66aa2-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="66aa2-109">Temel alınan sayısal değerler, aşağıdaki örnekte gösterildiği gibi temel alınan tür atama doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66aa2-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

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

<span data-ttu-id="66aa2-110">Enum yerine sayısal bir tür kullanmanın yararları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="66aa2-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="66aa2-111">Açıkça istemci kodu hangi değişken için geçerli değerler için belirtin.</span><span class="sxs-lookup"><span data-stu-id="66aa2-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="66aa2-112">İçinde [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense tanımlanan değerleri listeler.</span><span class="sxs-lookup"><span data-stu-id="66aa2-112">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense lists the defined values.</span></span>

<span data-ttu-id="66aa2-113">Numaralandırıcı listedeki öğelerin değerlerini belirtmediğinde değerleri otomatik olarak 1 artırılır.</span><span class="sxs-lookup"><span data-stu-id="66aa2-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="66aa2-114">Önceki örnekte, `Day.Sunday` 0 ' değerine sahip `Day.Monday` 1 ve benzeri bir değer içeriyor.</span><span class="sxs-lookup"><span data-stu-id="66aa2-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="66aa2-115">Yeni bir oluşturduğunuzda `Day` nesnesi, varsayılan değer olan olacaktır `Day.Sunday` (0), açıkça, bir değer atamazsanız.</span><span class="sxs-lookup"><span data-stu-id="66aa2-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="66aa2-116">Enum oluşturduğunuzda, en mantıklı varsayılan değer seçin ve sıfır değeri verin.</span><span class="sxs-lookup"><span data-stu-id="66aa2-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="66aa2-117">Oluşturuldukları sırada açıkça bir değer atanmışlarsa değil, bu varsayılan değere sahip tüm numaralandırmaları neden.</span><span class="sxs-lookup"><span data-stu-id="66aa2-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="66aa2-118">Varsa değişkeni `meetingDay` türü `Day`, (açık atama) yalnızca bunu tarafından tanımlanan değerlerden biri atayabilirsiniz sonra `Day`.</span><span class="sxs-lookup"><span data-stu-id="66aa2-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="66aa2-119">Ve toplantı gün değişse yeni bir değer atayabilirsiniz `Day` için `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="66aa2-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="66aa2-120">Herhangi bir rastgele tamsayı değerine atamak da mümkündür `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="66aa2-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="66aa2-121">Örneğin, bu kod satırı hata üretmez: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="66aa2-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="66aa2-122">Örtük beklenir bir enum değişken yalnızca enum tarafından tanımlanan değerlerden biri tutacak, çünkü ancak, bunu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="66aa2-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="66aa2-123">Rastgele bir değeri bir numaralandırma türü değişkenine atamak için yüksek riskli hataları uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="66aa2-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="66aa2-124">Bir numaralandırma türünün Numaralandırıcı listesindeki öğeleri herhangi bir değeri atayabilir ve hesaplanan değerler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66aa2-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="66aa2-125">Bit bayrakları olarak numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="66aa2-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="66aa2-126">Bir numaralandırma türü, bit bayrakları tanımlamak için hangi Numaralandırıcı listesinde tanımlanan değerlerin herhangi bir birleşimini depolamak için numaralandırma türü örneğini etkinleştirir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66aa2-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="66aa2-127">(Doğal olarak, bazı birleşimleri anlamlı veya izin verilen program kodunuzda olmayabilir.)</span><span class="sxs-lookup"><span data-stu-id="66aa2-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="66aa2-128">Bit bayrakları enum uygulayarak oluşturun <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği ve değerleri uygun şekilde tanımlama böylece `AND`, `OR`, `NOT` ve `XOR` bit düzeyinde işlemler bunlar üzerinde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66aa2-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="66aa2-129">Adlandırılmış bir sabit "hiçbir bayraklarını ayarlayın." anlamına gelir sıfır değeri ile bir bit bayrakları enum içindeki içerir</span><span class="sxs-lookup"><span data-stu-id="66aa2-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="66aa2-130">"Hiçbir bayraklarını ayarlayın" gelmez, bir bayrak sıfır değeri vermeyin.</span><span class="sxs-lookup"><span data-stu-id="66aa2-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="66aa2-131">Aşağıdaki örnekte, başka bir sürümü `Day` adlı enum `Days`, tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="66aa2-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="66aa2-132">`Days`sahip `Flags` öznitelik ve her değer 2'in sonraki büyük üssü atanır.</span><span class="sxs-lookup"><span data-stu-id="66aa2-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="66aa2-133">Bu oluşturmanızı sağlayan bir `Days` değişken değeri `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="66aa2-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="66aa2-134">Enum üzerinde bir bayrak belirlemek için bitwise kullanmak `OR` aşağıdaki örnekte gösterildiği gibi işleci:</span><span class="sxs-lookup"><span data-stu-id="66aa2-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="66aa2-135">Belirli bir bayrağı ayarlanmış olup olmadığını belirlemek için bit kullanmak `AND` işlemi, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="66aa2-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="66aa2-136">Numaralandırma türleri ile tanımladığınızda dikkat edilmesi gerekenler hakkında daha fazla bilgi için <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği için bkz: <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66aa2-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="66aa2-137">System.Enum yöntemleri kullanarak bulmak ve enum değerleri</span><span class="sxs-lookup"><span data-stu-id="66aa2-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="66aa2-138">Tüm numaralandırmaları örnekleridir <xref:System.Enum?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="66aa2-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="66aa2-139">Yeni sınıflardan türetilemez <xref:System.Enum?displayProperty=nameWithType>, ancak kendi yöntemleri hakkında bilgi bulmak ve enum örneğindeki değerlerini değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66aa2-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="66aa2-140">Daha fazla bilgi için bkz. <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66aa2-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="66aa2-141">Bir genişletme yöntemi kullanarak, bir numaralandırma için yeni bir yöntem de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66aa2-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="66aa2-142">Daha fazla bilgi için bkz: [nasıl yapılır: numaralandırma için yeni bir yöntem oluşturma](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="66aa2-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66aa2-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66aa2-143">See also</span></span>
 <xref:System.Enum?displayProperty=nameWithType>  
 [<span data-ttu-id="66aa2-144">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="66aa2-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="66aa2-145">Enum</span><span class="sxs-lookup"><span data-stu-id="66aa2-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
