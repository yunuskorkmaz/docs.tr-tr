---
title: "Internet Information Service Barındırma Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7dd9d70a3b93faf721b5ac3bbd5f1114bf5c1461
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="e1cc0-102">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e1cc0-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="e1cc0-103">Internet Information Services (IIS) tarafından barındırılan örnekleri çalıştırmak için IIS düzgün yüklendiğinden ve çalıştığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="e1cc0-104">Windows Server 2008 R2'de IIS sürüm 7.5 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1cc0-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="e1cc0-105">Gelen **Sunucu Yöneticisi'ni**seçin **rolleri.**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="e1cc0-106">Altında **Rol Özeti**, tıklatın **rolleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="e1cc0-107">Tıklatın **sonraki** görüntülemek için **Sunucu Rollerini Seç** iletişim.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="e1cc0-108">Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="e1cc0-109">Seçin **Web sunucusu (IIS)** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="e1cc0-110">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken özellikleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="e1cc0-111">Tıklatın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="e1cc0-112">Genişletme **Yönetim Araçları**, genişletin ve ardından **IIS 6 Yönetim uyumluluğu**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="e1cc0-113">Seçin **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="e1cc0-114">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken rol hizmetlerini Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="e1cc0-115">
              **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-115">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="e1cc0-116">Seçim Özeti doğru ise, tıklatın **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="e1cc0-117">Yükleme tamamlandığında tıklayın **Kapat**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="e1cc0-118">IIS sürüm 7.5 Windows 7 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1cc0-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1.  <span data-ttu-id="e1cc0-119">Tıklatın **Başlat**ve ardından **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="e1cc0-120">Açık **programları** grubu.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-120">Open the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="e1cc0-121">Altında **programlar ve Özellikler**, tıklatın **Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="e1cc0-122">**Kullanıcı hesabı denetimi** iletişim kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="e1cc0-123">
              **Devam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-123">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="e1cc0-124">**Windows özelliklerini** iletişim kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="e1cc0-125">Öğesi etiketli genişletin **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="e1cc0-126">Öğesi etiketli genişletin **World Wide Web Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="e1cc0-127">Öğesi etiketli genişletin **uygulama geliştirme özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="e1cc0-128">Aşağıdaki öğeler seçili olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="e1cc0-128">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="e1cc0-129">**.NET genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-129">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="e1cc0-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-130">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="e1cc0-131">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-131">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="e1cc0-132">**ISAPI Filtreleri**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="e1cc0-133">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **ortak Http özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="e1cc0-134">Emin olun **statik içerik** seçilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="e1cc0-135">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="e1cc0-136">Olduğundan emin olun **Windows kimlik doğrulaması** seçilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="e1cc0-137">Altında **Internet Information Services** dizin öğesi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="e1cc0-138">Öğesi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="e1cc0-139">Altında **Internet Information Services** dizin öğesi etiketli genişletin **Microsoft .NET Framework 3.5.1**ve ardından **Windows Communication Foundation Http etkinleştirmesi**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="e1cc0-140">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="e1cc0-141">Windows Server 2008'de IIS 7.0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1cc0-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="e1cc0-142">Gelen **Sunucu Yöneticisi'ni**seçin **rolleri**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="e1cc0-143">Altında **Rol Özeti**, tıklatın **rolleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="e1cc0-144">Tıklatın **sonraki** görüntülemek için **Sunucu Rollerini Seç** iletişim.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="e1cc0-145">Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="e1cc0-146">Seçin **Web sunucusu (IIS)** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="e1cc0-147">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken özellikleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="e1cc0-148">Tıklatın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="e1cc0-149">Genişletme **Yönetim Araçları**, genişletin ve ardından **IIS 6 Yönetim uyumluluğu**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="e1cc0-150">Seçin **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="e1cc0-151">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken rol hizmetlerini Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="e1cc0-152">
              **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-152">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="e1cc0-153">Seçim Özeti doğru ise, tıklatın **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="e1cc0-154">Yükleme tamamlandığında tıklayın **Kapat**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="e1cc0-155">Windows Vista'da IIS'in 7.0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1cc0-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1.  <span data-ttu-id="e1cc0-156">Başlat'ı tıklatın ve ardından Denetim Masası'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-156">Click Start, and then click Control Panel.</span></span>  
  
