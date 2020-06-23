---
title: Uygulama Etki Alanları ve Derlemelerle Programlama
description: .NET 'teki uygulama etki alanları ve Derlemeleriyle programlamayı öğrenin. Bkz. nasıl yapılır konularına bağlantılar & uygulama etki alanları oluşturma hakkında örnekler & derlemeler.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903444"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="8b77c-104">Uygulama Etki Alanları ve Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="8b77c-104">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="8b77c-105">Microsoft Internet Explorer, ASP.NET ve Windows kabuğu gibi konaklar, ortak dil çalışma zamanını bir işleme yükler, bu işlemde bir [uygulama etki alanı](application-domains.md) oluşturur ve ardından .NET Framework bir uygulama çalıştırırken bu uygulama etki alanında Kullanıcı kodunu yükler ve yürütür.</span><span class="sxs-lookup"><span data-stu-id="8b77c-105">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="8b77c-106">Çoğu durumda, çalışma zamanı ana bilgisayarı bu görevleri gerçekleştirdiğinden, uygulama etki alanları oluşturma ve bunlara derleme yükleme konusunda endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8b77c-106">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="8b77c-107">Bununla birlikte, ortak dil çalışma zamanını barındıracak bir uygulama oluşturuyorsanız, programlı olarak kaldırmak istediğiniz araçları veya kodu oluşturun ya da bir yandan kaldırılabileceğiniz ve yeniden yüklenebilir olan takılabilir bileşenler oluşturun, kendi uygulama etki alanlarınızı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="8b77c-107">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="8b77c-108">Çalışma zamanı ana bilgisayarı oluşturmasanız bile, bu bölümde bu uygulama etki alanlarında yüklü uygulama etki alanları ve Derlemeleriyle çalışma hakkında önemli bilgiler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b77c-108">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b77c-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8b77c-109">In This Section</span></span>  

[<span data-ttu-id="8b77c-110">Uygulama Etki Alanları ve Derlemeler Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="8b77c-110">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="8b77c-111">Uygulama etki alanları ve Derlemeleriyle programlama için kavramsal belgelerde bulunan tüm nasıl yapılır konularına bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b77c-111">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="8b77c-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b77c-112">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="8b77c-113">Uygulama etki alanları oluşturma, yapılandırma ve kullanma örnekleri sunar.</span><span class="sxs-lookup"><span data-stu-id="8b77c-113">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="8b77c-114">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="8b77c-114">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="8b77c-115">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b77c-115">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b77c-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8b77c-116">Related Sections</span></span>  

[<span data-ttu-id="8b77c-117">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="8b77c-117">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="8b77c-118">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b77c-118">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="8b77c-119">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="8b77c-119">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="8b77c-120">Derlemeler üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b77c-120">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="8b77c-121">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="8b77c-121">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="8b77c-122">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b77c-122">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="8b77c-123">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="8b77c-123">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="8b77c-124">Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b77c-124">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
