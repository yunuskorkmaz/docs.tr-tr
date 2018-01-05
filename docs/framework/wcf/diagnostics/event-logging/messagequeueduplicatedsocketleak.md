---
title: MessageQueueDuplicatedSocketLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ea58a826920d440ab903270f796a3d94d17ad47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="8055e-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="8055e-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="8055e-103">Kimliği: 165</span><span class="sxs-lookup"><span data-stu-id="8055e-103">Id: 165</span></span>  
  
 <span data-ttu-id="8055e-104">Önem derecesi: hata</span><span class="sxs-lookup"><span data-stu-id="8055e-104">Severity: Error</span></span>  
  
 <span data-ttu-id="8055e-105">Kategori: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="8055e-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="8055e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8055e-106">Description</span></span>  
 <span data-ttu-id="8055e-107">Bu olay, yinelenen bir yuva gönderilirken bir hata oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8055e-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="8055e-108">Bu işleyici şimdi işlemde sızmış.</span><span class="sxs-lookup"><span data-stu-id="8055e-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="8055e-109">Olay kaynağı, özel durum, işlem adı ve işlem kimliği listeler</span><span class="sxs-lookup"><span data-stu-id="8055e-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8055e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8055e-110">See Also</span></span>  
 [<span data-ttu-id="8055e-111">Günlüğe Olay Kaydetme</span><span class="sxs-lookup"><span data-stu-id="8055e-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="8055e-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8055e-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
