---
title: kısmi yöntem - C# Referans
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713228"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="655e1-102">kısmi yöntem (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="655e1-102">partial method (C# Reference)</span></span>

<span data-ttu-id="655e1-103">Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır.</span><span class="sxs-lookup"><span data-stu-id="655e1-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="655e1-104">Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="655e1-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="655e1-105">Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="655e1-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="655e1-106">Aşağıdaki koşullar kısmi yöntemler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="655e1-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="655e1-107">Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="655e1-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="655e1-108">Yöntem boş döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="655e1-108">The method must return void.</span></span>

- <span data-ttu-id="655e1-109">Hiçbir erişim değiştiricisine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="655e1-109">No access modifiers are allowed.</span></span> <span data-ttu-id="655e1-110">Kısmi yöntemler dolaylı olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="655e1-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="655e1-111">Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:</span><span class="sxs-lookup"><span data-stu-id="655e1-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="655e1-112">Daha fazla bilgi için Kısmi [Sınıflar ve Yöntemler'e](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="655e1-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="655e1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="655e1-113">See also</span></span>

- [<span data-ttu-id="655e1-114">C# Referans</span><span class="sxs-lookup"><span data-stu-id="655e1-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="655e1-115">kısmi tip</span><span class="sxs-lookup"><span data-stu-id="655e1-115">partial type</span></span>](partial-type.md)
