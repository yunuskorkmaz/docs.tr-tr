---
title: Derlemeler Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8490351b4ab1bb115e4bd7277f43ad22b144a2df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752071"
---
# <a name="creating-assemblies"></a><span data-ttu-id="68b6d-102">Derlemeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="68b6d-102">Creating Assemblies</span></span>
<span data-ttu-id="68b6d-103">Bir IDE kullanarak tek bir dosya veya birden çok dosya derlemeleri oluşturabilirsiniz [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], veya derleyicileri ve de tarafından sağlanan araçları [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68b6d-103">You can create single-file or multifile assemblies using an IDE, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="68b6d-104">En basit derleme basit bir ad ve tek bir uygulama etki alanına yüklü olduğu bir tek dosyadır.</span><span class="sxs-lookup"><span data-stu-id="68b6d-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="68b6d-105">Bu derleme uygulama dizininin dışındaki diğer derlemelerden tarafından başvurulamaz ve sürüm denetimi uygulanabilecek değil.</span><span class="sxs-lookup"><span data-stu-id="68b6d-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="68b6d-106">Derlemenin oluşan uygulamayı kaldırmak için yalnızca şu bulunduğu dizini silin.</span><span class="sxs-lookup"><span data-stu-id="68b6d-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="68b6d-107">Birçok geliştiriciler için bu özelliklere sahip bir derleme bir uygulamayı dağıtmak için gereken tek şey.</span><span class="sxs-lookup"><span data-stu-id="68b6d-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>  
  
 <span data-ttu-id="68b6d-108">Birkaç kod modülleri ve kaynak dosyaları, birden fazla dosya derlemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68b6d-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="68b6d-109">Birden çok uygulama tarafından paylaşılan bir derleme de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68b6d-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="68b6d-110">Paylaşılan bir derleme güçlü bir adı olması gerekir ve genel derleme önbelleğinde dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="68b6d-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="68b6d-111">Kod modülleri ve kaynaklarına aşağıdaki etkenlere bağlı olarak derlemeler halinde gruplandırma, birkaç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="68b6d-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>  
  
-   <span data-ttu-id="68b6d-112">Sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="68b6d-112">Versioning</span></span>  
  
     <span data-ttu-id="68b6d-113">Aynı sürüm bilgisini içermelidir Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="68b6d-113">Group modules that should have the same version information.</span></span>  
  
-   <span data-ttu-id="68b6d-114">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="68b6d-114">Deployment</span></span>  
  
     <span data-ttu-id="68b6d-115">Grup kod modülleri ve modelinizi dağıtım desteği kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="68b6d-115">Group code modules and resources that support your model of deployment.</span></span>  
  
-   <span data-ttu-id="68b6d-116">Yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="68b6d-116">Reuse</span></span>  
  
     <span data-ttu-id="68b6d-117">Bunlar mantıksal olarak birlikte bazı amaç için kullanılıp kullanılamayacağını modülleri grup.</span><span class="sxs-lookup"><span data-stu-id="68b6d-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="68b6d-118">Örneğin, türleri ve seyrek program bakımı için kullanılan sınıflar oluşan bir derlemeyi aynı bütünleştirilmiş kodda beklemeye getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="68b6d-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="68b6d-119">Ayrıca, birden çok uygulama ile paylaşmak istiyorsanız türleri bir derlemeye gruplandırılmalıdır ve derleme tanımlayıcı bir ad ile oturum açmış olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68b6d-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>  
  
-   <span data-ttu-id="68b6d-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="68b6d-120">Security</span></span>  
  
     <span data-ttu-id="68b6d-121">Aynı güvenlik izinleri gerektiren türleri içeren Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="68b6d-121">Group modules containing types that require the same security permissions.</span></span>  
  
-   <span data-ttu-id="68b6d-122">Kapsamı</span><span class="sxs-lookup"><span data-stu-id="68b6d-122">Scoping</span></span>  
  
     <span data-ttu-id="68b6d-123">Görünürlüğü aynı bütünleştirilmiş sınırlandırılmalıdır türleri içeren Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="68b6d-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>  
  
 <span data-ttu-id="68b6d-124">Ortak dil çalışma zamanı derlemeleri yönetilmeyen COM uygulamalarına yaparken özel konuları göz önünde bulundurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68b6d-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="68b6d-125">Yönetilmeyen kod ile çalışma hakkında daha fazla bilgi için bkz: [.NET Framework bileşenlerini COM'da gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="68b6d-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b6d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68b6d-126">See Also</span></span>  
 [<span data-ttu-id="68b6d-127">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="68b6d-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="68b6d-128">Bütünleştirilmiş Kod Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="68b6d-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="68b6d-129">Nasıl yapılır: Tek Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="68b6d-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [<span data-ttu-id="68b6d-130">Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="68b6d-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="68b6d-131">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="68b6d-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="68b6d-132">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="68b6d-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
