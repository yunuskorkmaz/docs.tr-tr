---
title: MessageQueueDuplicatedSocketLeak
ms.date: 03/30/2017
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
ms.openlocfilehash: 8533d53dc6a2d4510ffec2dcbf0e9bef15cde6ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206128"
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="b6441-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="b6441-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="b6441-103">Kimliği: 165</span><span class="sxs-lookup"><span data-stu-id="b6441-103">Id: 165</span></span>  
  
 <span data-ttu-id="b6441-104">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="b6441-104">Severity: Error</span></span>  
  
 <span data-ttu-id="b6441-105">Kategori: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="b6441-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="b6441-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6441-106">Description</span></span>  
 <span data-ttu-id="b6441-107">Bu olay, yinelenen bir yuva gönderilirken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6441-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="b6441-108">Bu işleyici, işlemde artık sızmış.</span><span class="sxs-lookup"><span data-stu-id="b6441-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="b6441-109">Olay kaynağı, özel durum, işlem adı ve işlem kimliği listeler</span><span class="sxs-lookup"><span data-stu-id="b6441-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6441-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6441-110">See also</span></span>

- [<span data-ttu-id="b6441-111">Günlüğe Olay Kaydetme</span><span class="sxs-lookup"><span data-stu-id="b6441-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="b6441-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b6441-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
