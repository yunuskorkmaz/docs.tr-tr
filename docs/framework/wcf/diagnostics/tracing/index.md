---
title: İzleme
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 4165dbb68ac962737c9dcc99e984248c668bb1b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506803"
---
# <a name="tracing"></a><span data-ttu-id="9c797-102">İzleme</span><span class="sxs-lookup"><span data-stu-id="9c797-102">Tracing</span></span>
<span data-ttu-id="9c797-103">Windows Communication Foundation (WCF), hata izleme ve analiz için uygulama izleme ve tanılama verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c797-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="9c797-104">Bir hata ayıklayıcı yerine izleme, bir uygulamanın nasıl davrandığını veya neden hataları anlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c797-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="9c797-105">Hataları ve işleme bir uçtan uca deneyim sağlamak üzere bileşenlerinde ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c797-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="9c797-106">WCF aşağıdaki tanılama izleme verilerini çıkarır:</span><span class="sxs-lookup"><span data-stu-id="9c797-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="9c797-107">İzlemeler işlem çağrıları gibi uygulamaların tüm bileşenleri arasında işlem kilometre taşları için özel durumlar, uyarılar ve diğer önemli işlem yüküyle olayları kod."</span><span class="sxs-lookup"><span data-stu-id="9c797-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="9c797-108">Windows hata olaylarını izleme özelliği yanlış olduğunda.</span><span class="sxs-lookup"><span data-stu-id="9c797-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c797-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9c797-109">In This Section</span></span>  
 [<span data-ttu-id="9c797-110">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9c797-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="9c797-111">Bu konuda, izlemeyi belirli gereksinimlerinize uyacak şekilde, farklı düzeylerde nasıl yapılandırabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c797-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="9c797-112">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="9c797-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="9c797-113">Bu bölümde, hata ayıklama yardımcı olmak için etkinlik izleme ve uçtan uca bağıntı yayması nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9c797-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="9c797-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="9c797-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="9c797-115">Bu bölümde, nasıl izleme uygulamanızda hata ayıklamak için kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c797-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="9c797-116">İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları</span><span class="sxs-lookup"><span data-stu-id="9c797-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="9c797-117">Bu konuda, WebHost kullanırken faydalı ipuçları yanı sıra açıklanmasını hassas bilgileri nasıl Koruyabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c797-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="9c797-118">İzleme Başvuruları</span><span class="sxs-lookup"><span data-stu-id="9c797-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="9c797-119">Bu konu, WCF tarafından oluşturulan tüm izlemeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="9c797-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c797-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c797-120">See also</span></span>
- [<span data-ttu-id="9c797-121">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="9c797-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
