---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 4578b708b10e93a7f5def5b9dc040eeb646bdc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130242"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="576ae-102">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="576ae-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="576ae-103">Bu bölümde, bir derleyicinin veya aracın, çalışma zamanında meta verileri ve Microsoft ara dili 'ni (MSIL) yayabilmesini ve isteğe bağlı olarak diskte taşınabilir bir çalıştırılabilir (PE) dosyası oluşturmasını sağlayan <xref:System.Reflection.Emit> ad alanındaki bir yönetilen türler kümesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="576ae-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="576ae-104">Komut dosyası motorları ve derleyiciler, bu ad alanının birincil kullanıcılardır.</span><span class="sxs-lookup"><span data-stu-id="576ae-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="576ae-105">Bu bölümde, <xref:System.Reflection.Emit> ad alanı tarafından sunulan işlevselliğe yansıma yayma denir.</span><span class="sxs-lookup"><span data-stu-id="576ae-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="576ae-106">Yansıma yayma aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="576ae-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="576ae-107">Çalışma zamanında hafif Global Yöntemler tanımlayın, <xref:System.Reflection.Emit.DynamicMethod> sınıfını kullanarak bunları temsilciler kullanarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="576ae-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="576ae-108">Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırın ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="576ae-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="576ae-109">Çalışma zamanında derlemeleri tanımlayın, çalıştırın ve ardından bunları kaldırın ve çöp toplamanın kaynaklarını geri kazanmak için izin verin.</span><span class="sxs-lookup"><span data-stu-id="576ae-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="576ae-110">Çalışma zamanında yeni derlemelerde modüller tanımlayın ve ardından bunları diske kaydedip/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="576ae-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="576ae-111">Çalışma zamanında modüllerde türler tanımlayın, bu türlerin örneklerini oluşturun ve yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="576ae-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="576ae-112">Hata ayıklayıcıları ve kod profil oluşturucular gibi araçlar tarafından kullanılabilen tanımlı modüller için sembolik bilgiler tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="576ae-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="576ae-113"><xref:System.Reflection.Emit> ad alanındaki yönetilen türlere ek olarak, [meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="576ae-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="576ae-114">Yönetilen yansıma yayma, daha güçlü anlamsal hata denetimi ve meta verilerin yönetilmeyen bir soyutlama düzeyini yönetilmeyen meta veri arabirimlerine göre sağlar.</span><span class="sxs-lookup"><span data-stu-id="576ae-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="576ae-115">Meta veriler ve MSIL ile çalışmaya yönelik başka bir faydalı kaynak, yaygın olarak kullanılan dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CıL yönerge kümesi".</span><span class="sxs-lookup"><span data-stu-id="576ae-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="576ae-116">Belgeler, [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) ve [ecma Web sitesinde](https://go.microsoft.com/fwlink/?LinkId=116487)çevrimiçi olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="576ae-116">The documentation is available online on [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](https://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="576ae-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="576ae-117">In This Section</span></span>
  
[<span data-ttu-id="576ae-118">Yansıma Yaymadaki güvenlik sorunları</span><span class="sxs-lookup"><span data-stu-id="576ae-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="576ae-119">Yansıma yayma kullanarak dinamik derlemeler oluşturmayla ilgili güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="576ae-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="576ae-120">[Nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="576ae-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="576ae-121">Basit bir dinamik yöntemin ve bir sınıfın örneğine bağlantılı dinamik yöntemin nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="576ae-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="576ae-122">[Nasıl yapılır: yansıma yayma ile genel tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="576ae-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="576ae-123">İki tür parametresiyle basit bir genel türün nasıl oluşturulduğunu, tür parametrelerine sınıf, arabirim ve özel kısıtlamaları uygulamayı ve sınıfın tür parametrelerini parametre türleri ve dönüş türleri olarak kullanan üyelerin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="576ae-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="576ae-124">[Nasıl yapılır: yansıma yayma ile genel bir yöntem tanımlama](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="576ae-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="576ae-125">Basit bir genel yöntemin nasıl oluşturulacağını, yayalınacağını ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="576ae-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="576ae-126">[Dinamik tür oluşturma Için toplanabilir derlemeler](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="576ae-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="576ae-127">, Oluşturuldukları uygulama etki alanını kaldırmadan kaldırılabilen dinamik derlemeler olan toplanabilir derlemeleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="576ae-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="576ae-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="576ae-128">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="576ae-129">Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL Yönerge kodlarını kataloglandırır.</span><span class="sxs-lookup"><span data-stu-id="576ae-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="576ae-130">Dinamik yöntemleri, derlemeleri ve türleri yayma için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="576ae-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="576ae-131">Yönetilen yansıma ve yansıma yayma türlerini temsil eden ve bu teknolojilerin kullanımına yönelik anahtar olan <xref:System.Type> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="576ae-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="576ae-132">Meta verileri ve yönetilen kodu araştırmak için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="576ae-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="576ae-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="576ae-133">Related Sections</span></span>  

[<span data-ttu-id="576ae-134">Yansıma</span><span class="sxs-lookup"><span data-stu-id="576ae-134">Reflection</span></span>](reflection.md)  
<span data-ttu-id="576ae-135">Meta verilerin ve yönetilen kodun nasıl araştırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="576ae-135">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="576ae-136">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="576ae-136">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="576ae-137">.NET uygulamalarında derlemelere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="576ae-137">Provides an overview of assemblies in .NET implementations.</span></span>
