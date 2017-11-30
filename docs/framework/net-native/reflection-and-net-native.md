---
title: "Yansıma ve .NET Yerel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9e4bdc26815feab7910e7518f7cd691a1f4dece
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-and-net-native"></a><span data-ttu-id="b59c1-102">Yansıma ve .NET Yerel</span><span class="sxs-lookup"><span data-stu-id="b59c1-102">Reflection and .NET Native</span></span>
<span data-ttu-id="b59c1-103">.NET Framework geliştirme destekler API yansıma yoluyla meta yönetilen.</span><span class="sxs-lookup"><span data-stu-id="b59c1-103">In the .NET Framework, managed development supports metaprogramming through the reflection API.</span></span> <span data-ttu-id="b59c1-104">Yansıma uygulama nesneleri inceleyin, inceleme bulunan nesnelerin yöntemleri çağırmak, çalışma zamanında yeni türleri oluşturmak olanak tanır ve diğer birçok dinamik kodu senaryolarını destekler.</span><span class="sxs-lookup"><span data-stu-id="b59c1-104">Reflection allows you to inspect objects in an app, call methods on objects discovered through inspection, generate new types at run time, and supports many other dynamic code scenarios.</span></span> <span data-ttu-id="b59c1-105">Seri hale getirme ve kalıcı ve daha sonra geri nesnenin alan değerlerini sağlayan seri durumdan çıkarma de destekler.</span><span class="sxs-lookup"><span data-stu-id="b59c1-105">It also supports serialization and deserialization, which allows an object's field values to be persisted and later restored.</span></span> <span data-ttu-id="b59c1-106">Bu senaryolar tüm kullanılabilir meta verileri temel alarak yerel kodu oluşturmak için .NET Framework tam zamanında (JIT) derleyici gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b59c1-106">These scenarios all require the .NET Framework just-in-time (JIT) compiler to generate native code based on available metadata.</span></span>  
  
 <span data-ttu-id="b59c1-107">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Çalışma zamanı JIT Derleyici içermez.</span><span class="sxs-lookup"><span data-stu-id="b59c1-107">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime doesn't include a JIT compiler.</span></span> <span data-ttu-id="b59c1-108">Sonuç olarak, tüm gerekli yerel kod önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b59c1-108">As a result, all necessary native code must be generated in advance.</span></span> <span data-ttu-id="b59c1-109">Buluşsal yöntemler kümesi hangi kod oluşturulması belirlemek için kullanılır, ancak bu buluşsal yöntemler tüm olası meta senaryolarını kapsamak olamaz.</span><span class="sxs-lookup"><span data-stu-id="b59c1-109">A set of heuristics is used to determine what code should be generated, but these heuristics cannot cover all possible metaprogramming scenarios.</span></span>  <span data-ttu-id="b59c1-110">Bu nedenle, ipuçlarını bu meta senaryolar için kullanarak sağlamanız gereken [çalışma zamanı yönergeleri](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="b59c1-110">Therefore, you must provide hints for these metaprogramming scenarios by using [runtime directives](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="b59c1-111">Gerekli meta veri veya uygulama kodu çalışma zamanında kullanılabilir durumda değilse, uygulamanızı oluşturur bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), veya [ Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) özel durum.</span><span class="sxs-lookup"><span data-stu-id="b59c1-111">If the necessary metadata or implementation code is not available at runtime, your app throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), or [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) exception.</span></span> <span data-ttu-id="b59c1-112">İki sorun gidericileri kullanılabilir özel ortadan kaldırır, çalışma zamanı yönergeleri dosyanızı uygun girişini üretir:</span><span class="sxs-lookup"><span data-stu-id="b59c1-112">Two troubleshooters are available that will generate the appropriate entry for your runtime directives file that eliminates the exception:</span></span>  
  
-   <span data-ttu-id="b59c1-113">[MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/type.html) türleri için.</span><span class="sxs-lookup"><span data-stu-id="b59c1-113">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
-   <span data-ttu-id="b59c1-114">[MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.</span><span class="sxs-lookup"><span data-stu-id="b59c1-114">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b59c1-115">Arka plan üzerinde neden sağlar .NET yerel derleme işlemine genel bakış için bir çalışma zamanı yönergeleri dosyası, bkz: gerekli [.NET yerel ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="b59c1-115">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](../../../docs/framework/net-native/net-native-and-compilation.md).</span></span>  
  
 <span data-ttu-id="b59c1-116">Ayrıca, [!INCLUDE[net_native](../../../includes/net-native-md.md)] özel üyeleri .NET Framework sınıf kitaplığı yansıtacak şekilde izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="b59c1-116">In addition, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't allow you to reflect over private members of the .NET Framework class library.</span></span> <span data-ttu-id="b59c1-117">Örneğin, bir çağrı <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> özelliği bir .NET Framework sınıf kitaplığı Türü alanlarının döndürür yalnızca genel veya korumalı alanlar alınamadı.</span><span class="sxs-lookup"><span data-stu-id="b59c1-117">For example, a call to the <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> property to retrieve the fields of a .NET Framework class library type returns only public or protected fields.</span></span>  
  
 <span data-ttu-id="b59c1-118">Aşağıdaki konular kavramsal sağlamak ve yansıma ve seri hale getirme uygulamalarınızla desteklemeniz gereken belgelerine başvuru:</span><span class="sxs-lookup"><span data-stu-id="b59c1-118">The following topics provide the conceptual and reference documentation that you need to support reflection and serialization in your apps:</span></span>  
  
-   [<span data-ttu-id="b59c1-119">Yansıma kullanan API'ler</span><span class="sxs-lookup"><span data-stu-id="b59c1-119">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [<span data-ttu-id="b59c1-120">Yansıtma API'si başvurusu</span><span class="sxs-lookup"><span data-stu-id="b59c1-120">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [<span data-ttu-id="b59c1-121">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="b59c1-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="b59c1-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b59c1-122">See Also</span></span>  
 [<span data-ttu-id="b59c1-123">.NET yerel ile uygulama derleme</span><span class="sxs-lookup"><span data-stu-id="b59c1-123">Compiling Apps with .NET Native</span></span>](../../../docs/framework/net-native/index.md)  
 [<span data-ttu-id="b59c1-124">.NET yerel ve derleme</span><span class="sxs-lookup"><span data-stu-id="b59c1-124">.NET Native and Compilation</span></span>](../../../docs/framework/net-native/net-native-and-compilation.md)
