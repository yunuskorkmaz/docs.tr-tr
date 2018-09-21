---
title: Internet Information Service Barındırma Yönergeleri
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 303fe47df987901b09cee8cc4292f12bcda2b74d
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480701"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="52e44-102">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="52e44-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="52e44-103">Internet Information Services (IIS) tarafından barındırılan örnekleri çalıştırmak için IIS doğru bir şekilde yüklendiğinden ve çalıştığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52e44-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="52e44-104">Windows Server 2008 R2'de IIS sürüm 7.5 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="52e44-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="52e44-105">Gelen **Sunucu Yöneticisi'ni**seçin **rolleri.**</span><span class="sxs-lookup"><span data-stu-id="52e44-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="52e44-106">Altında **rollerin özeti**, tıklayın **rolleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="52e44-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="52e44-107">Tıklayın **sonraki** görüntülenecek **Sunucu Rollerini Seç** iletişim.</span><span class="sxs-lookup"><span data-stu-id="52e44-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="52e44-108">Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.</span><span class="sxs-lookup"><span data-stu-id="52e44-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="52e44-109">Seçin **Web sunucusu (IIS)** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="52e44-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="52e44-110">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gereken özellikleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="52e44-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="52e44-111">Tıklayın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim.</span><span class="sxs-lookup"><span data-stu-id="52e44-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="52e44-112">Genişletin **Yönetim Araçları**ve ardından **IIS 6 Yönetim uyumluluğu**.</span><span class="sxs-lookup"><span data-stu-id="52e44-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="52e44-113">Seçin **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="52e44-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="52e44-114">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gerekli rol hizmetleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="52e44-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="52e44-115">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="52e44-115">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="52e44-116">Seçim Özeti doğruysa **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="52e44-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="52e44-117">Yükleme tamamlandığında, tıklayın **Kapat**.</span><span class="sxs-lookup"><span data-stu-id="52e44-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="52e44-118">Windows 7'de IIS sürüm 7.5 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="52e44-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1.  <span data-ttu-id="52e44-119">Tıklayın **Başlat**ve ardından **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="52e44-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="52e44-120">Açık **programlar** grubu.</span><span class="sxs-lookup"><span data-stu-id="52e44-120">Open the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="52e44-121">Altında **programlar ve Özellikler**, tıklayın **Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="52e44-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="52e44-122">**Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="52e44-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="52e44-123">
              \*\*Devam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="52e44-123">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="52e44-124">**Windows özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="52e44-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="52e44-125">Öğeyi etiketli genişletin **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="52e44-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="52e44-126">Öğeyi etiketli genişletin **World Wide Web Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="52e44-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="52e44-127">Öğeyi etiketli genişletin **uygulama geliştirme özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="52e44-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="52e44-128">Aşağıdaki öğeler seçili olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="52e44-128">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="52e44-129">**.NET genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="52e44-129">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="52e44-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="52e44-130">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="52e44-131">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="52e44-131">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="52e44-132">**ISAPI Filtreleri**</span><span class="sxs-lookup"><span data-stu-id="52e44-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="52e44-133">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **genel Http özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="52e44-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="52e44-134">Emin **statik içerik** seçilir.</span><span class="sxs-lookup"><span data-stu-id="52e44-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="52e44-135">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="52e44-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="52e44-136">Emin olun **Windows kimlik doğrulaması** seçilir.</span><span class="sxs-lookup"><span data-stu-id="52e44-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="52e44-137">Altında **Internet Information Services** dizine öğeyi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="52e44-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="52e44-138">Öğeyi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="52e44-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="52e44-139">Altında **Internet Information Services** dizine öğeyi etiketli genişletin **Microsoft .NET Framework 3.5.1**ve ardından **Windows Communication Foundation Http etkinleştirme**.</span><span class="sxs-lookup"><span data-stu-id="52e44-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="52e44-140">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="52e44-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="52e44-141">Windows Server 2008'de IIS'in 7.0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="52e44-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="52e44-142">Gelen **Sunucu Yöneticisi'ni**seçin **rolleri**.</span><span class="sxs-lookup"><span data-stu-id="52e44-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="52e44-143">Altında **rollerin özeti**, tıklayın **rolleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="52e44-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="52e44-144">Tıklayın **sonraki** görüntülenecek **Sunucu Rollerini Seç** iletişim.</span><span class="sxs-lookup"><span data-stu-id="52e44-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="52e44-145">Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.</span><span class="sxs-lookup"><span data-stu-id="52e44-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="52e44-146">Seçin **Web sunucusu (IIS)** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="52e44-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="52e44-147">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gereken özellikleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="52e44-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="52e44-148">Tıklayın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim.</span><span class="sxs-lookup"><span data-stu-id="52e44-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="52e44-149">Genişletin **Yönetim Araçları**ve ardından **IIS 6 Yönetim uyumluluğu**.</span><span class="sxs-lookup"><span data-stu-id="52e44-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="52e44-150">Seçin **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="52e44-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="52e44-151">Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gerekli rol hizmetleri Ekle**.</span><span class="sxs-lookup"><span data-stu-id="52e44-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="52e44-152">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="52e44-152">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="52e44-153">Seçim Özeti doğruysa **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="52e44-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="52e44-154">Yükleme tamamlandığında, tıklayın **Kapat**.</span><span class="sxs-lookup"><span data-stu-id="52e44-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="52e44-155">Windows Vista'da IIS'in 7.0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="52e44-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1.  <span data-ttu-id="52e44-156">Başlat'a tıklayın ve ardından Denetim Masası'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="52e44-156">Click Start, and then click Control Panel.</span></span>  
  
