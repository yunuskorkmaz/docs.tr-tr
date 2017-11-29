---
title: "Sanal Dizin Ayarlama Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b727f391abfeb1112de1b6cde3ceb564d3860974
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="d150c-102">Sanal Dizin Ayarlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d150c-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="d150c-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Örnekleri %SystemDrive%\inetpub\wwwroot\servicemodelsamples klasörüne eşlenmiş servicemodelsamples adlı ortak bir sanal dizini paylaşmak için yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d150c-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d150c-104">% SYSTEMDRIVE % genellikle C: veya D:, Internet Information Services (IIS) yüklü olduğu sürücü bağlı olarak konumudur.</span><span class="sxs-lookup"><span data-stu-id="d150c-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="d150c-105">Setupvroot.bat ve Cleanupvroot.bat dosyalarından çalıştırabilirsiniz [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) sanal dizin oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="d150c-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="d150c-106">Sanal dizin el ile oluşturmayı tercih ederseniz, aşağıdaki yordamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="d150c-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d150c-107">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d150c-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="d150c-108">IIS 7.0 veya 7.5 bir sanal dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d150c-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="d150c-109">Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın **inetmgr** Internet Information Services (IIS) MMC ek bileşenini açmak için.</span><span class="sxs-lookup"><span data-stu-id="d150c-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="d150c-110">Sol bölmede, bilgisayarın adıyla düğümünü genişletin ve ardından **siteleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="d150c-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="d150c-111">Sağ **varsayılan Web sitesi**ve ardından **uygulama Ekle** açmak için **uygulama Ekle penceresi**.</span><span class="sxs-lookup"><span data-stu-id="d150c-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="d150c-112">Penceresinde yazın `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.</span><span class="sxs-lookup"><span data-stu-id="d150c-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="d150c-113">Şu dizin oluşturulamıyor: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="d150c-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="d150c-114">Fiziksel yolu % SystemDrive%\inetpub\wwwroot\servicemodelsamples ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="d150c-115">WCF örnekleri çoğu hizmeti yürütülebilir dosyaları yapılandırıldığında bu konuma kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="d150c-116">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d150c-116">Click **OK**.</span></span> <span data-ttu-id="d150c-117">Web uygulaması şimdi WCF örnekleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d150c-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d150c-118">Bu görevi yalnızca bir kez, çünkü gerçekleştirilmesi gereken tüm [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri aynı servicemodelsamples Web uygulaması kullanın.</span><span class="sxs-lookup"><span data-stu-id="d150c-118">This task must be performed only once, because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d150c-119">Bu belge, amacıyla terimi `virtual directory` ile çalışır `Web application`.</span><span class="sxs-lookup"><span data-stu-id="d150c-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="d150c-120">Sanal dizin oluşturmaya ek olarak, özelliklerini etkinleştirmek için de ayarlamalısınız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalıştırmak için hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="d150c-120">In addition to creating the virtual directory, you must also set its properties to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to run.</span></span> <span data-ttu-id="d150c-121">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="d150c-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="d150c-122">IIS 5.1 veya 6.0 bir sanal dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d150c-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="d150c-123">Bir komut istemi penceresi açıp `start inetmgr` Internet Information Services (IIS) MMC ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="d150c-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="d150c-124">Sol bölmede, bilgisayarın adıyla düğümünü genişletin ve ardından **Web siteleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="d150c-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="d150c-125">Sağ **varsayılan Web sitesi** seçip **yeni, sanal dizin** sanal dizin oluşturma Sihirbazı'nı açın.</span><span class="sxs-lookup"><span data-stu-id="d150c-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="d150c-126">Sihirbazı'nda yazın `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.</span><span class="sxs-lookup"><span data-stu-id="d150c-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="d150c-127">Yolun % SystemDrive%\inetpub\wwwroot\servicemodelsamples ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="d150c-128">Çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri hizmeti yürütülebilir dosyaları yapılandırıldığında bu konuma kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-128">Most of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="d150c-129">
              **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="d150c-130">Varsayılan olarak, aşağıdaki onay kutularını seçilir:</span><span class="sxs-lookup"><span data-stu-id="d150c-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="d150c-131">**Okuma**</span><span class="sxs-lookup"><span data-stu-id="d150c-131">**Read**</span></span>  
  
    -   <span data-ttu-id="d150c-132">**(Örneğin, ASP) komut dosyalarını çalıştır**</span><span class="sxs-lookup"><span data-stu-id="d150c-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="d150c-133">Tıklatın **sonraki**ve ardından **son** Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d150c-134">Bu görevi yalnızca bir kez çünkü gerçekleştirilmesi gereken tüm [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri aynı servicemodelsamples sanal dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d150c-134">This task must be performed only once because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="d150c-135">Ek sanal dizin özellikleri IIS 7.0 veya 7.5 ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d150c-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="d150c-136">Servicemodelsamples düğümünü tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d150c-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="d150c-137">Pencerenin altındaki iki görünüm listelenir.</span><span class="sxs-lookup"><span data-stu-id="d150c-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="d150c-138">Seçin **özellikler görünümü** zaten seçili değilse.</span><span class="sxs-lookup"><span data-stu-id="d150c-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="d150c-139">İçin girişi çift **Dizin tarama**.</span><span class="sxs-lookup"><span data-stu-id="d150c-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="d150c-140">Eylemler bölmesinde seçin **etkinleştirmek** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d150c-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="d150c-141">Bu, bir hizmet hata ayıklama sırasında yardımcı olan Internet Explorer kullanarak dizininin dizin erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d150c-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="d150c-142">Son olarak, başkaları tarafından erişilebilmesi izin vermek için servicemodelsamples klasörün güvenlik özelliklerini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d150c-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="d150c-143">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="d150c-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="d150c-144">IIS 5.1 ek sanal dizin özelliklerinde veya 6.0 ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d150c-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="d150c-145">Servicemodelsamples düğümünü sağ tıklatın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d150c-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d150c-146">Varsayılan olarak, aşağıdaki onay kutularını seçilir:</span><span class="sxs-lookup"><span data-stu-id="d150c-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="d150c-147">**Okuma**</span><span class="sxs-lookup"><span data-stu-id="d150c-147">**Read**</span></span>  
  
    -   <span data-ttu-id="d150c-148">**Ziyaretleri günlüğe yaz**</span><span class="sxs-lookup"><span data-stu-id="d150c-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="d150c-149">**Bu kaynak dizini**</span><span class="sxs-lookup"><span data-stu-id="d150c-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="d150c-150">Seçin **Dizin tarama** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="d150c-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="d150c-151">Bu, bir hizmet hata ayıklama sırasında yardımcı olan Internet Explorer kullanarak dizininin dizin erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d150c-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="d150c-152">IIS 7.0 veya 7.5 klasörü güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d150c-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="d150c-153">% SystemDrive%\inetpub\wwwroot\servicemodelsamples gidin.</span><span class="sxs-lookup"><span data-stu-id="d150c-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="d150c-154">Servicemodelsamples klasörü sağ tıklatın ve **paylaşımı** veya **paylaşımı ile**.</span><span class="sxs-lookup"><span data-stu-id="d150c-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="d150c-155">Sol tarafındaki aşağı oka tıklayın **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d150c-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="d150c-156">Seçin **Bul** girişi.</span><span class="sxs-lookup"><span data-stu-id="d150c-156">Select the **Find** entry.</span></span> <span data-ttu-id="d150c-157">**Kullanıcıları veya Grupları Seç** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="d150c-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="d150c-158">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="d150c-159">Tıklatın **konumları**.</span><span class="sxs-lookup"><span data-stu-id="d150c-159">Click **Locations**.</span></span> <span data-ttu-id="d150c-160">**Konumları** penceredir artık açık.</span><span class="sxs-lookup"><span data-stu-id="d150c-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="d150c-161">Kullanılan bilgisayar girişini seçin.</span><span class="sxs-lookup"><span data-stu-id="d150c-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="d150c-162">Yerel bilgisayar ve bir giriş değil tüm etki alanları veya listelenen ağları seçmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d150c-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="d150c-163">Bilgisayar seçildikten sonra tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d150c-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="d150c-164">Tıklatın **Şimdi Bul**.</span><span class="sxs-lookup"><span data-stu-id="d150c-164">Click **Find Now**.</span></span> <span data-ttu-id="d150c-165">Bu, arama sonuçlarını yerel bilgisayarla ilişkili nesneleri ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="d150c-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="d150c-166">Bul **IIS_IUSRS** girişi **adı (göreli ayırt edici adı)** sütun.</span><span class="sxs-lookup"><span data-stu-id="d150c-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="d150c-167">Bu girişi seçin ve tıklatın **Tamam** sonuçlarını pencere arama'yı kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="d150c-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="d150c-168">Tıklatın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** penceresi.</span><span class="sxs-lookup"><span data-stu-id="d150c-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="d150c-169">Tıklatın **paylaşımı** değişiklikleri kalıcı hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="d150c-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="d150c-170">Paylaşıma değişiklik tamamlandıktan sonra tıklatın **Bitti** kapatmak için **dosya paylaşımı** penceresi.</span><span class="sxs-lookup"><span data-stu-id="d150c-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="d150c-171">IIS 5.1 veya 6.0 klasörü güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d150c-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="d150c-172">% SystemDrive%\inetpub\wwwroot\servicemodelsamples gidin.</span><span class="sxs-lookup"><span data-stu-id="d150c-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="d150c-173">Sağ **servicemodelsamples** klasörünü ve ardından **paylaşım ve güvenlik.**</span><span class="sxs-lookup"><span data-stu-id="d150c-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="d150c-174">Tıklatın **güvenlik** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d150c-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="d150c-175">IIS 6. 0'da, içinde kullanıyorsanız **grup veya kullanıcı adları** onay kutusuna olup olmadığını **Internet Konuk hesabı** listelenir.</span><span class="sxs-lookup"><span data-stu-id="d150c-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="d150c-176">Listelenmemişse:</span><span class="sxs-lookup"><span data-stu-id="d150c-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="d150c-177">Tıklatın **Başlat** ve ardından **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="d150c-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="d150c-178">Görmüyorsanız, **kullanıcı hesapları** simgesini tıklatın **kategori görünümüne geçiş**.</span><span class="sxs-lookup"><span data-stu-id="d150c-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="d150c-179">Tıklatın **kullanıcı hesapları** simgesi.</span><span class="sxs-lookup"><span data-stu-id="d150c-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="d150c-180">Altında "veya Denetim Masası simgesi seçin" tıklatın **kullanıcı hesaplarını**.</span><span class="sxs-lookup"><span data-stu-id="d150c-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="d150c-181">İçinde **kullanıcı hesapları** iletişim kutusu, tıklatın **Gelişmiş** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d150c-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="d150c-182">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d150c-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="d150c-183">İçinde **yerel kullanıcılar ve gruplar** iletişim kutusu, genişletmek için tıklatın **kullanıcılar** klasör.</span><span class="sxs-lookup"><span data-stu-id="d150c-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="d150c-184">Sağ bölmede, çift **Internet Konuk hesabı**.</span><span class="sxs-lookup"><span data-stu-id="d150c-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="d150c-185">İçinde **özellikleri** iletişim kutusu, kopyalama Internet Konuk hesabı olarak kullanılan adı.</span><span class="sxs-lookup"><span data-stu-id="d150c-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="d150c-186">Varsayılan olarak, adı "bilgisayar adından USR_" ile başlar.</span><span class="sxs-lookup"><span data-stu-id="d150c-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="d150c-187">**Özellikler** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="d150c-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="d150c-188">Kapat **yerel kullanıcılar ve gruplar** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d150c-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="d150c-189">Kapat **kullanıcı hesapları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d150c-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="d150c-190">Diğer kapatmak **kullanıcı hesapları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d150c-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="d150c-191">İçinde **servicemodelsamples özellikleri** iletişim kutusundaki **güvenlik** sekmesini tıklatın, **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d150c-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="d150c-192">Ardından bir eğik bilgisayarın adını yazın, sonra Internet kullanıcı hesabının, örneğin, myMachineName adını yapıştırın\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="d150c-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="d150c-193">Tıklatın **Adları Denetle** eklenmesini doğrulamak için.</span><span class="sxs-lookup"><span data-stu-id="d150c-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="d150c-194">Geçerli ise, ad büyük harflerle olduğu ve altı çizilir.</span><span class="sxs-lookup"><span data-stu-id="d150c-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="d150c-195">Ağ hizmeti listelenen IIS 6.0 için ayrıca kontrol **grup veya kullanıcı adları** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d150c-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="d150c-196">Ağ hizmeti listelenmemişse:</span><span class="sxs-lookup"><span data-stu-id="d150c-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="d150c-197">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d150c-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="d150c-198">İçinde **kullanıcıları veya Grupları Seç** iletişim kutusuna bilgisayarın adını ve ardından bir eğik.</span><span class="sxs-lookup"><span data-stu-id="d150c-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="d150c-199">Tür **hizmet** ters eğik çizgi (boşluksuz) sonra.</span><span class="sxs-lookup"><span data-stu-id="d150c-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="d150c-200">Tıklatın **Adları Denetle**.</span><span class="sxs-lookup"><span data-stu-id="d150c-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="d150c-201">Birden çok ad bulunursa seçip **ağ hizmeti** tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d150c-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="d150c-202">Tıklatın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d150c-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="d150c-203">IIS 5.1 ile Windows XP SP2 kullanıyorsanız, Internet Konuk hesabı ve ASPNET listelendiğini kontrol **grup veya kullanıcı adları** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d150c-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="d150c-204">ASPNET kullanıcı yerleşik üyesi olabileceğine dikkat edin **kullanıcılar** güvenlik grubu.</span><span class="sxs-lookup"><span data-stu-id="d150c-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="d150c-205">Bu durumda, ardından IF **kullanıcılar** Grup iletişim kutusunda listelenen, ayrı bir öğe olarak izin verilen kullanıcıları listesine eklemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d150c-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="d150c-206">ASPNET parçası olup olmadığını denetlemek için **kullanıcılar** güvenlik grubu:</span><span class="sxs-lookup"><span data-stu-id="d150c-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="d150c-207">Üzerinde **Başlat** menüsünde tıklatın **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="d150c-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="d150c-208">Tıklatın **kullanıcı hesapları** simgesi.</span><span class="sxs-lookup"><span data-stu-id="d150c-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="d150c-209">İçinde **grup** sütun denetleyin değeri **ASPNET** "kullanıcıları."</span><span class="sxs-lookup"><span data-stu-id="d150c-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d150c-210">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d150c-210">See Also</span></span>  
 [<span data-ttu-id="d150c-211">Internet Information Service barındırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d150c-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
