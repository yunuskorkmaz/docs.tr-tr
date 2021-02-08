---
description: "Hakkında daha fazla bilgi edinin: BC32022: ' <eventname> ' bir olaydır ve doğrudan çağrılamaz"
title: "'<eventname>' bir olaydır ve doğrudan çağrılamaz"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: f9d4b8fe54e1101e7963933f871cf5af2c1af903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796450"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="80ae3-103">BC32022: ' \<eventname> ' bir olaydır ve doğrudan çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="80ae3-103">BC32022: '\<eventname>' is an event, and cannot be called directly</span></span>

<span data-ttu-id="80ae3-104">' <`eventname`> ' bir olaydır, bu nedenle doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="80ae3-104">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="80ae3-105">Bir `RaiseEvent` olayı yükseltmek için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="80ae3-105">Use a `RaiseEvent` statement to raise an event.</span></span>

 <span data-ttu-id="80ae3-106">Yordam çağrısı, yordam adı için bir olay belirtir.</span><span class="sxs-lookup"><span data-stu-id="80ae3-106">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="80ae3-107">Olay işleyicisi bir yordamdır, ancak olayın kendisi, oluşturulması ve işlenmesi gereken bir sinyal aygıtıdır.</span><span class="sxs-lookup"><span data-stu-id="80ae3-107">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>

 <span data-ttu-id="80ae3-108">**Hata kimliği:** BC32022</span><span class="sxs-lookup"><span data-stu-id="80ae3-108">**Error ID:** BC32022</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="80ae3-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="80ae3-109">To correct this error</span></span>

- <span data-ttu-id="80ae3-110">Bir `RaiseEvent` olayı işaret etmek ve onu işleyen yordamı ya da yordamları çağırmak için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="80ae3-110">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>

## <a name="see-also"></a><span data-ttu-id="80ae3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80ae3-111">See also</span></span>

- [<span data-ttu-id="80ae3-112">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="80ae3-112">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
