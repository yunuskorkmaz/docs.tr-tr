---
title: Numaralandırma türleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 7c40e16e9c495c5e69dcdd74c3698d51b0d49785
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240066"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="0f955-102">Numaralandırma türleri (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f955-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="0f955-103">(Ayrıca bir numaralandırma veya bir sabit listesi adlı) bir numaralandırma türü bir değişkene atanabilir adlandırılmış integral sabitleri tanımlamak için etkili bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f955-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="0f955-104">Örneğin, değeri haftanın bir gününü temsil edecek bir değişkeni tanımlamak sahip olduğunuzu varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f955-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="0f955-105">Bu değişken her zamankinden depolayacak yalnızca yedi anlamlı değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0f955-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="0f955-106">Bu değerleri tanımlamak için kullanılarak bildirilen bir numaralandırma türü kullanabilirsiniz [enum](../../csharp/language-reference/keywords/enum.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0f955-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="0f955-107">Varsayılan olarak temel alınan her öğenin sabit listesi türünde [int](../../csharp/language-reference/keywords/int.md). Önceki örnekte gösterilen şekilde bir virgül kullanarak başka bir integral sayısal tür belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f955-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="0f955-108">Olası türlerinin tam listesi için bkz. [enum (C# Başvurusu)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="0f955-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="0f955-109">Temel alınan sayısal değerler, aşağıdaki örnekte gösterildiği gibi temel türdeki tür atama doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f955-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

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

<span data-ttu-id="0f955-110">Bir sabit listesi yerine bir sayısal tür kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0f955-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="0f955-111">Açıkça için istemci kodu hangi değişken için geçerli değerler belirtin.</span><span class="sxs-lookup"><span data-stu-id="0f955-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="0f955-112">Visual Studio IntelliSense tanımlanan değerleri listeler.</span><span class="sxs-lookup"><span data-stu-id="0f955-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="0f955-113">Numaralandırıcı listesinde öğelerin değerlerini belirtmediğinizde değerleri otomatik olarak 1 artar.</span><span class="sxs-lookup"><span data-stu-id="0f955-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="0f955-114">Önceki örnekte, `Day.Sunday` 0 değerine sahiptir `Day.Monday` 1 ve benzeri değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f955-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="0f955-115">Yeni bir oluşturduğunuzda `Day` nesnesi, varsayılan değerine sahip olacak `Day.Sunday` , açıkça bu değeri atamazsanız (0).</span><span class="sxs-lookup"><span data-stu-id="0f955-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="0f955-116">Enum oluşturduğunuzda en mantıklı varsayılan değer seçin ve sıfır değerini verin.</span><span class="sxs-lookup"><span data-stu-id="0f955-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="0f955-117">Oluşturulduğunda kullanıcılara açıkça bir değer atanmaz ise, varsayılan değere sahip tüm sabit listelerini neden.</span><span class="sxs-lookup"><span data-stu-id="0f955-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="0f955-118">Değişken `meetingDay` türünde `Day`, sonra da (açık bir yayın olmadan) yalnızca uygulamayı tanımlanan değerlerden birini atayabilirsiniz `Day`.</span><span class="sxs-lookup"><span data-stu-id="0f955-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="0f955-119">Ve toplantı gün değişirse, yeni bir değer atayabilirsiniz `Day` için `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="0f955-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="0f955-120">Rasgele tamsayı değerdeki atamak mümkün mü `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="0f955-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="0f955-121">Örneğin, bu kod satırı hata üretmez: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="0f955-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="0f955-122">Enum değişkeni yalnızca tanımlanan enum değerlerinden biri tutar, örtük beklentisi olduğundan ancak, bunu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0f955-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="0f955-123">Rastgele bir değeri bir sabit listesi türünde bir değişken için bir yüksek riskli hatalara tanıtmak için atamaktır.</span><span class="sxs-lookup"><span data-stu-id="0f955-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="0f955-124">Numaralandırıcı listesindeki bir numaralandırma türü öğeler için herhangi bir değer atayın ve hesaplanan değerler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f955-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="0f955-125">Bit bayrakları olarak numaralandırma türleri</span><span class="sxs-lookup"><span data-stu-id="0f955-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="0f955-126">Bir numaralandırma türü bit bayrakları tanımlamak için herhangi bir birleşimini Numaralandırıcı listesinde tanımlanan değerleri depolamak için numaralandırma türünün bir örneği sağlayan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f955-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="0f955-127">(Kuşkusuz, bazı birleşimleri anlamlı veya izin verilen program kodunuzda olmayabilir.)</span><span class="sxs-lookup"><span data-stu-id="0f955-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="0f955-128">Uygulayarak bir bit bayrakları sabit listesi oluşturma <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği ve değerleri uygun şekilde tanımlama böylece `AND`, `OR`, `NOT` ve `XOR` bunlar üzerinde bit düzeyinde işlemler gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f955-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="0f955-129">Bit bayrakları enum'da "hiçbir bayrakları ayarlanmış." anlamına gelen sıfır değerine sahip adlandırılmış bir sabit Ekle</span><span class="sxs-lookup"><span data-stu-id="0f955-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="0f955-130">"Hiçbir bayrakları ayarlanmış" gelmez, bayrak sıfır değeri vermeyin.</span><span class="sxs-lookup"><span data-stu-id="0f955-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="0f955-131">Aşağıdaki örnekte, başka bir sürümü `Day` adlı sabit listesi `Days`, tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f955-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="0f955-132">`Days` sahip `Flags` özniteliği ve her bir değeri 2'in sonraki büyük güç atanır.</span><span class="sxs-lookup"><span data-stu-id="0f955-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="0f955-133">Bu sayede oluşturmak bir `Days` değişken değeri `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="0f955-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="0f955-134">Bir numaralandırma üzerinde bir bayrak belirlemek için mü kullanmak `OR` aşağıdaki örnekte gösterildiği bir işleç:</span><span class="sxs-lookup"><span data-stu-id="0f955-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="0f955-135">Belirli bir bayrağı ayarlanmış olup olmadığını belirlemek için bir mü kullanmak `AND` işlemi, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="0f955-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="0f955-136">Numaralandırma türleri ile tanımladığınızda göz önüne alınması gerekenler hakkında daha fazla bilgi için <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği için bkz: <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f955-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="0f955-137">Keşfedin ve sabit listesi değerlerinin işlemek için System.Enum yöntemlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0f955-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="0f955-138">Tüm numaralandırmalar örnekleridir <xref:System.Enum?displayProperty=nameWithType> türü.</span><span class="sxs-lookup"><span data-stu-id="0f955-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="0f955-139">Yeni sınıflardan türetilemez <xref:System.Enum?displayProperty=nameWithType>, ancak enum örneği değerleri hakkında bilgi bulmak ve yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f955-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="0f955-140">Daha fazla bilgi için bkz. <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f955-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0f955-141">Bir genişletme yöntemi kullanarak, bir numaralandırma için yeni bir yöntem de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f955-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="0f955-142">Daha fazla bilgi için [nasıl yapılır: Numaralandırma için yeni bir yöntem oluşturma](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0f955-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f955-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f955-143">See Also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>  
- [<span data-ttu-id="0f955-144">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0f955-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0f955-145">enum</span><span class="sxs-lookup"><span data-stu-id="0f955-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
