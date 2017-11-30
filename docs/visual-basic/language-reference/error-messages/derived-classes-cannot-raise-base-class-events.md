---
title: "Türetilmiş sınıflar temel sınıf olayları oluşturamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="eb7cf-102">Türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="eb7cf-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="eb7cf-103">Bir olay, içinde bildirildiği yalnızca bildirim alanından yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="eb7cf-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="eb7cf-104">Bu nedenle, bir sınıfın başka bir sınıf, hatta bir onu türetildiği olaylarından yükseltemez.</span><span class="sxs-lookup"><span data-stu-id="eb7cf-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="eb7cf-105">**Hata Kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="eb7cf-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb7cf-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="eb7cf-106">To correct this error</span></span>  
  
-   <span data-ttu-id="eb7cf-107">Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta; bu nedenle deyimi.</span><span class="sxs-lookup"><span data-stu-id="eb7cf-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7cf-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb7cf-108">See Also</span></span>  
 [<span data-ttu-id="eb7cf-109">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="eb7cf-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="eb7cf-110">RaiseEvent deyimi</span><span class="sxs-lookup"><span data-stu-id="eb7cf-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
