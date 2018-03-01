---
title: "&#39; &lt;eventname&gt;&#39; bir olaydır ve doğrudan çağrılamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="21e9f-102">&#39; &lt;eventname&gt;&#39; bir olaydır ve doğrudan çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="21e9f-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="21e9f-103">' <`eventname`>' bir olaydır ve bu nedenle doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="21e9f-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="21e9f-104">Kullanım bir `RaiseEvent` deyimi bir olayı.</span><span class="sxs-lookup"><span data-stu-id="21e9f-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="21e9f-105">Bir yordam çağrısı yordam adı için bir olay belirtir.</span><span class="sxs-lookup"><span data-stu-id="21e9f-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="21e9f-106">Olay işleyicisi bir yordamdır, ancak olay gerçekleşti ve işlenmiş gerekir bir sinyal, aygıttır.</span><span class="sxs-lookup"><span data-stu-id="21e9f-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="21e9f-107">**Hata Kimliği:** BC32022</span><span class="sxs-lookup"><span data-stu-id="21e9f-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21e9f-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="21e9f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="21e9f-109">Kullanım bir `RaiseEvent` bir olay sinyal ve yordam ya da bu yordamlar çağırma bildirimini.</span><span class="sxs-lookup"><span data-stu-id="21e9f-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e9f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21e9f-110">See Also</span></span>  
 [<span data-ttu-id="21e9f-111">RaiseEvent deyimi</span><span class="sxs-lookup"><span data-stu-id="21e9f-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
