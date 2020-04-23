---
title: Yönetilmeyen kodla birlikte çalışma
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
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457959"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="29080-102">Yönetilmeyen kodla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="29080-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="29080-103">.NET Framework, COM bileşenleri, COM+ Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi hizmeti ile etkileşimi yükseltir.</span><span class="sxs-lookup"><span data-stu-id="29080-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="29080-104">Veri türleri, yöntem imzaları ve hata işleme mekanizmaları, yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="29080-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="29080-105">.NET Framework bileşenleri ve yönetilmeyen kod arasında birlikte çalışabilirlik kolaylaştırmak ve geçiş yolunu kolaylaştırmak için, ortak dil çalışma zamanı hem istemcilerden hem de sunuculardan bu nesne modellerindeki farklılıkları önler.</span><span class="sxs-lookup"><span data-stu-id="29080-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="29080-106">Çalışma zamanının denetimi altında yürütülen koda yönetilen kod denir.</span><span class="sxs-lookup"><span data-stu-id="29080-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="29080-107">Buna karşılık, çalışma zamanının dışında çalışan koda yönetilmeyen kod denir.</span><span class="sxs-lookup"><span data-stu-id="29080-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="29080-108">COM bileşenleri, ActiveX arabirimleri ve Windows API işlevleri, yönetilmeyen koda örnektir.</span><span class="sxs-lookup"><span data-stu-id="29080-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="29080-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="29080-109">In this section</span></span>

[<span data-ttu-id="29080-110">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="29080-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="29080-111">.NET Framework uygulamalardan COM bileşenlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="29080-112">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="29080-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="29080-113">COM uygulamalarından .NET Framework bileşenlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="29080-114">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="29080-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="29080-115">Platform Invoke kullanılarak yönetilmeyen DLL işlevlerinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="29080-116">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="29080-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="29080-117">COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="29080-118">Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme</span><span class="sxs-lookup"><span data-stu-id="29080-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="29080-119">Özel durumlar ve HRESULTs arasındaki eşlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="29080-120">Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri</span><span class="sxs-lookup"><span data-stu-id="29080-120">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="29080-121">COM türleri için tür bilgilerinin derlemelerde nasıl gömülü olduğunu ve ortak dil çalışma zamanının gömülü COM türlerinin denklik düzeyini nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-121">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="29080-122">Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29080-122">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="29080-123">*Tlbimp. exe* (tür kitaplığı alma) kullanarak birincil birlikte çalışma derlemelerinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-123">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="29080-124">Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme</span><span class="sxs-lookup"><span data-stu-id="29080-124">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="29080-125">Projelerinizde başvurmadan önce birincil birlikte çalışma derlemelerinin nasıl kaydedileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29080-125">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="29080-126">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="29080-126">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="29080-127">COM birlikte çalışabilirliğine Windows kayıt defteri kullanmadan bileşenleri nasıl etkinleştirebileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29080-127">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="29080-128">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29080-128">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="29080-129">Bir uygulama bildirimi oluşturmayı ve bir bileşen bildirimi oluşturmayı ve eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-129">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="29080-130">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="29080-130">Related sections</span></span>

[<span data-ttu-id="29080-131">COM sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="29080-131">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="29080-132">COM birlikte çalışma tarafından sunulan sarmalayıcıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="29080-132">Describes the wrappers provided by COM interop.</span></span>