2.  <span data-ttu-id="52e44-157">Seçin **programlar** grubu.</span><span class="sxs-lookup"><span data-stu-id="52e44-157">Select the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="52e44-158">Altında **programlar ve Özellikler**, tıklayın **Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="52e44-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="52e44-159">**Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="52e44-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="52e44-160">
              \*\*Devam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="52e44-160">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="52e44-161">**Windows özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="52e44-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="52e44-162">Öğeyi etiketli genişletin **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="52e44-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="52e44-163">Öğeyi etiketli genişletin **World Wide Web Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="52e44-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="52e44-164">Öğeyi etiketli genişletin **uygulama geliştirme özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="52e44-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="52e44-165">Aşağıdaki öğeler seçili olduğundan emin olun:</span><span class="sxs-lookup"><span data-stu-id="52e44-165">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="52e44-166">**.NET genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="52e44-166">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="52e44-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="52e44-167">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="52e44-168">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="52e44-168">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="52e44-169">**ISAPI Filtreleri**</span><span class="sxs-lookup"><span data-stu-id="52e44-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="52e44-170">Öğeyi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.</span><span class="sxs-lookup"><span data-stu-id="52e44-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="52e44-171">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **genel Http özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="52e44-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="52e44-172">Emin **statik içerik** seçilir.</span><span class="sxs-lookup"><span data-stu-id="52e44-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="52e44-173">Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="52e44-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="52e44-174">Emin **Windows kimlik doğrulaması** seçilir.</span><span class="sxs-lookup"><span data-stu-id="52e44-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="52e44-175">Öğeyi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.</span><span class="sxs-lookup"><span data-stu-id="52e44-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="52e44-176">Öğeyi etiketli genişletin **Microsoft .NET Framework 3.0**ve ardından **Windows Communication Foundation Http etkinleştirme**.</span><span class="sxs-lookup"><span data-stu-id="52e44-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="52e44-177">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="52e44-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="52e44-178">Windows Server 2003'te IIS 6.0 sürümü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="52e44-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="52e44-179">Gelen **sunucunuzu yönetin**, tıklayın **ekleme veya bir rolü kaldırma**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="52e44-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="52e44-180">Seçin **uygulama sunucusu (IIS, ASP.NET)** gelen **sunucu rolü** listeleyin ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="52e44-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="52e44-181">Seçin **ASP** onay kutusunu işaretleyin ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="52e44-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="52e44-182">Seçim Özeti doğru ise, İleri'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="52e44-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="52e44-183">IIS 5.1 sürüm, Windows XP Service Pack 2 ve Service Pack 3'ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="52e44-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1.  <span data-ttu-id="52e44-184">Denetim Masası'nda tıklatın **Program Ekle veya Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="52e44-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="52e44-185">İçinde **Program Ekle veya Kaldır** iletişim kutusu, tıklayın **Windows Bileşenlerini Ekle/Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="52e44-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="52e44-186">İçinde **Windows Bileşenleri Sihirbazı'nı**seçin **Internet Information Services (IIS)** onay kutusunu işaretleyin ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="52e44-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="52e44-187">Varsa **gerekli dosyaları** iletişim kutusu görüntülenir, işletim sistemi yükleme diski takın, i386 klasöre göz atın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="52e44-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="52e44-188">Yükleme tamamlandığında, tıklayın **son**.</span><span class="sxs-lookup"><span data-stu-id="52e44-188">When installation completes, click **Finish**.</span></span>  
  
6.  <span data-ttu-id="52e44-189">Kapatma **Program Ekle veya Kaldır** iletişim kutusunu ve sonra close **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="52e44-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="52e44-190">IIS ve ASP.NET yüklemesini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="52e44-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1.  <span data-ttu-id="52e44-191">HTML dosyasını Kaydet kök \InetPub\wwwroot dizininde bu konunun sonunda bulunan ve Default.aspx olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="52e44-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2.  <span data-ttu-id="52e44-192">Bir tarayıcı penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="52e44-192">Open a browser window.</span></span>  
  
3.  <span data-ttu-id="52e44-193">Tür `http://localhost/Default.aspx` adres kutusuna ve ardından ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="52e44-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="52e44-194">"Hello World" metni ile bir Web sayfasında görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="52e44-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52e44-195">Her seferinde yeni bir sürümünü yüklemek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], aspnet_isapi bir Web hizmeti uzantısı IIS yeniden kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="52e44-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="52e44-196">Bunu yapmak için sorunu `aspnet_regiis –I –enable` komutu.</span><span class="sxs-lookup"><span data-stu-id="52e44-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="52e44-197">Örnek kod</span><span class="sxs-lookup"><span data-stu-id="52e44-197">Sample Code</span></span>  
  
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
