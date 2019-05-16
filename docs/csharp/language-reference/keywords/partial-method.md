---
title: Kısmi yöntem - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 14bcd3329b6ca8e46f6c180c97174a561108d143
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633354"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="4e4dc-102">Kısmi yöntem (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4e4dc-102">partial method (C# Reference)</span></span>

<span data-ttu-id="4e4dc-103">Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="4e4dc-104">Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="4e4dc-105">Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="4e4dc-106">Aşağıdaki koşullar kısmi yöntemler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4e4dc-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="4e4dc-107">Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="4e4dc-108">Yöntem boş döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-108">The method must return void.</span></span>

- <span data-ttu-id="4e4dc-109">Hiçbir erişim değiştiricisine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-109">No access modifiers are allowed.</span></span> <span data-ttu-id="4e4dc-110">Kısmi yöntemler dolaylı olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="4e4dc-111">Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:</span><span class="sxs-lookup"><span data-stu-id="4e4dc-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="4e4dc-112">Daha fazla bilgi için [kısmi sınıflar ve yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4e4dc-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e4dc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e4dc-113">See also</span></span>

- [<span data-ttu-id="4e4dc-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4e4dc-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e4dc-115">Kısmi türü</span><span class="sxs-lookup"><span data-stu-id="4e4dc-115">partial type</span></span>](partial-type.md)
