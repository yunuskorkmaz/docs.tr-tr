---
title: "Dinamik Yöntemleri ve Derlemeleri Yayma"
ms.custom: 
ms.date: 08/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91b0cc4614834f2ad8f7b54d9364d484ca9a6990
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="54bce-102">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="54bce-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="54bce-103">Bu bölümde bir yönetilen türlerinde açıklar <xref:System.Reflection.Emit> derleyici veya meta veri ve Microsoft Ara dili (MSIL çalışma zamanında ve isteğe bağlı olarak) yaymak üzere aracı izin ad alanı oluşturmak disk üzerinde bir taşınabilir yürütülebilir (PE) dosyası.</span><span class="sxs-lookup"><span data-stu-id="54bce-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="54bce-104">Komut dosyası motorları ve derleyicileri bu ad alanı birincil kullanıcıları olan.</span><span class="sxs-lookup"><span data-stu-id="54bce-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="54bce-105">Bu bölümde, işlev tarafından sağlanan <xref:System.Reflection.Emit> ad alanı yansıma yayma adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="54bce-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="54bce-106">Yansıma yayma aşağıdaki yetenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="54bce-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="54bce-107">Basit genel yöntemler çalışma tanımlamak, kullanarak istediğiniz zaman <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve bunları yürütmek temsilcileri kullanma.</span><span class="sxs-lookup"><span data-stu-id="54bce-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="54bce-108">Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırmak ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="54bce-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="54bce-109">Çalışma zamanında derlemeleri tanımlamak, bunları ve ardından bunları kaldırma çalıştırıp kaynaklarını geri kazanmak atık toplama izin verin.</span><span class="sxs-lookup"><span data-stu-id="54bce-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="54bce-110">Modülleri çalışma zamanında yeni derlemelerde tanımlayın ve ardından çalıştırın ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="54bce-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="54bce-111">Modülleri çalışma zamanında türlerini tanımlayın, bu tür örnekleri oluşturmak ve kendi yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="54bce-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="54bce-112">Simgesel hata ayıklayıcıları ve kod profil oluşturucuları gibi araçları tarafından kullanılan tanımlı modülleri bilgilerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="54bce-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="54bce-113">Yönetilen türler yanı sıra <xref:System.Reflection.Emit> ad alanı, açıklanan yönetilmeyen meta veri arabirimleri vardır [meta veri arabirimleri](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerini.</span><span class="sxs-lookup"><span data-stu-id="54bce-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="54bce-114">Yönetilen yansıma yayma daha güçlü anlamsal hata denetimi ve yönetilmeyen meta veri arabirimleri soyutlama meta verilerin daha üst bir düzeyde sağlar.</span><span class="sxs-lookup"><span data-stu-id="54bce-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="54bce-115">MSIL ve meta verileri ile çalışmak için başka bir kullanışlı "özellikle Bölüm II: meta veri tanım ve semantik" ve "Bölüm III: CIL yönerge kümesi" ortak dil altyapısı (CLI) belgeleri kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="54bce-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="54bce-116">Belge üzerinde çevrimiçidir [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) ve [Ecma Web sitesi](http://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="54bce-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54bce-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="54bce-117">In This Section</span></span>
  
[<span data-ttu-id="54bce-118">Güvenlik sorunları yansıma yayma</span><span class="sxs-lookup"><span data-stu-id="54bce-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="54bce-119">Yansıma kullanarak dinamik derlemeleri oluşturulmasıyla ilgili sorunları yayma güvenlik açıklar.</span><span class="sxs-lookup"><span data-stu-id="54bce-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="54bce-120">[Nasıl yapılır: dinamik yöntemleri çalıştırma ve tanımlayın](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="54bce-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="54bce-121">Nasıl basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı dinamik yöntemi yürütüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="54bce-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="54bce-122">[Nasıl yapılır: yansıma ile genel tür tanımlama yayma](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="54bce-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="54bce-123">İki tür parametreleri ile basit bir genel tür oluşturma, tür parametreleri sınıfı, arabirimi ve özel kısıtlamalar uygulamak nasıl ve parametre türleri olarak sınıfının tür parametreleri kullanan ve dönüş türleri memers oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54bce-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create memers that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="54bce-124">[Nasıl yapılır: yansıma ile genel yöntem tanımlama yayma](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="54bce-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="54bce-125">Oluşturma, yayma ve basit bir genel yöntem çağırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="54bce-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="54bce-126">[Dinamik tür oluşturma için collectible derlemeler](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="54bce-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="54bce-127">Bunlar oluşturulduğu uygulama etki alanı kaldırılması olmadan kaldırılamıyor dinamik derlemeleri collectible derlemeler tanıtır.</span><span class="sxs-lookup"><span data-stu-id="54bce-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="54bce-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="54bce-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="54bce-129">Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL yönerge kodları kataloglar.</span><span class="sxs-lookup"><span data-stu-id="54bce-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="54bce-130">Dinamik yöntemleri, derlemeler ve türleri yaymak üzere kullanılan yönetilen sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="54bce-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="54bce-131">Açıklar <xref:System.Type> yönetilen yansıma türleri temsil eden sınıf ve yansıma yayma ve bu teknolojiler kullanımını anahtarına olduğu.</span><span class="sxs-lookup"><span data-stu-id="54bce-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="54bce-132">Meta veri ve yönetilen kod keşfetmek için kullanılan yönetilen sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="54bce-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="54bce-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="54bce-133">Related Sections</span></span>  
 [<span data-ttu-id="54bce-134">Yansıma</span><span class="sxs-lookup"><span data-stu-id="54bce-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="54bce-135">Meta veri ve yönetilen kod keşfetmek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54bce-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="54bce-136">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="54bce-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="54bce-137">.NET uygulamalarında derlemeleri genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="54bce-137">Provides an overview of assemblies in .NET implementations.</span></span>
