---
title: Derlemeler ve Genel Derleme Önbelleği ile Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91e780ed7e841809f21130822babe55ad4935670
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744310"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="068b1-102">Derlemeler ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="068b1-102">Working with Assemblies and the Global Assembly Cache</span></span>
<span data-ttu-id="068b1-103">Eğer bir derlemeyi birden çok uygulama arasında paylaşmak istiyorsanız, bu derlemeyi genel bütünleştirilmiş kod önbelleğine yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="068b1-103">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="068b1-104">Ortak dil çalışma zamanının yüklü olduğu tüm bilgisayarlar, makine düzeyindeki bu kod önbelleğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="068b1-104">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="068b1-105">Genel Derleme Önbelleği özellikle bilgisayarda çeşitli uygulamalar tarafından paylaşılmak üzere belirtilen derlemelerini depolar.</span><span class="sxs-lookup"><span data-stu-id="068b1-105">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="068b1-106">Bir derlemenin genel bütünleştirilmiş kod önbelleğine yüklenebilmesi için tanımlayıcı ada sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="068b1-106">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="068b1-107">Genel bütünleştirilmiş kod önbelleğine yerleştirilen derlemeler aynı derleme adı ve dosya adına sahip olmalıdır (dosya adı uzantısı dahil değil).</span><span class="sxs-lookup"><span data-stu-id="068b1-107">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="068b1-108">Örneğin, myAssembly derleme adına sahip bir derlemenin, myAssembly.exe ya da myAssembly.dll dosya adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="068b1-108">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
 <span data-ttu-id="068b1-109">Derlemeleri, yalnızca gerektiğinde genel bütünleştirilmiş kod önbelleğine yükleyerek paylaşmalısınız.</span><span class="sxs-lookup"><span data-stu-id="068b1-109">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="068b1-110">Derlemeyi paylaşmanız kesinlikle gerekli olmadığı sürece, genel bir kılavuz olarak, derleme bağımlılıklarını özel tutun ve derlemeleri uygulama dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="068b1-110">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="068b1-111">Ek olarak, derlemeleri COM ile birlikte çalışmaya veya yönetilmeyen koda erişilebilir yapmak için genel bütünleştirilmiş kod önbelleğine yüklemeniz gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="068b1-111">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
 <span data-ttu-id="068b1-112">Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek istemeniz için birkaç neden vardır:</span><span class="sxs-lookup"><span data-stu-id="068b1-112">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="068b1-113">Paylaşılan konum.</span><span class="sxs-lookup"><span data-stu-id="068b1-113">Shared location.</span></span>  
  
     <span data-ttu-id="068b1-114">Uygulamalar tarafından kullanılması gereken derlemeler genel bütünleştirilmiş kod önbelleğine konulabilir.</span><span class="sxs-lookup"><span data-stu-id="068b1-114">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="068b1-115">Örneğin, eğer tüm uygulamaların genel bütünleştirilmiş kod önbelleğinde bulunan bir derlemeyi kullanması gerekiyorsa bir sürüm ilkesi, başvuruları derlemeye yeniden yönlendiren Machine.config dosyasına eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="068b1-115">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
-   <span data-ttu-id="068b1-116">Dosya güvenliği.</span><span class="sxs-lookup"><span data-stu-id="068b1-116">File security.</span></span>  
  
     <span data-ttu-id="068b1-117">Yöneticiler, yazma ve yürütme erişimini denetlemek için systemroot dizinini genellikle bir Erişim Denetim Listesi (ACL) kullanarak korur.</span><span class="sxs-lookup"><span data-stu-id="068b1-117">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="068b1-118">Genel bütünleştirilmiş kod önbelleği systemroot dizininde yüklü olduğu için, bu dizinin ACL'sini devralır.</span><span class="sxs-lookup"><span data-stu-id="068b1-118">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="068b1-119">Yalnızca yönetici ayrıcalıklarına sahip kullanıcılar, Genel Derleme Önbelleği'nden dosyalarını silmek için izin önerilir.</span><span class="sxs-lookup"><span data-stu-id="068b1-119">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