2.  <span data-ttu-id="e1cc0-157">Seçin **programları** grubu.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-157">Select the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="e1cc0-158">Altında **programlar ve Özellikler**, tıklatın **Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="e1cc0-159">**Kullanıcı hesabı denetimi** iletişim kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="e1cc0-160">
              **Devam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-160">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="e1cc0-161">**Windows özelliklerini** iletişim kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="e1cc0-162">Öğesi etiketli genişletin **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="e1cc0-163">Öğesi etiketli genişletin **World Wide Web Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="e1cc0-164">Öğesi etiketli genişletin **uygulama geliştirme özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="e1cc0-165">Aşağıdaki öğeler seçili olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="e1cc0-165">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="e1cc0-166">**.NET genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-166">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="e1cc0-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-167">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="e1cc0-168">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-168">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="e1cc0-169">**ISAPI Filtreleri**</span><span class="sxs-lookup"><span data-stu-id="e1cc0-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="e1cc0-170">Öğesi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="e1cc0-171">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **ortak Http özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="e1cc0-172">Emin olun **statik içerik** seçilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="e1cc0-173">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="e1cc0-174">Emin olun **Windows kimlik doğrulaması** seçilir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="e1cc0-175">Öğesi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="e1cc0-176">Öğesi etiketli genişletin **Microsoft .NET Framework 3.0**ve ardından **Windows Communication Foundation Http etkinleştirmesi**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="e1cc0-177">Tıklatın**Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-177">Click**OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="e1cc0-178">IIS sürüm 6.0 Windows Server 2003'te yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1cc0-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="e1cc0-179">Gelen **sunucunuzu yönetin**, tıklatın **ekleme veya kaldırma rol**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="e1cc0-180">Seçin **uygulama sunucusu (IIS, ASP.NET)** gelen **sunucu rolü** listeleyin ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="e1cc0-181">Seçin **ASP** onay kutusunu işaretleyin ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="e1cc0-182">Seçim Özeti doğru ise, İleri'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="e1cc0-183">IIS sürüm 5.1, Windows XP Service Pack 2 ve Service Pack 3'ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e1cc0-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1.  <span data-ttu-id="e1cc0-184">Denetim Masası'nda tıklatın **Program Ekle veya Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="e1cc0-185">İçinde **Program Ekle veya Kaldır** iletişim kutusu, tıklatın **Windows Bileşenlerini Ekle/Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="e1cc0-186">İçinde **Windows Bileşenleri Sihirbazı'nı**seçin **Internet Information Services (IIS)** onay kutusunu işaretleyin ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="e1cc0-187">Varsa **gerekli dosyaları** iletişim kutusu görüntülenir, işletim sistemi yükleme diski takın, i386 klasörüne göz atın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="e1cc0-188">Yükleme tamamlandığında tıklayın **son**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-188">When installation completes, click **Finish**.</span></span>  
  
6.  <span data-ttu-id="e1cc0-189">Kapat **Program Ekle veya Kaldır** iletişim kutusunu ve ardından Kapat **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="e1cc0-190">IIS ve ASP.NET yüklemesini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="e1cc0-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1.  <span data-ttu-id="e1cc0-191">HTML dosyasını Kaydet kök \InetPub\wwwroot dizinini bu konudaki sonunda bulunan ve Default.aspx adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2.  <span data-ttu-id="e1cc0-192">Bir tarayıcı penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-192">Open a browser window.</span></span>  
  
3.  <span data-ttu-id="e1cc0-193">Tür `http://localhost/Default.aspx` adresi kutusunda ve ENTER tuşuna BASIN.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="e1cc0-194">"Hello World" metni ile bir Web sayfasında görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1cc0-195">Her zaman yeni bir sürümünü yüklemek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], aspnet_isapi bir Web hizmeti uzantısı olarak IIS için yeniden kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="e1cc0-196">Bunu yapmak için sorunu `aspnet_regiis –I –enable` komutu.</span><span class="sxs-lookup"><span data-stu-id="e1cc0-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="e1cc0-197">Örnek kod</span><span class="sxs-lookup"><span data-stu-id="e1cc0-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
