---
title: Hata Ayıklama, İzleme ve Profil Oluşturma
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 855a1329c9804e4b40d796c639bbe8768156dcc2
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092507"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="a0173-102">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0173-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="a0173-103">Bir .NET Framework uygulamasında hata ayıklamak için derleyici ve çalışma zamanı ortamı uygulamaya eklemek bir hata ayıklayıcı etkinleştirmek için yapılandırılması gerekir ve hem simge hem de satır üretmek için mümkün olduğunda, uygulama ve onun ilişkili Microsoft Ara eşler Dil (MSIL).</span><span class="sxs-lookup"><span data-stu-id="a0173-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="a0173-104">Yönetilen bir uygulama hata ayıklama sonra performansını artırmak üzere profili.</span><span class="sxs-lookup"><span data-stu-id="a0173-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="a0173-105">Profil oluşturma değerlendirir ve en sık yürütülen kodu kaynak kodu satırlarını açıklar ve ne kadar bunları yürütmek için alır.</span><span class="sxs-lookup"><span data-stu-id="a0173-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="a0173-106">.NET framework uygulamaları, kolayca configuration ayrıntıların birçoğu işleme Visual Studio kullanarak hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="a0173-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="a0173-107">Visual Studio yüklü değilse, inceleyin ve .NET Framework'te hata ayıklama sınıfları kullanarak .NET Framework uygulamalarının performansını <xref:System.Diagnostics> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a0173-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="a0173-108">Bu ad alanı içerir <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, ve <xref:System.Diagnostics.TraceSource> yürütme akışı izleme için sınıfları ve <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, ve <xref:System.Diagnostics.PerformanceCounter> kod profil oluşturma için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="a0173-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0173-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a0173-109">In This Section</span></span>  
 [<span data-ttu-id="a0173-110">JIT-Ekleme Hata Ayıklamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a0173-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="a0173-111">JIT-ekleme için kayıt defterini yapılandırmak bir .NET Framework uygulamasına bir hata ayıklama altyapısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0173-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="a0173-112">Görüntüde Hata Ayıklamayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="a0173-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="a0173-113">Bir derlemeyi hata ayıklama daha kolay hale getirmek üzere üzerinde JIT izleme ve iyileştirme kapatmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0173-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="a0173-114">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="a0173-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="a0173-115">Çalışır durumdayken ve ne kadar iyi görüntülemek için araç haline getirmek için onu gerçekleştiriyor nasıl mı bir sorun oluştu, uygulamanın yürütülmesini izlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="a0173-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="a0173-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a0173-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="a0173-117">Ortak dil çalışma zamanı (CLR) çalışma zamanı durum bilgilerini sağlamak için birlikte çalışan yardımlarda hata ayıklar, yönetilen hata ayıklama Yardımcıları (Mda'lar) açıklar.</span><span class="sxs-lookup"><span data-stu-id="a0173-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="a0173-118">Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="a0173-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="a0173-119">Geliştirici bir türün ne nasıl belirteceğinizi açıklar türü bir hata ayıklayıcıda zaman görüntülendiği gibi görünecektir.</span><span class="sxs-lookup"><span data-stu-id="a0173-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="a0173-120">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="a0173-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="a0173-121">Uygulama performansını izlemek için kullanabileceğiniz sayaçlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0173-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a0173-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a0173-122">Related Sections</span></span>  
 [<span data-ttu-id="a0173-123">Visual Studio'da ASP.NET veya ASP.NET Core uygulamalarının hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="a0173-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 <span data-ttu-id="a0173-124">Önkoşullar ve nasıl bir ASP.NET uygulama geliştirme süresince veya dağıtım sonrasında hata ayıklama için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0173-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="a0173-125">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a0173-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="a0173-126">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0173-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
