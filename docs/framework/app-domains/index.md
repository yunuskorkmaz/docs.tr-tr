---
title: "Uygulama Etki Alanları ve Derlemelerle Programlama"
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
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6dcf8e4c9bf2401309b1d80d2306bd619b96460d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="47558-102">Uygulama Etki Alanları ve Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="47558-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="47558-103">Microsoft Internet Explorer, ASP.NET ve Windows Kabuk yük ortak dil çalışma zamanı bir işlemine gibi konakları Oluştur bir [uygulama etki alanı](../../../docs/framework/app-domains/application-domains.md) söz işlemek ve ardından yükleme ve o uygulama etki alanında kullanıcı kodu yürütme .NET Framework uygulama çalışırken.</span><span class="sxs-lookup"><span data-stu-id="47558-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="47558-104">Çoğu durumda, uygulama etki alanları oluşturma ve bunların içine çalışma zamanı ana bilgisayarı bu görevleri gerçekleştirdiğinden derlemeleri yükleme hakkında endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="47558-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="47558-105">Ortak dil çalışma zamanı barındıracak bir uygulama araçlar veya programlama yoluyla kaldırmak istediğiniz kod oluşturma veya kaldırıldığında ve yeniden takılabilir bileşenler anında oluşturma oluşturuyorsanız, ancak siz kendi oluşturacağınız uygulama etki alanları.</span><span class="sxs-lookup"><span data-stu-id="47558-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="47558-106">Bir çalışma zamanı ana oluşturmadığınızı olsa bile, bu bölümde uygulama etki alanları ve bu uygulama etki alanlarında yüklenen derlemeler ile çalışma konusunda önemli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="47558-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47558-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="47558-107">In This Section</span></span>  
 [<span data-ttu-id="47558-108">Uygulama etki alanları ve derlemeler nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="47558-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="47558-109">Uygulama etki alanları ve derlemeler ile programlama kavramsal belgelerinde bulunan tüm nasıl yapılır konuları için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="47558-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="47558-110">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="47558-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="47558-111">Oluşturma, yapılandırma ve uygulama etki alanları kullanılarak örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47558-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="47558-112">Derlemelerle programlama</span><span class="sxs-lookup"><span data-stu-id="47558-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="47558-113">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="47558-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="47558-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="47558-114">Related Sections</span></span>  
 [<span data-ttu-id="47558-115">Dinamik yöntemleri ve derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="47558-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="47558-116">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="47558-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="47558-117">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="47558-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="47558-118">Derlemeler üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="47558-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="47558-119">Uygulama etki alanları</span><span class="sxs-lookup"><span data-stu-id="47558-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="47558-120">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="47558-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="47558-121">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="47558-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="47558-122">Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="47558-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
