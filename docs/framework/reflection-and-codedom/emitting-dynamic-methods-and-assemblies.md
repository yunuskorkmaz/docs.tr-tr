---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0ed1d02fd40a94d4ae63deea3c09b04bfc9bd8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562378"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="f1877-102">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="f1877-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="f1877-103">Bu bölümde bir yönetilen türleri açıklar <xref:System.Reflection.Emit> izin derleyici veya aracının meta verileri ve Microsoft Ara dilini (MSIL) çalışma zamanında ve isteğe bağlı olarak göstermek için bir ad alanı diskte taşınabilir yürütülebilir (PE) dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1877-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="f1877-104">Komut dosyası motorları ve derleyiciler bu ad alanının birincil kullanıcıları olan.</span><span class="sxs-lookup"><span data-stu-id="f1877-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="f1877-105">Bu bölümde, işlevi tarafından sağlanan <xref:System.Reflection.Emit> ad alanı yansıma yayma adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f1877-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="f1877-106">Yansıma yayma aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="f1877-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="f1877-107">Basit genel definovat çalıştırmada kullandığınızdan <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve bunları yürütmek temsilcileri kullanma.</span><span class="sxs-lookup"><span data-stu-id="f1877-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="f1877-108">Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırmak ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f1877-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="f1877-109">Çalışma zamanında derlemeleri tanımlamak, bunları, bunları kaldırma ve kendi kaynaklarınızı geri kazanmanız çöp toplamaya olanak tanımak.</span><span class="sxs-lookup"><span data-stu-id="f1877-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="f1877-110">Modüller yeni derlemelerde çalışma zamanında tanımlayın ve ardından çalıştırın ve/veya diske kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f1877-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="f1877-111">Çalışma zamanında modüllerde türlerini tanımlayın, bu türlerin örneklerini oluşturmak ve kendi yöntemlerini çağırmak.</span><span class="sxs-lookup"><span data-stu-id="f1877-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="f1877-112">Hata ayıklayıcıları ve kod profil oluşturucuları gibi araçlar tarafından kullanılan tanımlanmış modüller için simgesel bilgiler tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f1877-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="f1877-113">Yönetilen türleri yanı sıra <xref:System.Reflection.Emit> ad alanı, açıklanan yönetilmeyen meta veri arabirimleri vardır [meta veri arabirimleri](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="f1877-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="f1877-114">Yönetilen yansıma yayma daha güçlü anlamsal hata denetimi ve daha yüksek düzeyde soyutlama meta verilerin daha yönetilmeyen meta veri arabirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1877-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="f1877-115">MSIL ve meta verileri ile çalışmak için yararlı başka bir kaynak ortak dil altyapısı (CLI), "özellikle Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CIL yönerge kümesi" belgelerdir.</span><span class="sxs-lookup"><span data-stu-id="f1877-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="f1877-116">Belgeler hakkında çevrimiçi kullanılabilir [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) ve [Ecma Web sitesi](https://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="f1877-116">The documentation is available online on [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](https://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1877-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f1877-117">In This Section</span></span>
  
[<span data-ttu-id="f1877-118">Yaymadaki güvenlik sorunları yansıma</span><span class="sxs-lookup"><span data-stu-id="f1877-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="f1877-119">Güvenlik yaymadaki yansıma kullanarak dinamik derlemeler oluşturma işlemiyle ilgili sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="f1877-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="f1877-120">[Nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="f1877-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="f1877-121">Basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı olarak dinamik bir yöntem yürütme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1877-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="f1877-122">[Nasıl yapılır: yansıma ile genel tür tanımlama yayma](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="f1877-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="f1877-123">İki tür parametreleri ile basit bir genel tür oluşturma için tür parametreleri, sınıf, arabirim ve özel kısıtlamalar uygulamak nasıl ve sınıf türü parametreler parametre türleri olarak kullanın ve dönüş türleri üye oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1877-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="f1877-124">[Nasıl yapılır: yansıma ile genel yöntem tanımlama yayma](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="f1877-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="f1877-125">Basit bir genel yöntem çağırma oluşturun ve yayma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1877-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="f1877-126">[Dinamik tür oluşturma için toplanabilir derlemeler](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="f1877-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="f1877-127">Oluşturulmuş olan uygulama etki alanını kaldırmadan kaldırılabilip kaldırılamayacağını dinamik derlemeler toplanabilir derlemeler tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f1877-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="f1877-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f1877-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="f1877-129">Metot gövdeleri oluşturmak için kullanabileceğiniz MSIL yönergesi kodları kataloglar.</span><span class="sxs-lookup"><span data-stu-id="f1877-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="f1877-130">Türleri dinamik yöntemleri ve derlemeleri Yayma almak için kullanılan yönetilen sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="f1877-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="f1877-131">Açıklar <xref:System.Type> türleri temsil eden sınıf yönetilen yansıma ve yansıma yayma ve bu teknolojilerin kullanımını anahtarına olduğu.</span><span class="sxs-lookup"><span data-stu-id="f1877-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="f1877-132">Meta veriler ve yönetilen kod keşfetmek için kullanılan yönetilen sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="f1877-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f1877-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f1877-133">Related Sections</span></span>  
 [<span data-ttu-id="f1877-134">Yansıma</span><span class="sxs-lookup"><span data-stu-id="f1877-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="f1877-135">Meta veriler ve yönetilen kod keşfedin açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1877-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="f1877-136">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="f1877-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="f1877-137">Derlemeler .NET uygulamalarında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1877-137">Provides an overview of assemblies in .NET implementations.</span></span>
