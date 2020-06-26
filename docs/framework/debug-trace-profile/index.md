---
title: Hata Ayıklama, İzleme ve Profil Oluşturma
description: .NET ' te hata ayıklama, izleme ve profil oluşturma hakkında bilgi edinin. Just-In-Time (JıT) hata ayıklamayı, uygulamaları izlemeyi ve ipucunu ve daha fazlasını kapsayan makalelere göz atın.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 745f16652c02e3409e7fa7a48beacbf7e777e924
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415985"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="224aa-104">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="224aa-104">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="224aa-105">.NET Framework bir uygulamada hata ayıklamak için, derleyici ve çalışma zamanı ortamı, bir hata ayıklayıcının uygulamaya iliştirmesine ve mümkünse uygulama ve karşılık gelen Microsoft ara dili (MSIL) için, mümkün olduğunda hem semboller hem de çizgi haritaları üretmesine imkan tanımak için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="224aa-105">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="224aa-106">Yönetilen bir uygulamanın hatası ayıklandıktan sonra, performansı artırmak için profili oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="224aa-106">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="224aa-107">Profil oluşturma, en sık yürütülen kodu oluşturan kaynak kodu satırlarını ve bunların yürütülmesi için ne kadar zaman harcanduğunu değerlendirir ve tanımlar.</span><span class="sxs-lookup"><span data-stu-id="224aa-107">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="224aa-108">.NET Framework uygulamalar, birçok yapılandırma ayrıntılarını işleyen Visual Studio kullanılarak kolayca hata ayıklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="224aa-108">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="224aa-109">Visual Studio yüklü değilse, .NET Framework ad alanındaki hata ayıklama sınıflarını kullanarak .NET Framework uygulamalarının performansını inceleyebilir ve geliştirebilirsiniz <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="224aa-109">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="224aa-110">Bu ad alanı, <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.TraceSource> izleme yürütme akışı için,, ve sınıflarını ve <xref:System.Diagnostics.Process> <xref:System.Diagnostics.EventLog> <xref:System.Diagnostics.PerformanceCounter> profil oluşturma kodu için, ve sınıflarını içerir.</span><span class="sxs-lookup"><span data-stu-id="224aa-110">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="224aa-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="224aa-111">In This Section</span></span>  
 [<span data-ttu-id="224aa-112">JIT-Ekleme Hata Ayıklamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="224aa-112">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="224aa-113">Bir .NET Framework uygulamasına bir hata ayıklama altyapısını JıT olarak eklemek için kayıt defterinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="224aa-113">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="224aa-114">Görüntüde Hata Ayıklamayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="224aa-114">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="224aa-115">Derlemeyi hata ayıklamanın daha kolay hale getirmek için JıT izlemenin açık ve en iyi duruma getirme özelliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="224aa-115">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="224aa-116">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="224aa-116">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="224aa-117">Uygulamasının çalışırken nasıl yapıldığını ve ne kadar iyi bir şeyin yanlış geçmiş olduğunu görüntülemek için nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="224aa-117">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="224aa-118">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="224aa-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="224aa-119">Çalışma zamanı durumu hakkında bilgi sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan hata ayıklama yardımlarından oluşan yönetilen hata ayıklama yardımcıları 'nı (MDAs) açıklar.</span><span class="sxs-lookup"><span data-stu-id="224aa-119">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="224aa-120">Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="224aa-120">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="224aa-121">Bir tür geliştiricisinin bir hata ayıklayıcıda görüntülendiğinde ne tür görüneceğini nasıl belirtbileceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="224aa-121">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="224aa-122">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="224aa-122">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="224aa-123">Bir uygulamanın performansını izlemek için kullanabileceğiniz sayaçları açıklar.</span><span class="sxs-lookup"><span data-stu-id="224aa-123">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="224aa-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="224aa-124">Related Sections</span></span>  
 [<span data-ttu-id="224aa-125">Visual Studio'da ASP.NET veya ASP.NET Core uygulamalarının hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="224aa-125">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="224aa-126">Geliştirme sırasında veya dağıtımdan sonra bir ASP.NET uygulamasında hata ayıklama için önkoşul ve yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="224aa-126">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="224aa-127">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="224aa-127">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="224aa-128">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="224aa-128">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
