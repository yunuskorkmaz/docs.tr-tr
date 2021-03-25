---
description: kısmi Yöntem-C# başvurusu
title: kısmi Yöntem-C# başvurusu
ms.date: 03/23/2021
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 240ad6f2f5792e4db9b032e36991f3c398f1d2f9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111016"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="28418-103">partial yöntemi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="28418-103">partial method (C# Reference)</span></span>

<span data-ttu-id="28418-104">Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır.</span><span class="sxs-lookup"><span data-stu-id="28418-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="28418-105">Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="28418-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="28418-106">Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="28418-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="28418-107">Aşağıdaki koşullar kısmi yöntemler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="28418-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="28418-108">Bildirimler bağlamsal anahtar sözcükle [kısmen](../../language-reference/keywords/partial-type.md)başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="28418-108">Declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md).</span></span>

- <span data-ttu-id="28418-109">Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="28418-109">Signatures in both parts of the partial type must match.</span></span>

<span data-ttu-id="28418-110">Kısmi yöntemin aşağıdaki durumlarda uygulanması gerekmez:</span><span class="sxs-lookup"><span data-stu-id="28418-110">A partial method isn't required to have an implementation in the following cases:</span></span>

- <span data-ttu-id="28418-111">Herhangi bir erişilebilirlik değiştiricilerine (varsayılan [özel](../../language-reference/keywords/private.md)dahil) sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="28418-111">It doesn't have any accessibility modifiers (including the default [private](../../language-reference/keywords/private.md)).</span></span>

- <span data-ttu-id="28418-112">[Void](../../language-reference/builtin-types/void.md)döndürür.</span><span class="sxs-lookup"><span data-stu-id="28418-112">It returns [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="28418-113">[Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi yok.</span><span class="sxs-lookup"><span data-stu-id="28418-113">It doesn't have any [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="28418-114">Şu değiştiricilerin herhangi birine sahip değildir [sanal](../../language-reference/keywords/virtual.md), [geçersiz kılma](../../language-reference/keywords/override.md), [Sealed](../../language-reference/keywords/sealed.md), [New](../../language-reference/keywords/new-modifier.md)veya [extern](../../language-reference/keywords/extern.md).</span><span class="sxs-lookup"><span data-stu-id="28418-114">It doesn't have any of the following modifiers [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), [sealed](../../language-reference/keywords/sealed.md), [new](../../language-reference/keywords/new-modifier.md), or [extern](../../language-reference/keywords/extern.md).</span></span>

<span data-ttu-id="28418-115">Tüm bu kısıtlamalara uymayan herhangi bir Yöntem (örneğin, `public virtual partial void` yöntemi) bir uygulama sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="28418-115">Any method that doesn't conform to all those restrictions (for example, `public virtual partial void` method), must provide an implementation.</span></span>

<span data-ttu-id="28418-116">Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:</span><span class="sxs-lookup"><span data-stu-id="28418-116">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="28418-117">Kısmi yöntemler de kaynak oluşturucularla birlikte yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="28418-117">Partial methods can also be useful in combination with source generators.</span></span> <span data-ttu-id="28418-118">Örneğin, bir Regex aşağıdaki model kullanılarak tanımlanabilir:</span><span class="sxs-lookup"><span data-stu-id="28418-118">For example a regex could be defined using the following pattern:</span></span>

```csharp
[RegexGenerated("(dog|cat|fish)")]
partial bool IsPetMatch(string input);
```

<span data-ttu-id="28418-119">Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="28418-119">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28418-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28418-120">See also</span></span>

- [<span data-ttu-id="28418-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="28418-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="28418-122">Kısmi tür</span><span class="sxs-lookup"><span data-stu-id="28418-122">partial type</span></span>](partial-type.md)
