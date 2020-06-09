---
title: Sanal Dizin Ayarlama Yönergeleri
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 2d9443431601ffc712da40bd1c085f595471336b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602368"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="4d5ab-102">Sanal Dizin Ayarlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4d5ab-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="4d5ab-103">Windows Communication Foundation (WCF) örnekleri,%SystemDrive%\inetpub\wwwroot\servicemodelsamples klasörüne eşlenmiş servicemodelsamples adlı ortak bir sanal dizinin paylaşılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d5ab-104">% SystemDrive%, Internet Information Services (IIS) yüklü olduğu sürücü konumuna bağlı olarak genellikle C: veya D: ' dır.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="4d5ab-105">Sanal dizin oluşturmak için [Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamından](one-time-setup-procedure-for-the-wcf-samples.md) Setupvroot. bat ve Cleanupvroot. bat dosyalarını çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="4d5ab-106">Sanal dizini el ile oluşturmayı tercih ediyorsanız, aşağıdaki yordamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4d5ab-107">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="4d5ab-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="4d5ab-108">IIS 7,0 veya 7,5 ' de bir sanal dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4d5ab-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="4d5ab-109">**Başlat** menüsünde **Çalıştır**' a tıklayın ve ardından Internet INFORMATION SERVICES (IIS) MMC ek bileşenini açmak için **inetmgr** yazın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="4d5ab-110">Sol bölmede, bilgisayarın adı ile düğümünü genişletin ve ardından **siteler** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="4d5ab-111">**Varsayılan Web sitesi**' ne sağ tıklayın ve **ardından uygulama Ekle ' yi seçerek** **Uygulama Ekle penceresini**açın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="4d5ab-112">Penceresinde, `servicemodelsamples` oluşturmakta olduğunuz sanal dizinin diğer adı olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="4d5ab-113">Şu dizini oluşturun:%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="4d5ab-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="4d5ab-114">Fiziksel yolu%SystemDrive%\inetpub\wwwroot\servicemodelsamples. olarak ayarla</span><span class="sxs-lookup"><span data-stu-id="4d5ab-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="4d5ab-115">WCF örneklerinin çoğu yapılandırıldığında bu konuma hizmet yürütülebilir dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="4d5ab-116">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-116">Click **OK**.</span></span> <span data-ttu-id="4d5ab-117">Web uygulaması artık WCF örnekleri için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4d5ab-118">Tüm WCF örnekleri aynı servicemodelsamples Web uygulamasını kullandığından, bu görevin yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4d5ab-119">Bu belgenin amacına yönelik terim, `virtual directory` ile eşanlamlıdır `Web application` .</span><span class="sxs-lookup"><span data-stu-id="4d5ab-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="4d5ab-120">Sanal dizin oluşturmanın yanı sıra, WCF hizmetlerinin çalışmasını sağlamak için özelliklerini de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="4d5ab-121">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="4d5ab-122">IIS 5,1 veya 6,0 ' de bir sanal dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4d5ab-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="4d5ab-123">Bir komut istemi penceresi açın ve `start inetmgr` Internet Information Services (IIS) MMC ek bileşenini açmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="4d5ab-124">Sol bölmede, bilgisayarın adı ile düğümünü genişletin ve ardından **Web siteleri** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="4d5ab-125">**Varsayılan Web sitesi** ' ne sağ tıklayın ve **Yeni, sanal dizin** ' i seçerek sanal dizin oluşturma Sihirbazı 'nı açın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="4d5ab-126">Sihirbazda, `servicemodelsamples` oluşturmakta olduğunuz sanal dizinin diğer adı olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="4d5ab-127">Yolu%SystemDrive%\inetpub\wwwroot\servicemodelsamples. olarak ayarlayın</span><span class="sxs-lookup"><span data-stu-id="4d5ab-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="4d5ab-128">WCF örneklerinin çoğu yapılandırıldığında bu konuma hizmet yürütülebilir dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="4d5ab-129">**İleri**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="4d5ab-130">Varsayılan olarak, aşağıdaki onay kutuları seçilidir:</span><span class="sxs-lookup"><span data-stu-id="4d5ab-130">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="4d5ab-131">**Okuyamaz**</span><span class="sxs-lookup"><span data-stu-id="4d5ab-131">**Read**</span></span>  
  
    - <span data-ttu-id="4d5ab-132">**Betikleri Çalıştır (ASP gibi)**</span><span class="sxs-lookup"><span data-stu-id="4d5ab-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="4d5ab-133">**İleri**' ye tıklayın ve Sihirbazı tamamladıktan sonra **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4d5ab-134">Tüm WCF örnekleri aynı servicemodelsamples sanal dizinini kullandığından, bu görevin yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="4d5ab-135">IIS 7,0 veya 7,5 ' de ek sanal dizin özellikleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4d5ab-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="4d5ab-136">Servicemodelsamples düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="4d5ab-137">Pencerenin alt kısmında iki görünüm listelenir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="4d5ab-138">Henüz seçili değilse **Özellikler Görünümü** ' nü seçin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="4d5ab-139">**Dizin tarama**girişine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="4d5ab-140">Eylemler bölmesinde **Etkinleştir** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="4d5ab-141">Bu, bir hizmetin Hata ayıklamasında yardımcı olan Internet Explorer 'ı kullanarak dizinin dizinine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="4d5ab-142">Son olarak, servicemodelsamples klasörünün güvenlik özelliklerini diğerlerinin erişmesine izin verecek şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="4d5ab-143">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="4d5ab-144">IIS 5,1 veya 6,0 ' de ek sanal dizin özellikleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4d5ab-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="4d5ab-145">Servicemodelsamples düğümüne sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="4d5ab-146">Varsayılan olarak, aşağıdaki onay kutuları seçilidir:</span><span class="sxs-lookup"><span data-stu-id="4d5ab-146">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="4d5ab-147">**Okuyamaz**</span><span class="sxs-lookup"><span data-stu-id="4d5ab-147">**Read**</span></span>  
  
    - <span data-ttu-id="4d5ab-148">**Günlüğe ziyaretleri Kaydet**</span><span class="sxs-lookup"><span data-stu-id="4d5ab-148">**Log visits**</span></span>  
  
    - <span data-ttu-id="4d5ab-149">**Bu kaynağı dizine oluştur**</span><span class="sxs-lookup"><span data-stu-id="4d5ab-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="4d5ab-150">**Dizin tarama** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="4d5ab-151">Bu, bir hizmetin Hata ayıklamasında yardımcı olan Internet Explorer 'ı kullanarak dizinin dizinine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="4d5ab-152">IIS 7,0 veya 7,5 ' de klasörün güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4d5ab-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="4d5ab-153">%SystemDrive%\inetpub\wwwroot\servicemodelsamples. adresine gidin</span><span class="sxs-lookup"><span data-stu-id="4d5ab-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="4d5ab-154">Servicemodelsamples klasörüne sağ tıklayın ve **paylaşma** ya da **paylaşma**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="4d5ab-155">**Ekle** düğmesinin solundaki aşağı oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="4d5ab-156">**Find** girişini seçin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-156">Select the **Find** entry.</span></span> <span data-ttu-id="4d5ab-157">**Kullanıcıları veya grupları seç** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="4d5ab-158">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="4d5ab-159">**Konumlar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-159">Click **Locations**.</span></span> <span data-ttu-id="4d5ab-160">**Konumlar** penceresi artık açıktır.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="4d5ab-161">Kullanılan bilgisayar için girişi seçin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="4d5ab-162">Listelenen herhangi bir etki alanı veya ağ için bir giriş değil, yerel bilgisayarı seçmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="4d5ab-163">Bilgisayarı seçtikten sonra **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="4d5ab-164">**Şimdi bul**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-164">Click **Find Now**.</span></span> <span data-ttu-id="4d5ab-165">Bu, arama sonuçlarını yerel bilgisayarla ilişkili nesnelerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="4d5ab-166">**Ad (göreli ayırt edici ad)** sütununda **IIS_IUSRS** girdisini bulun.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="4d5ab-167">Bu girişi seçin ve **Tamam** ' a tıklayarak arama sonuçları penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="4d5ab-168">**Tamam** ' a tıklayarak **kullanıcıları veya grupları seç** penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="4d5ab-169">Değişiklikleri kalıcı hale getirmek için **paylaşma** ' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="4d5ab-170">Paylaşımı etkinleştirme değişiklikleri tamamlandıktan sonra, **dosya paylaşımı** penceresini kapatmak için **bitti** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="4d5ab-171">IIS 5,1 veya 6,0 ' de klasörün güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4d5ab-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="4d5ab-172">%SystemDrive%\inetpub\wwwroot\servicemodelsamples. adresine gidin</span><span class="sxs-lookup"><span data-stu-id="4d5ab-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="4d5ab-173">**Servicemodelsamples** klasörüne sağ tıklayın ve ardından **Paylaşım ve güvenlik** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="4d5ab-174">**Güvenlik** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="4d5ab-175">IIS 6,0 kullanıyorsanız, **Grup veya Kullanıcı adları** kutusunda **Internet Konuk hesabının** listelenip listelenmediğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="4d5ab-176">Listede yoksa:</span><span class="sxs-lookup"><span data-stu-id="4d5ab-176">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="4d5ab-177">**Başlat** ' a ve ardından **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="4d5ab-178">**Kullanıcı hesapları** simgesini görmüyorsanız **Kategori görünümüne geç ' e**tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="4d5ab-179">**Kullanıcı hesapları** simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-179">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="4d5ab-180">"Veya bir Denetim Masası simgesi seçin" altında **Kullanıcı hesapları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="4d5ab-181">**Kullanıcı hesapları** Iletişim kutusunda **Gelişmiş** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="4d5ab-182">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-182">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="4d5ab-183">**Yerel kullanıcılar ve gruplar** Iletişim kutusunda **Kullanıcılar** klasörünü genişletmek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="4d5ab-184">Sağ bölmede **Internet Konuk hesabı**' na çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="4d5ab-185">**Özellikler** iletişim kutusunda, Internet Konuk hesabı olarak kullanılan adı kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="4d5ab-186">Varsayılan olarak, ad "USR_" ile başlar ve ardından bilgisayarın adı gelir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="4d5ab-187">**Özellikler** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="4d5ab-188">**Yerel kullanıcılar ve gruplar** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="4d5ab-189">**Kullanıcı hesapları** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="4d5ab-190">Diğer **Kullanıcı hesapları** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="4d5ab-191">**Servicemodelsamples özellikleri** iletişim kutusunda, **güvenlik** sekmesinde, **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="4d5ab-192">Bilgisayarın adını ve ters eğik çizgiyi yazın, ardından Internet Kullanıcı hesabının adını yapıştırın, örneğin, myMachineName \\ % InternetGuestAccountName%</span><span class="sxs-lookup"><span data-stu-id="4d5ab-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="4d5ab-193">Eklemeyi doğrulamak için **adları denetle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="4d5ab-194">Geçerliyse, ad tüm büyük harflerle ve altı çizilir.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="4d5ab-195">IIS 6,0 için, ağ HIZMETI 'nin **Grup veya Kullanıcı adları** kutusunda listelendiğini de denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="4d5ab-196">Ağ HIZMETI listelenmiyorsa:</span><span class="sxs-lookup"><span data-stu-id="4d5ab-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="4d5ab-197">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-197">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="4d5ab-198">**Kullanıcı veya Grup Seç** iletişim kutusunda, bilgisayarın adını ve ardından bir ters eğik çizgi yazın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="4d5ab-199">Ters eğik çizgiden sonra **hizmet** yazın (boşluk olmadan).</span><span class="sxs-lookup"><span data-stu-id="4d5ab-199">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="4d5ab-200">**Adları denetle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-200">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="4d5ab-201">Birden çok ad bulunursa **ağ hizmeti** ' ni seçin ve **Tamam**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="4d5ab-202">**Tamam** ' a tıklayarak **kullanıcıları veya grupları seç** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="4d5ab-203">IIS 5,1 ile Windows XP SP2 kullanıyorsanız, hem Internet Konuk hesabı hem de ASPNET 'in **Grup veya Kullanıcı adları** kutusunda listelendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="4d5ab-204">ASPNET kullanıcısının yerleşik **Kullanıcılar** güvenlik grubunun bir üyesi olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="4d5ab-205">Bu durumda, **Kullanıcılar** grubu iletişim kutusunda listeleniyorsa, izin verilen kullanıcılar listesine ayrı bir öğe olarak eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="4d5ab-206">ASPNET 'in **Kullanıcılar** güvenlik grubunun bir parçası olup olmadığını denetlemek için:</span><span class="sxs-lookup"><span data-stu-id="4d5ab-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="4d5ab-207">**Başlat** menüsünde, **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="4d5ab-208">**Kullanıcı hesapları** simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-208">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="4d5ab-209">**Grup** sütununda, **ASPNET** değerinin "kullanıcılar" olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5ab-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d5ab-210">See also</span></span>

- [<span data-ttu-id="4d5ab-211">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4d5ab-211">Internet Information Service Hosting Instructions</span></span>](internet-information-service-hosting-instructions.md)
