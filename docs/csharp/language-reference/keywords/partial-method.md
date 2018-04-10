---
title: partial (Yöntem) (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03962a59d5dbe0146cad9835f81d41c06914795b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="57fd5-102">partial (Yöntem) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="57fd5-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="57fd5-103">Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır.</span><span class="sxs-lookup"><span data-stu-id="57fd5-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="57fd5-104">Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="57fd5-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="57fd5-105">Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="57fd5-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="57fd5-106">Aşağıdaki koşullar kısmi yöntemler için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="57fd5-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="57fd5-107">Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="57fd5-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="57fd5-108">Yöntem boş döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="57fd5-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="57fd5-109">Hiçbir erişim değiştiricisine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="57fd5-109">No access modifiers are allowed.</span></span> <span data-ttu-id="57fd5-110">Kısmi yöntemler dolaylı olarak özeldir.</span><span class="sxs-lookup"><span data-stu-id="57fd5-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="57fd5-111">Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:</span><span class="sxs-lookup"><span data-stu-id="57fd5-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="57fd5-112">Daha fazla bilgi için bkz: [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="57fd5-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57fd5-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57fd5-113">See Also</span></span>  
 [<span data-ttu-id="57fd5-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="57fd5-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="57fd5-115">partial (tür)</span><span class="sxs-lookup"><span data-stu-id="57fd5-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
