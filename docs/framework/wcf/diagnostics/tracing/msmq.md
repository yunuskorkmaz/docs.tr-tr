---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475292"
---
# <a name="msmq"></a><span data-ttu-id="28e75-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="28e75-102">MSMQ</span></span>
<span data-ttu-id="28e75-103">MSMQ uygulamada hiçbir ek etkinlik MSMQ sıraya alınan kanala ve sıraya alınan kanal MSMQ aktarılır.</span><span class="sxs-lookup"><span data-stu-id="28e75-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="28e75-104">Ayrıca, MSMQ ileti kimliği ve SOAP iletisi kimliği (birlikte etkinlik varsa kimliği) gönderme işlemi üzerinde sıraya alınan kanal izlemeleri bir parçası olarak izlenecek.</span><span class="sxs-lookup"><span data-stu-id="28e75-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="28e75-105">MSMQ ileti kimliği ve SOAP iletisi kimliği (birlikte etkinliği kimliği, varsa mevcut) bir alma işlemi üzerinde sıraya alınan kanal izlemeleri bir parçası olarak izlenmesini.</span><span class="sxs-lookup"><span data-stu-id="28e75-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="28e75-106">Alma işlemi üzerinde gerekli aktarımları için herhangi bir aktarım benzer şekilde yürütülür (almak bayt -> işlemi iletisi işlemi ->).</span><span class="sxs-lookup"><span data-stu-id="28e75-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
