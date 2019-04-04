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
ms.openlocfilehash: edec95ea729fdf26e384b6658c241ca307e60851
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408983"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="2e120-102">Yönetilmeyen kod ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="2e120-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="2e120-103">.NET Framework COM bileşenleri, COM + Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi Hizmetleri ile etkileşim yükseltir.</span><span class="sxs-lookup"><span data-stu-id="2e120-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="2e120-104">Veri türleri, yöntem imzaları ve hata işleme düzenekleri yönetilen ve yönetilmeyen nesne modeli arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e120-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="2e120-105">.NET Framework bileşenlerini ve yönetilmeyen kod arasındaki birlikte çalışabilirlik basitleştirin ve geçiş yolunun kolaylaştırmak için ortak dil çalışma zamanı istemcilerinden ve sunucuları bu nesne modellerini farklılıkları gizler.</span><span class="sxs-lookup"><span data-stu-id="2e120-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="2e120-106">Çalışma zamanı denetimi altında yürütülen kodu, yönetilen kod adı verilir.</span><span class="sxs-lookup"><span data-stu-id="2e120-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="2e120-107">Buna karşılık, çalışma zamanı dışında çalışan kod, yönetilmeyen kod adı verilir.</span><span class="sxs-lookup"><span data-stu-id="2e120-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="2e120-108">COM bileşenleri ve ActiveX arabirimleri Windows API işlevlerinde yönetilmeyen kod örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="2e120-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2e120-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="2e120-109">In this section</span></span>

[<span data-ttu-id="2e120-110">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="2e120-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="2e120-111">.NET Framework uygulamalarında COM bileşenlerini kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e120-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="2e120-112">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="2e120-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="2e120-113">COM uygulamaları .NET Framework bileşenlerini kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e120-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="2e120-114">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="2e120-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="2e120-115">Yönetilmeyen çağrı açıklamaktadır platformunu kullanarak DLL işlevleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="2e120-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="2e120-116">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="2e120-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="2e120-117">COM birlikte çalışması ve platform çağırma için hazırlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e120-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="2e120-118">Nasıl yapılır: Harita HRESULTs ve özel durumları</span><span class="sxs-lookup"><span data-stu-id="2e120-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="2e120-119">Özel durumlar ve HRESULT'ları arasındaki eşlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e120-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="2e120-120">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="2e120-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="2e120-121">COM birlikte çalışma tarafından sağlanan sarmalayıcıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e120-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="2e120-122">Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri</span><span class="sxs-lookup"><span data-stu-id="2e120-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="2e120-123">COM türleri için tür bilgisi derlemelerde nasıl katıştırılır ve ortak dil çalışma zamanı katıştırılmış COM tür denklik etiketleneceğini nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e120-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="2e120-124">Nasıl yapılır: Tlbimp.exe kullanarak birincil birlikte çalışma derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e120-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="2e120-125">Kullanarak birincil birlikte çalışma derlemeleri oluşturmak nasıl açıklar *Tlbimp.exe* (tür kitaplığı içeri Aktarıcı).</span><span class="sxs-lookup"><span data-stu-id="2e120-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="2e120-126">Nasıl yapılır: Birincil birlikte çalışma derlemelerini kaydetme</span><span class="sxs-lookup"><span data-stu-id="2e120-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="2e120-127">Projelerinizde başvurabilirsiniz önce birincil birlikte çalışma derlemelerini kaydetme işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e120-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="2e120-128">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="2e120-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="2e120-129">Windows kayıt defteri kullanmadan COM birlikte çalışma bileşenlerini nasıl etkinleştirebilirsiniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e120-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="2e120-130">Nasıl yapılır: Kayıtsız etkinleştirme için .NET Framework tabanlı COM bileşenlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2e120-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="2e120-131">Bir uygulama bildirimi oluşturma ve nasıl oluşturulacağı ve bileşen bildirim katıştırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="2e120-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>
