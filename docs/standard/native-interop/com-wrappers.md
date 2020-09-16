---
title: COM Sarmalayıcıları
description: COM istemcileri ve .NET nesneleri, COM çağrılabilir bir sarmalayıcı ve çalışma zamanında çağrılabilir sarmalayıcı kullanılarak etkileşim kurar. CLR sarmalayıcıları otomatik olarak oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
ms.openlocfilehash: cde574be6d4fadb78805548cff1b42ee354bf36f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558959"
---
# <a name="com-wrappers"></a><span data-ttu-id="2a04e-104">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="2a04e-104">COM Wrappers</span></span>
<span data-ttu-id="2a04e-105">COM, .NET çalışma zamanı nesne modelinden çeşitli önemli yollarla farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="2a04e-105">COM differs from the .NET runtime object model in several important ways:</span></span>  
  
- <span data-ttu-id="2a04e-106">COM nesnelerinin istemcileri bu nesnelerin ömrünü yönetmelidir; ortak dil çalışma zamanı, ortamındaki nesnelerin ömrünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="2a04e-106">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
- <span data-ttu-id="2a04e-107">COM nesnelerinin istemcileri, bu hizmeti sağlayan bir arabirim isteyerek bir hizmetin kullanılabilir olup olmadığını ve bir arabirim işaretçisi geri almanızı bulur.</span><span class="sxs-lookup"><span data-stu-id="2a04e-107">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="2a04e-108">.NET nesnelerinin istemcileri, yansıma kullanarak bir nesnenin işlevselliğinin açıklamasını elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="2a04e-108">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
- <span data-ttu-id="2a04e-109">NET nesneleri .NET çalışma zamanı yürütme ortamı tarafından yönetilen bellekte bulunur.</span><span class="sxs-lookup"><span data-stu-id="2a04e-109">NET objects reside in memory managed by the .NET runtime execution environment.</span></span> <span data-ttu-id="2a04e-110">Yürütme ortamı, performans nedenleriyle nesneleri belleğin etrafında taşıyabilir ve hareket yaptığı nesnelere tüm başvuruları güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2a04e-110">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="2a04e-111">Bir nesnenin işaretçisini elde eden yönetilmeyen istemciler, aynı konumda kalmak için nesnesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a04e-111">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="2a04e-112">Bu istemciler, konumu düzeltilmeyen bir nesneyle ilgili bir mekanizmaya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="2a04e-112">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="2a04e-113">Bu farklılıkları aşmak için, çalışma zamanı, hem yönetilen hem de yönetilmeyen istemcilerin kendi ortamları içinde nesne aramasını düşündüğünü sağlamak için sarmalayıcı sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a04e-113">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="2a04e-114">Yönetilen istemciniz bir COM nesnesinde bir yöntem çağırdığında, çalışma zamanı, bir [çalışma zamanı çağrılabilir sarmalayıcı](runtime-callable-wrapper.md) (RCW) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a04e-114">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="2a04e-115">RCWs, yönetilen ve yönetilmeyen başvuru mekanizmaları arasındaki farklılıkları diğer şeyler arasında soyutlar.</span><span class="sxs-lookup"><span data-stu-id="2a04e-115">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="2a04e-116">Çalışma zamanı, işlemi tersine çevirmek için bir [com çağrılabilir sarmalayıcı](com-callable-wrapper.md) (CCW) oluşturur ve bir com istemcisinin bir .net nesnesine sorunsuz bir şekilde çağrı çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a04e-116">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="2a04e-117">Aşağıdaki çizimde gösterildiği gibi, çağıran kodun perspektifi, çalışma zamanının hangi sarmalayıcı sınıfını oluşturduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="2a04e-117">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![COM sarmalayıcı genel bakış](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="2a04e-119">Çoğu durumda, çalışma zamanı tarafından oluşturulan standart RCW veya CCW, COM ile .NET çalışma zamanı arasında sınır alan çağrılar için yeterli sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a04e-119">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET runtime.</span></span> <span data-ttu-id="2a04e-120">Özel öznitelikleri kullanarak, isteğe bağlı olarak, çalışma zamanının yönetilen ve yönetilmeyen kodu temsil ettiği yöntemi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a04e-120">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a04e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a04e-121">See also</span></span>

- <span data-ttu-id="2a04e-122">[.NET Framework 'de gelişmiş COM birlikte çalışabilirlik](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a04e-122">[Advanced COM Interoperability in .NET Framework](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="2a04e-123">Çalışma Zamanı Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="2a04e-123">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="2a04e-124">COM Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="2a04e-124">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="2a04e-125">[.NET Framework 'de standart sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a04e-125">[Customizing Standard Wrappers in .NET Framework](/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="2a04e-126">[Nasıl yapılır: .NET Framework içindeki çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a04e-126">[How to: Customize Runtime Callable Wrappers in .NET Framework](/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
