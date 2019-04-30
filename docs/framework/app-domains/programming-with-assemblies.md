---
title: Derlemelerle Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a20a2e678c10157fed7da6f5de9f3ffee0c9ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705551"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="03d34-102">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="03d34-102">Programming with Assemblies</span></span>
<span data-ttu-id="03d34-103">Derlemeler .NET Framework'ün yapı taşlarıdır; Bunlar, dağıtım, sürüm denetimi, yeniden kullanma, aktivasyon kapsamı ve güvenlik izinleri temel birimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="03d34-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="03d34-104">Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar.</span><span class="sxs-lookup"><span data-stu-id="03d34-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="03d34-105">Türleri ve birlikte çalışan ve mantıksal bir işlevsellik birimi oluşturacak biçimde oluşturulan kaynakların bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="03d34-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="03d34-106">Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.</span><span class="sxs-lookup"><span data-stu-id="03d34-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="03d34-107">Bu bölümde, modülleri oluşturabilir, modüllerden bütünleştirilmiş kodları oluşturma, bir anahtar çifti oluşturma ve derlemeyi bir katı adla imzalamak ve bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="03d34-108">Ayrıca, bu bölümde nasıl kullanılacağını açıklar [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derleme bildirimi bilgilerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="03d34-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03d34-109">.NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklü çalışma zamanı daha yüksek bir sürüm numarasına sahip .NET Framework sürümü ile derlenen bütünleştirilmiş yüklemez.</span><span class="sxs-lookup"><span data-stu-id="03d34-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="03d34-110">Bu sürüm numarasının büyük ve küçük bileşenleri birleşimi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="03d34-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03d34-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="03d34-111">In This Section</span></span>  
 [<span data-ttu-id="03d34-112">Bütünleştirilmiş Kodlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="03d34-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="03d34-113">Tek dosya ve çok dosyalı derlemeler genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d34-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="03d34-114">Bütünleştirilmiş Kod Adları</span><span class="sxs-lookup"><span data-stu-id="03d34-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="03d34-115">Derleme adlandırma genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d34-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="03d34-116">Nasıl yapılır: Bir derlemenin tam olarak nitelenmiş adını belirleme</span><span class="sxs-lookup"><span data-stu-id="03d34-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="03d34-117">Bir derlemenin tam adını belirlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="03d34-118">Tam Güvende İntranet Uygulamalarını Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="03d34-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="03d34-119">Bir intranet paylaşımında tam güven derlemeleri için eski güvenlik ilkesini belirtin açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="03d34-120">Bütünleştirilmiş Kod Konumu</span><span class="sxs-lookup"><span data-stu-id="03d34-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="03d34-121">Derlemeleri nerede genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d34-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="03d34-122">Nasıl yapılır: Tek Dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="03d34-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="03d34-123">Tek dosyalı bir derlemenin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="03d34-124">Çok Dosyalı Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="03d34-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="03d34-125">Birden çok dosya derlemeleri oluşturmak için nedenleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03d34-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="03d34-126">Nasıl yapılır: Bir çoklu dosya derlemesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="03d34-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="03d34-127">Çok dosyalı bir derlemenin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="03d34-128">Bütünleştirilmiş Kod Özniteliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="03d34-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="03d34-129">Derleme özniteliklerinin ve bunların nasıl ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="03d34-130">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="03d34-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="03d34-131">Neden ve nasıl bir derlemeyi katı bir adla imzalamak açıklar ve nasıl yapılır konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="03d34-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="03d34-132">Bütünleştirilmiş Kod İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="03d34-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="03d34-133">Açıklayan nasıl bir derlemeyi Gecikmeli imzalayın.</span><span class="sxs-lookup"><span data-stu-id="03d34-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="03d34-134">Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="03d34-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="03d34-135">Neden ve nasıl derlemeleri genel derleme önbelleğine ekleme açıklar ve nasıl yapılır konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="03d34-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="03d34-136">Nasıl yapılır: Derleme içeriği görüntüle</span><span class="sxs-lookup"><span data-stu-id="03d34-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="03d34-137">Derleme içerikleri görüntülemek için MSIL Disassembler (Ildasm.exe) kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="03d34-138">Ortak Dil Çalışma Zamanı Modülünde Tür İletme</span><span class="sxs-lookup"><span data-stu-id="03d34-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="03d34-139">Tür iletme mevcut uygulamaları bozmadan farklı bir derlemeye bir tür taşımak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="03d34-140">Başvuru</span><span class="sxs-lookup"><span data-stu-id="03d34-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="03d34-141">.NET Framework sınıf bir bütünleştirilmiş kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="03d34-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="03d34-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="03d34-142">Related Sections</span></span>  
 [<span data-ttu-id="03d34-143">Nasıl yapılır: Derlemeden tür ve üye bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="03d34-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="03d34-144">Program aracılığıyla bir derlemeden tür ve diğer bilgileri alma açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="03d34-145">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="03d34-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="03d34-146">Kavramsal genel bakış ortak dil çalışma zamanı derlemeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d34-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="03d34-147">Bütünleştirilmiş Kod Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="03d34-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="03d34-148">Derleme bağlama'nin ve bir genel bakış sağlar <xref:System.Reflection.AssemblyVersionAttribute> ve <xref:System.Reflection.AssemblyInformationalVersionAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="03d34-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="03d34-149">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="03d34-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="03d34-150">Çalışma zamanının hangi derleme bağlama isteğini yerine getirmek için kullanılacak etiketleneceğini nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="03d34-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="03d34-151">Yansıma</span><span class="sxs-lookup"><span data-stu-id="03d34-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="03d34-152">Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="03d34-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
