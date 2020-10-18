---
title: "'<eventname>' bir olaydır ve doğrudan çağrılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 246cb92daa2c838c95f695542f33cf02af42764d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161991"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="7e93b-102">BC32022: ' \<eventname> ' bir olaydır ve doğrudan çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="7e93b-102">BC32022: '\<eventname>' is an event, and cannot be called directly</span></span>

<span data-ttu-id="7e93b-103">' <`eventname`> ' bir olaydır, bu nedenle doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="7e93b-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="7e93b-104">Bir `RaiseEvent` olayı yükseltmek için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e93b-104">Use a `RaiseEvent` statement to raise an event.</span></span>

 <span data-ttu-id="7e93b-105">Yordam çağrısı, yordam adı için bir olay belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e93b-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="7e93b-106">Olay işleyicisi bir yordamdır, ancak olayın kendisi, oluşturulması ve işlenmesi gereken bir sinyal aygıtıdır.</span><span class="sxs-lookup"><span data-stu-id="7e93b-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>

 <span data-ttu-id="7e93b-107">**Hata kimliği:** BC32022</span><span class="sxs-lookup"><span data-stu-id="7e93b-107">**Error ID:** BC32022</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7e93b-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7e93b-108">To correct this error</span></span>

- <span data-ttu-id="7e93b-109">Bir `RaiseEvent` olayı işaret etmek ve onu işleyen yordamı ya da yordamları çağırmak için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e93b-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e93b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e93b-110">See also</span></span>

- [<span data-ttu-id="7e93b-111">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="7e93b-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
