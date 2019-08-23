---
title: Internet Information Service Barındırma Yönergeleri
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929107"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="91d73-102">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="91d73-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="91d73-103">Internet Information Services (IIS) tarafından barındırılan örnekleri çalıştırmak için, IIS 'nin düzgün bir şekilde yüklendiğinden ve çalıştığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91d73-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="91d73-104">Windows Server 2008 R2 'de IIS sürüm 7,5 ' ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="91d73-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="91d73-105">**Sunucu Yöneticisi**, roller ' i seçin **.**</span><span class="sxs-lookup"><span data-stu-id="91d73-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="91d73-106">**Roller Özeti**altında **Rol Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="91d73-107">**İleri** ' ye tıklayarak **sunucu rollerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="91d73-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="91d73-108">**Roller** listesinden **uygulama sunucusu** ' nu seçin ve ardından iki kez **Ileri** ' ye tıklayarak uygulama sunucusu rolü için **rol hizmetlerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="91d73-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="91d73-109">**Web sunucusu (IIS)** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="91d73-110">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli özellikleri ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="91d73-111">Web sunucusu (IIS) rolü için **rol hizmetlerini Seç** iletişim kutusunu göstermek için Iki kez **İleri** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="91d73-112">**Yönetim Araçları**' nı genişletin ve ardından **IIS 6 Yönetim uyumluluğu**' nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="91d73-113">**IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="91d73-114">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli rol hizmetleri Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="91d73-115">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="91d73-116">Seçimlerin Özeti doğru ise, **yükler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="91d73-117">Yükleme tamamlandığında **Kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="91d73-118">Windows 7 ' ye IIS sürüm 7,5 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="91d73-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="91d73-119">**Başlat**' a ve ardından **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="91d73-120">**Programlar** grubunu açın.</span><span class="sxs-lookup"><span data-stu-id="91d73-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="91d73-121">**Programlar ve Özellikler**altında, **Windows özelliklerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="91d73-122">**Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="91d73-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="91d73-123">**Devam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="91d73-124">**Windows özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="91d73-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="91d73-125">**Internet Information Services**etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="91d73-126">**World Wide Web Services**etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="91d73-127">**Uygulama geliştirme özellikleri**etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="91d73-128">Aşağıdaki öğelerin seçildiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="91d73-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="91d73-129">**.NET Genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="91d73-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="91d73-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="91d73-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="91d73-131">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="91d73-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="91d73-132">**ISAPI Filtreleri**</span><span class="sxs-lookup"><span data-stu-id="91d73-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="91d73-133">**World Wide Web Services**etiketli öğe altında **ortak http özellikleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="91d73-134">**Statik içeriğin** seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="91d73-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="91d73-135">**World Wide Web Services**etiketli öğe altında **güvenlik**' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="91d73-136">**Windows kimlik doğrulamasının** seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="91d73-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="91d73-137">**Internet Information Services** dizininde, **Web yönetim araçları**etiketli öğeyi genişletin ve ardından **IIS Yönetim Konsolu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="91d73-138">**IIS 6 Yönetim uyumluluğu**etiketli öğeyi genişletin ve ardından **IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="91d73-139">**Internet Information Services** dizininde, **Microsoft .NET Framework 3.5.1**etiketli öğeyi genişletin ve ardından **http etkinleştirme Windows Communication Foundation**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="91d73-140">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="91d73-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="91d73-141">Windows Server 2008 ' ye IIS 7,0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="91d73-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="91d73-142">**Sunucu Yöneticisi**, **Roller**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="91d73-143">**Roller Özeti**altında **Rol Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="91d73-144">**İleri** ' ye tıklayarak **sunucu rollerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="91d73-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="91d73-145">**Roller** listesinden **uygulama sunucusu** ' nu seçin ve ardından iki kez **Ileri** ' ye tıklayarak uygulama sunucusu rolü için **rol hizmetlerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="91d73-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="91d73-146">**Web sunucusu (IIS)** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="91d73-147">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli özellikleri ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="91d73-148">Web sunucusu (IIS) rolü için **rol hizmetlerini Seç** iletişim kutusunu göstermek için Iki kez **İleri** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="91d73-149">**Yönetim Araçları**' nı genişletin ve ardından **IIS 6 Yönetim uyumluluğu**' nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="91d73-150">**IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="91d73-151">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli rol hizmetleri Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="91d73-152">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="91d73-153">Seçimlerin Özeti doğru ise, **yükler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="91d73-154">Yükleme tamamlandığında **Kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="91d73-155">Windows Vista 'da IIS sürüm 7,0 ' ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="91d73-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="91d73-156">Başlat ' a ve ardından Denetim Masası ' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="91d73-157">**Programlar** grubunu seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="91d73-158">**Programlar ve Özellikler**altında, **Windows özelliklerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="91d73-159">**Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="91d73-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="91d73-160">**Devam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="91d73-161">**Windows özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="91d73-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="91d73-162">**Internet Information Services**etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="91d73-163">**World Wide Web Services**etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="91d73-164">**Uygulama geliştirme özellikleri**etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="91d73-165">Aşağıdaki öğelerin seçildiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="91d73-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="91d73-166">**.NET Genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="91d73-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="91d73-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="91d73-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="91d73-168">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="91d73-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="91d73-169">**ISAPI Filtreleri**</span><span class="sxs-lookup"><span data-stu-id="91d73-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="91d73-170">**Web yönetimi araçları**etiketli öğeyi genişletin ve ardından **IIS Yönetim Konsolu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="91d73-171">**World Wide Web Services**etiketli öğe altında **ortak http özellikleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="91d73-172">**Statik içeriğin** seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="91d73-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="91d73-173">**World Wide Web Services**etiketli öğe altında **güvenlik**' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="91d73-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="91d73-174">**Windows kimlik doğrulamasının** seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="91d73-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="91d73-175">**IIS 6 Yönetim uyumluluğu**etiketli öğeyi genişletin ve ardından **IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="91d73-176">**Microsoft .NET Framework 3,0**etiketli öğeyi genişletin ve sonra **Windows Communication Foundation HTTP etkinleştirmesi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="91d73-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="91d73-177">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="91d73-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="91d73-178">Windows Server 2003 ' ye IIS 6,0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="91d73-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="91d73-179">**Sunucunuzu Yönetin**' ten **bir rol Ekle veya Kaldır ' a**tıklayın ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="91d73-180">**Sunucu rolü** listesinden **uygulama sunucusu (IIS, ASP.net)** öğesini seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="91d73-181">**ASP.net etkinleştir** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="91d73-182">Seçimlerin Özeti doğru ise Ileri ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="91d73-183">Service Pack 2 ve Service Pack 3 yüklü Windows XP 'de IIS sürüm 5,1 ' ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="91d73-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="91d73-184">Denetim Masası 'nda **Program Ekle veya Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="91d73-185">**Program Ekle veya Kaldır** Iletişim kutusunda **Windows Bileşenlerini Ekle/Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="91d73-186">**Windows bileşenleri sihirbazında** **Internet Information Services (IIS)** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="91d73-187">**Gerekli dosyalar** iletişim kutusu görüntülenirse, işletim sistemi yükleme diskinizi takın, i386 klasörüne gidin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="91d73-188">Yükleme tamamlandığında **son**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="91d73-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="91d73-189">**Program Ekle veya Kaldır** iletişim kutusunu kapatın ve ardından **Denetim Masası**' nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="91d73-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="91d73-190">IIS ve ASP.NET 'in yüklenmesini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="91d73-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="91d73-191">Bu konunun sonunda bulunan HTML dosyasını kök \Inetpub\Wwwroot dizinine kaydedin ve default. aspx olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="91d73-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="91d73-192">Bir tarayıcı penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="91d73-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="91d73-193">Adres `http://localhost/Default.aspx` kutusuna yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91d73-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="91d73-194">"Merhaba Dünya" metnine sahip bir Web sayfası görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="91d73-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91d73-195">.NET Framework yeni bir sürümünü her yüklediğinizde, aspnet_isapi IIS için bir Web hizmeti uzantısı olarak yeniden kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91d73-195">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="91d73-196">Bunu yapmak için `aspnet_regiis –I –enable` komutunu verin.</span><span class="sxs-lookup"><span data-stu-id="91d73-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="91d73-197">Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="91d73-197">Sample Code</span></span>  
  
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
