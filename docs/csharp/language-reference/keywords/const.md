---
title: const anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: f586b6d097a8592fd74e92df7886b519d623e478
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393011"
---
# <a name="const-c-reference"></a><span data-ttu-id="722a9-102">const (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="722a9-102">const (C# Reference)</span></span>

<span data-ttu-id="722a9-103">Kullandığınız `const` bir sabit alanı ya da sabit yerel bildirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="722a9-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="722a9-104">Sabit alanlar ve yerel değişkenleri değildir ve değiştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="722a9-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="722a9-105">Sabitler, sayı, Boole değerleri, dize veya null başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="722a9-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="722a9-106">Dilediğiniz zaman değiştirin beklediğiniz bilgileri temsil eden bir sabit oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="722a9-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="722a9-107">Örneğin, sabit bir alan bir hizmeti, bir ürün sürüm numarası veya bir şirketin marka adı fiyatı depolamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="722a9-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="722a9-108">Bu değerler, zaman içinde değişebilir ve derleyiciler sabitleri yayıldığından Kitaplıklarınızı ile derlenmiş olan diğer kod değişiklikleri görmek için yeniden derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="722a9-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="722a9-109">Ayrıca bkz: [salt okunur](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="722a9-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="722a9-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="722a9-110">For example:</span></span>

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="722a9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="722a9-111">Remarks</span></span>

<span data-ttu-id="722a9-112">Sabit bildirimi türü bildirimin gösterdiği üyelerin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="722a9-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="722a9-113">Başlatıcı bir sabit yerel öğesi veya sabit alanının hedef türe örtük olarak dönüştürülebilir bir sabit ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="722a9-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="722a9-114">Sabit bir ifade derleme zamanında tam olarak değerlendirilebilecek bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="722a9-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="722a9-115">Başvuru türü sabitleri için bu nedenle, tek olası değerler `string` ve null bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="722a9-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="722a9-116">Sabit bildiriminde aşağıdaki gibi birden fazla sabit bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="722a9-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

<span data-ttu-id="722a9-117">`static` Değiştiricisi Sabit bildiriminde izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="722a9-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="722a9-118">Bir sabit sabit bir ifadede gibi katılabilir:</span><span class="sxs-lookup"><span data-stu-id="722a9-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> <span data-ttu-id="722a9-119">[Salt okunur](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğünden farklıdır `const` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="722a9-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="722a9-120">A `const` alanı alanın bildiriminde yalnızca başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="722a9-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="722a9-121">A `readonly` alanı bildirimde veya oluşturucuda başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="722a9-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="722a9-122">Bu nedenle, `readonly` alanları kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="722a9-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="722a9-123">Ayrıca, ancak bir `const` alandır bir derleme zamanı sabiti `readonly` alan, bu satırda olduğu gibi çalışma zamanı sabitleri için kullanılabilir: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="722a9-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="722a9-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="722a9-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="722a9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="722a9-125">Example</span></span>

<span data-ttu-id="722a9-126">Bu örnek, sabitlerin yerel değişkenler olarak kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="722a9-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="722a9-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="722a9-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="722a9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="722a9-128">See also</span></span>

- [<span data-ttu-id="722a9-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="722a9-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="722a9-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="722a9-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="722a9-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="722a9-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="722a9-132">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="722a9-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="722a9-133">readonly</span><span class="sxs-lookup"><span data-stu-id="722a9-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
