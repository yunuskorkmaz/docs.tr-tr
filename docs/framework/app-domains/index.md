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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73119812"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="3b399-102">Uygulama Etki Alanları ve Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="3b399-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="3b399-103">Microsoft Internet Explorer, ASP.NET ve Windows kabuğu gibi ana bilgisayarlar, ortak dil çalışma zamanını bir işleme yükler, bu işlemde bir [uygulama etki alanı](application-domains.md) oluşturur ve bir .NET Framework uygulamasını çalıştırırken kullanıcı kodunu bu uygulama etki alanında yükleyip çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="3b399-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="3b399-104">Çoğu durumda, çalışma zamanı ana bilgisayar bu görevleri gerçekleştirdiğinden, uygulama etki alanları oluşturma ve derlemeleri bunlara yükleme konusunda endişelenmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b399-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="3b399-105">Ancak, ortak dil çalışma süresini barındıracak bir uygulama oluşturuyorsanız, programlı olarak boşaltmak istediğiniz araçlar veya kodlar oluşturuyorsanız veya anında boşaltılabilir ve yeniden yüklenebilir takılabilir bileşenler oluşturuyorsanız, kendi uygulama etki alanları.</span><span class="sxs-lookup"><span data-stu-id="3b399-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="3b399-106">Çalışma zamanı ana bilgisayar oluşturmasanız bile, bu bölüm, bu uygulama etki alanlarında yüklenen uygulama etki alanları ve derlemeleriyle nasıl çalışacağınız hakkında önemli bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b399-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b399-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3b399-107">In This Section</span></span>  

[<span data-ttu-id="3b399-108">Uygulama Etki Alanları ve Derlemeler Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3b399-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="3b399-109">Uygulama etki alanları ve derlemeleri ile programlama için kavramsal belgelerde bulunan tüm Nasıl Yapılacağını konularına bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b399-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="3b399-110">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="3b399-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="3b399-111">Uygulama etki alanlarını oluşturma, yapılandırma ve kullanma örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b399-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="3b399-112">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="3b399-112">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="3b399-113">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="3b399-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3b399-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3b399-114">Related Sections</span></span>  

[<span data-ttu-id="3b399-115">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="3b399-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="3b399-116">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="3b399-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="3b399-117">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="3b399-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="3b399-118">Derlemeler üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b399-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="3b399-119">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="3b399-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="3b399-120">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b399-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="3b399-121">Yansımaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b399-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="3b399-122">Bir derleme hakkında bilgi edinmek için **Yansıma** sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3b399-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
