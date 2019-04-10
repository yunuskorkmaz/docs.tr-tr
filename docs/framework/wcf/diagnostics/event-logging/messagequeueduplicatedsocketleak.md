---
title: MessageQueueDuplicatedSocketLeak
ms.date: 03/30/2017
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
ms.openlocfilehash: 8533d53dc6a2d4510ffec2dcbf0e9bef15cde6ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206128"
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="c151a-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="c151a-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="c151a-103">Kimliği: 165</span><span class="sxs-lookup"><span data-stu-id="c151a-103">Id: 165</span></span>  
  
 <span data-ttu-id="c151a-104">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="c151a-104">Severity: Error</span></span>  
  
 <span data-ttu-id="c151a-105">Kategori: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="c151a-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="c151a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c151a-106">Description</span></span>  
 <span data-ttu-id="c151a-107">Bu olay, yinelenen bir yuva gönderilirken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c151a-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="c151a-108">Bu işleyici, işlemde artık sızmış.</span><span class="sxs-lookup"><span data-stu-id="c151a-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="c151a-109">Olay kaynağı, özel durum, işlem adı ve işlem kimliği listeler</span><span class="sxs-lookup"><span data-stu-id="c151a-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c151a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c151a-110">See also</span></span>

- [<span data-ttu-id="c151a-111">Etkinlikleri Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="c151a-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="c151a-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c151a-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
