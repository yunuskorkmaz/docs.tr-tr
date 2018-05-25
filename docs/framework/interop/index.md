---
title: Yönetilmeyen kod ile birlikte çalışma
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 583cfb6e3a5145c6c0dfc82ec9ff64c6d87414ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="17b8c-102">Yönetilmeyen kod ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="17b8c-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="17b8c-103">.NET Framework COM bileşenleri, COM + Hizmetleri, dış tür kitaplıklarını ve birçok işletim sistemi Hizmetleri ile etkileşim yükseltir.</span><span class="sxs-lookup"><span data-stu-id="17b8c-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="17b8c-104">Veri türleri, yöntem imzaları ve hata işleme mekanizmaları yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="17b8c-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="17b8c-105">Yönetilmeyen kod ile .NET Framework bileşenleri arasındaki birlikte çalışabilirlik basitleştirmek ve geçiş yolunun kolaylaştırmak için istemciler ve sunucular bu nesne modelleri farklılıkları ortak dil çalışma zamanı gizler.</span><span class="sxs-lookup"><span data-stu-id="17b8c-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="17b8c-106">Çalışma zamanı denetiminde yürütülen kodu yönetilen kod adı verilir.</span><span class="sxs-lookup"><span data-stu-id="17b8c-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="17b8c-107">Buna karşılık, çalışma zamanı dışında çalışan kod yönetilmeyen kod denir.</span><span class="sxs-lookup"><span data-stu-id="17b8c-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="17b8c-108">COM bileşenlerini, ActiveX arabirimleri ve Win32 API işlevleri yönetilmeyen kod gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="17b8c-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="17b8c-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="17b8c-109">In this section</span></span>

[<span data-ttu-id="17b8c-110">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="17b8c-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="17b8c-111">.NET Framework uygulamalarında COM bileşenlerini kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="17b8c-112">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="17b8c-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="17b8c-113">COM uygulamaları .NET Framework bileşenlerini kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="17b8c-114">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="17b8c-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="17b8c-115">Yönetilmeyen çağrılacağını açıklar platformu kullanılarak DLL işlevleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="17b8c-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="17b8c-116">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="17b8c-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="17b8c-117">COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="17b8c-118">Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme</span><span class="sxs-lookup"><span data-stu-id="17b8c-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="17b8c-119">Özel durumlar ve HRESULTs arasında eşleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="17b8c-120">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="17b8c-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="17b8c-121">COM birlikte çalışma tarafından sağlanan sarmalayıcıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="17b8c-122">Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri</span><span class="sxs-lookup"><span data-stu-id="17b8c-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="17b8c-123">Derlemeleri COM türleri için tür bilgisi nasıl katıştırılır ve ortak dil çalışma zamanı katıştırılmış COM türlerini eşdeğer nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="17b8c-124">Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Bütünleştirilmiş Kodları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="17b8c-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="17b8c-125">Kullanarak birincil birlikte çalışma derlemeleri üretmek açıklar *Tlbimp.exe* (tür kitaplığı içeri Aktarıcı).</span><span class="sxs-lookup"><span data-stu-id="17b8c-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="17b8c-126">Nasıl yapılır: Birincil Birlikte Çalışma Bütünleştirilmiş Kodlarını Kaydetme</span><span class="sxs-lookup"><span data-stu-id="17b8c-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="17b8c-127">Birincil birlikte çalışma derlemeleri projelerinizde başvuru önce kaydetmeniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="17b8c-128">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="17b8c-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="17b8c-129">Windows Kayıt Defteri'ni kullanarak olmadan COM birlikte çalışma bileşenleri nasıl etkinleştirebilir açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="17b8c-130">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="17b8c-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="17b8c-131">Bir uygulama bildirimi oluşturmak ve oluşturmak ve bir bileşen bildirimi katıştırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="17b8c-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>
