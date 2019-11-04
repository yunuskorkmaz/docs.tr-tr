---
title: const anahtar sözcüğü C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 81660e6a56efe5737600122d4ff7e182654f9a9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422887"
---
# <a name="const-c-reference"></a><span data-ttu-id="e6ef0-102">const (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e6ef0-102">const (C# Reference)</span></span>

<span data-ttu-id="e6ef0-103">`const` anahtar sözcüğünü kullanarak sabit bir alan veya sabit bir yerel değer bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="e6ef0-104">Sabit alanlar ve Yereller değişken değildir ve değiştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="e6ef0-105">Sabitler sayı, Boole değeri, dize veya null başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="e6ef0-106">İstediğiniz zaman değiştirilmesini düşündüğünüz bilgileri temsil etmek için bir sabit oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="e6ef0-107">Örneğin, bir hizmetin fiyatını, ürün sürüm numarasını veya şirketin marka adını depolamak için sabit bir alan kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="e6ef0-108">Bu değerler zaman içinde değişebilir ve derleyiciler yaydığı için, kitaplıklarınız ile derlenen diğer kodun değişiklikleri görmek için yeniden derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="e6ef0-109">Ayrıca bkz. [ReadOnly](./readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-109">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="e6ef0-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e6ef0-110">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="e6ef0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6ef0-111">Remarks</span></span>

<span data-ttu-id="e6ef0-112">Sabit bir bildirimin türü, bildirimin sunmakta olduğu üyelerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="e6ef0-113">Sabit bir yerel veya sabit alanın başlatıcısı, hedef türe örtük olarak dönüştürülemeyen bir sabit ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="e6ef0-114">Sabit bir ifade, derleme zamanında tam olarak değerlendirilebilen bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="e6ef0-115">Bu nedenle, başvuru türlerinin sabitleri için tek olası değerler `string` ve null bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="e6ef0-116">Sabit bildirimi, şöyle birçok sabit bildirebilir:</span><span class="sxs-lookup"><span data-stu-id="e6ef0-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="e6ef0-117">Sabit bildiriminde `static` değiştiriciye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="e6ef0-118">Bir sabit, aşağıdaki gibi bir sabit ifadeye katılabilir:</span><span class="sxs-lookup"><span data-stu-id="e6ef0-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="e6ef0-119">[ReadOnly](./readonly.md) anahtar sözcüğü `const` anahtar sözcüğünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-119">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="e6ef0-120">Bir `const` alanı yalnızca alanın bildiriminde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="e6ef0-121">`readonly` alan, bildirimde veya bir oluşturucuda başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="e6ef0-122">Bu nedenle, `readonly` alanlar kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="e6ef0-123">Ayrıca, bir `const` alanı bir derleme zamanı sabiti olsa da, `readonly` alanı şu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="e6ef0-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="e6ef0-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6ef0-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="e6ef0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6ef0-125">Example</span></span>

<span data-ttu-id="e6ef0-126">Bu örnek, sabitlerin yerel değişkenler olarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="e6ef0-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e6ef0-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e6ef0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ef0-128">See also</span></span>

- [<span data-ttu-id="e6ef0-129">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="e6ef0-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e6ef0-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e6ef0-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e6ef0-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e6ef0-131">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="e6ef0-132">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="e6ef0-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e6ef0-133">readonly</span><span class="sxs-lookup"><span data-stu-id="e6ef0-133">readonly</span></span>](./readonly.md)
