---
title: Derleme oluşturma
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740512"
---
# <a name="create-assemblies"></a><span data-ttu-id="69a5f-102">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="69a5f-102">Create assemblies</span></span>

<span data-ttu-id="69a5f-103">Visual Studio gibi bir IDE veya Windows SDK tarafından sağlanan derleyiciler ve araçlar kullanarak tek dosyalı veya çok dosyalı derlemeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69a5f-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="69a5f-104">En basit derleme, basit bir ada sahip olan ve tek bir uygulama etki alanına yüklenen tek bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="69a5f-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="69a5f-105">Bu derleme, uygulama dizini dışındaki diğer derlemeler tarafından başvurulamaz ve sürüm denetiminden geçmez.</span><span class="sxs-lookup"><span data-stu-id="69a5f-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="69a5f-106">Derlemeden oluşan uygulamayı kaldırmak için, bulunduğu yerdeki dizini silmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="69a5f-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="69a5f-107">Birçok geliştirici için, bu özelliklere sahip bir derleme, bir uygulamayı dağıtmak için gereken tek şeydir.</span><span class="sxs-lookup"><span data-stu-id="69a5f-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="69a5f-108">Çeşitli kod modüllerinden ve kaynak dosyalarından çok dosyalı bir derleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69a5f-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="69a5f-109">Ayrıca, birden çok uygulama tarafından paylaşılabilir bir derleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69a5f-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="69a5f-110">Paylaşılan bir derlemenin güçlü bir adı olmalıdır ve genel derleme önbelleğinde dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="69a5f-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="69a5f-111">Kod modüllerini ve kaynaklarını aşağıdaki etkenlere bağlı olarak derlemeler halinde gruplandırmak için birkaç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="69a5f-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="69a5f-112">Sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="69a5f-112">Versioning</span></span>

     <span data-ttu-id="69a5f-113">Aynı sürüm bilgilerine sahip olması gereken modülleri gruplandırma.</span><span class="sxs-lookup"><span data-stu-id="69a5f-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="69a5f-114">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="69a5f-114">Deployment</span></span>

     <span data-ttu-id="69a5f-115">Dağıtım modelinizi destekleyen kod modüllerini ve kaynakları gruplandırma.</span><span class="sxs-lookup"><span data-stu-id="69a5f-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="69a5f-116">Yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="69a5f-116">Reuse</span></span>

     <span data-ttu-id="69a5f-117">Modülleri mantıksal olarak bir amaç için birlikte kullanılabiliyorsa gruplayın.</span><span class="sxs-lookup"><span data-stu-id="69a5f-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="69a5f-118">Örneğin, program bakımı için seyrek kullanılan tür ve sınıflardan oluşan bir derleme aynı derlemeye konabilir.</span><span class="sxs-lookup"><span data-stu-id="69a5f-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="69a5f-119">Buna ek olarak, birden çok uygulamayla paylaşmayı istediğiniz türler bir derleme halinde gruplandırılmalı ve derleme güçlü bir adla imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69a5f-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="69a5f-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="69a5f-120">Security</span></span>

     <span data-ttu-id="69a5f-121">Aynı güvenlik izinleri gerektiren türleri içeren modülleri gruplandırma.</span><span class="sxs-lookup"><span data-stu-id="69a5f-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="69a5f-122">Kapsam</span><span class="sxs-lookup"><span data-stu-id="69a5f-122">Scoping</span></span>

     <span data-ttu-id="69a5f-123">Görünürlüğü aynı montajla sınırlandırılmalı türleri içeren grupları gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="69a5f-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="69a5f-124">Yönetilmeyen COM uygulamaları için ortak dil çalışma zamanı derlemeleri yaparken özel hususlar vardır.</span><span class="sxs-lookup"><span data-stu-id="69a5f-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="69a5f-125">Yönetilmeyen kodla çalışma hakkında daha fazla bilgi için [bkz.](../../framework/interop/exposing-dotnet-components-to-com.md)</span><span class="sxs-lookup"><span data-stu-id="69a5f-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69a5f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69a5f-126">See also</span></span>

- [<span data-ttu-id="69a5f-127">Montaj sürümü</span><span class="sxs-lookup"><span data-stu-id="69a5f-127">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="69a5f-128">Nasıl yapılı: Tek dosyalı derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="69a5f-128">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="69a5f-129">Nasıl yapılı: Çok dosyalı derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="69a5f-129">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="69a5f-130">Çalışma zamanı derlemeleri nasıl bulur?</span><span class="sxs-lookup"><span data-stu-id="69a5f-130">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="69a5f-131">Çok dosyalı derlemeler</span><span class="sxs-lookup"><span data-stu-id="69a5f-131">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
