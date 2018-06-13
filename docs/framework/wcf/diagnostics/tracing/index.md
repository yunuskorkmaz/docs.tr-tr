---
title: İzleme
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 6f427425b1bbf19ecd8b30fb1498634a7a3d5fa9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809322"
---
# <a name="tracing"></a><span data-ttu-id="63544-102">İzleme</span><span class="sxs-lookup"><span data-stu-id="63544-102">Tracing</span></span>
<span data-ttu-id="63544-103">Windows Communication Foundation (WCF) uygulama izleme ve tanılama verilerini hata izleme ve çözümleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="63544-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="63544-104">Bir uygulamanın nasıl davrandığını veya neden hataları anlamak için izleme yerine bir hata ayıklayıcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63544-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="63544-105">Hataları ve işleme bir uçtan uca deneyim sağlamak üzere bileşenler genelinde ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63544-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="63544-106">WCF aşağıdaki tanılama izleme verilerini çıkarır:</span><span class="sxs-lookup"><span data-stu-id="63544-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="63544-107">İşlem kilometre taşları gibi işlem çağrıları uygulamalarının tüm bileşenleri arasında izlemelerini özel durumlar, uyarılar ve diğer önemli bir işleme olayları code."</span><span class="sxs-lookup"><span data-stu-id="63544-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="63544-108">Windows hata olaylarını izleme özelliği düzgün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="63544-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63544-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="63544-109">In This Section</span></span>  
 [<span data-ttu-id="63544-110">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="63544-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="63544-111">Bu konuda, belirli gereksiniminize uygun olarak farklı düzeylerde izleme nasıl yapılandırabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63544-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="63544-112">Uçtan Uca İzleme</span><span class="sxs-lookup"><span data-stu-id="63544-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="63544-113">Bu bölümde, hata ayıklama yardımcı olmak üzere Etkinlik izleme ve uçtan uca bağıntı yayması nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="63544-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="63544-114">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="63544-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="63544-115">Bu bölümde, nasıl izleme uygulamanızda hata ayıklama için kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63544-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="63544-116">İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları</span><span class="sxs-lookup"><span data-stu-id="63544-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="63544-117">Bu konuda, hem de WebHost kullanırken yararlı ipuçları açıklanmasını hassas bilgileri nasıl koruyabilirim açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63544-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="63544-118">İzleme Başvuruları</span><span class="sxs-lookup"><span data-stu-id="63544-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="63544-119">Bu konu, WCF tarafından oluşturulan tüm izlemeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="63544-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63544-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63544-120">See Also</span></span>  
 [<span data-ttu-id="63544-121">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="63544-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
