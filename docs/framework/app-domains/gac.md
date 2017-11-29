---
title: "Genel Derleme Önbelleği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ca51a06e6e7ec89576facf3a70c789325fd893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="global-assembly-cache"></a><span data-ttu-id="76ece-102">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="76ece-102">Global Assembly Cache</span></span>
<span data-ttu-id="76ece-103">Ortak dil çalışma zamanı yüklendiği her bilgisayarda, genel derleme önbelleği olarak adlandırılan bir makineye kod önbelleği bulunur.</span><span class="sxs-lookup"><span data-stu-id="76ece-103">Each computer where the common language runtime is installed has a machine-wide code cache called the global assembly cache.</span></span> <span data-ttu-id="76ece-104">Genel Derleme Önbelleği özellikle bilgisayarda çeşitli uygulamalar tarafından paylaşılmak üzere belirtilen derlemelerini depolar.</span><span class="sxs-lookup"><span data-stu-id="76ece-104">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="76ece-105">Yalnızca, gerektiğinde bunları genel derleme önbelleğine yükleme tarafından derlemeleri paylaşması gerekir.</span><span class="sxs-lookup"><span data-stu-id="76ece-105">You should share assemblies by installing them into the global assembly cache only when you need to.</span></span> <span data-ttu-id="76ece-106">Genel bir kılavuz olarak derleme bağımlılıkları gizliliğini korumak ve bir derlemeyi paylaşımı kesinlikle gerekli olmadığı sürece derlemeleri uygulama dizininde bulun.</span><span class="sxs-lookup"><span data-stu-id="76ece-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="76ece-107">Buna ek olarak, COM birlikte çalışma veya yönetilmeyen kod için erişilebilir hale getirmek için genel derleme önbelleğine derlemelerini yüklemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="76ece-107">In addition, it is not necessary to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76ece-108">Açıkça bir derlemeyi genel derleme önbelleğine yüklemek istediğiniz olmayan senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="76ece-108">There are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="76ece-109">Genel Derleme Önbelleği uygulamada oluşturan derlemeler birini yerleştirirseniz, artık çoğaltmak veya uygulamayı kullanarak yüklemek **xcopy** uygulama dizini kopyalamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="76ece-109">If you place one of the assemblies that make up an application in the global assembly cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="76ece-110">Derleme genel derleme önbelleğinde de taşımanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="76ece-110">You must move the assembly in the global assembly cache as well.</span></span>  
  
 <span data-ttu-id="76ece-111">Bir derlemeyi genel derleme önbelleğine dağıtmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="76ece-111">There are two ways to deploy an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="76ece-112">Genel Derleme Önbelleği ile çalışmak üzere tasarlanmış bir yükleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="76ece-112">Use an installer designed to work with the global assembly cache.</span></span> <span data-ttu-id="76ece-113">Derlemeleri genel derleme önbelleğine yükleme için tercih edilen seçenek budur.</span><span class="sxs-lookup"><span data-stu-id="76ece-113">This is the preferred option for installing assemblies into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="76ece-114">Adlı bir geliştirici aracı [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="76ece-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76ece-115">Dağıtım senaryolarında, derlemeleri genel derleme önbelleğine yüklemek için Windows Installer 2.0'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="76ece-115">In deployment scenarios, use Windows Installer to install assemblies into the global assembly cache.</span></span> <span data-ttu-id="76ece-116">Derleme başvurusu sayım ve Windows Installer kullanırken sağlanan diğer özellikleri sağlamadığından yalnızca geliştirme senaryolarda Genel Derleme Önbelleği Aracı'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="76ece-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="76ece-117">.NET Framework 4 ile başlayarak, genel derleme önbelleği için varsayılan konum olan **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="76ece-117">Starting with the .NET Framework 4, the default location for the global assembly cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="76ece-118">.NET Framework önceki sürümlerde varsayılan konumdur **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="76ece-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="76ece-119">Yöneticiler genellikle yazma denetlemek ve yürütme erişimi için bir erişim denetimi listesi (ACL) kullanılarak systemroot dizini koruyun.</span><span class="sxs-lookup"><span data-stu-id="76ece-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="76ece-120">Genel Derleme Önbelleği systemroot dizinin bir alt dizinde yüklü olduğundan, bu dizinin ACL devralır.</span><span class="sxs-lookup"><span data-stu-id="76ece-120">Because the global assembly cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="76ece-121">Yalnızca yönetici ayrıcalıklarına sahip kullanıcılar, Genel Derleme Önbelleği'nden dosyalarını silmek için izin önerilir.</span><span class="sxs-lookup"><span data-stu-id="76ece-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
 <span data-ttu-id="76ece-122">Derlemeleri genel derleme önbelleğinde dağıtılan güçlü bir adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="76ece-122">Assemblies deployed in the global assembly cache must have a strong name.</span></span> <span data-ttu-id="76ece-123">Bir derlemeyi genel derleme önbelleğine eklendiğinde, bütünlük denetimlerinin derlemeyi oluşturan tüm dosyalar üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="76ece-123">When an assembly is added to the global assembly cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="76ece-124">Önbellek, bir derlemeyi, örneğin, bir dosya değişti, ancak bildirim değişikliği yansıtmayan durumlarda değiştirilmemiş emin olmak için bu bütünlüğü denetler.</span><span class="sxs-lookup"><span data-stu-id="76ece-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ece-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76ece-125">See Also</span></span>  
 [<span data-ttu-id="76ece-126">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="76ece-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="76ece-127">Derlemeler ve genel derleme önbelleği ile çalışma</span><span class="sxs-lookup"><span data-stu-id="76ece-127">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="76ece-128">Tanımlayıcı adlı derlemeler</span><span class="sxs-lookup"><span data-stu-id="76ece-128">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
