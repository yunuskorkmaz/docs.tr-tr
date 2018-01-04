---
title: Derlemelerle Programlama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46cc7d1be867ff94ca25d0d6ffaaf46a6dc9514b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="7654e-102">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="7654e-102">Programming with Assemblies</span></span>
<span data-ttu-id="7654e-103">Derlemeler, .NET Framework'ün yapı taşlarıdır; Bunlar, dağıtım, sürüm denetimi, yeniden, etkinleştirme kapsamı ve güvenlik izinleri temel birimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7654e-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="7654e-104">Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar.</span><span class="sxs-lookup"><span data-stu-id="7654e-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="7654e-105">Türleri ve birlikte çalışır ve işlevlerin bir mantıksal birim oluşturmak için yerleşik kaynakların bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="7654e-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="7654e-106">Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.</span><span class="sxs-lookup"><span data-stu-id="7654e-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="7654e-107">Bu bölümde, modülleri oluşturma, modüllerden derlemeleri oluşturma, bir anahtar çifti oluşturma ve bir derlemeyi tanımlayıcı adla imzalama ve bir derlemeyi genel derleme önbelleğine yükleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="7654e-108">Ayrıca, bu bölümde nasıl kullanılacağını açıklar [MSIL ayrıştırıcı (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derleme bildirimi bilgilerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="7654e-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7654e-109">.NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklenen çalışma zamanı'den daha yüksek bir sürüm numarası .NET Framework sürümü için derlenmiş bir derlemeyi yüklemez.</span><span class="sxs-lookup"><span data-stu-id="7654e-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="7654e-110">Bu sürüm numarası birincil ve ikincil bileşenlerinin birleşimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7654e-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7654e-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7654e-111">In This Section</span></span>  
 [<span data-ttu-id="7654e-112">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7654e-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="7654e-113">Tek dosya ve birden çok dosya derlemeleri genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7654e-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="7654e-114">Bütünleştirilmiş Kod Adları</span><span class="sxs-lookup"><span data-stu-id="7654e-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="7654e-115">Adlandırma derleme genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7654e-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="7654e-116">Nasıl yapılır: Bir Bütünleştirilmiş Kodun Tam Adını Belirleme</span><span class="sxs-lookup"><span data-stu-id="7654e-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="7654e-117">Derleme tam olarak nitelenmiş adını belirlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="7654e-118">Tam Güvende İntranet Uygulamalarını Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7654e-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="7654e-119">Bir intranet paylaşımında tam güven derlemeler için eski güvenlik ilkesini belirtmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="7654e-120">Bütünleştirilmiş Kod Konumu</span><span class="sxs-lookup"><span data-stu-id="7654e-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="7654e-121">Derlemeleri yerleştireceğinizi genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7654e-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="7654e-122">Nasıl yapılır: Tek Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="7654e-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="7654e-123">Tek Dosyalı derleme oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="7654e-124">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="7654e-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="7654e-125">Birden çok dosya derlemeleri oluşturma nedenleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7654e-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="7654e-126">Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="7654e-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="7654e-127">Birden fazla dosya derlemesi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="7654e-128">Bütünleştirilmiş Kod Özniteliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="7654e-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="7654e-129">Derleme özniteliklerinin ve bunları nasıl ayarlayacağınız açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7654e-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="7654e-130">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="7654e-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="7654e-131">Neden ve nasıl bir derlemeyi tanımlayıcı adla oturum açıklar ve nasıl yapılır konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="7654e-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="7654e-132">Bütünleştirilmiş Kod İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="7654e-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="7654e-133">Açıklar nasıl geciktirin bütünleştirilmiş yapılır.</span><span class="sxs-lookup"><span data-stu-id="7654e-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="7654e-134">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="7654e-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="7654e-135">Neden ve nasıl derlemeleri genel derleme önbelleğine ekleme açıklar ve nasıl yapılır konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="7654e-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="7654e-136">Nasıl yapılır: Bütünleştirilmiş Kod İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7654e-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="7654e-137">MSIL ayrıştırıcı (Ildasm.exe) derleme içeriğini görüntülemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="7654e-138">Ortak Dil Çalışma Zamanı Modülünde Tür İletme</span><span class="sxs-lookup"><span data-stu-id="7654e-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="7654e-139">Tür iletme uygulamalarınız bozmadan bir türü farklı bir derlemeye taşımak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7654e-140">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7654e-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="7654e-141">Bir derlemeyi temsil eden .NET Framework sınıf.</span><span class="sxs-lookup"><span data-stu-id="7654e-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7654e-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7654e-142">Related Sections</span></span>  
 [<span data-ttu-id="7654e-143">Nasıl yapılır: Bir Bütünleştirilmiş Koddan Tür ve Üye Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="7654e-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="7654e-144">Program aracılığıyla bir derlemeden tür ve diğer bilgileri elde etmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="7654e-145">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="7654e-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="7654e-146">Kavramsal genel bakış ortak dil çalışma zamanı derlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7654e-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="7654e-147">Bütünleştirilmiş Kod Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7654e-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="7654e-148">Derleme bağlama'nin ve bir genel bakış sunulmaktadır <xref:System.Reflection.AssemblyVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="7654e-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="7654e-149">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="7654e-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="7654e-150">Çalışma zamanı bağlama isteği yerine getirmek için kullanılacak hangi derleme nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7654e-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="7654e-151">Yansıma</span><span class="sxs-lookup"><span data-stu-id="7654e-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="7654e-152">Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="7654e-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
