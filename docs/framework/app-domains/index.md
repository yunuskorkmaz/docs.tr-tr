---
title: Uygulama Etki Alanları ve Derlemelerle Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 2c849d27c70971d17bf4359ee7ae1081ee976a5f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119812"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="65a8b-102">Uygulama Etki Alanları ve Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="65a8b-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="65a8b-103">Microsoft Internet Explorer, ASP.NET ve Windows kabuğu gibi konaklar, ortak dil çalışma zamanını bir işleme yükler, bu işlemde bir [uygulama etki alanı](application-domains.md) oluşturur ve ardından bir .net çalıştırırken bu uygulama etki alanında Kullanıcı kodunu yükler ve yürütür Framework uygulaması.</span><span class="sxs-lookup"><span data-stu-id="65a8b-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="65a8b-104">Çoğu durumda, çalışma zamanı ana bilgisayarı bu görevleri gerçekleştirdiğinden, uygulama etki alanları oluşturma ve bunlara derleme yükleme konusunda endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="65a8b-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="65a8b-105">Bununla birlikte, ortak dil çalışma zamanını barındıracak bir uygulama oluşturuyorsanız, programlı olarak kaldırmak istediğiniz araçları veya kodu oluşturun ya da bir yandan kaldırılabildiği ve yeniden yüklenebilir olan eklenebilir bileşenler oluşturun uygulama etki alanları.</span><span class="sxs-lookup"><span data-stu-id="65a8b-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="65a8b-106">Çalışma zamanı ana bilgisayarı oluşturmasanız bile, bu bölümde bu uygulama etki alanlarında yüklü uygulama etki alanları ve Derlemeleriyle çalışma hakkında önemli bilgiler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="65a8b-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65a8b-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="65a8b-107">In This Section</span></span>  

[<span data-ttu-id="65a8b-108">Uygulama Etki Alanları ve Bütünleştirilmiş Kodlar için Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="65a8b-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="65a8b-109">Uygulama etki alanları ve Derlemeleriyle programlama için kavramsal belgelerde bulunan tüm nasıl yapılır konularına bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a8b-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="65a8b-110">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="65a8b-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="65a8b-111">Uygulama etki alanları oluşturma, yapılandırma ve kullanma örnekleri sunar.</span><span class="sxs-lookup"><span data-stu-id="65a8b-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="65a8b-112">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="65a8b-112">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="65a8b-113">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="65a8b-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="65a8b-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="65a8b-114">Related Sections</span></span>  

[<span data-ttu-id="65a8b-115">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="65a8b-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="65a8b-116">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="65a8b-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="65a8b-117">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="65a8b-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="65a8b-118">Derlemeler üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a8b-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="65a8b-119">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="65a8b-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="65a8b-120">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a8b-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="65a8b-121">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="65a8b-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="65a8b-122">Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="65a8b-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
