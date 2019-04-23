---
title: Sanal Dizin Ayarlama Yönergeleri
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: fdff88026a49989870ee5c47f9a38a65ecad3c80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325351"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="6330d-102">Sanal Dizin Ayarlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6330d-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="6330d-103">Windows Communication Foundation (WCF) örnekleri %SystemDrive%\inetpub\wwwroot\servicemodelsamples klasörle eşlendi servicemodelsamples adlı ortak bir sanal dizin paylaşmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6330d-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6330d-104">% SYSTEMDRIVE % genellikle C: veya D:, Internet Information Services (IIS) yüklü olduğu sürücü bağlı olarak konumudur.</span><span class="sxs-lookup"><span data-stu-id="6330d-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="6330d-105">Setupvroot.bat ve Cleanupvroot.bat dosyalarından çalıştırabileceğiniz [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) sanal dizin oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6330d-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="6330d-106">Sanal dizin el ile oluşturmak isterseniz, aşağıdaki yordamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="6330d-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="6330d-107">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="6330d-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="6330d-108">IIS 7.0 veya 7.5 bir sanal dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6330d-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="6330d-109">Gelen **Başlat** menüsünde, tıklayın **çalıştırın**, yazın **inetmgr** Internet Information Services (IIS) MMC ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="6330d-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="6330d-110">Sol bölmede, bilgisayarın adını içeren düğüme genişletin ve ardından **siteleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="6330d-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="6330d-111">Sağ **varsayılan Web sitesi**ve ardından **uygulama Ekle** açmak için **uygulama Ekle penceresi**.</span><span class="sxs-lookup"><span data-stu-id="6330d-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="6330d-112">Penceresinde `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.</span><span class="sxs-lookup"><span data-stu-id="6330d-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="6330d-113">Şu dizin oluşturma: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="6330d-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="6330d-114">% SystemDrive%\inetpub\wwwroot\servicemodelsamples fiziksel yolunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="6330d-115">WCF örnekleri çoğu hizmet yürütülebilir dosya oluşturulduğunda bu konuma kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="6330d-116">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6330d-116">Click **OK**.</span></span> <span data-ttu-id="6330d-117">Web uygulaması WCF örnekleri için oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="6330d-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6330d-118">Tüm WCF örnekleri aynı servicemodelsamples Web uygulamasını kullanmak için bu görevi yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6330d-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6330d-119">Bu belge, amacıyla terimi `virtual directory` ile eşanlamlıdır `Web application`.</span><span class="sxs-lookup"><span data-stu-id="6330d-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="6330d-120">Sanal dizin oluşturmaya ek olarak, WCF hizmetlerini çalıştırmak için etkinleştirmek için özelliklerini de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6330d-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="6330d-121">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="6330d-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="6330d-122">IIS 5.1 veya 6.0 sanal bir dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6330d-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="6330d-123">Bir komut istemi penceresi açıp `start inetmgr` Internet Information Services (IIS) MMC ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="6330d-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="6330d-124">Sol bölmede, bilgisayarın adını içeren düğüme genişletin ve ardından **Web siteleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="6330d-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="6330d-125">Sağ **varsayılan Web sitesi** seçip **yeni sanal dizin** sanal dizin oluşturma Sihirbazı'nı açın.</span><span class="sxs-lookup"><span data-stu-id="6330d-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="6330d-126">Sihirbazı'nda yazın `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.</span><span class="sxs-lookup"><span data-stu-id="6330d-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="6330d-127">% SystemDrive%\inetpub\wwwroot\servicemodelsamples yolunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="6330d-128">WCF örnekleri çoğu hizmet yürütülebilir dosya oluşturulduğunda bu konuma kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="6330d-129">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="6330d-130">Varsayılan olarak, aşağıdaki onay kutularını seçilir:</span><span class="sxs-lookup"><span data-stu-id="6330d-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="6330d-131">**Read**</span><span class="sxs-lookup"><span data-stu-id="6330d-131">**Read**</span></span>  
  
    -   <span data-ttu-id="6330d-132">**Komut dosyalarını (örn. ASP) Çalıştır**</span><span class="sxs-lookup"><span data-stu-id="6330d-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="6330d-133">Tıklayın **sonraki**ve ardından **son** Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6330d-134">Tüm WCF örnekleri aynı servicemodelsamples sanal dizinin kullandığı için bu görevi yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6330d-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="6330d-135">Ek sanal dizin özelliklerini IIS 7.0 veya 7.5 ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6330d-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="6330d-136">Servicemodelsamples düğümünü tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6330d-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="6330d-137">Pencerenin altındaki iki görünüm listelenir.</span><span class="sxs-lookup"><span data-stu-id="6330d-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="6330d-138">Seçin **özellikler görünümü** zaten seçili değilse.</span><span class="sxs-lookup"><span data-stu-id="6330d-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="6330d-139">Girişini çift **Dizin tarama**.</span><span class="sxs-lookup"><span data-stu-id="6330d-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="6330d-140">Eylemler bölmesinde seçin **etkinleştirme** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6330d-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="6330d-141">Bu, dizini dizinin bir hizmetinde hata ayıklarken yardımcı olan Internet Explorer'ı kullanarak erişmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6330d-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="6330d-142">Son olarak, güvenlik özellikleri servicemodelsamples klasörün başkaları tarafından erişilmesine izin verecek şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6330d-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="6330d-143">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="6330d-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="6330d-144">Ek sanal dizini IIS 5.1 özelliklerinde veya 6. 0'ı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6330d-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="6330d-145">Servicemodelsamples düğümüne sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="6330d-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="6330d-146">Varsayılan olarak, aşağıdaki onay kutularını seçilir:</span><span class="sxs-lookup"><span data-stu-id="6330d-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="6330d-147">**Read**</span><span class="sxs-lookup"><span data-stu-id="6330d-147">**Read**</span></span>  
  
    -   <span data-ttu-id="6330d-148">**Günlük ziyaret eder.**</span><span class="sxs-lookup"><span data-stu-id="6330d-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="6330d-149">**Bu kaynağı dizine Ekle**</span><span class="sxs-lookup"><span data-stu-id="6330d-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="6330d-150">Seçin **Dizin tarama** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="6330d-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="6330d-151">Bu, dizini dizinin bir hizmetinde hata ayıklarken yardımcı olan Internet Explorer'ı kullanarak erişmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6330d-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="6330d-152">IIS 7.0 veya 7.5 klasör güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6330d-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="6330d-153">% SystemDrive%\inetpub\wwwroot\servicemodelsamples için gidin.</span><span class="sxs-lookup"><span data-stu-id="6330d-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="6330d-154">Servicemodelsamples klasörü sağ tıklatıp **paylaşımı** veya **paylaşımı ile**.</span><span class="sxs-lookup"><span data-stu-id="6330d-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="6330d-155">Solundaki aşağı oka tıklayın **Ekle** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="6330d-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="6330d-156">Seçin **Bul** girişi.</span><span class="sxs-lookup"><span data-stu-id="6330d-156">Select the **Find** entry.</span></span> <span data-ttu-id="6330d-157">**Kullanıcıları veya Grupları Seç** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="6330d-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="6330d-158">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="6330d-159">Tıklayın **konumları**.</span><span class="sxs-lookup"><span data-stu-id="6330d-159">Click **Locations**.</span></span> <span data-ttu-id="6330d-160">**Konumları** penceresi açıksa artık.</span><span class="sxs-lookup"><span data-stu-id="6330d-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="6330d-161">Kullanılan bilgisayar girişini seçin.</span><span class="sxs-lookup"><span data-stu-id="6330d-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="6330d-162">Yerel bilgisayar ve bir giriş değil herhangi bir etki alanı veya listelenen ağları seçmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6330d-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="6330d-163">Bilgisayar seçildikten sonra tıklayın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6330d-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="6330d-164">Tıklayın **Şimdi Bul**.</span><span class="sxs-lookup"><span data-stu-id="6330d-164">Click **Find Now**.</span></span> <span data-ttu-id="6330d-165">Bu, arama sonuçlarını yerel bilgisayarla ilişkili nesneleri ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="6330d-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="6330d-166">Bulma **IIS_IUSRS** girişi **adı (göreli ayırt edici adı)** sütun.</span><span class="sxs-lookup"><span data-stu-id="6330d-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="6330d-167">Bu girdiyi seçin ve tıklayın **Tamam** sonuçları penceresini aramayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="6330d-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="6330d-168">Tıklayın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** penceresi.</span><span class="sxs-lookup"><span data-stu-id="6330d-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="6330d-169">Tıklayın **paylaşımı** değişiklikleri kalıcı hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="6330d-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="6330d-170">Paylaşmayı etkinleştirmek için değişiklik tamamlandıktan sonra tıklayın **Bitti** kapatmak için **dosya paylaşımı** penceresi.</span><span class="sxs-lookup"><span data-stu-id="6330d-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="6330d-171">IIS 5.1 veya 6.0 klasör güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6330d-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="6330d-172">% SystemDrive%\inetpub\wwwroot\servicemodelsamples için gidin.</span><span class="sxs-lookup"><span data-stu-id="6330d-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="6330d-173">Sağ **servicemodelsamples** klasörünü ve ardından **paylaşım ve güvenlik.**</span><span class="sxs-lookup"><span data-stu-id="6330d-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="6330d-174">Tıklayın **güvenlik** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="6330d-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="6330d-175">IIS 6. 0'da, içinde kullanıyorsanız **grup veya kullanıcı adları** onay kutusuna olup olmadığını **Internet Konuk hesabı** listelenir.</span><span class="sxs-lookup"><span data-stu-id="6330d-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="6330d-176">Bu listede yoksa:</span><span class="sxs-lookup"><span data-stu-id="6330d-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="6330d-177">Tıklayın **Başlat** ve ardından **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="6330d-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="6330d-178">Görmüyorsanız, **kullanıcı hesaplarını** simgesini tıklayın **kategori görünümüne geçiş**.</span><span class="sxs-lookup"><span data-stu-id="6330d-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="6330d-179">Tıklayın **kullanıcı hesaplarını** simgesi.</span><span class="sxs-lookup"><span data-stu-id="6330d-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="6330d-180">Altında "veya bir Denetim Masası simgesi seçin" tıklayın **kullanıcı hesaplarını**.</span><span class="sxs-lookup"><span data-stu-id="6330d-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="6330d-181">İçinde **kullanıcı hesaplarını** iletişim kutusu, tıklayın **Gelişmiş** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="6330d-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="6330d-182">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6330d-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="6330d-183">İçinde **yerel kullanıcılar ve gruplar** iletişim kutusu, genişletmek için tıklatın **kullanıcılar** klasör.</span><span class="sxs-lookup"><span data-stu-id="6330d-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="6330d-184">Sağ bölmede **Internet Konuk hesabı**.</span><span class="sxs-lookup"><span data-stu-id="6330d-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="6330d-185">İçinde **özellikleri** iletişim kutusu, kopyalama Internet Konuk hesabı olarak kullanılan adı.</span><span class="sxs-lookup"><span data-stu-id="6330d-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="6330d-186">Varsayılan olarak, adı "USR_ bilgisayar adından" ile başlar.</span><span class="sxs-lookup"><span data-stu-id="6330d-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="6330d-187">**Özellikler** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="6330d-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="6330d-188">Kapat **yerel kullanıcılar ve gruplar** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="6330d-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="6330d-189">Kapat **kullanıcı hesaplarını** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="6330d-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="6330d-190">Diğer kapatmak **kullanıcı hesaplarını** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="6330d-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="6330d-191">İçinde **servicemodelsamples özellikleri** iletişim kutusundaki **güvenlik** sekmesinde **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="6330d-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="6330d-192">Ardından bir eğik bilgisayarın adını yazın ve ardından Internet kullanıcı hesabı, örneğin, myMachineName adını yapıştırın\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="6330d-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="6330d-193">Tıklayın **Adları Denetle** eklemeyi doğrulamak için.</span><span class="sxs-lookup"><span data-stu-id="6330d-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="6330d-194">Geçerliyse, adı tamamı büyük harf olduğundan çizilir.</span><span class="sxs-lookup"><span data-stu-id="6330d-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="6330d-195">IIS 6.0 için Ayrıca ağ hizmeti listelendiğini kontrol **grup veya kullanıcı adları** kutusu.</span><span class="sxs-lookup"><span data-stu-id="6330d-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="6330d-196">Ağ hizmeti listede yoksa:</span><span class="sxs-lookup"><span data-stu-id="6330d-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="6330d-197">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6330d-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="6330d-198">İçinde **kullanıcıları veya Grupları Seç** iletişim kutusuna bir ters eğik çizgi ardından bilgisayar adı.</span><span class="sxs-lookup"><span data-stu-id="6330d-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="6330d-199">Tür **hizmet** sonra ters eğik çizgi (boşluksuz).</span><span class="sxs-lookup"><span data-stu-id="6330d-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="6330d-200">Tıklayın **Adları Denetle**.</span><span class="sxs-lookup"><span data-stu-id="6330d-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="6330d-201">Birden fazla adı bulunursa seçip **ağ hizmeti** tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="6330d-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="6330d-202">Tıklayın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="6330d-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="6330d-203">IIS 5.1 ile Windows XP SP2 kullanıyorsanız, hem Internet Konuk hesabı hem de ASP.NET listelendiğini kontrol **grup veya kullanıcı adları** kutusu.</span><span class="sxs-lookup"><span data-stu-id="6330d-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="6330d-204">ASP.NET kullanıcı yerleşik üyesi olabileceğini unutmayın **kullanıcılar** güvenlik grubu.</span><span class="sxs-lookup"><span data-stu-id="6330d-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="6330d-205">Bu durumda, sonra eğer **kullanıcılar** Grup iletişim kutusunda listelenen, izin verilen kullanıcıların listesi için ayrı bir öğe olarak eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6330d-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="6330d-206">ASP.NET parçası olup olmadığını denetlemek için **kullanıcılar** güvenlik grubu:</span><span class="sxs-lookup"><span data-stu-id="6330d-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="6330d-207">Üzerinde **Başlat** menüsünde tıklatın **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="6330d-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="6330d-208">Tıklayın **kullanıcı hesaplarını** simgesi.</span><span class="sxs-lookup"><span data-stu-id="6330d-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="6330d-209">İçinde **grubu** sütun kontrol değeri **ASPNET** "kullanıcıları."</span><span class="sxs-lookup"><span data-stu-id="6330d-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6330d-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6330d-210">See also</span></span>

- [<span data-ttu-id="6330d-211">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6330d-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
