---
title: "Uygulamanızda Sorun Giderme için İzleme Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7676b9bb-cbd1-41fd-9a93-cc615af6e2d0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb46ad5fe95405c78baf3173a982969e0e7092fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-tracing-to-troubleshoot-your-application"></a><span data-ttu-id="28780-102">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="28780-102">Using Tracing to Troubleshoot Your Application</span></span>
<span data-ttu-id="28780-103">Bu bölüm nasıl izleme uygulamanızda sorun giderme için kullanabileceğiniz açıklayan çeşitli konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="28780-103">This section contains various topics that describe how you can use tracing to troubleshoot your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28780-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="28780-104">In This Section</span></span>  
 [<span data-ttu-id="28780-105">İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="28780-105">Recommended Settings for Tracing and Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)  
 <span data-ttu-id="28780-106">Üretim ve hata ayıklama ortamları için önerilen ayarları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="28780-106">Describes suggested settings for production and debugging environments.</span></span>  
  
 [<span data-ttu-id="28780-107">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="28780-107">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 <span data-ttu-id="28780-108">Hizmet izleme Görüntüleyicisi aracı görüntülemek, bağıntılı ve izleme verileri çözümlemek için nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="28780-108">Describes how you can use the Service Trace Viewer tool to view, correlate and analyze trace data.</span></span>  
  
 [<span data-ttu-id="28780-109">Önemli İzlemeler</span><span class="sxs-lookup"><span data-stu-id="28780-109">Significant Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/significant-traces.md)  
 <span data-ttu-id="28780-110">Önemli izlemeler tarafından gösterilen listesini [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28780-110">A list of major traces emitted by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="28780-111">İstemcide Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="28780-111">Debugging on the Client</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/debugging-on-the-client.md)  
 <span data-ttu-id="28780-112">İstemcilerin uygulamanızda hata ayıklama olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="28780-112">Enables clients to debug your application.</span></span>  
  
 [<span data-ttu-id="28780-113">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="28780-113">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="28780-114">E2E için kullanılan izlemeleri açıklar [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] senaryolarında, örneğin, zaman uyumlu wsHttp istek-yanıt ve zaman uyumsuz TCP tek yönlü istekleri.</span><span class="sxs-lookup"><span data-stu-id="28780-114">Describes traces used for E2E [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] scenarios, for example, synchronous wsHttp request-replies, and asynchronous TCP one-way requests.</span></span>  
  
 [<span data-ttu-id="28780-115">Kullanıcı Kodu İzlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="28780-115">Emitting User-Code Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)  
 <span data-ttu-id="28780-116">Tanılama amaçla ve WCF izlemeleri ile bağıntı daha sonra kullanılmak üzere izleme verileri proaktif olarak oluşturabilmesi için program aracılığıyla içinde kullanıcı kodu izleri yayma açıklar.</span><span class="sxs-lookup"><span data-stu-id="28780-116">Describes how to emit traces programmatically in user code, so that you can proactively create instrumentation data to be used later for diagnostic purpose, and in correlation with WCF traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28780-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28780-117">See Also</span></span>  
 [<span data-ttu-id="28780-118">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="28780-118">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="28780-119">İzleme</span><span class="sxs-lookup"><span data-stu-id="28780-119">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="28780-120">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="28780-120">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
