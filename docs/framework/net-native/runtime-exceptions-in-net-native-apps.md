---
title: .NET Native Uygulamalarında Çalışma Zamanı Özel Durumları
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 3132e2c9502c91cbfa0b120f664fd0c6f99a2663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128139"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="b7e70-102">.NET Native Uygulamalarında Çalışma Zamanı Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="b7e70-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="b7e70-103">Hata ayıklama ve yayın yapılandırmaları tamamen farklı olduğundan, Evrensel Windows Platformu uygulamanızın sürüm yapılarını hedef platformlarda test etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b7e70-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="b7e70-104">Varsayılan olarak, hata ayıklama yapılandırması uygulamanızı derlemek için .NET Core çalışma zamanını kullanır, ancak yayın yapılandırması uygulamanızı yerel koda derlemek için .NET Native kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7e70-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b7e70-105">Uygulamanızın yayın sürümlerini sınarken karşılaşabileceğiniz [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları ile ilgili bilgi için, bkz. "4. Adım: Eksik meta verileri el ile çözümleyin: [Başlarken](getting-started-with-net-native.md) konusunun yanı sıra [yansıma ve .NET Native](reflection-and-net-native.md) ile [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="b7e70-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="b7e70-106">Hata ayıklama ve yayın yapıları</span><span class="sxs-lookup"><span data-stu-id="b7e70-106">Debug and release builds</span></span>  
 <span data-ttu-id="b7e70-107">Hata ayıklama derlemesi .NET Core çalışma zamanına karşı yürütüldüğünde, yerel koda derlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="b7e70-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="b7e70-108">Bu, normalde çalışma zamanı tarafından sağlanan tüm hizmetlerin uygulamanızda kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7e70-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="b7e70-109">Öte yandan, yayın derlemesi hedef platformları için yerel koda derlenir, dış çalışma zamanları ve kitaplıklarda birçok bağımlılığı kaldırır ve en yüksek performans için kodu yoğun olarak iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="b7e70-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="b7e70-110">.NET Native kullanılarak derlenen sürüm Derlemeleriyle ilgili hataları ayıkladığınızda:</span><span class="sxs-lookup"><span data-stu-id="b7e70-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="b7e70-111">Normal .NET hata ayıklama araçlarından farklı olan .NET Native hata ayıklama altyapısını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b7e70-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="b7e70-112">Yürütülebilir dosyanızın boyutu mümkün olduğunca azalır.</span><span class="sxs-lookup"><span data-stu-id="b7e70-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="b7e70-113">.NET Native bir yürütülebilir dosyanın boyutunu azaltmanın bir yolu, çalışma [zamanı özel durum iletileri bölümünde daha](#Messages) ayrıntılı bir şekilde ele alınan çalışma zamanı özel durum iletilerini önemli ölçüde kırpmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b7e70-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="b7e70-114">Kodunuz yoğun bir şekilde iyileştirildi.</span><span class="sxs-lookup"><span data-stu-id="b7e70-114">Your code is heavily optimized.</span></span> <span data-ttu-id="b7e70-115">Bu, mümkün olan her durumda satır içinde kullanıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b7e70-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="b7e70-116">(Intıl, kodu dış yordamlardan çağıran yordama taşıtırlar.)   .NET Native, özel bir çalışma zamanı sağlar ve agresif kullanımı uygularsa hata ayıklarken görüntülenen çağrı yığınını etkiler.</span><span class="sxs-lookup"><span data-stu-id="b7e70-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="b7e70-117">Daha fazla bilgi için bkz. [çalışma zamanı çağrı yığını](#CallStack) bölümü.</span><span class="sxs-lookup"><span data-stu-id="b7e70-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7e70-118">Hata ayıklama ve sürüm derlemelerinin, **.NET Native araç zinciri Ile derle** kutusunu işaretleyerek veya işaretleyerek .NET Native araç zinciriyle derlenip derlenmediğini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7e70-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="b7e70-119">Ancak, Windows Mağazası 'nın .NET Native araç zinciri ile uygulamanızın üretim sürümünü her zaman derlendiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b7e70-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="b7e70-120">Çalışma zamanı özel durum iletileri</span><span class="sxs-lookup"><span data-stu-id="b7e70-120">Runtime exception messages</span></span>  
 <span data-ttu-id="b7e70-121">Uygulama yürütülebilir boyutunu en aza indirmek için .NET Native özel durum iletilerinin tam metnini içermez.</span><span class="sxs-lookup"><span data-stu-id="b7e70-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="b7e70-122">Sonuç olarak, sürüm Derlemeleriyle oluşturulan çalışma zamanı özel durumları, özel durum iletilerinin tam metnini görüntülemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="b7e70-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="b7e70-123">Bunun yerine, metin bir alt dizeden ve daha fazla bilgi için bir bağlantı ile birlikte yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="b7e70-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="b7e70-124">Örneğin, özel durum bilgileri şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="b7e70-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="b7e70-125">Tüm özel durum iletisine ihtiyacınız varsa, bunun yerine hata ayıklama derlemesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7e70-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="b7e70-126">Örneğin, yayın derlemeden önceki özel durum bilgileri hata ayıklama derlemesinde aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="b7e70-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="b7e70-127">Çalışma zamanı çağrı yığını</span><span class="sxs-lookup"><span data-stu-id="b7e70-127">Runtime call stack</span></span>  
 <span data-ttu-id="b7e70-128">Satır içi ve diğer iyileştirmeler nedeniyle, .NET Native araç zinciri tarafından derlenen bir uygulama tarafından görünen çağrı yığını, çalışma zamanı özel durumunun yolunu açıkça belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b7e70-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="b7e70-129">Tam yığını almak için bunun yerine hata ayıklama derlemesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7e70-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e70-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7e70-130">See also</span></span>

- [<span data-ttu-id="b7e70-131">Windows Evrensel uygulamalarında .NET Native hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b7e70-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="b7e70-132">Başlarken</span><span class="sxs-lookup"><span data-stu-id="b7e70-132">Getting Started</span></span>](getting-started-with-net-native.md)