-   <span data-ttu-id="068b1-120">Yan yana sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="068b1-120">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="068b1-121">Genel bütünleştirilmiş kod önbelleğinde derlemelerin aynı ada ancak farklı sürüm bilgisine sahip olan birden çok kopyası tutulabilir.</span><span class="sxs-lookup"><span data-stu-id="068b1-121">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="068b1-122">Ek arama konumu.</span><span class="sxs-lookup"><span data-stu-id="068b1-122">Additional search location.</span></span>  
  
     <span data-ttu-id="068b1-123">Ortak dil çalışma zamanı, bir yapılandırma dosyasındaki kod temeli bilgisini algılamadan veya kullanmadan önce, derleme isteğiyle eşleşen bir derleme için genel bütünleştirilmiş kod önbelleğini kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="068b1-123">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="068b1-124">Bir derlemeyi genel bütünleştirilmiş kod önbelleğine açıkça yüklemek istemeyeceğiniz senaryolar olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="068b1-124">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="068b1-125">Eğer bir uygulamayı oluşturan derlemelerden birini genel bütünleştirilmiş kod önbelleğine yerleştirirseniz, uygulama dizinini kopyalamak için XCOPY'i kullanarak uygulamayı artık çoğaltamaz veya yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="068b1-125">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="068b1-126">Bu durumda, derlemeyi de genel bütünleştirilmiş kod önbelleğine taşımanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="068b1-126">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="068b1-127">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="068b1-127">In This Section</span></span>  
 [<span data-ttu-id="068b1-128">Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme</span><span class="sxs-lookup"><span data-stu-id="068b1-128">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 <span data-ttu-id="068b1-129">Bir derlemeyi genel bütünleştirilmiş kod belleğine yükleme yöntemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="068b1-129">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
 [<span data-ttu-id="068b1-130">Nasıl yapılır: Genel Derleme Önbelleğinin İçeriğini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="068b1-130">How to: View the Contents of the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 <span data-ttu-id="068b1-131">Nasıl kullanılacağı açıklanmaktadır [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) genel derleme önbelleğinin içeriğini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="068b1-131">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="068b1-132">Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğinden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="068b1-132">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 <span data-ttu-id="068b1-133">Nasıl kullanılacağı açıklanmaktadır [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) bir derlemeyi Genel Derleme Önbelleği'nden kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="068b1-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
 [<span data-ttu-id="068b1-134">Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="068b1-134">Using Serviced Components with the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 <span data-ttu-id="068b1-135">Hizmet verilen bileşenlerin (yönetilen COM+ bileşenleri) neden genel bütünleştirilmiş kod önbelleğine yerleştirilmesi gerektiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="068b1-135">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="068b1-136">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="068b1-136">Related Sections</span></span>  
 [<span data-ttu-id="068b1-137">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="068b1-137">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="068b1-138">Derleme oluşturmaya genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="068b1-138">Provides an overview of creating assemblies.</span></span>  
  
 [<span data-ttu-id="068b1-139">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="068b1-139">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 <span data-ttu-id="068b1-140">Genel bütünleştirilmiş kod önbelleğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="068b1-140">Describes the global assembly cache.</span></span>  
  
 [<span data-ttu-id="068b1-141">Nasıl yapılır: Bütünleştirilmiş Kod İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="068b1-141">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="068b1-142">Nasıl kullanılacağı açıklanmaktadır [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bir derlemede Microsoft Ara dili (MSIL) bilgilerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="068b1-142">Explains how to use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
 [<span data-ttu-id="068b1-143">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="068b1-143">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="068b1-144">Ortak dil çalışma zamanının uygulamanızı oluşturan derlemeleri nasıl konumlandırdığını ve yüklediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="068b1-144">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
 [<span data-ttu-id="068b1-145">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="068b1-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="068b1-146">Yönetilen uygulamaların yapı taşları olan derlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="068b1-146">Describes assemblies, the building blocks of managed applications.</span></span>
