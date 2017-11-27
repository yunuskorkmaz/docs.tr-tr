---
title: Derleme Bildirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df64129a0ae15b5bad387a62ca60bb4b1b92f7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-manifest"></a><span data-ttu-id="fe0e5-102">Derleme Bildirimi</span><span class="sxs-lookup"><span data-stu-id="fe0e5-102">Assembly Manifest</span></span>
<span data-ttu-id="fe0e5-103">Statik veya dinamik tüm derlemeler, derleme içindeki öğelerin birbirleriyle nasıl ilişkili olduğunu açıklayan bir veri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-103">Every assembly, whether static or dynamic, contains a collection of data that describes how the elements in the assembly relate to each other.</span></span> <span data-ttu-id="fe0e5-104">Derleme bildirimi, bu derleme metaverilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-104">The assembly manifest contains this assembly metadata.</span></span> <span data-ttu-id="fe0e5-105">Bir derleme bildirimi, derlemenin sürüm gereksinimlerini ve güvenlik kimliğini belirtmek, derlemenin kapsamını tanımlamak ve kaynaklara, sınıflara yapılan atıfları çözmek için gereken tüm metaverileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-105">An assembly manifest contains all the metadata needed to specify the assembly's version requirements and security identity, and all metadata needed to define the scope of the assembly and resolve references to resources and classes.</span></span> <span data-ttu-id="fe0e5-106">Derleme bildirimi, Microsoft ara dili (MSIL) koduyla bir PE dosyası halinde (bir .exe veya .dll) veya yalnızca derleme bildirimi bilgilerini içeren tek bir PE dosyasında tutulabilir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-106">The assembly manifest can be stored in either a PE file (an .exe or .dll) with Microsoft intermediate language (MSIL) code or in a standalone PE file that contains only assembly manifest information.</span></span>  
  
 <span data-ttu-id="fe0e5-107">Aşağıdaki görselde, bildirimin saklanabileceği farklı şekilleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-107">The following illustration shows the different ways the manifest can be stored.</span></span>  
  
 <span data-ttu-id="fe0e5-108">![Tek bir &#45; dosya derleme](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span><span class="sxs-lookup"><span data-stu-id="fe0e5-108">![A single&#45;file assembly](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span></span>  
<span data-ttu-id="fe0e5-109">Derleme türleri</span><span class="sxs-lookup"><span data-stu-id="fe0e5-109">Types of assemblies</span></span>  
  
 <span data-ttu-id="fe0e5-110">İlişkili tek bir dosyaya sahip bir derlemede, tek dosyalı derleme oluşturmak amacıyla bildirim PE dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-110">For an assembly with one associated file, the manifest is incorporated into the PE file to form a single-file assembly.</span></span> <span data-ttu-id="fe0e5-111">Bağımsız bir bildirim dosyasına veya bildirim derlemesindeki PE dosyalarından birine ekli şekilde bir çoklu dosya derlemesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-111">You can create a multifile assembly with a standalone manifest file or with the manifest incorporated into one of the PE files in the assembly.</span></span>  
  
 <span data-ttu-id="fe0e5-112">Her derlemenin bildirimi, aşağıdaki işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="fe0e5-112">Each assembly's manifest performs the following functions:</span></span>  
  
-   <span data-ttu-id="fe0e5-113">Derlemeyi oluşturan dosyaları listeler.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-113">Enumerates the files that make up the assembly.</span></span>  
  
-   <span data-ttu-id="fe0e5-114">Derlemenin türlerine ve kaynaklarına yapılan atıfların, tanımlarını ve uygulamalarını içeren dosyalarla nasıl eşleştirildiğini yönetir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-114">Governs how references to the assembly's types and resources map to the files that contain their declarations and implementations.</span></span>  
  
-   <span data-ttu-id="fe0e5-115">Derlemenin bağımlı olduğu diğer derlemeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-115">Enumerates other assemblies on which the assembly depends.</span></span>  
  
-   <span data-ttu-id="fe0e5-116">Derlemenin tüketicileri ve derlemenin uygulama ayrıntıları arasında bir yöneltme düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-116">Provides a level of indirection between consumers of the assembly and the assembly's implementation details.</span></span>  
  
-   <span data-ttu-id="fe0e5-117">Derlemeyi kendini açıklayan hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-117">Renders the assembly self-describing.</span></span>  
  
## <a name="assembly-manifest-contents"></a><span data-ttu-id="fe0e5-118">Derleme Bildirimi İçerikleri</span><span class="sxs-lookup"><span data-stu-id="fe0e5-118">Assembly Manifest Contents</span></span>  
 <span data-ttu-id="fe0e5-119">Aşağıdaki tabloda, derleme bildiriminde bulunan bilgiler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-119">The following table shows the information contained in the assembly manifest.</span></span> <span data-ttu-id="fe0e5-120">İlk dört öğe—derlemenin adı, sürüm numarası, kültür ve tanımlayıcı ad bilgisi— derlemenin kimliğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-120">The first four items—the assembly name, version number, culture, and strong name information—make up the assembly's identity.</span></span>  
  
|<span data-ttu-id="fe0e5-121">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="fe0e5-121">Information</span></span>|<span data-ttu-id="fe0e5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe0e5-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="fe0e5-123">Derleme adı</span><span class="sxs-lookup"><span data-stu-id="fe0e5-123">Assembly name</span></span>|<span data-ttu-id="fe0e5-124">Derlemenin adını belirten bir metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-124">A text string specifying the assembly's name.</span></span>|  
|<span data-ttu-id="fe0e5-125">Sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="fe0e5-125">Version number</span></span>|<span data-ttu-id="fe0e5-126">Bir ana ve alt sürüm numarası ve bir düzeltme ve yapı numarası.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-126">A major and minor version number, and a revision and build number.</span></span> <span data-ttu-id="fe0e5-127">Ortak dil çalışma zamanı sürüm ilkesini uygulamak için bu numaraları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-127">The common language runtime uses these numbers to enforce version policy.</span></span>|  
|<span data-ttu-id="fe0e5-128">Kültür</span><span class="sxs-lookup"><span data-stu-id="fe0e5-128">Culture</span></span>|<span data-ttu-id="fe0e5-129">Derlemenin desteklediği kültür veya dil hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-129">Information on the culture or language the assembly supports.</span></span> <span data-ttu-id="fe0e5-130">Bu bilgiler, yalnızca bir derlemeyi kültüre veya dile özel bilgi içeren bir uydu derleme olarak tanımlamak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-130">This information should be used only to designate an assembly as a satellite assembly containing culture- or language-specific information.</span></span> <span data-ttu-id="fe0e5-131">(Kültür bilgisine sahip bir derleme, otomatik olarak bir uydu derleme kabul edilir.)</span><span class="sxs-lookup"><span data-stu-id="fe0e5-131">(An assembly with culture information is automatically assumed to be a satellite assembly.)</span></span>|  
|<span data-ttu-id="fe0e5-132">Tanımlayıcı ad bilgisi</span><span class="sxs-lookup"><span data-stu-id="fe0e5-132">Strong name information</span></span>|<span data-ttu-id="fe0e5-133">Derlemeye tanımlayıcı ad verilmişse yayımcıdan gelen ortak anahtar.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-133">The public key from the publisher if the assembly has been given a strong name.</span></span>|  
|<span data-ttu-id="fe0e5-134">Derlemedeki tüm dosyaların listesi</span><span class="sxs-lookup"><span data-stu-id="fe0e5-134">List of all files in the assembly</span></span>|<span data-ttu-id="fe0e5-135">Derlemede bulunan her dosyayla bir dosya adının karması.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-135">A hash of each file contained in the assembly and a file name.</span></span> <span data-ttu-id="fe0e5-136">Derlemeyi oluşturan tüm dosyaların, derleme bildirimini içeren dosyayla aynı dizinde olması gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-136">Note that all files that make up the assembly must be in the same directory as the file containing the assembly manifest.</span></span>|  
|<span data-ttu-id="fe0e5-137">Tür başvuru bilgisi</span><span class="sxs-lookup"><span data-stu-id="fe0e5-137">Type reference information</span></span>|<span data-ttu-id="fe0e5-138">Çalışma zamanı tarafından bir tür başvurusu ile bildirimini ve uygulamasını içeren dosyanın eşleştirilmesi için kullanılan bilgiler.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-138">Information used by the runtime to map a type reference to the file that contains its declaration and implementation.</span></span> <span data-ttu-id="fe0e5-139">Bu, derlemeden dışarı aktarılan türler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-139">This is used for types that are exported from the assembly.</span></span>|  
|<span data-ttu-id="fe0e5-140">Atıfta bulunulan derlemeler hakkında bilgi</span><span class="sxs-lookup"><span data-stu-id="fe0e5-140">Information on referenced assemblies</span></span>|<span data-ttu-id="fe0e5-141">Derleme tarafından statik olarak atıfta bulunulan diğer derlemelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-141">A list of other assemblies that are statically referenced by the assembly.</span></span> <span data-ttu-id="fe0e5-142">Her başvuru, bağımlı derlemenin adını, derleme metaverilerini (sürüm, kültür, işletim sistemi vb.) ve, derleme tanımlayıcı ada sahipse, ortak anahtarı içerir.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-142">Each reference includes the dependent assembly's name, assembly metadata (version, culture, operating system, and so on), and public key, if the assembly is strong named.</span></span>|  
  
 <span data-ttu-id="fe0e5-143">Kodunuzda derleme öznitelikleri kullanarak derleme bildirimine bazı bilgiler ekleyebilir veya bazı bilgileri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-143">You can add or change some information in the assembly manifest by using assembly attributes in your code.</span></span> <span data-ttu-id="fe0e5-144">Ticari Marka, Telif Hakkı, Ürün, Şirket ve Bilgilendirme Sürümü dahil olmak üzere sürüm bilgilerini ve bilgilendirme özniteliklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-144">You can change version information and informational attributes, including Trademark, Copyright, Product, Company, and Informational Version.</span></span> <span data-ttu-id="fe0e5-145">Derleme özniteliklerinin tam bir listesi için bkz: [ayarı derleme özniteliklerinin](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fe0e5-145">For a complete list of assembly attributes, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0e5-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe0e5-146">See Also</span></span>  
 [<span data-ttu-id="fe0e5-147">Derleme içerikleri</span><span class="sxs-lookup"><span data-stu-id="fe0e5-147">Assembly Contents</span></span>](../../../docs/framework/app-domains/assembly-contents.md)  
 [<span data-ttu-id="fe0e5-148">Derleme sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe0e5-148">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="fe0e5-149">Uydu derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe0e5-149">Creating Satellite Assemblies</span></span>](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [<span data-ttu-id="fe0e5-150">Tanımlayıcı adlı derlemeler</span><span class="sxs-lookup"><span data-stu-id="fe0e5-150">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
