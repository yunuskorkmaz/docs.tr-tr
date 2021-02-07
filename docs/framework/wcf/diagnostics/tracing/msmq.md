---
description: 'Daha fazla bilgi edinin: MSMQ'
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 3d694fdab202cd2b3b03c377f72d93c22cbae263
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720585"
---
# <a name="msmq"></a><span data-ttu-id="faba0-103">MSMQ</span><span class="sxs-lookup"><span data-stu-id="faba0-103">MSMQ</span></span>

<span data-ttu-id="faba0-104">MSMQ uygulamasında, sıraya alınan kanaldan MSMQ 'ya ve MSMQ 'dan kuyruğa alınan kanala başka bir etkinlik aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="faba0-104">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="faba0-105">Ayrıca, MSMQ Ileti KIMLIĞI ve SOAP ileti KIMLIĞI (varsa etkinlik KIMLIĞI ile birlikte), bir gönderme işleminde sıraya alınan kanal izlemelerinin bir parçası olarak izlenmektir.</span><span class="sxs-lookup"><span data-stu-id="faba0-105">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="faba0-106">MSMQ Ileti KIMLIĞI ve SOAP ileti KIMLIĞI (varsa etkinlik KIMLIĞI ile birlikte), bir alma işleminde sıraya alınan kanal izlemelerinin bir parçası olarak izleniyor.</span><span class="sxs-lookup"><span data-stu-id="faba0-106">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="faba0-107">Alma işlemindeki gerekli aktarımlar, diğer aktarımlara benzer şekilde yürütülür (bayt al >Işlem iletisi > işlemi).</span><span class="sxs-lookup"><span data-stu-id="faba0-107">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
