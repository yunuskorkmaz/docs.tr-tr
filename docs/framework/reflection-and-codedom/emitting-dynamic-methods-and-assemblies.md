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
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="022d3-102">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="022d3-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="022d3-103">Bu bölümde, <xref:System.Reflection.Emit> ad alanında, derleyicinin veya aracın çalışma zamanında meta veri ve Microsoft ara dili (MSIL) yayarlar ve isteğe bağlı olarak diskte taşınabilir bir yürütülebilir (PE) dosya oluşturmasına olanak tanıyan yönetilen türler kümesi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="022d3-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="022d3-104">Komut dosyası motorları ve derleyiciler bu ad alanının birincil kullanıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="022d3-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="022d3-105">Bu bölümde, <xref:System.Reflection.Emit> ad alanı tarafından sağlanan işlevsellik yansıma yayan olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="022d3-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="022d3-106">Yansıma yayan aşağıdaki yetenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="022d3-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="022d3-107">Sınıfı kullanarak çalışma zamanında hafif <xref:System.Reflection.Emit.DynamicMethod> genel yöntemleri tanımlayın ve bunları temsilciler kullanarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="022d3-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="022d3-108">Derlemeleri çalışma zamanında tanımlayın ve çalıştırın ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="022d3-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="022d3-109">Derlemeleri çalışma zamanında tanımlayın, çalıştırın ve sonra boşaltın ve çöp toplamanın kaynaklarını geri almasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="022d3-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="022d3-110">Modülleri çalışma zamanında yeni derlemelerde tanımlayın ve ardından çalıştırın ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="022d3-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="022d3-111">Çalışma zamanında modüllerde türleri tanımlayın, bu tür örnekleri oluşturun ve yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="022d3-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="022d3-112">Hata ayıklayıcılar ve kod profilcileri gibi araçlar tarafından kullanılabilecek tanımlanmış modüller için sembolik bilgileri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="022d3-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="022d3-113">Ad alanında yönetilen türlere ek olarak, [Meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır. <xref:System.Reflection.Emit></span><span class="sxs-lookup"><span data-stu-id="022d3-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="022d3-114">Yönetilen yansıma, daha güçlü anlamsal hata denetimi ve yönetilmeyen meta veri arabirimlerinden daha yüksek bir soyutlama düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="022d3-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="022d3-115">Meta veri ve MSIL ile çalışmak için bir diğer yararlı kaynak ortak dil altyapısı (CLI) belgeleri, özellikle "Bölüm II: Meta veri tanımı ve semantik" ve "Bölüm III: CIL Öğretim Kümesi"dir.</span><span class="sxs-lookup"><span data-stu-id="022d3-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="022d3-116">Dokümantasyon [Ecma Web sitesinde](https://www.ecma-international.org/publications/standards/Ecma-335.htm)nağmeler online olarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="022d3-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="022d3-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="022d3-117">In This Section</span></span>
  
[<span data-ttu-id="022d3-118">Yansıma yayan güvenlik sorunları</span><span class="sxs-lookup"><span data-stu-id="022d3-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="022d3-119">Yansıma yonu kullanarak dinamik derlemeler oluşturmayla ilgili güvenlik sorunlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="022d3-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="022d3-120">[Nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md) Basit bir dinamik yöntemin ve sınıfın örneğine bağlı dinamik bir yöntemin nasıl yürütüleceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="022d3-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="022d3-121">[Nasıl yapılır: Yansıma yayıyla genel bir tür tanımla](how-to-define-a-generic-type-with-reflection-emit.md) İki tür parametresi içeren basit bir genel yazının nasıl oluşturulacağı, sınıf, arabirim ve özel kısıtlamaların tür parametrelerine nasıl uygulanacağı ve sınıfın tür parametrelerini parametre türleri ve iade türleri olarak kullanan üyelerin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="022d3-121">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="022d3-122">[Nasıl yapılsın: Yansıma yayan genel bir yöntem tanımlayın](how-to-define-a-generic-method-with-reflection-emit.md) Basit bir genel yöntemin nasıl oluşturulup, yarayıp nasıl başlatılsüreceğini ve çağırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="022d3-122">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="022d3-123">[Dinamik tip üretimi için tahsil montajları](collectible-assemblies.md) Oluşturuldukları uygulama etki alanını boşaltmadan boşaltılabilen dinamik derlemeler olan tahsil derlemeleri sunar.</span><span class="sxs-lookup"><span data-stu-id="022d3-123">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="022d3-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="022d3-124">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="022d3-125">Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL talimat kodlarını kataloglar.</span><span class="sxs-lookup"><span data-stu-id="022d3-125">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="022d3-126">Dinamik yöntemler, derlemeler ve türler yontmak için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="022d3-126">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="022d3-127">Yönetilen <xref:System.Type> yansıma ve yansıma yayan türleri temsil eden ve bu teknolojilerin kullanımının anahtarı olan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="022d3-127">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="022d3-128">Meta verileri ve yönetilen kodu keşfetmek için kullanılan yönetilen sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="022d3-128">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="022d3-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="022d3-129">Related Sections</span></span>  

[<span data-ttu-id="022d3-130">Yansıma</span><span class="sxs-lookup"><span data-stu-id="022d3-130">Reflection</span></span>](reflection.md)  
<span data-ttu-id="022d3-131">Meta verilerin ve yönetilen kodun nasıl araştırılabildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="022d3-131">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="022d3-132">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="022d3-132">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="022d3-133">.NET uygulamalarındaki derlemelere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="022d3-133">Provides an overview of assemblies in .NET implementations.</span></span>
