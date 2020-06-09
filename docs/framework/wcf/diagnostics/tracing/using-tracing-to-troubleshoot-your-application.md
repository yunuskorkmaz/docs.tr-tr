---
title: Uygulamanızda Sorun Giderme için İzleme Kullanma
ms.date: 03/30/2017
ms.assetid: 7676b9bb-cbd1-41fd-9a93-cc615af6e2d0
ms.openlocfilehash: 78280a399c3490afb0dd2293c60b58d9d00fc228
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587644"
---
# <a name="using-tracing-to-troubleshoot-your-application"></a><span data-ttu-id="cf8b7-102">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf8b7-102">Using Tracing to Troubleshoot Your Application</span></span>
<span data-ttu-id="cf8b7-103">Bu bölüm, uygulamanızın sorunlarını gidermek için izlemeyi nasıl kullanabileceğinizi betimleyen çeşitli konular içerir.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-103">This section contains various topics that describe how you can use tracing to troubleshoot your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf8b7-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cf8b7-104">In This Section</span></span>  
 [<span data-ttu-id="cf8b7-105">İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar</span><span class="sxs-lookup"><span data-stu-id="cf8b7-105">Recommended Settings for Tracing and Message Logging</span></span>](recommended-settings-for-tracing-and-message-logging.md)  
 <span data-ttu-id="cf8b7-106">Üretim ve hata ayıklama ortamları için önerilen ayarları açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-106">Describes suggested settings for production and debugging environments.</span></span>  
  
 [<span data-ttu-id="cf8b7-107">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma </span><span class="sxs-lookup"><span data-stu-id="cf8b7-107">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 <span data-ttu-id="cf8b7-108">İzleme verilerini görüntülemek, ilişkilendirmek ve analiz etmek için hizmet Izleme Görüntüleyicisi aracını nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-108">Describes how you can use the Service Trace Viewer tool to view, correlate and analyze trace data.</span></span>  
  
 [<span data-ttu-id="cf8b7-109">Önemli İzlemeler</span><span class="sxs-lookup"><span data-stu-id="cf8b7-109">Significant Traces</span></span>](significant-traces.md)  
 <span data-ttu-id="cf8b7-110">WCF tarafından yayılan ana izlemelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-110">A list of major traces emitted by WCF.</span></span>  
  
 [<span data-ttu-id="cf8b7-111">İstemcide Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cf8b7-111">Debugging on the Client</span></span>](debugging-on-the-client.md)  
 <span data-ttu-id="cf8b7-112">İstemcilerin uygulamanızda hata ayıklamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-112">Enables clients to debug your application.</span></span>  
  
 [<span data-ttu-id="cf8b7-113">Uçtan Uca İzleme Senaryoları</span><span class="sxs-lookup"><span data-stu-id="cf8b7-113">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="cf8b7-114">E2E WCF senaryolarında kullanılan izlemeleri açıklar; Örneğin, zaman uyumlu wsHttp isteği-yanıtları ve zaman uyumsuz TCP tek yönlü istekler.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-114">Describes traces used for E2E WCF scenarios, for example, synchronous wsHttp request-replies, and asynchronous TCP one-way requests.</span></span>  
  
 [<span data-ttu-id="cf8b7-115">Kullanıcı Kodu İzleri Yayma</span><span class="sxs-lookup"><span data-stu-id="cf8b7-115">Emitting User-Code Traces</span></span>](emitting-user-code-traces.md)  
 <span data-ttu-id="cf8b7-116">Daha sonra tanılama amacına ve WCF izlemelerle bağıntılanmak üzere daha sonra kullanılmak üzere izleme verileri oluşturmak için Kullanıcı kodundaki izlemeleri programlı bir şekilde nasıl yayılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-116">Describes how to emit traces programmatically in user code, so that you can proactively create instrumentation data to be used later for diagnostic purpose, and in correlation with WCF traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8b7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf8b7-117">See also</span></span>

- [<span data-ttu-id="cf8b7-118">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="cf8b7-118">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="cf8b7-119">İzleme</span><span class="sxs-lookup"><span data-stu-id="cf8b7-119">Tracing</span></span>](index.md)
- [<span data-ttu-id="cf8b7-120">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="cf8b7-120">End-to-End Tracing</span></span>](end-to-end-tracing.md)
