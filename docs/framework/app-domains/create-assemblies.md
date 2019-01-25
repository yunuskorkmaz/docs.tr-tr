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
ms.openlocfilehash: 2713011d61b41dfa4d72a635c656c0c00cb42f8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643617"
---
# <a name="creating-assemblies"></a><span data-ttu-id="0bb32-102">Derlemeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0bb32-102">Creating Assemblies</span></span>

<span data-ttu-id="0bb32-103">Visual Studio gibi bir IDE kullanarak tek dosya veya çok dosyalı derlemeler oluşturabilir veya derleyiciler ve araçlar sağlayan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0bb32-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="0bb32-104">Basit, basit bir ada sahip ve tek bir uygulama etki alanına yüklü olduğu tek bir dosyaya derlemesidir.</span><span class="sxs-lookup"><span data-stu-id="0bb32-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="0bb32-105">Bu derleme, uygulama dizininin dışındaki diğer derlemeler tarafından başvurulamaz ve sürüm denetimi yapmak değil.</span><span class="sxs-lookup"><span data-stu-id="0bb32-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="0bb32-106">Derlemenin oluşan uygulamayı kaldırmak için basitçe bulunduğu dizini silin.</span><span class="sxs-lookup"><span data-stu-id="0bb32-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="0bb32-107">Birçok geliştirici için bu özelliklere sahip bir derleme bir uygulamayı dağıtmak için gereken şey.</span><span class="sxs-lookup"><span data-stu-id="0bb32-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="0bb32-108">Birkaç kod modülleri ve kaynak dosyalarını, bir çoklu dosya derlemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bb32-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="0bb32-109">Birden çok uygulama tarafından paylaşılabilen bir derlemeyi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bb32-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="0bb32-110">Paylaşılan bir derleme tanımlayıcı bir ada sahip olmalıdır ve genel derleme önbelleğinde dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bb32-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="0bb32-111">Derlemeler, aşağıdaki etkenlere bağlı olarak içine kod modülleri ve kaynakları gruplama birkaç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="0bb32-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

-   <span data-ttu-id="0bb32-112">Sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="0bb32-112">Versioning</span></span>

     <span data-ttu-id="0bb32-113">Grup modüller aynı sürüm bilgisini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="0bb32-113">Group modules that should have the same version information.</span></span>

-   <span data-ttu-id="0bb32-114">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="0bb32-114">Deployment</span></span>

     <span data-ttu-id="0bb32-115">Grup kod modülleri ve modelinizin dağıtımı destekleyen kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="0bb32-115">Group code modules and resources that support your model of deployment.</span></span>

-   <span data-ttu-id="0bb32-116">Yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="0bb32-116">Reuse</span></span>

     <span data-ttu-id="0bb32-117">Bunlar mantıksal olarak birlikte bazı amaç için kullanılabiliyorsa modülleri gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="0bb32-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="0bb32-118">Örneğin, aynı derlemede türlerin ve sınıfların program bakımı için kullanılmayan oluşan bir derleme içine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0bb32-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="0bb32-119">Ayrıca, birden çok uygulama ile paylaşmak için istediğinize türleri bir derlemeye gruplandırılmasını ve derlemeyi bir güçlü ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0bb32-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

-   <span data-ttu-id="0bb32-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0bb32-120">Security</span></span>

     <span data-ttu-id="0bb32-121">Aynı güvenlik izinleri gerektiren türler içeren Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="0bb32-121">Group modules containing types that require the same security permissions.</span></span>

-   <span data-ttu-id="0bb32-122">Kapsam belirleme</span><span class="sxs-lookup"><span data-stu-id="0bb32-122">Scoping</span></span>

     <span data-ttu-id="0bb32-123">Görünürlüğü aynı derlemeye sınırlandırılmalıdır türleri içeren Grup modüllerinin.</span><span class="sxs-lookup"><span data-stu-id="0bb32-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="0bb32-124">Özel durumlar, ortak dil çalışma zamanı derlemeleri yönetilmeyen COM uygulamalarına yaparken yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb32-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="0bb32-125">Yönetilmeyen kod ile çalışma hakkında daha fazla bilgi için bkz. [.NET Framework bileşenlerini COM'da gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="0bb32-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bb32-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bb32-126">See also</span></span>

- [<span data-ttu-id="0bb32-127">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="0bb32-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="0bb32-128">Bütünleştirilmiş Kod Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0bb32-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="0bb32-129">Nasıl yapılır: Tek Dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="0bb32-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="0bb32-130">Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="0bb32-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="0bb32-131">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="0bb32-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="0bb32-132">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="0bb32-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)