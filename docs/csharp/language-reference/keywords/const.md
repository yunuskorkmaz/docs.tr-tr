---
description: const anahtar sözcüğü-C# başvurusu
title: const anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 312725c3a231f0ca766d5b99bf7d9308ddd634c4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142095"
---
# <a name="const-c-reference"></a><span data-ttu-id="0b07c-103">const (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0b07c-103">const (C# Reference)</span></span>

<span data-ttu-id="0b07c-104">`const`Sabit bir alan veya sabit bir yerel değer bildirmek için anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0b07c-104">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="0b07c-105">Sabit alanlar ve Yereller değişken değildir ve değiştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-105">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="0b07c-106">Sabitler sayı, Boole değeri, dize veya null başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-106">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="0b07c-107">İstediğiniz zaman değiştirilmesini düşündüğünüz bilgileri temsil etmek için bir sabit oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="0b07c-107">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="0b07c-108">Örneğin, bir hizmetin fiyatını, ürün sürüm numarasını veya şirketin marka adını depolamak için sabit bir alan kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0b07c-108">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="0b07c-109">Bu değerler zaman içinde değişebilir ve derleyiciler yaydığı için, kitaplıklarınız ile derlenen diğer kodun değişiklikleri görmek için yeniden derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-109">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="0b07c-110">Ayrıca bkz. [ReadOnly](./readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0b07c-110">See also the [readonly](./readonly.md) keyword.</span></span> <span data-ttu-id="0b07c-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0b07c-111">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="0b07c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b07c-112">Remarks</span></span>

<span data-ttu-id="0b07c-113">Sabit bir bildirimin türü, bildirimin sunmakta olduğu üyelerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-113">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="0b07c-114">Sabit bir yerel veya sabit alanın başlatıcısı, hedef türe örtük olarak dönüştürülemeyen bir sabit ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b07c-114">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="0b07c-115">Sabit bir ifade, derleme zamanında tam olarak değerlendirilebilen bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-115">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="0b07c-116">Bu nedenle, başvuru türlerinin sabitlerinin tek olası değerleri `string` ve null bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="0b07c-116">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="0b07c-117">Sabit bildirimi, şöyle birçok sabit bildirebilir:</span><span class="sxs-lookup"><span data-stu-id="0b07c-117">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="0b07c-118">`static`Sabit bildiriminde değiştiriciye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="0b07c-118">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="0b07c-119">Bir sabit, aşağıdaki gibi bir sabit ifadeye katılabilir:</span><span class="sxs-lookup"><span data-stu-id="0b07c-119">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="0b07c-120">[ReadOnly](./readonly.md) anahtar sözcüğü `const` anahtar sözcükten farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0b07c-120">The [readonly](./readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="0b07c-121">Bir `const` alan yalnızca alanın bildiriminde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-121">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="0b07c-122">Bir `readonly` alan, bildirimde ya da bir Oluşturucu içinde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-122">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="0b07c-123">Bu nedenle, `readonly` alan, kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-123">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="0b07c-124">Ayrıca, `const` alan bir derleme zamanı sabiti olsa da, `readonly` Bu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="0b07c-124">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="0b07c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b07c-125">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="0b07c-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b07c-126">Example</span></span>

<span data-ttu-id="0b07c-127">Bu örnek, sabitlerin yerel değişkenler olarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b07c-127">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="0b07c-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0b07c-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0b07c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b07c-129">See also</span></span>

- [<span data-ttu-id="0b07c-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0b07c-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0b07c-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b07c-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0b07c-132">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0b07c-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="0b07c-133">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="0b07c-133">Modifiers</span></span>](index.md)
- [<span data-ttu-id="0b07c-134">readonly</span><span class="sxs-lookup"><span data-stu-id="0b07c-134">readonly</span></span>](./readonly.md)
