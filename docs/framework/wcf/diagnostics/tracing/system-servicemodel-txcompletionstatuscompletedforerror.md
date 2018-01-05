---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25106bffe6d541a89c786035db3d3266d861fd5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="6eb5f-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="6eb5f-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="6eb5f-103">Belirtilen işlem için belirtilen işlem, bir işlenmemiş yürütme özel durum nedeniyle tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6eb5f-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eb5f-104">Description</span></span>  
 <span data-ttu-id="6eb5f-105">Geçerli işlemi tamamlamak için girişimi sırasında bir hata oluştuğunda izlenen.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="6eb5f-106">Bir yanıt önce aşması veya hataya çağırana gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6eb5f-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="6eb5f-107">Troubleshooting</span></span>  
 <span data-ttu-id="6eb5f-108">Özel durum iletisi ve tıklatılabilir tüm öğeler için izlenen iletisini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb5f-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6eb5f-109">See Also</span></span>  
 [<span data-ttu-id="6eb5f-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="6eb5f-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6eb5f-111">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="6eb5f-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6eb5f-112">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="6eb5f-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
