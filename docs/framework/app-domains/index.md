---
title: Uygulama Etki Alanları ve Derlemelerle Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675357"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="aa3fc-102">Uygulama Etki Alanları ve Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="aa3fc-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="aa3fc-103">Microsoft Internet Explorer, ASP.NET ve Windows Kabuğu yük işleme, ortak dil çalışma zamanı gibi ana bilgisayarları oluşturma bir [uygulama etki alanı](../../../docs/framework/app-domains/application-domains.md) uygulamasındaki işlemek ve ardından yükleme ve bu uygulama etki alanında kullanıcı kodu yürütme bir .NET Framework uygulama çalışırken.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="aa3fc-104">Çoğu durumda, uygulama etki alanları oluşturma ve bunları çalışma zamanı ana bilgisayarı, bu görevleri gerçekleştirdiğinden derlemeleri yükleme hakkında endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="aa3fc-105">Araçlar veya programlama yoluyla kaldırmak istediğiniz kod oluşturma veya kaldırılmış ve yeniden takılabilir bileşenleri hızla oluşturma, ortak dil çalışma zamanı barındıracak bir uygulama oluşturuyorsanız, ancak kendi oluşturacağınız uygulama etki alanları.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="aa3fc-106">Bir çalışma zamanı ana bilgisayarı oluşturmadığınızı olsa bile, bu bölümde uygulama etki alanları ve bu uygulama etki alanlarında yüklenen derlemeler ile nasıl çalışılacağı hakkında önemli bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa3fc-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aa3fc-107">In This Section</span></span>  
 [<span data-ttu-id="aa3fc-108">Uygulama Etki Alanları ve Bütünleştirilmiş Kodlar için Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="aa3fc-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="aa3fc-109">Programlama uygulama etki alanları ve derlemeler için kavramsal belgelerde bulunan tüm nasıl yapılır konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="aa3fc-110">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="aa3fc-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="aa3fc-111">Oluşturma, yapılandırma ve uygulama etki alanları kullanılarak örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="aa3fc-112">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="aa3fc-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="aa3fc-113">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa3fc-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="aa3fc-114">Related Sections</span></span>  
 [<span data-ttu-id="aa3fc-115">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="aa3fc-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="aa3fc-116">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="aa3fc-117">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="aa3fc-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="aa3fc-118">Derlemeler üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="aa3fc-119">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="aa3fc-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="aa3fc-120">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="aa3fc-121">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="aa3fc-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="aa3fc-122">Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="aa3fc-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
