---
title: Yönetilmeyen kodla birlikte çalışma
description: Yönetilmeyen kod ile birlikte çalışabilirliği gözden geçirin. CLR, istemci ve sunuculardan, .NET bileşenlerinin nesne modellerinin ve yönetilmeyen kodun farklı bir şekilde farklılık gösterir.
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
ms.openlocfilehash: 1cebd75907fd202715cb337593186d248107bdbb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621879"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="16699-104">Yönetilmeyen kodla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="16699-104">Interoperating with unmanaged code</span></span>

<span data-ttu-id="16699-105">.NET Framework, COM bileşenleri, COM+ Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi hizmeti ile etkileşimi yükseltir.</span><span class="sxs-lookup"><span data-stu-id="16699-105">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="16699-106">Veri türleri, yöntem imzaları ve hata işleme mekanizmaları, yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="16699-106">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="16699-107">.NET Framework bileşenleri ve yönetilmeyen kod arasında birlikte çalışabilirlik kolaylaştırmak ve geçiş yolunu kolaylaştırmak için, ortak dil çalışma zamanı hem istemcilerden hem de sunuculardan bu nesne modellerindeki farklılıkları önler.</span><span class="sxs-lookup"><span data-stu-id="16699-107">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="16699-108">Çalışma zamanının denetimi altında yürütülen koda yönetilen kod denir.</span><span class="sxs-lookup"><span data-stu-id="16699-108">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="16699-109">Buna karşılık, çalışma zamanının dışında çalışan koda yönetilmeyen kod denir.</span><span class="sxs-lookup"><span data-stu-id="16699-109">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="16699-110">COM bileşenleri, ActiveX arabirimleri ve Windows API işlevleri, yönetilmeyen koda örnektir.</span><span class="sxs-lookup"><span data-stu-id="16699-110">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="16699-111">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="16699-111">In this section</span></span>

[<span data-ttu-id="16699-112">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="16699-112">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="16699-113">.NET Framework uygulamalardan COM bileşenlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-113">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="16699-114">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="16699-114">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="16699-115">COM uygulamalarından .NET Framework bileşenlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-115">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="16699-116">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="16699-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="16699-117">Platform Invoke kullanılarak yönetilmeyen DLL işlevlerinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="16699-118">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="16699-118">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="16699-119">COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-119">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="16699-120">Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme</span><span class="sxs-lookup"><span data-stu-id="16699-120">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="16699-121">Özel durumlar ve HRESULTs arasındaki eşlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-121">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="16699-122">Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri</span><span class="sxs-lookup"><span data-stu-id="16699-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="16699-123">COM türleri için tür bilgilerinin derlemelerde nasıl gömülü olduğunu ve ortak dil çalışma zamanının gömülü COM türlerinin denklik düzeyini nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="16699-124">Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="16699-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="16699-125">*Tlbimp.exe* (tür kitaplığı alma) kullanarak birincil birlikte çalışma derlemelerinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="16699-126">Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme</span><span class="sxs-lookup"><span data-stu-id="16699-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="16699-127">Projelerinizde başvurmadan önce birincil birlikte çalışma derlemelerinin nasıl kaydedileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16699-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="16699-128">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="16699-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="16699-129">COM birlikte çalışabilirliğine Windows kayıt defteri kullanmadan bileşenleri nasıl etkinleştirebileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16699-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="16699-130">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="16699-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="16699-131">Bir uygulama bildirimi oluşturmayı ve bir bileşen bildirimi oluşturmayı ve eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="16699-132">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="16699-132">Related sections</span></span>

[<span data-ttu-id="16699-133">COM sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="16699-133">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="16699-134">COM birlikte çalışma tarafından sunulan sarmalayıcıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="16699-134">Describes the wrappers provided by COM interop.</span></span>
