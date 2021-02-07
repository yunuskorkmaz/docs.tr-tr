---
description: 'Hakkında daha fazla bilgi edinin: Internet Information Service barındırma yönergeleri'
title: Internet Information Service Barındırma Yönergeleri
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 51f5230ecbb8eaf4a909c5c09366680b8c555165
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726383"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="d5eb8-103">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d5eb8-103">Internet Information Service Hosting Instructions</span></span>

<span data-ttu-id="d5eb8-104">Internet Information Services (IIS) tarafından barındırılan örnekleri çalıştırmak için, IIS 'nin düzgün bir şekilde yüklendiğinden ve çalıştığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-104">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="d5eb8-105">Windows Server 2008 R2 'de IIS sürüm 7,5 ' ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d5eb8-105">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="d5eb8-106">**Sunucu Yöneticisi**, roller ' i seçin **.**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-106">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="d5eb8-107">**Roller Özeti** altında **Rol Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-107">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="d5eb8-108">**İleri** ' ye tıklayarak **sunucu rollerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-108">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="d5eb8-109">**Roller** listesinden **uygulama sunucusu** ' nu seçin ve ardından iki kez **Ileri** ' ye tıklayarak uygulama sunucusu rolü için **rol hizmetlerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-109">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="d5eb8-110">**Web sunucusu (IIS)** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-110">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="d5eb8-111">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli özellikleri ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-111">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="d5eb8-112">Web sunucusu (IIS) rolü için **rol hizmetlerini Seç** iletişim kutusunu göstermek için Iki kez **İleri** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-112">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="d5eb8-113">**Yönetim Araçları**' nı genişletin ve ardından **IIS 6 Yönetim uyumluluğu**' nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-113">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="d5eb8-114">**IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-114">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="d5eb8-115">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli rol hizmetleri Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-115">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="d5eb8-116">**İleri**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-116">Click **Next**.</span></span>  
  
6. <span data-ttu-id="d5eb8-117">Seçimlerin Özeti doğru ise, **yükler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-117">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="d5eb8-118">Yükleme tamamlandığında **Kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-118">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="d5eb8-119">Windows 7 ' ye IIS sürüm 7,5 yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d5eb8-119">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="d5eb8-120">**Başlat**' a ve ardından **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-120">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="d5eb8-121">**Programlar** grubunu açın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-121">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="d5eb8-122">**Programlar ve Özellikler** altında, **Windows özelliklerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-122">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="d5eb8-123">**Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-123">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="d5eb8-124">**Devam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-124">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="d5eb8-125">**Windows özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-125">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="d5eb8-126">**Internet Information Services** etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-126">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="d5eb8-127">**World Wide Web Services** etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-127">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="d5eb8-128">**Uygulama geliştirme özellikleri** etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-128">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="d5eb8-129">Aşağıdaki öğelerin seçildiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="d5eb8-129">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="d5eb8-130">**.NET Genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-130">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="d5eb8-131">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-131">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="d5eb8-132">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-132">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="d5eb8-133">**ISAPI filtreleri**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-133">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="d5eb8-134">**World Wide Web Services** etiketli öğe altında **ortak http özellikleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-134">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="d5eb8-135">**Statik içeriğin** seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-135">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="d5eb8-136">**World Wide Web Services** etiketli öğe altında **güvenlik**' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-136">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="d5eb8-137">**Windows kimlik doğrulamasının** seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-137">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="d5eb8-138">**Internet Information Services** dizininde, **Web yönetim araçları** etiketli öğeyi genişletin ve ardından **IIS Yönetim Konsolu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-138">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="d5eb8-139">**IIS 6 Yönetim uyumluluğu** etiketli öğeyi genişletin ve ardından **IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-139">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="d5eb8-140">**Internet Information Services** dizininde, **Microsoft .NET Framework 3.5.1** etiketli öğeyi genişletin ve ardından **http etkinleştirme Windows Communication Foundation**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-140">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="d5eb8-141">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-141">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="d5eb8-142">Windows Server 2008 ' ye IIS 7,0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d5eb8-142">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="d5eb8-143">**Sunucu Yöneticisi**, **Roller**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-143">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="d5eb8-144">**Roller Özeti** altında **Rol Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-144">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="d5eb8-145">**İleri** ' ye tıklayarak **sunucu rollerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-145">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="d5eb8-146">**Roller** listesinden **uygulama sunucusu** ' nu seçin ve ardından iki kez **Ileri** ' ye tıklayarak uygulama sunucusu rolü için **rol hizmetlerini Seç** iletişim kutusunu görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-146">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="d5eb8-147">**Web sunucusu (IIS)** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-147">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="d5eb8-148">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli özellikleri ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-148">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="d5eb8-149">Web sunucusu (IIS) rolü için **rol hizmetlerini Seç** iletişim kutusunu göstermek için Iki kez **İleri** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-149">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="d5eb8-150">**Yönetim Araçları**' nı genişletin ve ardından **IIS 6 Yönetim uyumluluğu**' nı genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-150">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="d5eb8-151">**IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-151">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="d5eb8-152">Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli rol hizmetleri Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-152">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="d5eb8-153">**İleri**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-153">Click **Next**.</span></span>  
  
