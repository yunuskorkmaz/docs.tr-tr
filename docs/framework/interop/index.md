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
ms.openlocfilehash: cdd8d2781331956289d2b74162e653ba1ee8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114233"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="c2c54-102">Yönetilmeyen kodla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="c2c54-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="c2c54-103">.NET Framework, COM bileşenleri, COM+ Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi hizmeti ile etkileşimi yükseltir.</span><span class="sxs-lookup"><span data-stu-id="c2c54-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="c2c54-104">Veri türleri, yöntem imzaları ve hata işleme mekanizmaları, yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2c54-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="c2c54-105">.NET Framework bileşenleri ve yönetilmeyen kod arasında birlikte çalışabilirlik kolaylaştırmak ve geçiş yolunu kolaylaştırmak için, ortak dil çalışma zamanı hem istemcilerden hem de sunuculardan bu nesne modellerindeki farklılıkları önler.</span><span class="sxs-lookup"><span data-stu-id="c2c54-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="c2c54-106">Çalışma zamanının denetimi altında yürütülen koda yönetilen kod denir.</span><span class="sxs-lookup"><span data-stu-id="c2c54-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="c2c54-107">Buna karşılık, çalışma zamanının dışında çalışan koda yönetilmeyen kod denir.</span><span class="sxs-lookup"><span data-stu-id="c2c54-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="c2c54-108">COM bileşenleri, ActiveX arabirimleri ve Windows API işlevleri, yönetilmeyen koda örnektir.</span><span class="sxs-lookup"><span data-stu-id="c2c54-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c2c54-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="c2c54-109">In this section</span></span>

[<span data-ttu-id="c2c54-110">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="c2c54-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="c2c54-111">.NET Framework uygulamalardan COM bileşenlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="c2c54-112">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="c2c54-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="c2c54-113">COM uygulamalarından .NET Framework bileşenlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="c2c54-114">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c2c54-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="c2c54-115">Platform Invoke kullanılarak yönetilmeyen DLL işlevlerinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="c2c54-116">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c2c54-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="c2c54-117">COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="c2c54-118">Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme</span><span class="sxs-lookup"><span data-stu-id="c2c54-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="c2c54-119">Özel durumlar ve HRESULTs arasındaki eşlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="c2c54-120">COM Sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="c2c54-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="c2c54-121">COM birlikte çalışma tarafından sunulan sarmalayıcıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="c2c54-122">Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri</span><span class="sxs-lookup"><span data-stu-id="c2c54-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="c2c54-123">COM türleri için tür bilgilerinin derlemelerde nasıl gömülü olduğunu ve ortak dil çalışma zamanının gömülü COM türlerinin denklik düzeyini nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="c2c54-124">Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Bütünleştirilmiş Kodları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2c54-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="c2c54-125">*Tlbimp. exe* (tür kitaplığı alma) kullanarak birincil birlikte çalışma derlemelerinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="c2c54-126">Nasıl yapılır: Birincil Birlikte Çalışma Bütünleştirilmiş Kodlarını Kaydetme</span><span class="sxs-lookup"><span data-stu-id="c2c54-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="c2c54-127">Projelerinizde başvurmadan önce birincil birlikte çalışma derlemelerinin nasıl kaydedileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2c54-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="c2c54-128">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="c2c54-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="c2c54-129">COM birlikte çalışabilirliğine Windows kayıt defteri kullanmadan bileşenleri nasıl etkinleştirebileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2c54-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="c2c54-130">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c2c54-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="c2c54-131">Bir uygulama bildirimi oluşturmayı ve bir bileşen bildirimi oluşturmayı ve eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c54-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>
