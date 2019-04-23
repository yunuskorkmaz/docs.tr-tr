---
title: Güvenlik Duvarı Yönergeleri
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: f1b576b4e413fa3bae70ef1eb8f8ed768e28e309
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773811"
---
# <a name="firewall-instructions"></a><span data-ttu-id="83f30-102">Güvenlik Duvarı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="83f30-102">Firewall Instructions</span></span>
<span data-ttu-id="83f30-103">Windows Communication Foundation (WCF) örnekleri çalışması birkaç Güvenlik Duvarı'nda Program veya bağlantı noktalarını etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="83f30-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="83f30-104">Birçok örnekleri 8000-8003 aralığındaki bağlantı noktaları kullanılarak iletişim kurmak ve 9000 bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="83f30-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="83f30-105">Güvenlik Duvarı varsayılan olarak açıktır ve bu bağlantı noktalarına erişimi engeller.</span><span class="sxs-lookup"><span data-stu-id="83f30-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="83f30-106">Örnekler için güvenlik duvarını etkinleştirmek için gereksinimler ve güvenlik ortamı bağlı olarak aşağıdaki yordamlardan birini tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="83f30-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="83f30-107">1. seçenek: Etkileşimli olarak çalışırken örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="83f30-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="83f30-108">Güvenlik duvarı yapılandırmanızı hiçbir öncelikli değişiklik yaparak oluşturmaya ve örnekleri çalıştırmaya başlamak için devam edin.</span><span class="sxs-lookup"><span data-stu-id="83f30-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="83f30-109">Bir örneği çalıştırdığınızda bir **Windows Güvenlik Uyarısı** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="83f30-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="83f30-110">Söz konusu örnek program ardından etkileşimli bir engeli listesine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="83f30-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="83f30-111">Bu yordamı kullanarak, ardından örnek yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="83f30-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="83f30-112">2. seçenek: Örnek programları önceden etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="83f30-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="83f30-113">Başlangıç **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması ve örnek çalıştırmak için plan programları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="83f30-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="83f30-114">Yürütülebilir dosyalar için program önce oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="83f30-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="83f30-115">Aşağıdaki yordamda ayrıntılı yönergeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83f30-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="83f30-116">Seçenek 3: Önceden bir bağlantı noktası aralığını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="83f30-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="83f30-117">Başlangıç **Windows Güvenlik Duvarı** **Denetim Masası** uygulaması ve etkinleştirme bağlantı noktası 80, 443, 8000 8003 ve örnekleri tarafından kullanılan 9000.</span><span class="sxs-lookup"><span data-stu-id="83f30-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="83f30-118">Aşağıdaki yordamda ayrıntılı yönergeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83f30-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="83f30-119">Bu bağlantı noktaları, yalnızca örnekleri kullanmak tüm programı izin verdiğinden bu diğerlerine göre daha az güvenli bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="83f30-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="83f30-120">Hangi yordamın emin değilseniz, ilk seçenek seçin.</span><span class="sxs-lookup"><span data-stu-id="83f30-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="83f30-121">Başka bir satıcıdan bir güvenlik duvarı çalıştırıyorsanız, benzer değişiklikler yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="83f30-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83f30-122">Güvenlik duvarı yapılandırmanızı değiştirmeden güvenlik etkiler.</span><span class="sxs-lookup"><span data-stu-id="83f30-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="83f30-123">Kaydettiğiniz değişiklikleri yapın ve örnekler ile çalışmayı bitirseniz bile bunları kaldırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="83f30-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="83f30-124">Önceden örnekleri programları etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="83f30-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="83f30-125">Örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="83f30-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="83f30-126">Tıklayın **Başlat**, tıklayın **çalıştırma**ve türü `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="83f30-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="83f30-127">Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="83f30-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83f30-128">Windows Güvenlik Duvarı üzerinden iletişim gerektirir örnekleri çalıştırmak için Güvenlik Duvarı ayarlarını değiştirme izniniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83f30-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="83f30-129">Bazı güvenlik duvarı ayarları ve bilgisayarınız bir etki alanına bağlıysa, sistem yöneticiniz bu ayarları Grup İlkesi aracılığıyla denetleme.</span><span class="sxs-lookup"><span data-stu-id="83f30-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="83f30-130">Bir program Windows Güvenlik Duvarı üzerinden izin vermek için aşağıdaki işletim belirli adımlardan birini tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="83f30-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="83f30-131">Windows 7 veya Windows Server 2008 r2 üzerinde tıklayın **bir programı veya özelliği Windows Güvenlik Duvarı üzerinden izin**.</span><span class="sxs-lookup"><span data-stu-id="83f30-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="83f30-132">Tıklayın **ayarlarını değiştir**, izin **başka bir Program...** .</span><span class="sxs-lookup"><span data-stu-id="83f30-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="83f30-133">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], tıklayın **bir programın Windows Güvenlik Duvarı üzerinden izin**.</span><span class="sxs-lookup"><span data-stu-id="83f30-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="83f30-134">Üzerinde **özel durumları** sekmesinde **Program Ekle**.</span><span class="sxs-lookup"><span data-stu-id="83f30-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="83f30-135">Tıklayın **Gözat** düğmesine tıklayın ve çalıştırmayı planladığınız örnek yürütülebilir dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="83f30-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="83f30-136">Yürütülebilir dosyalar çalıştırmayı planladığınız tüm örnekleri ekleyene kadar 4 ve 5. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="83f30-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="83f30-137">Tıklayın **Tamam** güvenlik duvarı uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="83f30-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="83f30-138">Önceden bir bağlantı noktası aralığı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="83f30-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="83f30-139">Tıklayın **Başlat**, tıklayın **çalıştırma**ve türü `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="83f30-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="83f30-140">Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="83f30-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="83f30-141">Windows 7 veya Windows Server 2008 R2, aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="83f30-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="83f30-142">Tıklayın **Gelişmiş ayarlar** Windows Güvenlik Duvarı'nı pencerenin sol sütunda.</span><span class="sxs-lookup"><span data-stu-id="83f30-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="83f30-143">Tıklayın **gelen kuralları** sol sütunda.</span><span class="sxs-lookup"><span data-stu-id="83f30-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="83f30-144">Tıklayın **yeni kurallar** sağ sütunda.</span><span class="sxs-lookup"><span data-stu-id="83f30-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="83f30-145">Seçin **bağlantı noktası** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="83f30-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="83f30-146">Seçin **TCP** girin `8000, 8001, 8002, 8003, 9000, 80, 443` içinde **belirli yerel bağlantı noktaları** alan.</span><span class="sxs-lookup"><span data-stu-id="83f30-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="83f30-147">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="83f30-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="83f30-148">Seçin **bağlantıya izin**, tıklatıp **sonraki** .</span><span class="sxs-lookup"><span data-stu-id="83f30-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="83f30-149">Seçin **etki alanı** ve **özel**, tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="83f30-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="83f30-150">Bu kural ad `WCF-WF 4.0 Samples`, tıklatıp **son**.</span><span class="sxs-lookup"><span data-stu-id="83f30-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="83f30-151">Tıklayın **giden kuralları** ve h c adımlarını yineleyin.</span><span class="sxs-lookup"><span data-stu-id="83f30-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="83f30-152">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], şu adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="83f30-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="83f30-153">Tıklayın **bir programın Windows Güvenlik Duvarı üzerinden izin**.</span><span class="sxs-lookup"><span data-stu-id="83f30-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="83f30-154">Üzerinde **özel durumları** sekmesinde **bağlantı noktası Ekle**.</span><span class="sxs-lookup"><span data-stu-id="83f30-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="83f30-155">Bir ad girin, 8000 bağlantı noktası numarasını girin ve seçin **TCP** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="83f30-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="83f30-156">Tıklayın **kapsamını Değiştir** düğmesini seçme **Ağ Bağlantılarım** (alt ağ) yalnızca seçeneğin seçeneğine tıklayıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="83f30-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="83f30-157">Bağlantı noktaları için 8001, b ve d adımları yineleyin 8002, 8003, 9000, 80 ve 443.</span><span class="sxs-lookup"><span data-stu-id="83f30-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="83f30-158">Tıklayın **Tamam** güvenlik duvarı uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="83f30-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83f30-159">Örnekleri ile işiniz bittiğinde, tüm güvenlik duvarı özel durumları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="83f30-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="83f30-160">Bunu yapmak için açık **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması ve tüm programları kaldırın veya bağlantı noktası, önceki yordamlarda tarafından eklenen girdileri.</span><span class="sxs-lookup"><span data-stu-id="83f30-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
