---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180536"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="87bb8-102">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="87bb8-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="87bb8-103">Bu bölümde, bir derleyicinin veya aracın, <xref:System.Reflection.Emit> çalışma zamanında meta verileri ve Microsoft ara dili 'NI (MSIL) yayabilmesini ve isteğe bağlı olarak diskte taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası oluşturmasını sağlayan ad alanındaki yönetilen türler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="87bb8-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="87bb8-104">Komut dosyası motorları ve derleyiciler, bu ad alanının birincil kullanıcılardır.</span><span class="sxs-lookup"><span data-stu-id="87bb8-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="87bb8-105">Bu bölümde, <xref:System.Reflection.Emit> ad alanı tarafından sunulan işlevselliğe yansıma yayma denir.</span><span class="sxs-lookup"><span data-stu-id="87bb8-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="87bb8-106">Yansıma yayma aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="87bb8-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="87bb8-107">Çalışma zamanında, <xref:System.Reflection.Emit.DynamicMethod> sınıfını kullanarak hafif Global Yöntemler tanımlayın ve temsilcileri kullanarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="87bb8-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="87bb8-108">Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırın ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="87bb8-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="87bb8-109">Çalışma zamanında derlemeleri tanımlayın, çalıştırın ve ardından bunları kaldırın ve çöp toplamanın kaynaklarını geri kazanmak için izin verin.</span><span class="sxs-lookup"><span data-stu-id="87bb8-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="87bb8-110">Çalışma zamanında yeni derlemelerde modüller tanımlayın ve ardından bunları diske kaydedip/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="87bb8-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="87bb8-111">Çalışma zamanında modüllerde türler tanımlayın, bu türlerin örneklerini oluşturun ve yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="87bb8-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="87bb8-112">Hata ayıklayıcıları ve kod profil oluşturucular gibi araçlar tarafından kullanılabilen tanımlı modüller için sembolik bilgiler tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="87bb8-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="87bb8-113"><xref:System.Reflection.Emit> Ad alanındaki yönetilen türlerin yanı sıra, [meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="87bb8-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="87bb8-114">Yönetilen yansıma yayma, daha güçlü anlamsal hata denetimi ve meta verilerin yönetilmeyen bir soyutlama düzeyini yönetilmeyen meta veri arabirimlerine göre sağlar.</span><span class="sxs-lookup"><span data-stu-id="87bb8-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="87bb8-115">Meta veriler ve MSIL ile çalışmaya yönelik başka bir faydalı kaynak, yaygın olarak kullanılan dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CıL yönerge kümesi".</span><span class="sxs-lookup"><span data-stu-id="87bb8-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="87bb8-116">Belgeler, [ecma Web sitesinde](https://www.ecma-international.org/publications/standards/Ecma-335.htm)çevrimiçi olarak sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87bb8-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87bb8-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="87bb8-117">In This Section</span></span>
  
[<span data-ttu-id="87bb8-118">Yansıma Yaymadaki güvenlik sorunları</span><span class="sxs-lookup"><span data-stu-id="87bb8-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="87bb8-119">Yansıma yayma kullanarak dinamik derlemeler oluşturmayla ilgili güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="87bb8-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="87bb8-120">[Nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md) Basit bir dinamik yöntemin ve bir sınıfın örneğine bağlantılı dinamik yöntemin nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="87bb8-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="87bb8-121">[Nasıl yapılır: yansıma yayma ile genel tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md) İki tür parametresiyle basit bir genel türün nasıl oluşturulduğunu, tür parametrelerine sınıf, arabirim ve özel kısıtlamaları uygulamayı ve sınıfın tür parametrelerini parametre türleri ve dönüş türleri olarak kullanan üyelerin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87bb8-121">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="87bb8-122">[Nasıl yapılır: yansıma yayma ile genel bir yöntem tanımlama](how-to-define-a-generic-method-with-reflection-emit.md) Basit bir genel yöntemin nasıl oluşturulacağını, yayalınacağını ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87bb8-122">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="87bb8-123">[Dinamik tür oluşturma Için toplanabilir derlemeler](collectible-assemblies.md) , Oluşturuldukları uygulama etki alanını kaldırmadan kaldırılabilen dinamik derlemeler olan toplanabilir derlemeleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="87bb8-123">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="87bb8-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="87bb8-124">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="87bb8-125">Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL Yönerge kodlarını kataloglandırır.</span><span class="sxs-lookup"><span data-stu-id="87bb8-125">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="87bb8-126">Dinamik yöntemleri, derlemeleri ve türleri yayma için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="87bb8-126">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="87bb8-127">Yönetilen yansıma <xref:System.Type> ve yansıma yayma türlerini temsil eden ve bu teknolojilerin kullanımına yönelik anahtar olan sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="87bb8-127">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="87bb8-128">Meta verileri ve yönetilen kodu araştırmak için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="87bb8-128">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="87bb8-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="87bb8-129">Related Sections</span></span>  

[<span data-ttu-id="87bb8-130">Yansıma</span><span class="sxs-lookup"><span data-stu-id="87bb8-130">Reflection</span></span>](reflection.md)  
<span data-ttu-id="87bb8-131">Meta verilerin ve yönetilen kodun nasıl araştırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="87bb8-131">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="87bb8-132">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="87bb8-132">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="87bb8-133">.NET uygulamalarında derlemelere genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="87bb8-133">Provides an overview of assemblies in .NET implementations.</span></span>
