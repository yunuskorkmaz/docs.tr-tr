---
title: "COM Sarmalayıcıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b899ed162fa626f8c378923907f275cebf9a7db4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="com-wrappers"></a><span data-ttu-id="6f852-102">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="6f852-102">COM Wrappers</span></span>
<span data-ttu-id="6f852-103">COM birçok önemli yoldan .NET Framework nesne modelinden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="6f852-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="6f852-104">COM nesneleri istemcileri bu nesnelerin ömrü yönetmeniz gerekir; Ortak dil çalışma zamanı kendi ortamında nesnelerin ömrü yönetir.</span><span class="sxs-lookup"><span data-stu-id="6f852-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="6f852-105">COM nesneleri istemcileri, hizmet bu hizmeti sağlayan bir arabirimi isteme ve bir arabirim işaretçisi veya geri alma kullanılabilir olup olmadığını bulur.</span><span class="sxs-lookup"><span data-stu-id="6f852-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="6f852-106">.NET nesneleri istemcileri yansıma kullanarak bir nesnenin işlevlerinin açıklaması elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f852-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="6f852-107">.NET Framework yürütme ortamı tarafından yönetilen bellekte NET nesneleri bulunur.</span><span class="sxs-lookup"><span data-stu-id="6f852-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="6f852-108">Yürütme Ortamı, performans nedenleriyle bellekte nesneleri hareket ettirin ve hareket nesneleri yapılan tüm başvuruları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="6f852-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="6f852-109">Yönetilmeyen istemciler, bir nesne için bir işaretçi elde aynı konumda kalır nesnesine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6f852-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="6f852-110">Bu istemciler, konumu sabitlenmemiş bir nesneyle ilgili hiçbir mekanizması vardır.</span><span class="sxs-lookup"><span data-stu-id="6f852-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="6f852-111">Bu farklılıklar aşmak için çalışma zamanı ilgili ortamlarına nesnelerinde aradığınız düşündüğünüz yönetilen ve yönetilmeyen istemcileri yapmak için sarmalayıcı sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f852-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="6f852-112">Yönetilen istemci bir COM nesnesi üzerinde bir yöntemi çağırır her çalışma zamanı oluşturur bir [çalışma zamanı aranabilir sarmalayıcısı](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="6f852-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="6f852-113">RCWs başka şeylerin yönetilen ve yönetilmeyen başvuru mekanizmaları arasındaki farklar soyut.</span><span class="sxs-lookup"><span data-stu-id="6f852-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="6f852-114">Çalışma zamanı da oluşturur bir [COM aranabilir sarmalayıcısı](../../../docs/framework/interop/com-callable-wrapper.md) sorunsuz bir .NET nesnesinde bir yöntemi çağırmak bir COM istemci etkinleştirme işlemi geri almak için (saat).</span><span class="sxs-lookup"><span data-stu-id="6f852-114">The runtime also creates a [COM callable wrapper](../../../docs/framework/interop/com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="6f852-115">Aşağıdaki çizimde gösterildiği gibi çağrıyı yapan kod açısından çalışma zamanı oluşturur hangi sarmalayıcı sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="6f852-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="6f852-116">![COM sarmalayıcı genel bakış](../../../docs/framework/interop/media/bidirectional.gif "çift yönlü")</span><span class="sxs-lookup"><span data-stu-id="6f852-116">![COM wrapper overview](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="6f852-117">COM sarmalayıcı genel bakış</span><span class="sxs-lookup"><span data-stu-id="6f852-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="6f852-118">Çoğu durumda, COM ve .NET Framework arasında sınır arası çağrılar için yeterli hazırlama standart RCW veya çalışma zamanı tarafından oluşturulan saatin tersi YÖNDE sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f852-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="6f852-119">Özel öznitelikler kullanarak, çalışma zamanı temsil eden yönetilen ve yönetilmeyen kod yolu isteğe bağlı olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f852-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f852-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f852-120">See Also</span></span>  
 [<span data-ttu-id="6f852-121">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="6f852-121">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="6f852-122">Çalışma Zamanında Çağrılabilir Sarmalayıcı</span><span class="sxs-lookup"><span data-stu-id="6f852-122">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="6f852-123">COM Çağrılabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="6f852-123">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)  
 [<span data-ttu-id="6f852-124">Standart sarmalayıcıları özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6f852-124">Customizing Standard Wrappers</span></span>](http://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d)  
 [<span data-ttu-id="6f852-125">Nasıl yapılır: çalışma zamanı aranabilir sarmalayıcıları özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6f852-125">How to: Customize Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732)
