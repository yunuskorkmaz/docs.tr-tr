---
title: Uygulama Etki Alanlarını Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: 6ee02a3f27a645f19fd6a327052939586fac4aa9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645435"
---
# <a name="using-application-domains"></a><span data-ttu-id="fc57f-102">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc57f-102">Using Application Domains</span></span>

<span data-ttu-id="fc57f-103">Uygulama etki alanları, ortak dil çalışma zamanı için bir yalıtım birimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="fc57f-104">Bunlar bir işlem içinde oluşturulup çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="fc57f-104">They are created and run inside a process.</span></span> <span data-ttu-id="fc57f-105">Uygulama etki alanları genellikle çalışma zamanının bir işleme yüklenmesi ve bir uygulama etki alanı içinde Kullanıcı kodu yürütmesi ile ilgili bir uygulama olan bir çalışma zamanı ana bilgisayarı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fc57f-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="fc57f-106">Çalışma zamanı ana bilgisayarı bir işlem ve varsayılan bir uygulama etki alanı oluşturur ve içinde yönetilen kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="fc57f-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="fc57f-107">Çalışma zamanı Konakları ASP.NET, Microsoft Internet Explorer ve Windows kabuğu içerir.</span><span class="sxs-lookup"><span data-stu-id="fc57f-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="fc57f-108">Çoğu uygulama için kendi uygulama etki alanınızı oluşturmanız gerekmez; çalışma zamanı ana bilgisayarı sizin için gerekli uygulama etki alanlarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc57f-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="fc57f-109">Ancak, uygulamanızın kodu yalıtması veya dll 'Leri kullanması veya yüklemesi gerekiyorsa ek uygulama etki alanları oluşturabilir ve yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc57f-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc57f-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fc57f-110">In This Section</span></span>  

[<span data-ttu-id="fc57f-111">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc57f-111">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="fc57f-112">Programlı olarak bir uygulama etki alanı oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-112">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="fc57f-113">Nasıl yapılır: Uygulama Etki Alanını Boşaltma</span><span class="sxs-lookup"><span data-stu-id="fc57f-113">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="fc57f-114">Bir uygulama etki alanını programlı olarak nasıl kaldırabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-114">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="fc57f-115">Nasıl yapılır: Uygulama Etki Alanını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc57f-115">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="fc57f-116">Uygulama etki alanı yapılandırmaya bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-116">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="fc57f-117">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="fc57f-117">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="fc57f-118">Bir uygulama etki alanından kurulum bilgilerinin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="fc57f-119">Nasıl yapılır: Uygulama Etki Alanına Bütünleştirilmiş Kodlar Yükleme</span><span class="sxs-lookup"><span data-stu-id="fc57f-119">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="fc57f-120">Bir derlemenin uygulama etki alanına nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-120">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="fc57f-121">Nasıl yapılır: Bir Derlemeden Tür ve Üye Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="fc57f-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="fc57f-122">Bir derleme hakkında bilgilerin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-122">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="fc57f-123">Gölge Kopyalama Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="fc57f-123">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="fc57f-124">Gölge kopyalamanın, kullanıldıkları sırada derlemeler için güncelleştirmelerin nasıl izin verdiğini ve gölge kopyalamayı nasıl yapılandıracağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="fc57f-125">Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma</span><span class="sxs-lookup"><span data-stu-id="fc57f-125">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="fc57f-126">Ortak dil çalışma zamanı özel durum işleyicilerini aramaya başlamadan önce bir özel durumun oluşturulduğu bildirimini nasıl alacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="fc57f-127">Derleme Yüklerini Çözme</span><span class="sxs-lookup"><span data-stu-id="fc57f-127">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="fc57f-128">Derleme yükleme başarısızlıklarını çözümlemek için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı kullanma hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fc57f-129">Başvuru</span><span class="sxs-lookup"><span data-stu-id="fc57f-129">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="fc57f-130">Bir uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fc57f-130">Represents an application domain.</span></span> <span data-ttu-id="fc57f-131">Uygulama etki alanları oluşturmak ve denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fc57f-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fc57f-132">Related Sections</span></span>  
[<span data-ttu-id="fc57f-133">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="fc57f-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="fc57f-134">Derlemeler tarafından gerçekleştirilen işlevlere genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="fc57f-135">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="fc57f-135">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="fc57f-136">Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="fc57f-137">Dinamik Yöntemleri ve Derlemeleri Yayma</span><span class="sxs-lookup"><span data-stu-id="fc57f-137">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="fc57f-138">Dinamik derlemelerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-138">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="fc57f-139">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="fc57f-139">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="fc57f-140">Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-140">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="fc57f-141">Yansımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="fc57f-141">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="fc57f-142">Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc57f-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
