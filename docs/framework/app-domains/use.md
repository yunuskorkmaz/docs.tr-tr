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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674902"
---
# <a name="using-application-domains"></a><span data-ttu-id="f5d92-102">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f5d92-102">Using Application Domains</span></span>
<span data-ttu-id="f5d92-103">Uygulama etki alanı yalıtım ortak dil çalışma zamanı için bir birim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f5d92-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="f5d92-104">Bunlar oluşturulur ve bir işlem içinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f5d92-104">They are created and run inside a process.</span></span> <span data-ttu-id="f5d92-105">Uygulama etki alanları genellikle Uygulama çalışma zamanını bir işleme yükleme ve bir uygulama etki alanındaki kullanıcı kodunun yürütülmesi için sorumlu olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f5d92-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="f5d92-106">Çalışma zamanı ana bilgisayarı, bir varsayılan uygulama etki alanı ve bir işlem oluşturur ve yönetilen kod içindeki çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f5d92-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="f5d92-107">Çalışma zamanı ana bilgisayarları, ASP.NET, Microsoft Internet Explorer ve Windows Kabuğu'nu içerir.</span><span class="sxs-lookup"><span data-stu-id="f5d92-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="f5d92-108">Çoğu uygulama için kendi uygulama etki alanı oluşturma gerekmez; çalışma zamanı ana bilgisayarı tüm gerekli uygulama etki alanları oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f5d92-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="f5d92-109">Ancak, oluşturabilir ve uygulamanızın kod yalıtmak için veya kullanın ve DLL'lerini Kaldır için gereken ek uygulama etki alanları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f5d92-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5d92-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f5d92-110">In This Section</span></span>  
 [<span data-ttu-id="f5d92-111">Nasıl yapılır: Bir uygulama etki alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5d92-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="f5d92-112">Program aracılığıyla uygulama etki alanı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="f5d92-113">Nasıl yapılır: Bir uygulama etki alanını boşaltma</span><span class="sxs-lookup"><span data-stu-id="f5d92-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="f5d92-114">Program aracılığıyla uygulama etki alanını kaldırma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5d92-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="f5d92-115">Nasıl yapılır: Bir uygulama etki alanını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f5d92-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="f5d92-116">Uygulama etki alanı yapılandırma için bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="f5d92-117">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="f5d92-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="f5d92-118">Bir uygulama etki alanından kurulum bilgilerini alma açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="f5d92-119">Nasıl yapılır: Uygulama etki alanına derlemeler yükleme</span><span class="sxs-lookup"><span data-stu-id="f5d92-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="f5d92-120">Uygulama etki alanına bir derlemeyi yüklemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="f5d92-121">Nasıl yapılır: Derlemeden tür ve üye bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="f5d92-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="f5d92-122">Bir derleme hakkında bilgi almak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="f5d92-123">Gölge Kopyalama Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="f5d92-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="f5d92-124">Bunlar kullanımdayken nasıl gölge kopyalama derlemeleri güncelleştirmeler sağlar ve gölge kopyalama yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5d92-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="f5d92-125">Nasıl yapılır: İlk fırsat özel durum bildirimleri alma</span><span class="sxs-lookup"><span data-stu-id="f5d92-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="f5d92-126">Ortak dil çalışma zamanı için özel durum işleyicileri aramaya başlamadan önce bir özel durum, olarak oluşturuldu bir bildirim nasıl alabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f5d92-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="f5d92-127">Bütünleştirilmiş Kod Yüklerini Çözme</span><span class="sxs-lookup"><span data-stu-id="f5d92-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="f5d92-128">Kullanma hakkında yönergeler sağlar <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> derleme yükleme hataları çözmek için olay.</span><span class="sxs-lookup"><span data-stu-id="f5d92-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f5d92-129">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f5d92-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="f5d92-130">Uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5d92-130">Represents an application domain.</span></span> <span data-ttu-id="f5d92-131">Oluşturma ve uygulama etki alanları denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f5d92-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f5d92-132">Related Sections</span></span>  
 [<span data-ttu-id="f5d92-133">Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="f5d92-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="f5d92-134">Derlemeler tarafından gerçekleştirilen işlevler genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="f5d92-135">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="f5d92-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="f5d92-136">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="f5d92-137">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="f5d92-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="f5d92-138">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="f5d92-139">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="f5d92-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="f5d92-140">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5d92-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="f5d92-141">Yansıma genel bakış</span><span class="sxs-lookup"><span data-stu-id="f5d92-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="f5d92-142">Nasıl kullanılacağını açıklar **yansıma** derleme hakkında bilgi edinmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f5d92-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
