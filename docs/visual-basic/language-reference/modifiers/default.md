---
title: "Varsayılan (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="default-visual-basic"></a><span data-ttu-id="27dfc-102">Varsayılan (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27dfc-102">Default (Visual Basic)</span></span>
<span data-ttu-id="27dfc-103">Bir özelliğin varsayılan özelliği sınıf, yapı veya arabirim tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27dfc-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27dfc-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27dfc-104">Remarks</span></span>  
 <span data-ttu-id="27dfc-105">Sınıf, yapı veya arabirim ve özelliklerini en fazla bir belirleyebileceğiniz *varsayılan özellik*, koşuluyla özelliği en az bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="27dfc-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="27dfc-106">Kod bir üye belirtilmeden bir sınıf veya yapı için bir başvuru yaparsa, Visual Basic bu varsayılan özellik referansı çözümler.</span><span class="sxs-lookup"><span data-stu-id="27dfc-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="27dfc-107">Varsayılan Özellikler kaynak kod-karakterlerini küçük azalmasına neden olabilir, ancak bunlar kodunuzu okumak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="27dfc-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="27dfc-108">Sınıf veya yapı adı için bir başvuru yaptığında, çağrıyı yapan kod, sınıf veya yapı, bilinen değilse, bu başvuru sınıf veya yapı kendisini veya varsayılan bir özellik mi erişen belirli olamaz.</span><span class="sxs-lookup"><span data-stu-id="27dfc-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="27dfc-109">Bu derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="27dfc-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="27dfc-110">Her zaman kullanarak varsayılan özellik hataları olasılığını biraz azaltabilir [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) denetlemesini derleyici türünü ayarlamak için `On`.</span><span class="sxs-lookup"><span data-stu-id="27dfc-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="27dfc-111">Önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir varsayılan bir özellik olup olmadığını ve bu durumda kullanmayı planlıyorsanız, ne adıdır.</span><span class="sxs-lookup"><span data-stu-id="27dfc-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="27dfc-112">Bu olumsuzlukları nedeniyle varsayılan özellikleri tanımlamaya değil göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="27dfc-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="27dfc-113">Kod okunabilirlik için ayrıca her zaman tüm özelliklerini açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.</span><span class="sxs-lookup"><span data-stu-id="27dfc-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="27dfc-114">`Default` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="27dfc-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="27dfc-115">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="27dfc-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="27dfc-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27dfc-116">See Also</span></span>  
 [<span data-ttu-id="27dfc-117">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="27dfc-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="27dfc-118">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="27dfc-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
