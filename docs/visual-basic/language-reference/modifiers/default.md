---
title: Varsayılan (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: f78ffe42a9d618d44da2a50c0de831396576430c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836733"
---
# <a name="default-visual-basic"></a><span data-ttu-id="4a377-102">Varsayılan (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a377-102">Default (Visual Basic)</span></span>
<span data-ttu-id="4a377-103">Bir özellik için varsayılan özelliği, sınıf, yapı veya arabirim tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a377-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a377-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a377-104">Remarks</span></span>  
 <span data-ttu-id="4a377-105">Bir sınıf, yapı veya arabirim özelliklerinden en fazla birine atayabilirsiniz *varsayılan özellik*, koşuluyla özellik en az bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="4a377-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="4a377-106">Kod, bir üye belirtilmeden bir sınıf veya yapı için bir başvuru yaparsa, Visual Basic varsayılan özelliğinin bu başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="4a377-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="4a377-107">Varsayılan Özellikler kaynak kod-harfler küçük azalmasına neden olabilir, ancak bunlar kodunuzu okunacak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="4a377-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="4a377-108">Bir sınıf veya yapı adı başvuru yaptığında çağıran kod, sınıf veya yapı, birlikte bilinen değilse, bu başvuruyu sınıf veya yapının kendisi veya varsayılan bir özellik olup erişen belirli olamaz.</span><span class="sxs-lookup"><span data-stu-id="4a377-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="4a377-109">Bu, derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a377-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="4a377-110">Her zaman kullanarak biraz varsayılan özellik hata olasılığını azaltabilirsiniz [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) derleyici tür denetlemesini ayarlanacak `On`.</span><span class="sxs-lookup"><span data-stu-id="4a377-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="4a377-111">Bir önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir, varsayılan bir özellik sahip olup olmadığını ve bu durumda kullanmayı planlıyorsanız, onun adı nedir?</span><span class="sxs-lookup"><span data-stu-id="4a377-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="4a377-112">Bu dezavantajların nedeniyle varsayılan özellikleri tanımlamaya değil dikkate almalısınız.</span><span class="sxs-lookup"><span data-stu-id="4a377-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="4a377-113">Kod okunabilirlik açısından, ayrıca her zaman tüm özelliklere açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.</span><span class="sxs-lookup"><span data-stu-id="4a377-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="4a377-114">`Default` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4a377-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="4a377-115">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="4a377-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4a377-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a377-116">See also</span></span>

- [<span data-ttu-id="4a377-117">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="4a377-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="4a377-118">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4a377-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
