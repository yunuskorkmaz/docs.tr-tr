---
title: Derlemelerle Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921427"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="c8551-102">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="c8551-102">Programming with Assemblies</span></span>
<span data-ttu-id="c8551-103">Derlemeler .NET Framework yapı taşlarıdır; temel dağıtım, sürüm denetimi, yeniden kullanım, etkinleştirme kapsamı ve güvenlik izinleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8551-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="c8551-104">Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar.</span><span class="sxs-lookup"><span data-stu-id="c8551-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="c8551-105">Birlikte çalışacak ve mantıksal bir işlevsellik birimi oluşturacak bir tür ve kaynak koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="c8551-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="c8551-106">Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.</span><span class="sxs-lookup"><span data-stu-id="c8551-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="c8551-107">Bu bölümde modüller oluşturma, modüllerden derlemeler oluşturma, bir anahtar çifti oluşturma ve bir derlemeyi tanımlayıcı adla imzalama ve genel bütünleştirilmiş kod önbelleğine bir derleme yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c8551-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="c8551-108">Ayrıca, bu bölümde, derleme bildirimi bilgilerini görüntülemek için [MSIL Disassembler (ıldadsm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ' nin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c8551-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8551-109">.NET Framework sürüm 2,0 ' den başlayarak, çalışma zamanı, yüklü olan çalışma zamanından daha yüksek bir sürüm numarasına sahip .NET Framework bir sürümle derlenen bir derlemeyi yüklemez.</span><span class="sxs-lookup"><span data-stu-id="c8551-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="c8551-110">Bu, sürüm numarasının büyük ve küçük bileşenlerinin birleşimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c8551-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8551-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c8551-111">In This Section</span></span>  
 [<span data-ttu-id="c8551-112">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8551-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="c8551-113">Tek dosyalı ve çoklu dosya Derlemeleriyle genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8551-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="c8551-114">Bütünleştirilmiş Kod Adları</span><span class="sxs-lookup"><span data-stu-id="c8551-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="c8551-115">Derleme adlandırmasına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8551-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="c8551-116">Nasıl yapılır: Bir derlemenin tam nitelikli adını belirleme</span><span class="sxs-lookup"><span data-stu-id="c8551-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="c8551-117">Bir derlemenin tam nitelikli adının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="c8551-118">Tam Güvende İntranet Uygulamalarını Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c8551-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="c8551-119">Bir intranet paylaşımında tam güvenle derlemeler için eski güvenlik ilkesinin nasıl belirtileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="c8551-120">Bütünleştirilmiş Kod Konumu</span><span class="sxs-lookup"><span data-stu-id="c8551-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="c8551-121">Derlemelerin nereye bulunacağı hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8551-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="c8551-122">Nasıl yapılır: Tek dosya derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8551-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="c8551-123">Tek dosya derlemesinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="c8551-124">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="c8551-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="c8551-125">Çok dosyalı derlemeler oluşturma nedenlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="c8551-126">Nasıl yapılır: Çoklu dosya derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8551-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="c8551-127">Çoklu dosya derlemesinin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="c8551-128">Bütünleştirilmiş Kod Özniteliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c8551-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="c8551-129">Derleme özniteliklerini ve bunların nasıl ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="c8551-130">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8551-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="c8551-131">Bir derlemeyi güçlü bir adla nasıl ve neden imzalayabileceğinizi açıklar ve nasıl yapılır konularını içerir.</span><span class="sxs-lookup"><span data-stu-id="c8551-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="c8551-132">Bütünleştirilmiş Kod İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="c8551-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="c8551-133">Bir derlemenin nasıl geciktirileneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="c8551-134">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="c8551-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="c8551-135">Derlemelerin nasıl ve neden genel derleme önbelleğine ekleneceğini ve nasıl yapılır konuları içerdiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="c8551-136">Nasıl yapılır: Derleme Içeriğini görüntüle</span><span class="sxs-lookup"><span data-stu-id="c8551-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="c8551-137">Derleme içeriğini görüntülemek için MSIL Disassembler (ıldadsm. exe) ' nin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="c8551-138">Ortak Dil Çalışma Zamanı Modülünde Tür İletme</span><span class="sxs-lookup"><span data-stu-id="c8551-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="c8551-139">Mevcut uygulamaları bozmadan bir türü farklı bir derlemeye taşımak için tür iletmenin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c8551-140">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c8551-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="c8551-141">Bir derlemeyi temsil eden .NET Framework sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c8551-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8551-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c8551-142">Related Sections</span></span>  
 [<span data-ttu-id="c8551-143">Nasıl yapılır: Bir derlemeden tür ve üye bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="c8551-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="c8551-144">Bir derlemeden program aracılığıyla tür ve diğer bilgilerin nasıl elde edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="c8551-145">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="c8551-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="c8551-146">Ortak dil çalışma zamanı derlemelerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8551-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="c8551-147">Bütünleştirilmiş Kod Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8551-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="c8551-148">Derleme bağlamaya ve <xref:System.Reflection.AssemblyVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> özniteliklerine ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8551-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="c8551-149">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c8551-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="c8551-150">Çalışma zamanının, bir bağlama isteğini yerine getirmek için hangi derlemeyi kullanacağınızı nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="c8551-151">Yansıma</span><span class="sxs-lookup"><span data-stu-id="c8551-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="c8551-152">Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8551-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
