---
title: "'<eventname>' bir olaydır ve doğrudan çağrılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4e27d9ce788ae7b9741c0cb80da776959748b8b9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272733"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="25d44-102">'\<eventname >' bir olaydır ve doğrudan çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="25d44-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="25d44-103">' <`eventname`>' bir olaydır ve bu nedenle doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="25d44-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="25d44-104">Kullanım bir `RaiseEvent` deyimi bir olay oluşturabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="25d44-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="25d44-105">Yordam çağrısı yordam adı için bir olay belirtir.</span><span class="sxs-lookup"><span data-stu-id="25d44-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="25d44-106">Bir olay işleyicisi bir yordam, ancak olay gerçekleşti ve işlenen gerekir bir sinyal bir cihaz.</span><span class="sxs-lookup"><span data-stu-id="25d44-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="25d44-107">**Hata Kimliği:** BC32022</span><span class="sxs-lookup"><span data-stu-id="25d44-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25d44-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="25d44-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="25d44-109">Kullanım bir `RaiseEvent` deyimini olaya sinyal ve yordamı veya bunu işleyen yordamlarını çağırma.</span><span class="sxs-lookup"><span data-stu-id="25d44-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d44-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25d44-110">See also</span></span>
- [<span data-ttu-id="25d44-111">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="25d44-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
