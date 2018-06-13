---
title: Uygulama Etki Alanlarını Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742477"
---
# <a name="using-application-domains"></a><span data-ttu-id="1a396-102">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1a396-102">Using Application Domains</span></span>
<span data-ttu-id="1a396-103">Uygulama etki alanları yalıtım ortak dil çalışma zamanı için bir birim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="1a396-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="1a396-104">Bunlar oluşturulur ve bir işlem içinde çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="1a396-104">They are created and run inside a process.</span></span> <span data-ttu-id="1a396-105">Uygulama etki alanları genellikle uygulamanın çalışma zamanı yükleme işlemi ve uygulama etki alanı içinde kullanıcı kodu yürütme sorumlu olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1a396-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="1a396-106">Çalışma zamanı ana bilgisayarı bir işlem ve bir varsayılan uygulama etki alanı oluşturur ve bunu içinde yönetilen kod çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1a396-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="1a396-107">Çalışma zamanı ana bilgisayarlarını, ASP.NET, Microsoft Internet Explorer ve Windows Kabuğu'nu içerir.</span><span class="sxs-lookup"><span data-stu-id="1a396-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="1a396-108">Çoğu uygulama için kendi uygulama etki alanı oluşturma gerekmez; çalışma zamanı ana bilgisayar tüm gerekli uygulama etki alanları sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a396-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="1a396-109">Ancak, oluşturabilir ve uygulamanızı kod ayırmak veya kullanın ve DLL'ler unload gerekiyorsa, ek uygulama etki alanlarını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="1a396-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1a396-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1a396-110">In This Section</span></span>  
 [<span data-ttu-id="1a396-111">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a396-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="1a396-112">Program aracılığıyla uygulama etki alanı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a396-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="1a396-113">Nasıl yapılır: Uygulama Etki Alanını Boşaltma</span><span class="sxs-lookup"><span data-stu-id="1a396-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="1a396-114">Program aracılığıyla bir uygulama etki alanını boşaltma açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a396-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="1a396-115">Nasıl yapılır: Uygulama Etki Alanını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1a396-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="1a396-116">Uygulama etki alanını yapılandırmak için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a396-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="1a396-117">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="1a396-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="1a396-118">Bir uygulama etki alanından kurulum bilgilerini almak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a396-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="1a396-119">Nasıl yapılır: Uygulama Etki Alanına Bütünleştirilmiş Kodlar Yükleme</span><span class="sxs-lookup"><span data-stu-id="1a396-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="1a396-120">Uygulama etki alanına bir derlemeyi yüklemeye açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a396-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="1a396-121">Nasıl yapılır: Bir Bütünleştirilmiş Koddan Tür ve Üye Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="1a396-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="1a396-122">Derleme hakkında bilgi almak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a396-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="1a396-123">Gölge Kopyalama Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="1a396-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="1a396-124">Bunlar kullanımdayken nasıl gölge kopyalama derlemeleri güncelleştirmeler sağlar ve gölge kopyalama yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a396-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="1a396-125">Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma</span><span class="sxs-lookup"><span data-stu-id="1a396-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="1a396-126">Ortak dil çalışma zamanı özel durum işleyicileri için arama başladıktan önce bir özel durum, olarak oluşturuldu bir bildirim nasıl alabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a396-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="1a396-127">Bütünleştirilmiş Kod Yüklerini Çözme</span><span class="sxs-lookup"><span data-stu-id="1a396-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="1a396-128">Kullanma hakkında yönergeler sunmaktadır <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> derleme yükleme hataları gidermek için olay.</span><span class="sxs-lookup"><span data-stu-id="1a396-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1a396-129">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1a396-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="1a396-130">Uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a396-130">Represents an application domain.</span></span> <span data-ttu-id="1a396-131">Oluşturma ve uygulama etki alanları denetleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a396-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1a396-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1a396-132">Related Sections</span></span>  
 [<span data-ttu-id="1a396-133">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="1a396-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="1a396-134">Derlemeleri tarafından gerçekleştirilen işlevler genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a396-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="1a396-135">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="1a396-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="1a396-136">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a396-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="1a396-137">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="1a396-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="1a396-138">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a396-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="1a396-139">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="1a396-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="1a396-140">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a396-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="1a396-141">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="1a396-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="1a396-142">Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1a396-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
