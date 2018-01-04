---
title: "Kayıtsız COM Birlikte Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1eee55b2036028dd491dc82f9bce7c51aca878fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="registration-free-com-interop"></a><span data-ttu-id="b7488-102">Kayıtsız COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="b7488-102">Registration-Free COM Interop</span></span>
<span data-ttu-id="b7488-103">Kayıtsız COM birlikte çalışma derleme bilgilerini depolamak için Windows kayıt defteri kullanmadan bir bileşen etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b7488-103">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="b7488-104">Bir bilgisayarda bir bileşen dağıtımı sırasında kayıt yerine, Win32 stil bildirim dosyaları bağlama ve etkinleştirme hakkında bilgi içeren tasarım zamanında oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7488-104">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="b7488-105">Bu bildirim dosyası yerine kayıt defteri anahtarları, bir nesne etkinleştirme doğrudan.</span><span class="sxs-lookup"><span data-stu-id="b7488-105">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="b7488-106">Dağıtım sırasında kaydetme yerine derlemeleriniz için kayıtsız etkinleştirme kullanarak iki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="b7488-106">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
-   <span data-ttu-id="b7488-107">Bir bilgisayarda birden fazla sürümü yüklü olduğunda hangi DLL sürümü etkinleştirilir kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7488-107">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
-   <span data-ttu-id="b7488-108">Son kullanıcılar, XCOPY veya FTP, uygulamanız kendi bilgisayarında uygun bir dizine kopyalamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7488-108">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="b7488-109">Uygulama, diğer dizinden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7488-109">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="b7488-110">Bu bölüm bildirimlerin Kayıtsız COM birlikte çalışma için gereken iki tür açıklar: uygulama ve bileşen bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="b7488-110">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="b7488-111">Bu bildirimler XML dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="b7488-111">These manifests are XML files.</span></span> <span data-ttu-id="b7488-112">Bir uygulama geliştiricisi tarafından oluşturulmuş bir uygulama bildirimi derlemeler ve derleme bağımlılıkları açıklayan meta veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="b7488-112">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="b7488-113">Bileşen bildirimi bileşen geliştirici tarafından oluşturulan Aksi takdirde Windows kayıt defterinde bulunan bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b7488-113">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="b7488-114">Kayıtsız COM birlikte çalışma için gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="b7488-114">Requirements for registration-free COM interop</span></span>  
  
1.  <span data-ttu-id="b7488-115">Kayıtsız COM birlikte çalışma için destek Kitaplık derlemesi türüne bağlı olarak biraz değişiklik gösterir; Özellikle, olup derleme yönetilmeyen (COM yan yana) olan veya yönetilen (. NET-based).</span><span class="sxs-lookup"><span data-stu-id="b7488-115">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="b7488-116">Aşağıdaki tabloda işletim sistemi ve .NET Framework sürüm gereksinimlerini her derleme türü için gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7488-116">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="b7488-117">Derleme türü</span><span class="sxs-lookup"><span data-stu-id="b7488-117">Assembly type</span></span>|<span data-ttu-id="b7488-118">İşletim sistemi</span><span class="sxs-lookup"><span data-stu-id="b7488-118">Operating system</span></span>|<span data-ttu-id="b7488-119">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="b7488-119">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="b7488-120">COM yan yana</span><span class="sxs-lookup"><span data-stu-id="b7488-120">COM side-by-side</span></span>|<span data-ttu-id="b7488-121">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="b7488-121">Microsoft Windows XP</span></span>|<span data-ttu-id="b7488-122">Gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b7488-122">Not required.</span></span>|  
    |<span data-ttu-id="b7488-123">. NET tabanlı</span><span class="sxs-lookup"><span data-stu-id="b7488-123">.NET-based</span></span>|<span data-ttu-id="b7488-124">Windows XP SP2</span><span class="sxs-lookup"><span data-stu-id="b7488-124">Windows XP with SP2</span></span>|<span data-ttu-id="b7488-125">.NET Framework sürüm 1.1 veya üstünün.</span><span class="sxs-lookup"><span data-stu-id="b7488-125">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="b7488-126">Windows Server 2003 ailesinin Kayıtsız COM birlikte çalışma için de destekler. NET tabanlı derlemeler.</span><span class="sxs-lookup"><span data-stu-id="b7488-126">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="b7488-127">İçin bir. Kayıt defteri boş etkinleştirmeden COM, sınıf ile uyumlu olacak şekilde sınıfı NET tabanlı bir varsayılan oluşturucuya sahip olmalıdır ve ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7488-127">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a default constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="b7488-128">COM bileşenlerini kayıtsız etkinleştirme için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7488-128">Configuring COM components for registration-free activation</span></span>  
  
1.  <span data-ttu-id="b7488-129">Bir COM bileşeni kayıtsız etkinleştirme katılmak yan yana derleme olarak dağıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7488-129">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="b7488-130">Yan yana derlemeler yönetilmeyen derlemeleri ' dir.</span><span class="sxs-lookup"><span data-stu-id="b7488-130">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="b7488-131">Daha fazla bilgi için bkz: [kullanarak yan yana derlemeler](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span><span class="sxs-lookup"><span data-stu-id="b7488-131">For more information, see [Using Side-by-side Assemblies](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span></span>  
  
     <span data-ttu-id="b7488-132">COM yan yana derlemeleri kullanmak için bir. NET tabanlı uygulama geliştiricisi bağlama ve etkinleştirme bilgilerini içeren bir uygulama bildirimi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7488-132">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="b7488-133">Yönetilmeyen yan yana derlemeler için destek Windows XP işletim sisteminde yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="b7488-133">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="b7488-134">Etkinleştirilmekte olan bileşen kayıt defterinde olmadığında işletim sistemi tarafından desteklenen COM çalışma zamanı etkinleştirme bilgileri için bir uygulama bildirimi tarar.</span><span class="sxs-lookup"><span data-stu-id="b7488-134">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="b7488-135">Kayıtsız etkinleştirme Windows XP üzerinde yüklü COM bileşenleri için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7488-135">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="b7488-136">Uygulamaya bir yan yana derleme ekleme hakkında ayrıntılı yönergeler için bkz: [kullanarak yan yana derlemeler](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span><span class="sxs-lookup"><span data-stu-id="b7488-136">For detailed instructions on adding a side-by-side assembly to an application, see [Using Side-by-side Assemblies](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7488-137">Yan yana yürütme çalışma zamanı birden fazla sürümünü ve uygulamaları ve çalışma zamanı sürümü aynı bilgisayarda aynı anda çalıştırmak için kullandığınız bileşenleri birden fazla sürümünü sağlayan bir .NET Framework özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="b7488-137">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="b7488-138">Yan yana yürütme ve yan yana derlemeler yan yana işlevselliği sağlamak için farklı mekanizmalardır.</span><span class="sxs-lookup"><span data-stu-id="b7488-138">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7488-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7488-139">See Also</span></span>  
 [<span data-ttu-id="b7488-140">Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7488-140">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
