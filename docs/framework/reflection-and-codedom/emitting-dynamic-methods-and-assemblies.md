---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
description: Bir derleyicinin veya aracın çalışma zamanında meta verileri ve MSIL kodunu yaymasına izin veren System. Reflection. yayma ad alanını kullanarak dinamik yöntemleri ve derlemeleri yayma.
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 76d2a83943d9df06cc66cf86c6869f18fac2a12c
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475053"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="d8314-103">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="d8314-103">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="d8314-104">Bu bölümde, <xref:System.Reflection.Emit> bir derleyicinin veya aracın, çalışma zamanında meta verileri ve Microsoft ara dili 'ni (MSIL) yayabilmesini ve isteğe bağlı olarak diskte taşınabilir bir çalıştırılabilir (PE) dosyası oluşturmasını sağlayan ad alanındaki yönetilen türler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d8314-104">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="d8314-105">Komut dosyası motorları ve derleyiciler, bu ad alanının birincil kullanıcılardır.</span><span class="sxs-lookup"><span data-stu-id="d8314-105">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="d8314-106">Bu bölümde, ad alanı tarafından sunulan işlevselliğe <xref:System.Reflection.Emit> yansıma yayma denir.</span><span class="sxs-lookup"><span data-stu-id="d8314-106">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="d8314-107">Yansıma yayma aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="d8314-107">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="d8314-108">Çalışma zamanında, sınıfını kullanarak hafif Global Yöntemler tanımlayın <xref:System.Reflection.Emit.DynamicMethod> ve temsilcileri kullanarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="d8314-108">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="d8314-109">Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırın ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d8314-109">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="d8314-110">Çalışma zamanında derlemeleri tanımlayın, çalıştırın ve ardından bunları kaldırın ve çöp toplamanın kaynaklarını geri kazanmak için izin verin.</span><span class="sxs-lookup"><span data-stu-id="d8314-110">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="d8314-111">Çalışma zamanında yeni derlemelerde modüller tanımlayın ve ardından bunları diske kaydedip/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d8314-111">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="d8314-112">Çalışma zamanında modüllerde türler tanımlayın, bu türlerin örneklerini oluşturun ve yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d8314-112">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="d8314-113">Hata ayıklayıcıları ve kod profil oluşturucular gibi araçlar tarafından kullanılabilen tanımlı modüller için sembolik bilgiler tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d8314-113">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="d8314-114">Ad alanındaki yönetilen türlerin yanı sıra <xref:System.Reflection.Emit> , [meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="d8314-114">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="d8314-115">Yönetilen yansıma yayma, daha güçlü anlamsal hata denetimi ve meta verilerin yönetilmeyen bir soyutlama düzeyini yönetilmeyen meta veri arabirimlerine göre sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8314-115">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="d8314-116">Meta veriler ve MSIL ile çalışmaya yönelik başka bir faydalı kaynak, yaygın olarak kullanılan dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CıL yönerge kümesi".</span><span class="sxs-lookup"><span data-stu-id="d8314-116">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="d8314-117">Belgeler, [ecma Web sitesinde](https://www.ecma-international.org/publications/standards/Ecma-335.htm)çevrimiçi olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8314-117">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8314-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d8314-118">In This Section</span></span>
  
[<span data-ttu-id="d8314-119">Yansıma Yaymadaki güvenlik sorunları</span><span class="sxs-lookup"><span data-stu-id="d8314-119">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="d8314-120">Yansıma yayma kullanarak dinamik derlemeler oluşturmayla ilgili güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8314-120">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="d8314-121">[Nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md) Basit bir dinamik yöntemin ve bir sınıfın örneğine bağlantılı dinamik yöntemin nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8314-121">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="d8314-122">[Nasıl yapılır: yansıma yayma ile genel tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md) İki tür parametresiyle basit bir genel türün nasıl oluşturulduğunu, tür parametrelerine sınıf, arabirim ve özel kısıtlamaları uygulamayı ve sınıfın tür parametrelerini parametre türleri ve dönüş türleri olarak kullanan üyelerin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8314-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="d8314-123">[Nasıl yapılır: yansıma yayma ile genel bir yöntem tanımlama](how-to-define-a-generic-method-with-reflection-emit.md) Basit bir genel yöntemin nasıl oluşturulacağını, yayalınacağını ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8314-123">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="d8314-124">[Dinamik tür oluşturma Için toplanabilir derlemeler](collectible-assemblies.md) , Oluşturuldukları uygulama etki alanını kaldırmadan kaldırılabilen dinamik derlemeler olan toplanabilir derlemeleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="d8314-124">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="d8314-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d8314-125">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="d8314-126">Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL Yönerge kodlarını kataloglandırır.</span><span class="sxs-lookup"><span data-stu-id="d8314-126">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="d8314-127">Dinamik yöntemleri, derlemeleri ve türleri yayma için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="d8314-127">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="d8314-128"><xref:System.Type>Yönetilen yansıma ve yansıma yayma türlerini temsil eden ve bu teknolojilerin kullanımına yönelik anahtar olan sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8314-128">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="d8314-129">Meta verileri ve yönetilen kodu araştırmak için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="d8314-129">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8314-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d8314-130">Related Sections</span></span>  

[<span data-ttu-id="d8314-131">Yansıma</span><span class="sxs-lookup"><span data-stu-id="d8314-131">Reflection</span></span>](reflection.md)  
<span data-ttu-id="d8314-132">Meta verilerin ve yönetilen kodun nasıl araştırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8314-132">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="d8314-133">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="d8314-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="d8314-134">.NET uygulamalarında derlemelere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8314-134">Provides an overview of assemblies in .NET implementations.</span></span>
