---
title: const anahtar kelime - C# Referans
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 812aeb331b6dd333075d19076a896246ecc5b374
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713673"
---
# <a name="const-c-reference"></a><span data-ttu-id="e25e8-102">const (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e25e8-102">const (C# Reference)</span></span>

<span data-ttu-id="e25e8-103">Anahtar kelimeyi `const` sabit bir alanı veya sabit yerel i</span><span class="sxs-lookup"><span data-stu-id="e25e8-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="e25e8-104">Sabit alanlar ve yerel alanlar değişken değildir ve değiştirilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="e25e8-105">Sabitler sayılar, Boolean değerleri, dizeleri veya null başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="e25e8-106">İstediğinuz zaman değiştirmeyi beklediğiniz bilgileri temsil etmek için sabit oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="e25e8-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="e25e8-107">Örneğin, bir hizmetin fiyatını, ürün sürüm numarasını veya bir şirketin marka adını depolamak için sabit bir alan kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e25e8-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="e25e8-108">Bu değerler zaman içinde değişebilir ve derleyiciler sabitleri yaydığından, kitaplıklarınızla derlenen diğer kodların değişiklikleri görmek için yeniden derlenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="e25e8-109">Ayrıca yalnızca [okunan](./readonly.md) anahtar kelimeye de bakın.</span><span class="sxs-lookup"><span data-stu-id="e25e8-109">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="e25e8-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e25e8-110">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="e25e8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e25e8-111">Remarks</span></span>

<span data-ttu-id="e25e8-112">Sabit bir bildirimin türü, bildirimin tanıttığü üyelerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="e25e8-113">Sabit bir yerel veya sabit alanın baş harflerini, dolaylı olarak hedef türüne dönüştürülebilecek sabit bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e25e8-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="e25e8-114">Sabit bir ifade, derleme zamanında tam olarak değerlendirilebilen bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="e25e8-115">Bu nedenle, başvuru türlerinin sabitleri `string` için tek olası değerler ve null başvuru vardır.</span><span class="sxs-lookup"><span data-stu-id="e25e8-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="e25e8-116">Sabit bildirim, aşağıdakiler gibi birden çok sabit bildirebilir:</span><span class="sxs-lookup"><span data-stu-id="e25e8-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="e25e8-117">`static` Değiştirici nin sürekli bir bildirimde yer almasına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="e25e8-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="e25e8-118">Bir sabit aşağıdaki gibi, sabit bir ifade katılabilir:</span><span class="sxs-lookup"><span data-stu-id="e25e8-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="e25e8-119">[Yalnızca okunan](./readonly.md) anahtar `const` kelime, anahtar kelimeden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e25e8-119">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="e25e8-120">Bir `const` alan yalnızca alanın bildiriminde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="e25e8-121">Bir `readonly` alan, bildirimde veya bir oluşturucuda başharflere alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="e25e8-122">Bu `readonly` nedenle, alanların kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="e25e8-123">Ayrıca, bir `const` alan derleme zamanı sabiti `readonly` olmasına rağmen, alan bu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="e25e8-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="e25e8-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e25e8-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="e25e8-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e25e8-125">Example</span></span>

<span data-ttu-id="e25e8-126">Bu örnek, sabitlerin yerel değişkenler olarak nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e25e8-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="e25e8-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e25e8-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e25e8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e25e8-128">See also</span></span>

- [<span data-ttu-id="e25e8-129">C# Referans</span><span class="sxs-lookup"><span data-stu-id="e25e8-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e25e8-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e25e8-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e25e8-131">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="e25e8-131">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="e25e8-132">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="e25e8-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e25e8-133">Readonly</span><span class="sxs-lookup"><span data-stu-id="e25e8-133">readonly</span></span>](./readonly.md)
