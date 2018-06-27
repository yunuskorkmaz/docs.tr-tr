---
title: const anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 985ba9cfefce458fac73aa4b92de0b3d438405c6
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948348"
---
# <a name="const-c-reference"></a><span data-ttu-id="08a83-102">const (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="08a83-102">const (C# Reference)</span></span>

<span data-ttu-id="08a83-103">Kullandığınız `const` sabit bir alan veya sabit bir yerel bildirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="08a83-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="08a83-104">Sabit alanları ve yerel değişkenleri değil ve değiştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="08a83-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="08a83-105">Sabitler numaraları, Boole değerleri, dize veya null bir başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="08a83-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="08a83-106">Herhangi bir zamanda değiştirmeniz beklediğiniz bilgileri temsil eden bir sabit oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="08a83-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="08a83-107">Örneğin, sabit bir alan, bir hizmet, bir ürün sürüm numarası veya bir şirket markası adını fiyat depolamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="08a83-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="08a83-108">Zaman içinde bu değerleri değiştirebilirsiniz ve derleyicileri sabitleri yayıldığından Kitaplıklarınızı ile derlenen diğer kod değişiklikleri görmek için derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="08a83-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="08a83-109">Ayrıca bkz. [readonly](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="08a83-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="08a83-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="08a83-110">For example:</span></span>

```csharp
const int x = 0;
public const double gravitationalConstant = 6.673e-11;
private const string productName = "Visual C#";
```

## <a name="remarks"></a><span data-ttu-id="08a83-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08a83-111">Remarks</span></span>

<span data-ttu-id="08a83-112">Sabit bildiriminde türü bildirimi tanıtır üyeleri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="08a83-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="08a83-113">Yerel bir sabit Başlatıcı veya sabit bir alan için hedef türü örtük olarak dönüştürülebilir sabit bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08a83-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>

<span data-ttu-id="08a83-114">Bir sabit ifadesine derleme zamanında tam olarak değerlendirilecek bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="08a83-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="08a83-115">Başvuru türleri sabitleri için bu nedenle, yalnızca olası değerler `string` ve bir null başvuru.</span><span class="sxs-lookup"><span data-stu-id="08a83-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>

<span data-ttu-id="08a83-116">Sabit bildiriminde birden çok sabitleri gibi bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="08a83-116">The constant declaration can declare multiple constants, such as:</span></span>

```csharp
public const double x = 1.0, y = 2.0, z = 3.0;
```

<span data-ttu-id="08a83-117">`static` Değiştiricisi Sabit bildiriminde izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="08a83-117">The `static` modifier is not allowed in a constant declaration.</span></span>

<span data-ttu-id="08a83-118">Bir sabit bir sabit ifadesine gibi katılabilmesi için:</span><span class="sxs-lookup"><span data-stu-id="08a83-118">A constant can participate in a constant expression, as follows:</span></span>

```csharp
public const int c1 = 5;
public const int c2 = c1 + 100;
```

> [!NOTE]
> <span data-ttu-id="08a83-119">[Readonly](../../../csharp/language-reference/keywords/readonly.md) anahtar sözcüğü farklı olarak `const` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="08a83-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="08a83-120">A `const` alan alan bildirimi sırasında yalnızca başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="08a83-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="08a83-121">A `readonly` bildirimi sırasında veya bir oluşturucuya alan başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="08a83-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="08a83-122">Bu nedenle, `readonly` alanları kullanılan Oluşturucusu bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="08a83-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="08a83-123">Ayrıca, ancak bir `const` alandır derleme zamanı sabiti `readonly` alan, bu satırı olduğu gibi çalışma zamanı sabitleri için kullanılabilir: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="08a83-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>

## <a name="example"></a><span data-ttu-id="08a83-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="08a83-124">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a><span data-ttu-id="08a83-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="08a83-125">Example</span></span>

<span data-ttu-id="08a83-126">Bu örnek, yerel değişkenleri olarak sabitleri kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="08a83-126">This example demonstrates how to use constants as local variables.</span></span>

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="08a83-127">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="08a83-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="08a83-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08a83-128">See also</span></span>

[<span data-ttu-id="08a83-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="08a83-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="08a83-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="08a83-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="08a83-131">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="08a83-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="08a83-132">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="08a83-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
[<span data-ttu-id="08a83-133">readonly</span><span class="sxs-lookup"><span data-stu-id="08a83-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
