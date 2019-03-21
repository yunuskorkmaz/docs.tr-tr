---
title: const anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 7cf4fc52691565a850b4f34574828ad4e043998e
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307895"
---
# <a name="const-c-reference"></a><span data-ttu-id="5ac70-102">const (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5ac70-102">const (C# Reference)</span></span>

<span data-ttu-id="5ac70-103">Kullandığınız `const` bir sabit alanı ya da sabit yerel bildirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5ac70-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="5ac70-104">Sabit alanlar ve yerel değişkenleri değildir ve değiştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="5ac70-105">Sabitler, sayı, Boole değerleri, dize veya null başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="5ac70-106">Dilediğiniz zaman değiştirin beklediğiniz bilgileri temsil eden bir sabit oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="5ac70-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="5ac70-107">Örneğin, sabit bir alan bir hizmeti, bir ürün sürüm numarası veya bir şirketin marka adı fiyatı depolamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5ac70-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="5ac70-108">Bu değerler, zaman içinde değişebilir ve derleyiciler sabitleri yayıldığından Kitaplıklarınızı ile derlenmiş olan diğer kod değişiklikleri görmek için yeniden derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="5ac70-109">Ayrıca bkz: [salt okunur](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5ac70-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="5ac70-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5ac70-110">For example:</span></span>

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="5ac70-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ac70-111">Remarks</span></span>

<span data-ttu-id="5ac70-112">Sabit bildirimi türü bildirimin gösterdiği üyelerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="5ac70-113">Başlatıcı bir sabit yerel öğesi veya sabit alanının hedef türe örtük olarak dönüştürülebilir bir sabit ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ac70-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="5ac70-114">Sabit bir ifade derleme zamanında tam olarak değerlendirilebilecek bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="5ac70-115">Başvuru türü sabitleri için bu nedenle, tek olası değerler `string` ve null bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="5ac70-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="5ac70-116">Sabit bildiriminde aşağıdaki gibi birden fazla sabit bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="5ac70-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

<span data-ttu-id="5ac70-117">`static` Değiştiricisi Sabit bildiriminde izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="5ac70-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="5ac70-118">Bir sabit sabit bir ifadede gibi katılabilir:</span><span class="sxs-lookup"><span data-stu-id="5ac70-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> <span data-ttu-id="5ac70-119">[Salt okunur](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğünden farklıdır `const` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5ac70-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="5ac70-120">A `const` alanı alanın bildiriminde yalnızca başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="5ac70-121">A `readonly` alanı bildirimde veya oluşturucuda başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="5ac70-122">Bu nedenle, `readonly` alanları kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="5ac70-123">Ayrıca, ancak bir `const` alandır bir derleme zamanı sabiti `readonly` alan, bu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="5ac70-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="5ac70-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac70-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="5ac70-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac70-125">Example</span></span>

<span data-ttu-id="5ac70-126">Bu örnek, sabitlerin yerel değişkenler olarak kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ac70-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="5ac70-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5ac70-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5ac70-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac70-128">See also</span></span>

- [<span data-ttu-id="5ac70-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5ac70-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="5ac70-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5ac70-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5ac70-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5ac70-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="5ac70-132">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5ac70-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="5ac70-133">readonly</span><span class="sxs-lookup"><span data-stu-id="5ac70-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
