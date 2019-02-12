---
title: COM Sarmalayıcıları
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d02d1b170362a5175fb24d68b00e4648819541e
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092663"
---
# <a name="com-wrappers"></a><span data-ttu-id="c6c67-102">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="c6c67-102">COM Wrappers</span></span>
<span data-ttu-id="c6c67-103">COM, .NET Framework nesne modeli birkaç önemli şekilde farklıdır:</span><span class="sxs-lookup"><span data-stu-id="c6c67-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="c6c67-104">COM nesnelerinin istemcileri bu nesnelerin ömrünü yönetmek gerekir; Ortak dil çalışma zamanı ortam nesnelerin ömrünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="c6c67-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="c6c67-105">COM nesnelerinin istemcileri, hizmet bu hizmeti sağlayan bir arabirimi isteyen ve bir arabirim işaretçisi veya geri alma kullanılabilir olup olmadığını bulur.</span><span class="sxs-lookup"><span data-stu-id="c6c67-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="c6c67-106">.NET nesnelerinin istemcileri, yansıma kullanarak bir nesnenin işlevlerinin açıklaması aşağıda elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c67-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="c6c67-107">NET nesneler, .NET Framework yürütme ortamı tarafından yönetilen bellekte yer alır.</span><span class="sxs-lookup"><span data-stu-id="c6c67-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="c6c67-108">Yürütme Ortamı, performans nedenleriyle bellekte nesnelerin değiştirmemiz ve onunla nesneler için tüm başvuruları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c6c67-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="c6c67-109">Yönetilmeyen istemciler, bir nesneye bir işaretçi elde aynı konumda kalır nesnesine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c6c67-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="c6c67-110">Bu istemciler konumu sabit bir nesne başa çıkmak için bir mekanizma vardır.</span><span class="sxs-lookup"><span data-stu-id="c6c67-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="c6c67-111">Bu farklar aşmak için çalışma zamanı hem yönetilen hem de yönetilmeyen istemcileri düşünün, kendi ortamlarından nesnelerinde çağırdığınızdan emin olmak için sarmalayıcı sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6c67-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="c6c67-112">Yönetilen istemci bir COM nesnesi üzerinde bir yöntemi çağırdığında, çalışma zamanı oluşturur bir [çalışma zamanı çağrılabilir sarmalayıcı](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="c6c67-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="c6c67-113">RCW, başka şeylerin yanında, yönetilen ve yönetilmeyen başvurusu mekanizmaları arasındaki farklar soyut.</span><span class="sxs-lookup"><span data-stu-id="c6c67-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="c6c67-114">Çalışma zamanı ayrıca oluşturur bir [COM çağrılabilir sarmalayıcısı](com-callable-wrapper.md) sorunsuz bir şekilde bir .NET nesnesi üzerinde bir yöntemi çağırmak bir COM istemcisi etkinleştirme işlemi geri almak için (CCW).</span><span class="sxs-lookup"><span data-stu-id="c6c67-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="c6c67-115">Aşağıdaki çizimde gösterildiği gibi çağıran kodun açısından çalışma zamanı oluşturur hangi sarmalayıcı sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="c6c67-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="c6c67-116">![COM sarmalayıcı genel bakış](media/bidirectional.gif "çift yönlü")</span><span class="sxs-lookup"><span data-stu-id="c6c67-116">![COM wrapper overview](media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="c6c67-117">COM sarmalayıcı genel bakış</span><span class="sxs-lookup"><span data-stu-id="c6c67-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="c6c67-118">Çoğu durumda standart RCW veya çalışma zamanı tarafından oluşturulan CCW sınır COM ve .NET Framework arasında çapraz aramalar için yeterli hazırlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6c67-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="c6c67-119">Özel öznitelikler kullanarak, çalışma zamanı temsil eden yönetilen ve yönetilmeyen kod yolu isteğe bağlı olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c67-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c67-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6c67-120">See also</span></span>
- <span data-ttu-id="c6c67-121">[Gelişmiş COM birlikte çalışabilirliği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c6c67-121">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="c6c67-122">Çalışma Zamanında Çağrılabilir Sarmalayıcı</span><span class="sxs-lookup"><span data-stu-id="c6c67-122">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="c6c67-123">COM Çağrılabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="c6c67-123">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="c6c67-124">[Standart sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c6c67-124">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="c6c67-125">[Nasıl yapılır: Çalışma zamanı aranabilir sarmalayıcılarını özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c6c67-125">[How to: Customize Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
