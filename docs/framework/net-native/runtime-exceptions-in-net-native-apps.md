---
title: ".NET yerel uygulamalar çalışma zamanı özel durumları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d4f5787faa2fdf5f5450d8ddce285919a658645
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="76d17-102">.NET yerel uygulamalar çalışma zamanı özel durumları</span><span class="sxs-lookup"><span data-stu-id="76d17-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="76d17-103">Hata ayıklama ve yayın yapılandırmaları tamamen farklı olduğundan, Evrensel Windows platformu uygulamanızın kendi hedef platformlarda yayın derlemeleri test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="76d17-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="76d17-104">Varsayılan olarak, uygulamanızı derlemeye .NET çekirdeği çalışma zamanı hata ayıklama yapılandırmasını kullanır, ancak sürüm yapılandırmasında uygulamanızı yerel koda derlemek için .NET yerel kullanır.</span><span class="sxs-lookup"><span data-stu-id="76d17-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76d17-105">Yapılacağı hakkında bilgi için [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) görebilirsiniz özel durumlar Uygulamanızı yayın sürümlerini test edilirken karşılaşırsanız bkz "4. adım: el ile eksik meta veri çözümleme: içinde [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md) konu yanı [yansıma ve .NET yerel](../../../docs/framework/net-native/reflection-and-net-native.md) ve [ Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="76d17-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="76d17-106">Hata ayıklama ve yayın derlemeleri</span><span class="sxs-lookup"><span data-stu-id="76d17-106">Debug and release builds</span></span>  
 <span data-ttu-id="76d17-107">Hata ayıklama derlemesi .NET çekirdeği çalışma zamanı karşı yürütüldüğünde, onu yerel koda derlenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="76d17-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="76d17-108">Bu genellikle, uygulamanızın kullanılabilir çalışma zamanı tarafından sağlanan hizmetlerin tümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="76d17-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="76d17-109">Diğer taraftan, yayın derlemesi Hedef platformlar için yerel koda derlenen, dış çalışma zamanları ve kitaplıkları çoğu bağımlılıkları kaldırır ve yoğun bir şekilde kod en yüksek performans için en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="76d17-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="76d17-110">Ne zaman .NET yerel kullanarak derlenmiş sürüm derlemeleri hata ayıklama:</span><span class="sxs-lookup"><span data-stu-id="76d17-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
-   <span data-ttu-id="76d17-111">Hata ayıklama araçları normal .NET farklı .NET yerel hata ayıklama altyapısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="76d17-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
-   <span data-ttu-id="76d17-112">Yürütülebilir dosyanın boyutunu mümkün olduğunca çok azdır.</span><span class="sxs-lookup"><span data-stu-id="76d17-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="76d17-113">.NET yerel bir yürütülebilir dosya boyutunu azaltır, yollardan biridir önemli ölçüde çalışma zamanı özel durum iletileri, daha ayrıntılı olarak ele alınan bir konu kırpma tarafından [çalışma zamanı özel durum iletilerini](#Messages) bölümü.</span><span class="sxs-lookup"><span data-stu-id="76d17-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
-   <span data-ttu-id="76d17-114">Kodunuzu yoğun getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="76d17-114">Your code is heavily optimized.</span></span> <span data-ttu-id="76d17-115">Bunun anlamı, satır içi kullanım mümkün olduğunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76d17-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="76d17-116">(Satır içi kullanım kodu dış yordamlarından yordamı çağrılırken taşır.)   .NET yerel özelleştirilmiş bir çalışma zamanı sağlar ve agresif satır içi kullanım etkiler hata ayıklama sırasında görüntülenen çağrı yığınını uygulayan, olgu.</span><span class="sxs-lookup"><span data-stu-id="76d17-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="76d17-117">Daha fazla bilgi için bkz: [çalışma zamanının çağrı yığını](#CallStack) bölümü.</span><span class="sxs-lookup"><span data-stu-id="76d17-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76d17-118">Hata ayıklama ve yayın derlemeleri denetleme veya işaretleyerek .NET yerel araç zinciri ile derlenen olup olmadığını kontrol edebilirsiniz **olan .NET yerel araç zinciri derleme** kutusu.</span><span class="sxs-lookup"><span data-stu-id="76d17-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="76d17-119">Ancak, Windows mağazası uygulamanızı .NET yerel araç zinciri ile üretim sürümü her zaman derlenir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76d17-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="76d17-120">Çalışma zamanı özel durum iletileri</span><span class="sxs-lookup"><span data-stu-id="76d17-120">Runtime exception messages</span></span>  
 <span data-ttu-id="76d17-121">Uygulama yürütülebilir boyutu en aza indirmek için .NET yerel özel durum iletilerinin tam metin içermez.</span><span class="sxs-lookup"><span data-stu-id="76d17-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="76d17-122">Sonuç olarak, çalışma zamanı özel durumları yayın derlemelerde oluşturulan özel durum iletilerinin tam metin görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="76d17-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="76d17-123">Bunun yerine, metin, daha fazla bilgi için izlemek için bir bağlantı ile birlikte bir alt dizenin oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="76d17-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="76d17-124">Örneğin, özel durum bilgisi olarak görünebilir:</span><span class="sxs-lookup"><span data-stu-id="76d17-124">For example, the exception information may appear as:</span></span>  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="76d17-125">Hata ayıklama derlemesi tam özel durum iletisi gerekiyorsa, bunun yerine çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="76d17-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="76d17-126">Örneğin, yayın derlemesi önceki özel durum bilgileri hata ayıklama derlemesi şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="76d17-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="76d17-127">Çalışma zamanı çağrı yığını</span><span class="sxs-lookup"><span data-stu-id="76d17-127">Runtime call stack</span></span>  
 <span data-ttu-id="76d17-128">Satır içi kullanım ve diğer iyileştirmeler nedeniyle .NET yerel araç zinciri tarafından derlenen bir uygulama tarafından görüntülenen çağrı yığını açıkça bir çalışma zamanı özel yoluna belirlemenize yardımcı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="76d17-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="76d17-129">Tam yığını almak için hata ayıklama derlemesi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="76d17-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d17-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76d17-130">See Also</span></span>  
 [<span data-ttu-id="76d17-131">.NET yerel Windows Evrensel uygulamaları hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="76d17-131">Debugging .NET Native Windows Universal Apps</span></span>](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [<span data-ttu-id="76d17-132">Başlarken</span><span class="sxs-lookup"><span data-stu-id="76d17-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
