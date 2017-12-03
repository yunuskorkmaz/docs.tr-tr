---
title: "İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d57517daaf78e737ea4417d5d46cf33400ff97a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tracing"></a><span data-ttu-id="e9d9f-102">İzleme</span><span class="sxs-lookup"><span data-stu-id="e9d9f-102">Tracing</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="e9d9f-103">Uygulama izleme ve tanılama verilerini hata izleme ve çözümleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-103"> provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="e9d9f-104">Bir uygulamanın nasıl davrandığını veya neden hataları anlamak için izleme yerine bir hata ayıklayıcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="e9d9f-105">Hataları ve işleme bir uçtan uca deneyim sağlamak üzere bileşenler genelinde ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="e9d9f-106">Aşağıdaki Tanılama izleme verilerini çıkarır:</span><span class="sxs-lookup"><span data-stu-id="e9d9f-106"> outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="e9d9f-107">İşlem kilometre taşları gibi işlem çağrıları uygulamalarının tüm bileşenleri arasında izlemelerini özel durumlar, uyarılar ve diğer önemli bir işleme olayları code."</span><span class="sxs-lookup"><span data-stu-id="e9d9f-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="e9d9f-108">Windows hata olaylarını izleme özelliği düzgün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9d9f-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e9d9f-109">In This Section</span></span>  
 [<span data-ttu-id="e9d9f-110">İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e9d9f-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="e9d9f-111">Bu konuda, belirli gereksiniminize uygun olarak farklı düzeylerde izleme nasıl yapılandırabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="e9d9f-112">Uçtan uca izleme</span><span class="sxs-lookup"><span data-stu-id="e9d9f-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="e9d9f-113">Bu bölümde, hata ayıklama yardımcı olmak üzere Etkinlik izleme ve uçtan uca bağıntı yayması nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="e9d9f-114">Uygulamanızda sorun giderme için izlemeyi kullanma</span><span class="sxs-lookup"><span data-stu-id="e9d9f-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="e9d9f-115">Bu bölümde, nasıl izleme uygulamanızda hata ayıklama için kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="e9d9f-116">Güvenlikle ilgili noktalar ve izleme için yararlı ipuçları</span><span class="sxs-lookup"><span data-stu-id="e9d9f-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="e9d9f-117">Bu konuda, hem de WebHost kullanırken yararlı ipuçları açıklanmasını hassas bilgileri nasıl koruyabilirim açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="e9d9f-118">İzleme başvuruları</span><span class="sxs-lookup"><span data-stu-id="e9d9f-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="e9d9f-119">Bu konu tarafından oluşturulan tüm izlemeleri listeler [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9d9f-119">This topic lists all the traces generated by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d9f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9d9f-120">See Also</span></span>  
 [<span data-ttu-id="e9d9f-121">Hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="e9d9f-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
