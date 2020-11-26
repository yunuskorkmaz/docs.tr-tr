---
title: İzleme
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 10b9be028710cdda378aeef0ca235a00aa451e08
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243917"
---
# <a name="tracing"></a><span data-ttu-id="ac16e-102">İzleme</span><span class="sxs-lookup"><span data-stu-id="ac16e-102">Tracing</span></span>

<span data-ttu-id="ac16e-103">Windows Communication Foundation (WCF), hata izleme ve analiz için uygulama izleme ve Tanılama verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac16e-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="ac16e-104">Bir uygulamanın nasıl davrandığına veya neden hata hatalarıyla karşılaşma anlamak için bir hata ayıklayıcı yerine izlemeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac16e-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="ac16e-105">Ayrıca, uçtan uca bir deneyim sağlamak için bileşenler arasındaki hataları ve işlemleri de ilişkilendirebilir.</span><span class="sxs-lookup"><span data-stu-id="ac16e-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="ac16e-106">WCF, Tanılama izleme için aşağıdaki verileri verir:</span><span class="sxs-lookup"><span data-stu-id="ac16e-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="ac16e-107">İşlem çağrıları, kod özel durumları, uyarılar ve diğer önemli işleme olayları gibi uygulamaların tüm bileşenleri genelinde işlem kilometre taşları için izlemeler. "</span><span class="sxs-lookup"><span data-stu-id="ac16e-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
- <span data-ttu-id="ac16e-108">İzleme özelliğinin düzgün çalışmamasına zaman Windows hata olayları.</span><span class="sxs-lookup"><span data-stu-id="ac16e-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac16e-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ac16e-109">In This Section</span></span>  

 [<span data-ttu-id="ac16e-110">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ac16e-110">Configuring Tracing</span></span>](configuring-tracing.md)  
  
 <span data-ttu-id="ac16e-111">Bu konu başlığı altında, farklı düzeylerde izlemeyi özel gereksinimlerinize uyacak şekilde nasıl yapılandırabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac16e-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="ac16e-112">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="ac16e-112">End-to-End Tracing</span></span>](end-to-end-tracing.md)  
  
 <span data-ttu-id="ac16e-113">Bu bölümde, hata ayıklamaya yardımcı olmak üzere uçtan uca bağıntı için etkinlik Izlemeyi ve yaymayı nasıl kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac16e-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="ac16e-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="ac16e-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="ac16e-115">Bu bölümde, uygulamanızda hata ayıklamak için izlemeyi nasıl kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac16e-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="ac16e-116">İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları</span><span class="sxs-lookup"><span data-stu-id="ac16e-116">Security Concerns and Useful Tips for Tracing</span></span>](security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="ac16e-117">Bu konu başlığı altında, gizli bilgilerin sunulanlarından nasıl koruyabileceğiniz ve WebHost kullanırken yararlı olan ipuçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac16e-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="ac16e-118">İzleme Başvuruları</span><span class="sxs-lookup"><span data-stu-id="ac16e-118">Traces Reference</span></span>](traces-reference.md)  
  
 <span data-ttu-id="ac16e-119">Bu konuda, WCF tarafından oluşturulan tüm izlemeler listelenir.</span><span class="sxs-lookup"><span data-stu-id="ac16e-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac16e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac16e-120">See also</span></span>

- [<span data-ttu-id="ac16e-121">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="ac16e-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
