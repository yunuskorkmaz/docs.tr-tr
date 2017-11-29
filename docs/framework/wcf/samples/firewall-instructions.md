---
title: "Güvenlik Duvarı Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0aac3a161b0482bad1a32f5223d2031402a632cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="firewall-instructions"></a><span data-ttu-id="deb01-102">Güvenlik Duvarı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="deb01-102">Firewall Instructions</span></span>
<span data-ttu-id="deb01-103">Birkaç bağlantı noktalarını etkinleştirmeniz gerekir ya da Güvenlik Duvarı'nda böylece programları [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] örnekleri işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="deb01-103">You must enable several ports or programs in the firewall so that the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can function.</span></span> <span data-ttu-id="deb01-104">Birçok örnekleri 8000-8003 aralığında bağlantı noktasını kullanarak iletişim kurmak ve 9000 bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="deb01-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="deb01-105">Güvenlik Duvarı varsayılan olarak açıktır ve bu bağlantı noktalarına erişimi engeller.</span><span class="sxs-lookup"><span data-stu-id="deb01-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="deb01-106">Örnekler için Güvenlik Duvarı'nı etkinleştirmek için gereksinimler ve güvenlik ortamı bağlı olarak aşağıdaki yordamlardan birini tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="deb01-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="deb01-107">Seçenek 1: Etkileşimli olarak çalıştırırken örnekleri etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="deb01-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="deb01-108">Güvenlik duvarı yapılandırmanızı hiçbir öncelikli değişiklik ve oluşturma ve çalıştırma örnekleri başlatmak için devam edin.</span><span class="sxs-lookup"><span data-stu-id="deb01-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="deb01-109">Bir örneği çalıştırdığınızda, bir **Windows Güvenlik Uyarısı** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="deb01-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="deb01-110">Örnek program söz konusu ardından etkileşimli olarak engeli listesine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="deb01-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="deb01-111">Bu yordamı kullanarak, örnek yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="deb01-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="deb01-112">Seçenek 2: örnek programlar önceden etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="deb01-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="deb01-113">Başlat **Windows Güvenlik Duvarı'nı Denetim Masası** uygulamasını ve örnek programları çalıştırmak için plan etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="deb01-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="deb01-114">Yürütülebilir dosyalar mevcut şekilde programları önce oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="deb01-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="deb01-115">Aşağıdaki yordamda daha ayrıntılı yönergeler bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="deb01-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="deb01-116">Seçenek 3: önceden bir bağlantı noktası aralığını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="deb01-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="deb01-117">Başlat **Windows Güvenlik Duvarı** **Denetim Masası** uygulaması ve Etkinleştir bağlantı noktası 80, 443, 8000 8003 ve örnekleri tarafından kullanılan 9000.</span><span class="sxs-lookup"><span data-stu-id="deb01-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="deb01-118">Aşağıdaki yordamda daha ayrıntılı yönergeler bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="deb01-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="deb01-119">Bu bağlantı noktaları, yalnızca örnekleri kullanmak herhangi bir programı sağladığından bu diğerlerinden daha az güvenli bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="deb01-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="deb01-120">Hangi yordamın emin değilseniz, ilk seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="deb01-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="deb01-121">Başka bir satıcıdan bir güvenlik duvarı çalıştırıyorsanız, benzer değişiklikler yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="deb01-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="deb01-122">Güvenlik duvarı yapılandırmanızı değiştirme güvenlik etkiler.</span><span class="sxs-lookup"><span data-stu-id="deb01-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="deb01-123">Değişiklikleri yapın ve örnekleri ile işiniz bittiğinde bunları kaldırın kayıt önerilir.</span><span class="sxs-lookup"><span data-stu-id="deb01-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="deb01-124">Örnekleri programları önceden etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="deb01-124">To enable samples programs in advance</span></span>  
  
1.  <span data-ttu-id="deb01-125">Örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="deb01-125">Build the sample.</span></span>  
  
