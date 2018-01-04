---
title: "Derlemeler Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2168cbcd19437c1e275da7a01aa0c75ab47600eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-assemblies"></a><span data-ttu-id="c6392-102">Derlemeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6392-102">Creating Assemblies</span></span>
<span data-ttu-id="c6392-103">Bir IDE kullanarak tek bir dosya veya birden çok dosya derlemeleri oluşturabilirsiniz [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], veya derleyicileri ve de tarafından sağlanan araçları [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6392-103">You can create single-file or multifile assemblies using an IDE, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="c6392-104">En basit derleme basit bir ad ve tek bir uygulama etki alanına yüklü olduğu bir tek dosyadır.</span><span class="sxs-lookup"><span data-stu-id="c6392-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="c6392-105">Bu derleme uygulama dizininin dışındaki diğer derlemelerden tarafından başvurulamaz ve sürüm denetimi uygulanabilecek değil.</span><span class="sxs-lookup"><span data-stu-id="c6392-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="c6392-106">Derlemenin oluşan uygulamayı kaldırmak için yalnızca şu bulunduğu dizini silin.</span><span class="sxs-lookup"><span data-stu-id="c6392-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="c6392-107">Birçok geliştiriciler için bu özelliklere sahip bir derleme bir uygulamayı dağıtmak için gereken tek şey.</span><span class="sxs-lookup"><span data-stu-id="c6392-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>  
  
 <span data-ttu-id="c6392-108">Birkaç kod modülleri ve kaynak dosyaları, birden fazla dosya derlemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6392-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="c6392-109">Birden çok uygulama tarafından paylaşılan bir derleme de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6392-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="c6392-110">Paylaşılan bir derleme güçlü bir adı olması gerekir ve genel derleme önbelleğinde dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6392-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="c6392-111">Kod modülleri ve kaynaklarına aşağıdaki etkenlere bağlı olarak derlemeler halinde gruplandırma, birkaç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="c6392-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>  
  
-   <span data-ttu-id="c6392-112">Sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6392-112">Versioning</span></span>  
  
     <span data-ttu-id="c6392-113">Aynı sürüm bilgisini içermelidir Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="c6392-113">Group modules that should have the same version information.</span></span>  
  
-   <span data-ttu-id="c6392-114">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="c6392-114">Deployment</span></span>  
  
     <span data-ttu-id="c6392-115">Grup kod modülleri ve modelinizi dağıtım desteği kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="c6392-115">Group code modules and resources that support your model of deployment.</span></span>  
  
-   <span data-ttu-id="c6392-116">Yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="c6392-116">Reuse</span></span>  
  
     <span data-ttu-id="c6392-117">Bunlar mantıksal olarak birlikte bazı amaç için kullanılıp kullanılamayacağını modülleri grup.</span><span class="sxs-lookup"><span data-stu-id="c6392-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="c6392-118">Örneğin, türleri ve seyrek program bakımı için kullanılan sınıflar oluşan bir derlemeyi aynı bütünleştirilmiş kodda beklemeye getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c6392-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="c6392-119">Ayrıca, birden çok uygulama ile paylaşmak istiyorsanız türleri bir derlemeye gruplandırılmalıdır ve derleme tanımlayıcı bir ad ile oturum açmış olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6392-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>  
  
-   <span data-ttu-id="c6392-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c6392-120">Security</span></span>  
  
     <span data-ttu-id="c6392-121">Aynı güvenlik izinleri gerektiren türleri içeren Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="c6392-121">Group modules containing types that require the same security permissions.</span></span>  
  
-   <span data-ttu-id="c6392-122">Kapsamı</span><span class="sxs-lookup"><span data-stu-id="c6392-122">Scoping</span></span>  
  
     <span data-ttu-id="c6392-123">Görünürlüğü aynı bütünleştirilmiş sınırlandırılmalıdır türleri içeren Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="c6392-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>  
  
 <span data-ttu-id="c6392-124">Ortak dil çalışma zamanı derlemeleri yönetilmeyen COM uygulamalarına yaparken özel konuları göz önünde bulundurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6392-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="c6392-125">Yönetilmeyen kod ile çalışma hakkında daha fazla bilgi için bkz: [.NET Framework bileşenlerini COM'da gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="c6392-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6392-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6392-126">See Also</span></span>  
 [<span data-ttu-id="c6392-127">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="c6392-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="c6392-128">Bütünleştirilmiş Kod Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6392-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="c6392-129">Nasıl yapılır: Tek Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="c6392-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [<span data-ttu-id="c6392-130">Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="c6392-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="c6392-131">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c6392-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="c6392-132">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="c6392-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
