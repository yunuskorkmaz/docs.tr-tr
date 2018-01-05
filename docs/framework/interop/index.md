---
title: "Yönetilmeyen Kod ile Birlikte Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f475877bcb7a794d1a58ef9202735e016363678b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="7e624-102">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="7e624-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="7e624-103">.NET Framework COM bileşenleri, COM + Hizmetleri, dış tür kitaplıklarını ve birçok işletim sistemi Hizmetleri ile etkileşim yükseltir.</span><span class="sxs-lookup"><span data-stu-id="7e624-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="7e624-104">Veri türleri, yöntem imzaları ve hata işleme mekanizmaları yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e624-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="7e624-105">Yönetilmeyen kod ile .NET Framework bileşenleri arasındaki birlikte çalışabilirlik basitleştirmek ve geçiş yolunun kolaylaştırmak için istemciler ve sunucular bu nesne modelleri farklılıkları ortak dil çalışma zamanı gizler.</span><span class="sxs-lookup"><span data-stu-id="7e624-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="7e624-106">Çalışma zamanı denetiminde yürütülen kodu yönetilen kod adı verilir.</span><span class="sxs-lookup"><span data-stu-id="7e624-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="7e624-107">Buna karşılık, çalışma zamanı dışında çalışan kod yönetilmeyen kod denir.</span><span class="sxs-lookup"><span data-stu-id="7e624-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="7e624-108">COM bileşenlerini, ActiveX arabirimleri ve Win32 API işlevleri yönetilmeyen kod gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="7e624-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e624-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7e624-109">In This Section</span></span>  
 [<span data-ttu-id="7e624-110">Yönetilmeyen kod nasıl yapılır konuları ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="7e624-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="7e624-111">Yönetilmeyen kod ile birlikte çalışma için kavramsal belgelerinde bulunan tüm nasıl yapılır konuları için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e624-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="7e624-112">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="7e624-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="7e624-113">.NET Framework uygulamalarında COM bileşenlerini kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e624-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="7e624-114">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="7e624-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="7e624-115">COM uygulamaları .NET Framework bileşenlerini kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e624-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="7e624-116">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7e624-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="7e624-117">Yönetilmeyen çağrılacağını açıklar platformu kullanılarak DLL işlevleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7e624-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="7e624-118">Birlikte çalışma için tasarım konuları</span><span class="sxs-lookup"><span data-stu-id="7e624-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="7e624-119">Tümleşik COM bileşenlerini yazmak için ipuçları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e624-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="7e624-120">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7e624-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="7e624-121">COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e624-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="7e624-122">Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme</span><span class="sxs-lookup"><span data-stu-id="7e624-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="7e624-123">Özel durumlar ve HRESULTs arasında eşleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="7e624-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="7e624-124">Genel türler kullanma birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="7e624-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="7e624-125">COM birlikte çalışma içinde kullanıldığında genel türler davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e624-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7e624-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7e624-126">Related Sections</span></span>  
 [<span data-ttu-id="7e624-127">Gelişmiş COM birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="7e624-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="7e624-128">COM bileşenlerini .NET Framework uygulamasına ekleme hakkında daha fazla bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e624-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>
