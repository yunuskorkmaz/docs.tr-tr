---
title: "Hata Ayıklama, İzleme ve Profil Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 21032358c9edb1b79d9e170e477502670f781fc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="e2596-102">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e2596-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="e2596-103">.NET Framework uygulama hatalarını ayıklamak için derleyici ve çalışma zamanı ortamı uygulamaya eklemek bir hata ayıklayıcısı etkinleştirmek için yapılandırılmış olmalıdır ve hem simge hem de satır üretmek için Mümkünse, uygulama ve onun karşılık gelen Microsoft Ara eşlemeleri dili (MSIL).</span><span class="sxs-lookup"><span data-stu-id="e2596-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="e2596-104">Yönetilen bir uygulamanın hata ayıklaması sonra performansı artırmak için profili.</span><span class="sxs-lookup"><span data-stu-id="e2596-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="e2596-105">Profil oluşturma değerlendirir ve en sık yürütülen kod oluşturma kaynak kod satırlarını açıklar ve ne kadar sürer bunları yürütmek için saat.</span><span class="sxs-lookup"><span data-stu-id="e2596-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="e2596-106">.NET framework uygulamaları kolayca birçok yapılandırma ayrıntılarını işler Visual Studio kullanarak ayıklandığını.</span><span class="sxs-lookup"><span data-stu-id="e2596-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="e2596-107">Visual Studio yüklü değilse, inceleyin ve .NET Framework'te hata ayıklama sınıfları kullanarak .NET Framework uygulamaları performansı <xref:System.Diagnostics> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e2596-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="e2596-108">Bu ad alanı içerir <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, ve <xref:System.Diagnostics.TraceSource> yürütme akış, izleme için sınıfları ve <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, ve <xref:System.Diagnostics.PerformanceCounter> kod profili oluşturma için sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e2596-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2596-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e2596-109">In This Section</span></span>  
 [<span data-ttu-id="e2596-110">JIT-ekleme hata ayıklama etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e2596-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="e2596-111">JIT-ekleme kayıt defterine yapılandırmak .NET Framework uygulamasına hata ayıklama altyapısı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2596-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="e2596-112">Bir görüntü hata ayıklamayı kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="e2596-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="e2596-113">JIT izlemeyi ve en iyi duruma getirme bir derlemeyi debug kolay hale getirmek için devre dışı bırakmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2596-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="e2596-114">İzleme ve uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e2596-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="e2596-115">Çalışırken ve ne kadar iyi görüntülemek için işaretlemesini gittiğini nasıl mı bir şeyler yanlış geçti, uygulamanızın yürütülmesini izlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2596-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="e2596-116">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="e2596-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="e2596-117">Hangi ortak dil çalışma zamanı (CLR) çalışma zamanı durumu hakkında bilgi sağlamak için birlikte çalışmak yardımları hata ayıklama yönetilen hata ayıklama Yardımcıları (Mda'lar) açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2596-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="e2596-118">Hata ayıklayıcı görüntü öznitelikleriyle hata ayıklamayı geliştirme</span><span class="sxs-lookup"><span data-stu-id="e2596-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="e2596-119">Geliştirici türü ne nasıl belirteceğinizi açıklar türü, bir hata ayıklayıcıda görüntülendiğinde gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="e2596-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="e2596-120">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="e2596-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="e2596-121">Bir uygulamanın performansını izlemek için kullanabileceğiniz sayaçları açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2596-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2596-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e2596-122">Related Sections</span></span>  
 [<span data-ttu-id="e2596-123">ASP.NET ve AJAX uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e2596-123">Debugging ASP.NET and AJAX Applications</span></span>](http://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 <span data-ttu-id="e2596-124">Önkoşullar ve geliştirme sırasında veya dağıtımdan sonra bir ASP.NET uygulama hata ayıklama hakkında yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2596-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="e2596-125">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e2596-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="e2596-126">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2596-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
