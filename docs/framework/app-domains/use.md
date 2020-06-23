---
title: Uygulama Etki Alanlarını Kullanma
description: Ortak dil çalışma zamanı (CLR) için bir yalıtım birimi sağlayan uygulama etki alanlarını kullanın. Uygulama etki alanları bir işlem içinde oluşturulur ve çalıştırılır.
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: df2a63716904ebfc6ee163121a1f07e53aa07514
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105178"
---
# <a name="using-application-domains"></a><span data-ttu-id="50f76-104">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="50f76-104">Using Application Domains</span></span>

<span data-ttu-id="50f76-105">Uygulama etki alanları, ortak dil çalışma zamanı için bir yalıtım birimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f76-105">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="50f76-106">Bunlar bir işlem içinde oluşturulup çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="50f76-106">They are created and run inside a process.</span></span> <span data-ttu-id="50f76-107">Uygulama etki alanları genellikle çalışma zamanının bir işleme yüklenmesi ve bir uygulama etki alanı içinde Kullanıcı kodu yürütmesi ile ilgili bir uygulama olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="50f76-107">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="50f76-108">Çalışma zamanı ana bilgisayarı bir işlem ve varsayılan bir uygulama etki alanı oluşturur ve içinde yönetilen kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="50f76-108">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="50f76-109">Çalışma zamanı Konakları ASP.NET, Microsoft Internet Explorer ve Windows kabuğu içerir.</span><span class="sxs-lookup"><span data-stu-id="50f76-109">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="50f76-110">Çoğu uygulama için kendi uygulama etki alanınızı oluşturmanız gerekmez; çalışma zamanı ana bilgisayarı sizin için gerekli uygulama etki alanlarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50f76-110">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="50f76-111">Ancak, uygulamanızın kodu yalıtması veya dll 'Leri kullanması veya yüklemesi gerekiyorsa ek uygulama etki alanları oluşturabilir ve yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50f76-111">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50f76-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="50f76-112">In This Section</span></span>  

[<span data-ttu-id="50f76-113">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="50f76-113">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="50f76-114">Programlı olarak bir uygulama etki alanı oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-114">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="50f76-115">Nasıl yapılır: Uygulama Etki Alanını Boşaltma</span><span class="sxs-lookup"><span data-stu-id="50f76-115">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="50f76-116">Bir uygulama etki alanını programlı olarak nasıl kaldırabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-116">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="50f76-117">Nasıl yapılır: Uygulama Etki Alanını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="50f76-117">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="50f76-118">Uygulama etki alanı yapılandırmaya bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f76-118">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="50f76-119">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="50f76-119">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="50f76-120">Bir uygulama etki alanından kurulum bilgilerinin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-120">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="50f76-121">Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme</span><span class="sxs-lookup"><span data-stu-id="50f76-121">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="50f76-122">Bir derlemenin uygulama etki alanına nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-122">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="50f76-123">Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="50f76-123">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="50f76-124">Bir derleme hakkında bilgilerin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-124">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="50f76-125">Gölge Kopyalama Derlemeleri</span><span class="sxs-lookup"><span data-stu-id="50f76-125">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="50f76-126">Gölge kopyalamanın, kullanıldıkları sırada derlemeler için güncelleştirmelerin nasıl izin verdiğini ve gölge kopyalamayı nasıl yapılandıracağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-126">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="50f76-127">Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma</span><span class="sxs-lookup"><span data-stu-id="50f76-127">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="50f76-128">Ortak dil çalışma zamanı özel durum işleyicilerini aramaya başlamadan önce bir özel durumun oluşturulduğu bildirimini nasıl alacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-128">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="50f76-129">Derleme Yüklerini Çözme</span><span class="sxs-lookup"><span data-stu-id="50f76-129">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="50f76-130"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>Derleme yükleme başarısızlıklarını çözümlemek için olayı kullanma hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f76-130">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="50f76-131">Başvuru</span><span class="sxs-lookup"><span data-stu-id="50f76-131">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="50f76-132">Bir uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="50f76-132">Represents an application domain.</span></span> <span data-ttu-id="50f76-133">Uygulama etki alanları oluşturmak ve denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f76-133">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="50f76-134">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="50f76-134">Related Sections</span></span>  
[<span data-ttu-id="50f76-135">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="50f76-135">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="50f76-136">Derlemeler tarafından gerçekleştirilen işlevlere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f76-136">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="50f76-137">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="50f76-137">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="50f76-138">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-138">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="50f76-139">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="50f76-139">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="50f76-140">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-140">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="50f76-141">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="50f76-141">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="50f76-142">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f76-142">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="50f76-143">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="50f76-143">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="50f76-144">Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="50f76-144">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
