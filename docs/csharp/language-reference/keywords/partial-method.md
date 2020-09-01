---
description: kısmi Yöntem-C# başvurusu
title: kısmi Yöntem-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: d6c433fd30f6ec51355bdefee90d815783487c1b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134386"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="ece3f-103">partial yöntemi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ece3f-103">partial method (C# Reference)</span></span>

<span data-ttu-id="ece3f-104">Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır.</span><span class="sxs-lookup"><span data-stu-id="ece3f-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="ece3f-105">Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ece3f-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="ece3f-106">Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ece3f-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="ece3f-107">Aşağıdaki koşullar kısmi yöntemler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ece3f-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="ece3f-108">Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ece3f-108">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="ece3f-109">Yöntem boş döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="ece3f-109">The method must return void.</span></span>

- <span data-ttu-id="ece3f-110">Hiçbir erişim değiştiricisine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ece3f-110">No access modifiers are allowed.</span></span> <span data-ttu-id="ece3f-111">Kısmi yöntemler dolaylı olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="ece3f-111">Partial methods are implicitly private.</span></span>

<span data-ttu-id="ece3f-112">Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:</span><span class="sxs-lookup"><span data-stu-id="ece3f-112">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="ece3f-113">Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ece3f-113">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ece3f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ece3f-114">See also</span></span>

- [<span data-ttu-id="ece3f-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ece3f-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ece3f-116">Kısmi tür</span><span class="sxs-lookup"><span data-stu-id="ece3f-116">partial type</span></span>](partial-type.md)
