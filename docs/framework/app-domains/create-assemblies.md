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
ms.openlocfilehash: 993c7f590f30b44f45e4833b4364b40ad9748b58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607774"
---
# <a name="creating-assemblies"></a><span data-ttu-id="ab638-102">Derlemeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab638-102">Creating Assemblies</span></span>

<span data-ttu-id="ab638-103">Visual Studio gibi bir IDE kullanarak tek dosya veya çok dosyalı derlemeler oluşturabilir veya derleyiciler ve araçlar sağlayan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab638-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="ab638-104">Basit, basit bir ada sahip ve tek bir uygulama etki alanına yüklü olduğu tek bir dosyaya derlemesidir.</span><span class="sxs-lookup"><span data-stu-id="ab638-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="ab638-105">Bu derleme, uygulama dizininin dışındaki diğer derlemeler tarafından başvurulamaz ve sürüm denetimi yapmak değil.</span><span class="sxs-lookup"><span data-stu-id="ab638-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="ab638-106">Derlemenin oluşan uygulamayı kaldırmak için basitçe bulunduğu dizini silin.</span><span class="sxs-lookup"><span data-stu-id="ab638-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="ab638-107">Birçok geliştirici için bu özelliklere sahip bir derleme bir uygulamayı dağıtmak için gereken şey.</span><span class="sxs-lookup"><span data-stu-id="ab638-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="ab638-108">Birkaç kod modülleri ve kaynak dosyalarını, bir çoklu dosya derlemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab638-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="ab638-109">Birden çok uygulama tarafından paylaşılabilen bir derlemeyi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab638-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="ab638-110">Paylaşılan bir derleme tanımlayıcı bir ada sahip olmalıdır ve genel derleme önbelleğinde dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab638-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="ab638-111">Derlemeler, aşağıdaki etkenlere bağlı olarak içine kod modülleri ve kaynakları gruplama birkaç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="ab638-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="ab638-112">Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab638-112">Versioning</span></span>

     <span data-ttu-id="ab638-113">Grup modüller aynı sürüm bilgisini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ab638-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="ab638-114">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="ab638-114">Deployment</span></span>

     <span data-ttu-id="ab638-115">Grup kod modülleri ve modelinizin dağıtımı destekleyen kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="ab638-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="ab638-116">Yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="ab638-116">Reuse</span></span>

     <span data-ttu-id="ab638-117">Bunlar mantıksal olarak birlikte bazı amaç için kullanılabiliyorsa modülleri gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="ab638-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="ab638-118">Örneğin, aynı derlemede türlerin ve sınıfların program bakımı için kullanılmayan oluşan bir derleme içine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ab638-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="ab638-119">Ayrıca, birden çok uygulama ile paylaşmak için istediğinize türleri bir derlemeye gruplandırılmasını ve derlemeyi bir güçlü ad ile imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab638-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="ab638-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ab638-120">Security</span></span>

     <span data-ttu-id="ab638-121">Aynı güvenlik izinleri gerektiren türler içeren Grup modüller.</span><span class="sxs-lookup"><span data-stu-id="ab638-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="ab638-122">Kapsam belirleme</span><span class="sxs-lookup"><span data-stu-id="ab638-122">Scoping</span></span>

     <span data-ttu-id="ab638-123">Görünürlüğü aynı derlemeye sınırlandırılmalıdır türleri içeren Grup modüllerinin.</span><span class="sxs-lookup"><span data-stu-id="ab638-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="ab638-124">Özel durumlar, ortak dil çalışma zamanı derlemeleri yönetilmeyen COM uygulamalarına yaparken yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab638-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="ab638-125">Yönetilmeyen kod ile çalışma hakkında daha fazla bilgi için bkz. [.NET Framework bileşenlerini COM'da gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="ab638-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab638-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab638-126">See also</span></span>

- [<span data-ttu-id="ab638-127">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="ab638-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="ab638-128">Bütünleştirilmiş Kod Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ab638-128">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="ab638-129">Nasıl yapılır: Tek Dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="ab638-129">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [<span data-ttu-id="ab638-130">Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="ab638-130">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="ab638-131">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="ab638-131">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ab638-132">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="ab638-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)