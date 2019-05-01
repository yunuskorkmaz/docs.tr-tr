---
title: "'<eventname>' bir olaydır ve doğrudan çağrılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: bf900566bdb4ecf8d8961a12b5dd67ba426caf27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803331"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="aa1fb-102">'\<eventname >' bir olaydır ve doğrudan çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="aa1fb-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="aa1fb-103">' <`eventname`>' bir olaydır ve bu nedenle doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="aa1fb-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="aa1fb-104">Kullanım bir `RaiseEvent` deyimi bir olay oluşturabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="aa1fb-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="aa1fb-105">Yordam çağrısı yordam adı için bir olay belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa1fb-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="aa1fb-106">Bir olay işleyicisi bir yordam, ancak olay gerçekleşti ve işlenen gerekir bir sinyal bir cihaz.</span><span class="sxs-lookup"><span data-stu-id="aa1fb-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="aa1fb-107">**Hata Kimliği:** BC32022</span><span class="sxs-lookup"><span data-stu-id="aa1fb-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa1fb-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="aa1fb-108">To correct this error</span></span>  
  
1. <span data-ttu-id="aa1fb-109">Kullanım bir `RaiseEvent` deyimini olaya sinyal ve yordamı veya bunu işleyen yordamlarını çağırma.</span><span class="sxs-lookup"><span data-stu-id="aa1fb-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa1fb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa1fb-110">See also</span></span>

- [<span data-ttu-id="aa1fb-111">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="aa1fb-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
