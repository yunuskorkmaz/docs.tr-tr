---
title: MessageQueueDuplicatedSocketLeak
ms.date: 03/30/2017
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
ms.openlocfilehash: 8533d53dc6a2d4510ffec2dcbf0e9bef15cde6ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999199"
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="a9a54-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="a9a54-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="a9a54-103">Kimliği: 165</span><span class="sxs-lookup"><span data-stu-id="a9a54-103">Id: 165</span></span>  
  
 <span data-ttu-id="a9a54-104">Önem derecesi: Hata</span><span class="sxs-lookup"><span data-stu-id="a9a54-104">Severity: Error</span></span>  
  
 <span data-ttu-id="a9a54-105">Kategori: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="a9a54-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="a9a54-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9a54-106">Description</span></span>  
 <span data-ttu-id="a9a54-107">Bu olay, yinelenen bir yuva gönderilirken bir hata oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9a54-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="a9a54-108">Bu işleyici, işlemde artık sızmış.</span><span class="sxs-lookup"><span data-stu-id="a9a54-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="a9a54-109">Olay kaynağı, özel durum, işlem adı ve işlem kimliği listeler</span><span class="sxs-lookup"><span data-stu-id="a9a54-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a54-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9a54-110">See also</span></span>

- [<span data-ttu-id="a9a54-111">Günlüğe Olay Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a9a54-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [<span data-ttu-id="a9a54-112">Etkinlik Genel Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a9a54-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
