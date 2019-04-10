---
title: .NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06e07c41d398c0792094b4481a38c69b2ba73004
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208286"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="5ecbe-102">.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="5ecbe-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="5ecbe-103">Hata ayıklama ve yayın yapılandırmaları tamamen farklı olduğundan kendi Hedef platformlar üzerinde Evrensel Windows platformu uygulamanızın sürüm derlemeleri test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="5ecbe-104">Varsayılan olarak, uygulamanızı derlemek için .NET Core çalışma zamanı hata ayıklama yapılandırması kullanır, ancak sürüm yapılandırmasını yerel kod için uygulamanızı derlemek için .NET Native kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ecbe-105">İşlemleri ile ilgili daha fazla bilgi için [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) olabilir, özel durumlar Yayın sürümleri uygulamanızı test ederken karşılaşırsanız, bkz: "4. adım: Meta veriler eksik elle Çözümle: içinde [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md) konu yanı [yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) ve [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="5ecbe-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="5ecbe-106">Hata ayıklama ve yayın derlemeleri</span><span class="sxs-lookup"><span data-stu-id="5ecbe-106">Debug and release builds</span></span>  
 <span data-ttu-id="5ecbe-107">Hata ayıklama derlemesini .NET Core çalışma zamanı karşı yürütüldüğünde, yerel koda derlenmedi.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="5ecbe-108">Bu, normalde uygulamanıza kullanılabilir çalışma zamanı tarafından sağlanan tüm hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="5ecbe-109">Öte yandan, sürüm yapısı, Hedef platformlar için yerel koda derleyen, dış çalışma zamanları ve kitaplıkları çoğu bağımlılıkları kaldırır ve yoğun bir şekilde kod en yüksek performans için en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="5ecbe-110">.NET Native ile derlenmiş sürüm yapıları için hata ayıklaması yaptığınızda:</span><span class="sxs-lookup"><span data-stu-id="5ecbe-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
-   <span data-ttu-id="5ecbe-111">.NET normal hata ayıklama araçları farklı .NET yerel hata ayıklama altyapısı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
-   <span data-ttu-id="5ecbe-112">Yürütülebilir dosyanızın boyutunu mümkün olduğunca azaltılır.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="5ecbe-113">.NET Native yürütülebilir bir dosya boyutunu azaltır, yollardan biridir önemli ölçüde daha ayrıntılı olarak ele alınan bir konu olan çalışma zamanı özel durum iletileri kırpma tarafından [çalışma zamanı özel durum iletileri](#Messages) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
-   <span data-ttu-id="5ecbe-114">Kodunuzu son derece iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-114">Your code is heavily optimized.</span></span> <span data-ttu-id="5ecbe-115">Yani bu satır içi kullanım, mümkün olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="5ecbe-116">(Satır içi kod dış rutinleri çağıran yordam taşır.)   .NET Native özelleştirilmiş bir çalışma zamanı sağlar ve agresif inlining'i etkiler görüntülenen hata ayıklama sırasında çağrı yığınını uygulayan, olgu.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="5ecbe-117">Daha fazla bilgi için [çalışma zamanının çağrı yığınındaki](#CallStack) bölümü.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ecbe-118">Hata ayıklama ve yayın derlemeleri denetleme veya işaretini .NET yerel araç zinciriyle derlenmiş olup olmadığını kontrol edebilirsiniz **.NET yerel araç zinciriyle derle** kutusu.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="5ecbe-119">Ancak, Windows Store, uygulamanızın .NET Native araç zinciri ile üretim sürümü her zaman derleyeceği unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="5ecbe-120">Çalışma zamanı özel durum iletileri</span><span class="sxs-lookup"><span data-stu-id="5ecbe-120">Runtime exception messages</span></span>  
 <span data-ttu-id="5ecbe-121">Uygulama yürütülebilir boyutu en aza indirmek için .NET Native özel durum iletilerinin tam metin içermez.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="5ecbe-122">Sonuç olarak, sürüm yapılarında durum çalışma zamanı özel durumları, özel durum iletilerinin tam metin görüntülenmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="5ecbe-123">Bunun yerine, metni daha fazla bilgi için izlemek için bir bağlantı ile birlikte bir alt dizenin oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="5ecbe-124">Örneğin, özel durum bilgilerini olarak görünebilir:</span><span class="sxs-lookup"><span data-stu-id="5ecbe-124">For example, the exception information may appear as:</span></span>  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="5ecbe-125">Hata ayıklama derlemesini, bunun yerine tam özel durum iletisi gerekirse çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="5ecbe-126">Örneğin, önceki sürüm yapısı özel durum bilgileri gibi hata ayıklama derlemesinde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="5ecbe-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="5ecbe-127">Çalışma zamanı çağrı yığını</span><span class="sxs-lookup"><span data-stu-id="5ecbe-127">Runtime call stack</span></span>  
 <span data-ttu-id="5ecbe-128">Satır içi kullanım ve diğer iyileştirmeler nedeniyle, çağrı yığınını .NET Native araç zinciri tarafından derlenmiş bir uygulama tarafından görüntülenen çalışma zamanı özel yoluna açıkça tanımlamak için yardımcı olabilir değil.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="5ecbe-129">Tam yığın almak için hata ayıklama derlemesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ecbe-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ecbe-130">See also</span></span>

- [<span data-ttu-id="5ecbe-131">.NET yerel Windows Evrensel uygulamaları hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5ecbe-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="5ecbe-132">Başlarken</span><span class="sxs-lookup"><span data-stu-id="5ecbe-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
