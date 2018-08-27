---
title: partial (Yöntem) (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 69e16dd8b0fe0055124aca90fea65a36d9e413f3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933691"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="a6ac3-102">partial (Yöntem) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a6ac3-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="a6ac3-103">Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="a6ac3-104">Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="a6ac3-105">Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="a6ac3-106">Aşağıdaki koşullar kısmi yöntemler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a6ac3-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="a6ac3-107">Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="a6ac3-108">Yöntem boş döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="a6ac3-109">Hiçbir erişim değiştiricisine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-109">No access modifiers are allowed.</span></span> <span data-ttu-id="a6ac3-110">Kısmi yöntemler dolaylı olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="a6ac3-111">Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:</span><span class="sxs-lookup"><span data-stu-id="a6ac3-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="a6ac3-112">Daha fazla bilgi için [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a6ac3-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ac3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6ac3-113">See Also</span></span>

- [<span data-ttu-id="a6ac3-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="a6ac3-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a6ac3-115">partial (Tür)</span><span class="sxs-lookup"><span data-stu-id="a6ac3-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
