---
title: .NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180944"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="c1511-102">.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="c1511-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="c1511-103">Hata ayıklama ve sürüm yapılandırmaları tamamen farklı olduğundan, Evrensel Windows Platformu uygulamanızın sürüm yapılarını hedef platformlarında sınamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c1511-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="c1511-104">Varsayılan olarak, hata ayıklama yapılandırması uygulamanızı derlemek için .NET Core çalışma zamanını kullanır, ancak sürüm yapılandırması uygulamanızı yerel koda derlemek için .NET Native kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1511-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c1511-105">[EksikMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)ve Uygulamanızın sürüm sürümlerini test ederken karşılaşabileceğiniz [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları ile ilgili bilgi için bkz: "Adım 4: Eksik meta verileri el ile çözmek: [Başlangıç](getting-started-with-net-native.md) konusunun yanı sıra [Yansıma ve .NET Yerli](reflection-and-net-native.md) ve Çalışma Zamanı [Direktifleri (rd.xml) Yapılandırma Dosya Başvurusu.](runtime-directives-rd-xml-configuration-file-reference.md)</span><span class="sxs-lookup"><span data-stu-id="c1511-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="c1511-106">Hata ayıklama ve sürüm yapılarını</span><span class="sxs-lookup"><span data-stu-id="c1511-106">Debug and release builds</span></span>  
 <span data-ttu-id="c1511-107">Hata ayıklama yapısı .NET Core çalışma süresine karşı yürütüldüğünde, yerel kodiçin derlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="c1511-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="c1511-108">Bu, normalde çalışma zamanı tarafından sağlanan tüm hizmetleri uygulamanız için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c1511-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="c1511-109">Diğer taraftan, sürüm yapısı hedef platformları için yerel koda derler, dış çalışma sürelerine ve kitaplıklara olan bağımlılıkların çoğunu kaldırır ve maksimum performans için kodu yoğun bir şekilde optimize eder.</span><span class="sxs-lookup"><span data-stu-id="c1511-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="c1511-110">.NET Native kullanılarak derlenen sürüm yapılarını hata ayıklama yaptığınızda:</span><span class="sxs-lookup"><span data-stu-id="c1511-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="c1511-111">Normal .NET hata ayıklama araçlarından farklı olan .NET Yerel hata ayıklama altyapısını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c1511-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="c1511-112">Çalıştırılabilir boyutunu mümkün olduğunca azalır.</span><span class="sxs-lookup"><span data-stu-id="c1511-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="c1511-113">.NET Native'in yürütülebilir boyutu azaltma yollarından biri, [Çalışma Zamanı özel durum iletileri](#Messages) bölümünde daha ayrıntılı olarak tartışılan bir konu olan çalışma zamanı özel durum iletilerini önemli ölçüde kırpmaktır.</span><span class="sxs-lookup"><span data-stu-id="c1511-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="c1511-114">Kodunuz ağır şekilde optimize edildi.</span><span class="sxs-lookup"><span data-stu-id="c1511-114">Your code is heavily optimized.</span></span> <span data-ttu-id="c1511-115">Bu, inlining mümkün olduğunda kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c1511-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="c1511-116">(Inlining kodu dış yordamlardan arama yordamına taşır.)   .NET Native'in özel bir çalışma süresi sağlaması ve agresif ara çizgi sini uygulamaları hata ayıklama yaparken görüntülenen çağrı yığınını etkiler.</span><span class="sxs-lookup"><span data-stu-id="c1511-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="c1511-117">Daha fazla bilgi için [Runtime arama yığını](#CallStack) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c1511-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1511-118">Hata ayıklama ve sürüm yapılarının .NET Native araç zinciriyle derlenip derlenmediğini,.NET **Native araç zinciri kutusuyla Derleme'yi** denetleyerek veya denetlemeyi denetleyerek denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1511-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="c1511-119">Ancak, Windows Mağazası'nın uygulamanızın üretim sürümünü her zaman .NET Native araç zinciriyle derlemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c1511-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a><span data-ttu-id="c1511-120">Çalışma zamanı özel durum iletileri</span><span class="sxs-lookup"><span data-stu-id="c1511-120">Runtime exception messages</span></span>  
 <span data-ttu-id="c1511-121">Uygulama yürütülebilir boyutunu en aza indirmek için ,NET Native özel durum iletilerinin tam metnini içermez.</span><span class="sxs-lookup"><span data-stu-id="c1511-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="c1511-122">Sonuç olarak, sürüm yapılarında atılan çalışma zamanı özel durumları özel durum iletilerinin tam metnini görüntülemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="c1511-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="c1511-123">Bunun yerine, metin daha fazla bilgi için takip etmek için bir bağlantı ile birlikte bir alt dize oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c1511-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="c1511-124">Örneğin, özel durum bilgileri aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="c1511-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="c1511-125">Tam özel durum iletisi gerekiyorsa, bunun yerine hata ayıklama yapıçalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1511-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="c1511-126">Örneğin, sürüm yapısındaki önceki özel durum bilgileri hata ayıklama yapısında aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="c1511-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a><span data-ttu-id="c1511-127">Çalışma zamanı arama yığını</span><span class="sxs-lookup"><span data-stu-id="c1511-127">Runtime call stack</span></span>  
 <span data-ttu-id="c1511-128">İçe doğru astarlama ve diğer optimizasyonlar nedeniyle,.NET Native araç zinciri tarafından derlenen bir uygulama tarafından görüntülenen çağrı yığını, çalışma zamanı özel duruma giden yolu net bir şekilde belirlemenize yardımcı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c1511-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="c1511-129">Tam yığını almak için hata ayıklama yapısını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1511-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1511-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1511-130">See also</span></span>

- [<span data-ttu-id="c1511-131">.NET Native Windows Universal Apps Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c1511-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="c1511-132">Başlarken</span><span class="sxs-lookup"><span data-stu-id="c1511-132">Getting Started</span></span>](getting-started-with-net-native.md)
