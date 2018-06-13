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
ms.openlocfilehash: 555e15110c7af501de05d1f395a72ca4b7800054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595156"
---
# <a name="default-visual-basic"></a><span data-ttu-id="79de1-102">Varsayılan (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79de1-102">Default (Visual Basic)</span></span>
<span data-ttu-id="79de1-103">Bir özelliğin varsayılan özelliği sınıf, yapı veya arabirim tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79de1-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79de1-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79de1-104">Remarks</span></span>  
 <span data-ttu-id="79de1-105">Sınıf, yapı veya arabirim ve özelliklerini en fazla bir belirleyebileceğiniz *varsayılan özellik*, koşuluyla özelliği en az bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="79de1-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="79de1-106">Kod bir üye belirtilmeden bir sınıf veya yapı için bir başvuru yaparsa, Visual Basic bu varsayılan özellik referansı çözümler.</span><span class="sxs-lookup"><span data-stu-id="79de1-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="79de1-107">Varsayılan Özellikler kaynak kod-karakterlerini küçük azalmasına neden olabilir, ancak bunlar kodunuzu okumak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="79de1-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="79de1-108">Sınıf veya yapı adı için bir başvuru yaptığında, çağrıyı yapan kod, sınıf veya yapı, bilinen değilse, bu başvuru sınıf veya yapı kendisini veya varsayılan bir özellik mi erişen belirli olamaz.</span><span class="sxs-lookup"><span data-stu-id="79de1-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="79de1-109">Bu derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="79de1-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="79de1-110">Her zaman kullanarak varsayılan özellik hataları olasılığını biraz azaltabilir [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) denetlemesini derleyici türünü ayarlamak için `On`.</span><span class="sxs-lookup"><span data-stu-id="79de1-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="79de1-111">Önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir varsayılan bir özellik olup olmadığını ve bu durumda kullanmayı planlıyorsanız, ne adıdır.</span><span class="sxs-lookup"><span data-stu-id="79de1-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="79de1-112">Bu olumsuzlukları nedeniyle varsayılan özellikleri tanımlamaya değil göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="79de1-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="79de1-113">Kod okunabilirlik için ayrıca her zaman tüm özelliklerini açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.</span><span class="sxs-lookup"><span data-stu-id="79de1-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="79de1-114">`Default` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="79de1-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="79de1-115">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="79de1-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="79de1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79de1-116">See Also</span></span>  
 [<span data-ttu-id="79de1-117">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="79de1-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="79de1-118">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="79de1-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
