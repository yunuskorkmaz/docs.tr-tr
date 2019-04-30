---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663732"
---
# <a name="msmq"></a><span data-ttu-id="7f32d-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="7f32d-102">MSMQ</span></span>
<span data-ttu-id="7f32d-103">MSMQ uygulamada herhangi bir ek eylem MSMQ sıraya alınan kanala ve sıraya alınan kanala MSMQ aktarılır.</span><span class="sxs-lookup"><span data-stu-id="7f32d-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="7f32d-104">Ayrıca, MSMQ ileti kimliği ve SOAP ileti kimliği (etkinlik varsa kimliği) ile birlikte bir gönderme işlemi üzerinde sıraya alınan kanal izlemelerini bir parçası olarak izlendiğini.</span><span class="sxs-lookup"><span data-stu-id="7f32d-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="7f32d-105">MSMQ ileti kimliği ve SOAP ileti kimliği (birlikte, etkinlik kimliği, varsa var), kuyruğa alınmış kanal izlemelerini alma işlemi üzerinde bir parçası olarak izlendiğini.</span><span class="sxs-lookup"><span data-stu-id="7f32d-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="7f32d-106">Alma işlemi üzerinde gerekli aktarımları herhangi bir aktarım için benzer şekilde yürütülür (almak bayt işlemi iletisi -> işlem ->).</span><span class="sxs-lookup"><span data-stu-id="7f32d-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
