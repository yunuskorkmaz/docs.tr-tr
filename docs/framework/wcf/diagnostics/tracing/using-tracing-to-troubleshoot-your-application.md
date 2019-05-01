---
title: Uygulamanızda Sorun Giderme için İzleme Kullanma
ms.date: 03/30/2017
ms.assetid: 7676b9bb-cbd1-41fd-9a93-cc615af6e2d0
ms.openlocfilehash: a173596b5b4bfbc97a1d013251d654d8073a5c10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964482"
---
# <a name="using-tracing-to-troubleshoot-your-application"></a><span data-ttu-id="1793e-102">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="1793e-102">Using Tracing to Troubleshoot Your Application</span></span>
<span data-ttu-id="1793e-103">Bu bölüm, nasıl izleme uygulamanızda sorun giderme için kullanabileceğiniz açıklayan çeşitli konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="1793e-103">This section contains various topics that describe how you can use tracing to troubleshoot your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1793e-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1793e-104">In This Section</span></span>  
 [<span data-ttu-id="1793e-105">İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="1793e-105">Recommended Settings for Tracing and Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)  
 <span data-ttu-id="1793e-106">Üretim ve hata ayıklama ortamları için önerilen ayarları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1793e-106">Describes suggested settings for production and debugging environments.</span></span>  
  
 [<span data-ttu-id="1793e-107">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="1793e-107">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 <span data-ttu-id="1793e-108">Görüntüleme, ilişkilendirmenize ve izleme verilerini analiz etmek için hizmet izleme Görüntüleyicisi aracı nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1793e-108">Describes how you can use the Service Trace Viewer tool to view, correlate and analyze trace data.</span></span>  
  
 [<span data-ttu-id="1793e-109">Önemli İzlemeler</span><span class="sxs-lookup"><span data-stu-id="1793e-109">Significant Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/significant-traces.md)  
 <span data-ttu-id="1793e-110">Önemli izlemeler WCF tarafından yayılan bir listesi.</span><span class="sxs-lookup"><span data-stu-id="1793e-110">A list of major traces emitted by WCF.</span></span>  
  
 [<span data-ttu-id="1793e-111">İstemcide Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1793e-111">Debugging on the Client</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/debugging-on-the-client.md)  
 <span data-ttu-id="1793e-112">Uygulamanızda hata ayıklamak için istemcileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1793e-112">Enables clients to debug your application.</span></span>  
  
 [<span data-ttu-id="1793e-113">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="1793e-113">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="1793e-114">Örneğin E2E WCF senaryoları için kullanılan izlemeleri, zaman uyumlu wsHttp istek-yanıt ve zaman uyumsuz TCP tek yönlü istekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1793e-114">Describes traces used for E2E WCF scenarios, for example, synchronous wsHttp request-replies, and asynchronous TCP one-way requests.</span></span>  
  
 [<span data-ttu-id="1793e-115">Kullanıcı Kodu İzlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="1793e-115">Emitting User-Code Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)  
 <span data-ttu-id="1793e-116">Daha sonra yurt içi hasıla ile WCF izleme ve tanılama amaçlı kullanılmak üzere ölçümlü izleme verilerini proaktif bir şekilde oluşturabilmeniz programlı olarak kullanıcı kodu izlemeleri yayma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="1793e-116">Describes how to emit traces programmatically in user code, so that you can proactively create instrumentation data to be used later for diagnostic purpose, and in correlation with WCF traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1793e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1793e-117">See also</span></span>

- [<span data-ttu-id="1793e-118">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="1793e-118">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="1793e-119">İzleme</span><span class="sxs-lookup"><span data-stu-id="1793e-119">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1793e-120">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="1793e-120">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