6. <span data-ttu-id="d5eb8-154">Seçimlerin Özeti doğru ise, **yükler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-154">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="d5eb8-155">Yükleme tamamlandığında **Kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-155">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="d5eb8-156">Windows Vista 'da IIS sürüm 7,0 ' ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d5eb8-156">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="d5eb8-157">Başlat ' a ve ardından Denetim Masası ' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-157">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="d5eb8-158">**Programlar** grubunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-158">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="d5eb8-159">**Programlar ve Özellikler** altında, **Windows özelliklerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-159">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="d5eb8-160">**Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-160">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="d5eb8-161">**Devam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-161">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="d5eb8-162">**Windows özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-162">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="d5eb8-163">**Internet Information Services** etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-163">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="d5eb8-164">**World Wide Web Services** etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-164">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="d5eb8-165">**Uygulama geliştirme özellikleri** etiketli öğeyi genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-165">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="d5eb8-166">Aşağıdaki öğelerin seçildiğinden emin olun:</span><span class="sxs-lookup"><span data-stu-id="d5eb8-166">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="d5eb8-167">**.NET Genişletilebilirliği**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-167">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="d5eb8-168">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-168">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="d5eb8-169">**ISAPI Uzantıları**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-169">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="d5eb8-170">**ISAPI filtreleri**</span><span class="sxs-lookup"><span data-stu-id="d5eb8-170">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="d5eb8-171">**Web yönetimi araçları** etiketli öğeyi genişletin ve ardından **IIS Yönetim Konsolu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-171">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="d5eb8-172">**World Wide Web Services** etiketli öğe altında **ortak http özellikleri**' ni genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-172">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="d5eb8-173">**Statik içeriğin** seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-173">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="d5eb8-174">**World Wide Web Services** etiketli öğe altında **güvenlik**' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-174">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="d5eb8-175">**Windows kimlik doğrulamasının** seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-175">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="d5eb8-176">**IIS 6 Yönetim uyumluluğu** etiketli öğeyi genişletin ve ardından **IIS 6 komut dosyası araçları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-176">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="d5eb8-177">**Microsoft .NET Framework 3,0** etiketli öğeyi genişletin ve sonra **Windows Communication Foundation HTTP etkinleştirmesi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-177">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="d5eb8-178">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-178">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="d5eb8-179">Windows Server 2003 ' ye IIS 6,0 sürümünü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d5eb8-179">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="d5eb8-180">**Sunucunuzu Yönetin**' ten **bir rol Ekle veya Kaldır ' a** tıklayın ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-180">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="d5eb8-181">**Sunucu rolü** listesinden **uygulama sunucusu (IIS, ASP.net)** öğesini seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-181">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="d5eb8-182">**ASP.net etkinleştir** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-182">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="d5eb8-183">Seçimlerin Özeti doğru ise Ileri ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-183">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="d5eb8-184">Service Pack 2 ve Service Pack 3 yüklü Windows XP 'de IIS sürüm 5,1 ' ü yüklemek için</span><span class="sxs-lookup"><span data-stu-id="d5eb8-184">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="d5eb8-185">Denetim Masası 'nda **Program Ekle veya Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-185">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="d5eb8-186">**Program Ekle veya Kaldır** Iletişim kutusunda **Windows Bileşenlerini Ekle/Kaldır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-186">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="d5eb8-187">**Windows bileşenleri sihirbazında** **Internet Information Services (IIS)** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-187">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="d5eb8-188">**Gerekli dosyalar** iletişim kutusu görüntülenirse, işletim sistemi yükleme diskinizi takın, i386 klasörüne gidin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-188">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="d5eb8-189">Yükleme tamamlandığında **son**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-189">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="d5eb8-190">**Program Ekle veya Kaldır** iletişim kutusunu kapatın ve ardından **Denetim Masası**' nı kapatın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-190">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="d5eb8-191">IIS ve ASP.NET 'in yüklenmesini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="d5eb8-191">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="d5eb8-192">Bu konunun sonunda bulunan HTML dosyasını kök \Inetpub\Wwwroot dizinine kaydedin ve default. aspx olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-192">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="d5eb8-193">Tarayıcı penceresini açın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-193">Open a browser window.</span></span>  
  
3. <span data-ttu-id="d5eb8-194">`http://localhost/Default.aspx`Adres kutusuna yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-194">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="d5eb8-195">"Merhaba Dünya" metnine sahip bir Web sayfası görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-195">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5eb8-196">.NET Framework yeni bir sürümünü her yüklediğinizde, aspnet_isapi IIS için bir Web hizmeti uzantısı olarak yeniden kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-196">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="d5eb8-197">Bunu yapmak için `aspnet_regiis –I –enable` komutunu verin.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-197">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="d5eb8-198">Örnek Kod</span><span class="sxs-lookup"><span data-stu-id="d5eb8-198">Sample Code</span></span>  
  
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
