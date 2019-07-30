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
ms.openlocfilehash: af9b87e83def5578ea38e94a4f69c657ac5f7c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631326"
---
# <a name="com-wrappers"></a><span data-ttu-id="75e64-102">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="75e64-102">COM Wrappers</span></span>
<span data-ttu-id="75e64-103">COM, .NET çalışma zamanı nesne modelinden çeşitli önemli yollarla farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="75e64-103">COM differs from the .NET runtime object model in several important ways:</span></span>  
  
- <span data-ttu-id="75e64-104">COM nesnelerinin istemcileri bu nesnelerin ömrünü yönetmelidir; ortak dil çalışma zamanı, ortamındaki nesnelerin ömrünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="75e64-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
- <span data-ttu-id="75e64-105">COM nesnelerinin istemcileri, bu hizmeti sağlayan bir arabirim isteyerek bir hizmetin kullanılabilir olup olmadığını ve bir arabirim işaretçisi geri almanızı bulur.</span><span class="sxs-lookup"><span data-stu-id="75e64-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="75e64-106">.NET nesnelerinin istemcileri, yansıma kullanarak bir nesnenin işlevselliğinin açıklamasını elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="75e64-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
- <span data-ttu-id="75e64-107">NET nesneleri .NET çalışma zamanı yürütme ortamı tarafından yönetilen bellekte bulunur.</span><span class="sxs-lookup"><span data-stu-id="75e64-107">NET objects reside in memory managed by the .NET runtime execution environment.</span></span> <span data-ttu-id="75e64-108">Yürütme ortamı, performans nedenleriyle nesneleri belleğin etrafında taşıyabilir ve hareket yaptığı nesnelere tüm başvuruları güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="75e64-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="75e64-109">Bir nesnenin işaretçisini elde eden yönetilmeyen istemciler, aynı konumda kalmak için nesnesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="75e64-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="75e64-110">Bu istemciler, konumu düzeltilmeyen bir nesneyle ilgili bir mekanizmaya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="75e64-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="75e64-111">Bu farklılıkları aşmak için, çalışma zamanı, hem yönetilen hem de yönetilmeyen istemcilerin kendi ortamları içinde nesne aramasını düşündüğünü sağlamak için sarmalayıcı sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="75e64-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="75e64-112">Yönetilen istemciniz bir COM nesnesinde bir yöntem çağırdığında, çalışma zamanı, bir [çalışma zamanı çağrılabilir sarmalayıcı](runtime-callable-wrapper.md) (RCW) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75e64-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="75e64-113">RCWs, yönetilen ve yönetilmeyen başvuru mekanizmaları arasındaki farklılıkları diğer şeyler arasında soyutlar.</span><span class="sxs-lookup"><span data-stu-id="75e64-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="75e64-114">Çalışma zamanı, işlemi tersine çevirmek için bir [com çağrılabilir sarmalayıcı](com-callable-wrapper.md) (CCW) oluşturur ve bir com istemcisinin bir .net nesnesine sorunsuz bir şekilde çağrı çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="75e64-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="75e64-115">Aşağıdaki çizimde gösterildiği gibi, çağıran kodun perspektifi, çalışma zamanının hangi sarmalayıcı sınıfını oluşturduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="75e64-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![COM sarmalayıcı genel bakış](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="75e64-117">Çoğu durumda, çalışma zamanı tarafından oluşturulan standart RCW veya CCW, COM ile .NET çalışma zamanı arasında sınır alan çağrılar için yeterli sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="75e64-117">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET runtime.</span></span> <span data-ttu-id="75e64-118">Özel öznitelikleri kullanarak, isteğe bağlı olarak, çalışma zamanının yönetilen ve yönetilmeyen kodu temsil ettiği yöntemi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75e64-118">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e64-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75e64-119">See also</span></span>

- <span data-ttu-id="75e64-120">[.NET Framework 'de gelişmiş COM birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="75e64-120">[Advanced COM Interoperability in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="75e64-121">Çalışma Zamanında Çağrılabilir Sarmalayıcı</span><span class="sxs-lookup"><span data-stu-id="75e64-121">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="75e64-122">COM Çağrılabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="75e64-122">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="75e64-123">[.NET Framework 'de standart sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="75e64-123">[Customizing Standard Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="75e64-124">[Nasıl yapılır: .NET Framework çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="75e64-124">[How to: Customize Runtime Callable Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
