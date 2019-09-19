---
title: Genel Derleme Önbelleği
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a2ac0c7fb5f89c7d6b9daba8da7b37d1135acb6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053179"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="21f4f-102">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="21f4f-102">Global Assembly Cache</span></span>
<span data-ttu-id="21f4f-103">Ortak dil çalışma zamanının yüklü olduğu her bilgisayarda, genel derleme önbelleği olarak adlandırılan makine genelindeki bir kod önbelleği bulunur.</span><span class="sxs-lookup"><span data-stu-id="21f4f-103">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="21f4f-104">Genel bütünleştirilmiş kod önbelleği, bilgisayardaki çeşitli uygulamalar tarafından paylaşılmak üzere özel olarak belirlenmiş derlemeleri depolar.</span><span class="sxs-lookup"><span data-stu-id="21f4f-104">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="21f4f-105">Derlemeleri yalnızca gerektiğinde genel derleme önbelleğine yükleyerek paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21f4f-105">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="21f4f-106">Genel bir kılavuz olarak, derleme bağımlılıklarını özel tutun ve bir derlemeyi paylaşıma açık bir şekilde gerekmediği sürece derlemeleri uygulama dizininde bulun.</span><span class="sxs-lookup"><span data-stu-id="21f4f-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="21f4f-107">Ayrıca, COM birlikte çalışma veya yönetilmeyen kod için erişilebilir hale getirmek üzere derlemeleri genel derleme önbelleğine yüklemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="21f4f-107">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21f4f-108">Genel bütünleştirilmiş kod önbelleğine bir derlemeyi doğrudan yüklemek istemediğiniz senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="21f4f-108">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="21f4f-109">Genel derleme önbelleğinde bir uygulamayı oluşturan derlemelerden birini yerleştirirseniz, uygulama dizinini kopyalamak için **xcopy** komutunu kullanarak uygulamayı artık çoğaltamaz veya yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="21f4f-109">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="21f4f-110">Derlemeyi genel derleme önbelleğinde de taşımanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="21f4f-110">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="21f4f-111">Bir derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="21f4f-111">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="21f4f-112">Genel derleme önbelleği ile çalışmak için tasarlanan bir yükleyici kullanın.</span><span class="sxs-lookup"><span data-stu-id="21f4f-112">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="21f4f-113">Bu, bütünleştirilmiş kodları genel derleme önbelleğine yüklemek için tercih edilen seçenektir.</span><span class="sxs-lookup"><span data-stu-id="21f4f-113">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="21f4f-114">Windows SDK tarafından verilen [genel derleme önbelleği aracı (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md)adlı bir geliştirici aracı kullanın.</span><span class="sxs-lookup"><span data-stu-id="21f4f-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="21f4f-115">Dağıtım senaryolarında, bütünleştirilmiş kodları genel derleme önbelleğine yüklemek için Windows Installer kullanın.</span><span class="sxs-lookup"><span data-stu-id="21f4f-115">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="21f4f-116">Genel bütünleştirilmiş kod önbelleği aracını yalnızca geliştirme senaryolarında kullanın, çünkü bu, Windows Installer kullanılırken belirtilen derleme başvuru sayma ve diğer özellikleri sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="21f4f-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="21f4f-117">.NET Framework 4 ' te başlayarak, genel derleme önbelleğinin varsayılan konumu **%windir%\Microsoft.NET\assembly**' dir.</span><span class="sxs-lookup"><span data-stu-id="21f4f-117">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="21f4f-118">.NET Framework önceki sürümlerinde, varsayılan konum **%windir%\Assembly**' dir.</span><span class="sxs-lookup"><span data-stu-id="21f4f-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="21f4f-119">Yöneticiler, yazma ve Yürütme erişimini denetlemek için genellikle bir erişim denetim listesi (ACL) kullanarak SystemRoot dizinini korur.</span><span class="sxs-lookup"><span data-stu-id="21f4f-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="21f4f-120">Genel derleme önbelleği, SystemRoot dizininin bir alt dizininde yüklü olduğundan, bu dizinin ACL 'sini devralır.</span><span class="sxs-lookup"><span data-stu-id="21f4f-120">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="21f4f-121">Yalnızca yönetici ayrıcalıklarına sahip kullanıcıların, dosyaları genel derleme önbelleğinden silmesine izin verilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="21f4f-121">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="21f4f-122">Genel bütünleştirilmiş kod önbelleğinde dağıtılan derlemelerin tanımlayıcı bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21f4f-122">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="21f4f-123">Genel bütünleştirilmiş kod önbelleğine bir derleme eklendiğinde, derlemeyi oluşturan tüm dosyalarda bütünlük denetimleri gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="21f4f-123">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="21f4f-124">Önbellek, bir derlemenin değiştirilmediğinden emin olmak için bu bütünlük denetimlerini gerçekleştirir, örneğin bir dosya değiştiğinde bildirim değişikliği yansıtmaz.</span><span class="sxs-lookup"><span data-stu-id="21f4f-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f4f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21f4f-125">See also</span></span>

- [<span data-ttu-id="21f4f-126">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="21f4f-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="21f4f-127">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="21f4f-127">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="21f4f-128">Kesin Adlandırılmış Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="21f4f-128">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
