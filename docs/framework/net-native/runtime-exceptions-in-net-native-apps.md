---
description: 'Daha fazla bilgi edinin: .NET Native uygulamalarda çalışma zamanı özel durumları'
title: .NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 11a85d36a95e74dac36cd45e080428fcba0c673e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801988"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="6978b-103">.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="6978b-103">Runtime Exceptions in .NET Native Apps</span></span>

<span data-ttu-id="6978b-104">Hata ayıklama ve yayın yapılandırmaları tamamen farklı olduğundan, Evrensel Windows Platformu uygulamanızın sürüm yapılarını hedef platformlarda test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6978b-104">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="6978b-105">Varsayılan olarak, hata ayıklama yapılandırması uygulamanızı derlemek için .NET Core çalışma zamanını kullanır, ancak yayın yapılandırması uygulamanızı yerel koda derlemek için .NET Native kullanır.</span><span class="sxs-lookup"><span data-stu-id="6978b-105">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6978b-106">Uygulamanızın yayın sürümlerini sınarken karşılaşabileceğiniz [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları ile ilgili bilgi için, bkz. "4. Adım: eksik meta verileri el ile çözme: [Başlarken](getting-started-with-net-native.md) konusunun yanı sıra [yansıma ve .NET Native](reflection-and-net-native.md) ve [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="6978b-106">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="6978b-107">Hata ayıklama ve yayın yapıları</span><span class="sxs-lookup"><span data-stu-id="6978b-107">Debug and release builds</span></span>  

 <span data-ttu-id="6978b-108">Hata ayıklama derlemesi .NET Core çalışma zamanına karşı yürütüldüğünde, yerel koda derlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="6978b-108">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="6978b-109">Bu, normalde çalışma zamanı tarafından sağlanan tüm hizmetlerin uygulamanızda kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6978b-109">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="6978b-110">Öte yandan, yayın derlemesi hedef platformları için yerel koda derlenir, dış çalışma zamanları ve kitaplıklarda birçok bağımlılığı kaldırır ve en yüksek performans için kodu yoğun olarak iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="6978b-110">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="6978b-111">.NET Native kullanılarak derlenen sürüm Derlemeleriyle ilgili hataları ayıkladığınızda:</span><span class="sxs-lookup"><span data-stu-id="6978b-111">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="6978b-112">Normal .NET hata ayıklama araçlarından farklı olan .NET Native hata ayıklama altyapısını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6978b-112">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="6978b-113">Yürütülebilir dosyanızın boyutu mümkün olduğunca azalır.</span><span class="sxs-lookup"><span data-stu-id="6978b-113">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="6978b-114">.NET Native bir yürütülebilir dosyanın boyutunu azaltmanın bir yolu, çalışma [zamanı özel durum iletileri bölümünde daha](#Messages) ayrıntılı bir şekilde ele alınan çalışma zamanı özel durum iletilerini önemli ölçüde kırpmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6978b-114">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="6978b-115">Kodunuz yoğun bir şekilde iyileştirildi.</span><span class="sxs-lookup"><span data-stu-id="6978b-115">Your code is heavily optimized.</span></span> <span data-ttu-id="6978b-116">Bu, mümkün olan her durumda satır içinde kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6978b-116">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="6978b-117">(Intıl, kodu dış yordamlardan çağıran yordama taşıtırlar.)   .NET Native, özel bir çalışma zamanı sağlar ve agresif kullanımı uygularsa hata ayıklarken görüntülenen çağrı yığınını etkiler.</span><span class="sxs-lookup"><span data-stu-id="6978b-117">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="6978b-118">Daha fazla bilgi için bkz. [çalışma zamanı çağrı yığını](#CallStack) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6978b-118">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6978b-119">Hata ayıklama ve sürüm derlemelerinin, **.NET Native araç zinciri Ile derle** kutusunu işaretleyerek veya işaretleyerek .NET Native araç zinciriyle derlenip derlenmediğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6978b-119">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="6978b-120">Ancak, Windows Mağazası 'nın .NET Native araç zinciri ile uygulamanızın üretim sürümünü her zaman derlendiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6978b-120">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>

## <a name="runtime-exception-messages"></a><span data-ttu-id="6978b-121">Çalışma zamanı özel durum iletileri</span><span class="sxs-lookup"><span data-stu-id="6978b-121">Runtime exception messages</span></span>  

 <span data-ttu-id="6978b-122">Uygulama yürütülebilir boyutunu en aza indirmek için .NET Native özel durum iletilerinin tam metnini içermez.</span><span class="sxs-lookup"><span data-stu-id="6978b-122">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="6978b-123">Sonuç olarak, sürüm Derlemeleriyle oluşturulan çalışma zamanı özel durumları, özel durum iletilerinin tam metnini görüntülemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="6978b-123">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="6978b-124">Bunun yerine, metin bir alt dizeden ve daha fazla bilgi için bir bağlantı ile birlikte yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="6978b-124">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="6978b-125">Örneğin, özel durum bilgileri şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="6978b-125">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="6978b-126">Tüm özel durum iletisine ihtiyacınız varsa, bunun yerine hata ayıklama derlemesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6978b-126">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="6978b-127">Örneğin, yayın derlemeden önceki özel durum bilgileri hata ayıklama derlemesinde aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="6978b-127">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>

## <a name="runtime-call-stack"></a><span data-ttu-id="6978b-128">Çalışma zamanı çağrı yığını</span><span class="sxs-lookup"><span data-stu-id="6978b-128">Runtime call stack</span></span>  

 <span data-ttu-id="6978b-129">Satır içi ve diğer iyileştirmeler nedeniyle, .NET Native araç zinciri tarafından derlenen bir uygulama tarafından görünen çağrı yığını, çalışma zamanı özel durumunun yolunu açıkça belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6978b-129">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="6978b-130">Tam yığını almak için bunun yerine hata ayıklama derlemesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6978b-130">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6978b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6978b-131">See also</span></span>

- [<span data-ttu-id="6978b-132">Windows Evrensel uygulamalarında .NET Native hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="6978b-132">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="6978b-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="6978b-133">Getting Started</span></span>](getting-started-with-net-native.md)