2.  <span data-ttu-id="deb01-126">Tıklatın **Başlat**, tıklatın **çalıştırmak**ve türü `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="deb01-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="deb01-127">Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="deb01-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="deb01-128">Windows Güvenlik Duvarı üzerinden iletişim kurmasına olanak gerektiren örnekleri çalıştırmak için Güvenlik Duvarı ayarlarını değiştirme izniniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="deb01-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="deb01-129">Bazı güvenlik duvarı ayarları kullanılamıyorsa ve bilgisayarınız bir etki alanına bağlıysa, sistem yöneticiniz bu ayarları Grup İlkesi aracılığıyla denetliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="deb01-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3.  <span data-ttu-id="deb01-130">Bir program Windows Güvenlik Duvarı aracılığıyla izin vermek için aşağıdaki işletim belirli adımları tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="deb01-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="deb01-131">Windows 7 veya Windows Server 2008 r2 üzerinde tıklatın **bir programı veya özelliği Windows Güvenlik Duvarı aracılığıyla izin**.</span><span class="sxs-lookup"><span data-stu-id="deb01-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="deb01-132">Tıklatın **Ayarları Değiştir**, izin **başka bir Program...** .</span><span class="sxs-lookup"><span data-stu-id="deb01-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="deb01-133">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], tıklatın **bir program Windows Güvenlik Duvarı aracılığıyla izin**.</span><span class="sxs-lookup"><span data-stu-id="deb01-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4.  <span data-ttu-id="deb01-134">Üzerinde **özel durumları** sekmesini tıklatın, **Program Ekle**.</span><span class="sxs-lookup"><span data-stu-id="deb01-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5.  <span data-ttu-id="deb01-135">Tıklatın **Gözat** düğmesini tıklatın ve çalıştırmayı düşündüğünüz örnek yürütülebilir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="deb01-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6.  <span data-ttu-id="deb01-136">Yürütülebilir dosyalar çalıştırmayı planladığınız tüm örnekleri ekleyene kadar 4 ve 5. adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="deb01-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7.  <span data-ttu-id="deb01-137">Tıklatın **Tamam** güvenlik duvarı uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="deb01-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="deb01-138">Bir bağlantı noktası aralığı önceden etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="deb01-138">To enable a port range in advance</span></span>  
  
1.  <span data-ttu-id="deb01-139">Tıklatın **Başlat**, tıklatın **çalıştırmak**ve türü `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="deb01-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="deb01-140">Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası** uygulaması.</span><span class="sxs-lookup"><span data-stu-id="deb01-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2.  <span data-ttu-id="deb01-141">Windows 7 veya Windows Server 2008 R2, aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="deb01-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="deb01-142">Tıklatın **Gelişmiş ayarları** Windows Güvenlik Duvarı penceresinin sol sütunda.</span><span class="sxs-lookup"><span data-stu-id="deb01-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="deb01-143">Tıklatın **gelen kuralları** sol sütunda.</span><span class="sxs-lookup"><span data-stu-id="deb01-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="deb01-144">Tıklatın **yeni kurallar** sağ sütundaki.</span><span class="sxs-lookup"><span data-stu-id="deb01-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="deb01-145">Seçin **bağlantı noktası** tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="deb01-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="deb01-146">Seçin **TCP** ve girin `8000, 8001, 8002, 8003, 9000, 80, 443` içinde **belirli yerel bağlantı noktaları** alan.</span><span class="sxs-lookup"><span data-stu-id="deb01-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="deb01-147">
              **İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="deb01-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="deb01-148">Seçin **bağlantıya izin**, tıklatıp **sonraki** .</span><span class="sxs-lookup"><span data-stu-id="deb01-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="deb01-149">Seçin **etki alanı** ve **özel**, tıklatıp **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="deb01-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="deb01-150">Bu kural adı `WCF-WF 4.0 Samples`, tıklatıp **son**.</span><span class="sxs-lookup"><span data-stu-id="deb01-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="deb01-151">Tıklatın **giden kuralları** ve h c adımlarını yineleyin.</span><span class="sxs-lookup"><span data-stu-id="deb01-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3.  <span data-ttu-id="deb01-152">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], şu adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="deb01-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="deb01-153">Tıklatın **bir program Windows Güvenlik Duvarı aracılığıyla izin**.</span><span class="sxs-lookup"><span data-stu-id="deb01-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="deb01-154">Üzerinde **özel durumları** sekmesini tıklatın, **bağlantı noktası Ekle**.</span><span class="sxs-lookup"><span data-stu-id="deb01-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="deb01-155">Bir ad girin, 8000 de bağlantı noktası numarası girin ve seçin **TCP** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="deb01-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="deb01-156">Tıklatın **Kapsamı Değiştir** düğmesi, select **Ağ Bağlantılarım** (alt ağ) tek seçenek ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="deb01-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="deb01-157">İçin bağlantı noktalarını 8001, d b adımları yineleyin 8002, 8003, 9000, 80 ve 443.</span><span class="sxs-lookup"><span data-stu-id="deb01-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4.  <span data-ttu-id="deb01-158">Tıklatın **Tamam** güvenlik duvarı uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="deb01-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="deb01-159">Örneklerle çalışma bittiğinde tüm güvenlik duvarı özel durumları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="deb01-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="deb01-160">Bunu yapmak için açık **Windows Güvenlik Duvarı'nı Denetim Masası** uygulaması ve tüm programları kaldırın veya bağlantı noktası, önceki yordamları tarafından eklenen girdileri.</span><span class="sxs-lookup"><span data-stu-id="deb01-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
