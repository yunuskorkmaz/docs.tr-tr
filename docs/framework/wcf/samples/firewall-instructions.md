---
title: Güvenlik Duvarı Yönergeleri
description: WCF örnekleri için güvenlik duvarında bağlantı noktalarını veya programları etkinleştirmeyi öğrenin. Gereksinimlerinize ve güvenlik ortamınıza bağlı olarak aşağıdaki yordamlardan birini kullanın.
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: de55d067960b8f2096c129f6feaf037219e06a96
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246149"
---
# <a name="firewall-instructions"></a><span data-ttu-id="df8f2-104">Güvenlik Duvarı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="df8f2-104">Firewall instructions</span></span>

<span data-ttu-id="df8f2-105">Windows Communication Foundation (WCF) örneklerinin çalışabilmesi için güvenlik duvarındaki çeşitli bağlantı noktalarını veya programları etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-105">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="df8f2-106">Örneklerin birçoğu 8000-8003 aralığındaki bağlantı noktalarını ve bağlantı noktası 9000 ' yi kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="df8f2-106">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="df8f2-107">Güvenlik Duvarı varsayılan olarak açıktır ve bu bağlantı noktalarına erişimi engeller.</span><span class="sxs-lookup"><span data-stu-id="df8f2-107">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="df8f2-108">Örneklere yönelik güvenlik duvarını etkinleştirmek için, gereksinimlerinize ve güvenlik ortamınıza bağlı olarak aşağıdaki yordamlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="df8f2-108">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>

- <span data-ttu-id="df8f2-109">Seçenek 1: çalışırken örnekleri etkileşimli olarak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-109">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="df8f2-110">Güvenlik Duvarı yapılandırmanızda hiçbir değişiklik yapmayın ve örnekleri oluşturmaya ve çalıştırmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-110">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="df8f2-111">Bir örnek çalıştırıldığında, bir **Windows Güvenlik Uyarısı** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-111">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="df8f2-112">Söz konusu örnek program, engeli kaldırılmış bir listeye etkileşimli olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-112">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="df8f2-113">Bu yordamla, örneği yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-113">With this procedure, you may have to then restart the sample.</span></span>

- <span data-ttu-id="df8f2-114">2. seçenek: örnek programları önceden etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-114">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="df8f2-115">**Windows Güvenlik Duvarı Denetim Masası** uygulamasını başlatın ve çalıştırmayı planladığınız örnek programları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-115">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="df8f2-116">Yürütülebilir dosyaların mevcut olması için önce programları derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-116">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="df8f2-117">Daha ayrıntılı yönergeleri aşağıdaki yordamda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df8f2-117">You can find more detailed instructions in the following procedure.</span></span>

- <span data-ttu-id="df8f2-118">Seçenek 3: bir bağlantı noktası aralığını önceden etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-118">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="df8f2-119">**Windows Güvenlik Duvarı Denetim Masası** uygulamasını başlatın ve örnekler tarafından kullanılan 80, 443, 8000-8003 ve 9000 bağlantı noktalarını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-119">Start the **Windows Firewall Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="df8f2-120">Daha ayrıntılı yönergeleri aşağıdaki yordamda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df8f2-120">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="df8f2-121">Bu seçenek, yalnızca örnekleri değil, herhangi bir programın bu bağlantı noktalarını kullanmasına izin verdiğinden, diğerlerinden daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-121">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>

<span data-ttu-id="df8f2-122">Hangi yordamın kullanılacağı konusunda emin değilseniz, ilk seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-122">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="df8f2-123">Başka bir satıcıdan güvenlik duvarı çalıştırıyorsanız, benzer değişiklikler yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-123">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df8f2-124">Güvenlik duvarı yapılandırmanızı değiştirmek güvenliği etkiler.</span><span class="sxs-lookup"><span data-stu-id="df8f2-124">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="df8f2-125">Yaptığınız değişiklikleri kaydetmeniz ve örneklerle çalışmayı bitirdiğinizde onları kaldırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-125">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>

## <a name="enable-samples-programs-in-advance"></a><span data-ttu-id="df8f2-126">Örnek programları önceden etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="df8f2-126">Enable samples programs in advance</span></span>

1. <span data-ttu-id="df8f2-127">Örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-127">Build the sample.</span></span>

2. <span data-ttu-id="df8f2-128">Çalıştırmayı **Başlat**  >  **Run**' ı seçin ve girin `firewall.cpl` .</span><span class="sxs-lookup"><span data-stu-id="df8f2-128">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="df8f2-129">Bu, **Windows Güvenlik Duvarı Denetim Masası** uygulamasını açar.</span><span class="sxs-lookup"><span data-stu-id="df8f2-129">This opens the **Windows Firewall Control Panel** applet.</span></span>

    > [!NOTE]
    > <span data-ttu-id="df8f2-130">Windows Güvenlik Duvarı üzerinden iletişim kurmayı gerektiren örnekleri çalıştırmak için güvenlik duvarı ayarlarını değiştirme izninizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-130">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="df8f2-131">Bazı güvenlik duvarı ayarları kullanılamaz durumdaysa ve bilgisayarınız bir etki alanına bağlıysa, sistem yöneticiniz bu ayarları grup ilkesi aracılığıyla denetliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="df8f2-131">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>

3. <span data-ttu-id="df8f2-132">Windows Güvenlik Duvarı aracılığıyla bir programa izin vermek için aşağıdaki işletim özel adımlardan birini doldurun:</span><span class="sxs-lookup"><span data-stu-id="df8f2-132">Complete one of the following operating-specific steps to allow a program through the Windows Firewall:</span></span>

    - <span data-ttu-id="df8f2-133">Windows 7 veya Windows Server 2008 R2 'de **Windows Güvenlik Duvarı üzerinden programa veya özelliğe Izin ver**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-133">On Windows 7 or Windows Server 2008 R2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="df8f2-134">**Ayarları Değiştir**  >  **başka bir programa izin ver**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-134">Click **Change Settings** > **Allow Another Program**.</span></span>

    - <span data-ttu-id="df8f2-135">Windows Vista veya Windows Server 2008 ' de, **Windows Güvenlik Duvarı üzerinden programa Izin ver**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-135">On Windows Vista or Windows Server 2008, click **Allow a program through Windows Firewall**.</span></span>

4. <span data-ttu-id="df8f2-136">**Özel durumlar** sekmesinde **Program Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-136">On the **Exceptions** tab, click **Add Program**.</span></span>

5. <span data-ttu-id="df8f2-137">**Araştır** düğmesine tıklayın ve çalıştırmayı planladığınız örneğin çalıştırılabilir dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-137">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>

6. <span data-ttu-id="df8f2-138">Çalıştırmayı planladığınız tüm örneklerin yürütülebilir dosyalarını ekleyinceye kadar 4 ve 5. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-138">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>

7. <span data-ttu-id="df8f2-139">Güvenlik Duvarı uygulamasını kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-139">Click **OK** to close the firewall applet.</span></span>

## <a name="enable-a-port-range-in-advance"></a><span data-ttu-id="df8f2-140">Bir bağlantı noktası aralığını önceden etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="df8f2-140">Enable a port range in advance</span></span>

1. <span data-ttu-id="df8f2-141">Çalıştırmayı **Başlat**  >  **Run**' ı seçin ve girin `firewall.cpl` .</span><span class="sxs-lookup"><span data-stu-id="df8f2-141">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="df8f2-142">Bu, **Windows Güvenlik Duvarı Denetim Masası** uygulamasını açar.</span><span class="sxs-lookup"><span data-stu-id="df8f2-142">This opens the **Windows Firewall Control Panel** applet.</span></span>

2. <span data-ttu-id="df8f2-143">Windows 7 veya Windows Server 2008 R2 'de, aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-143">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>

    1. <span data-ttu-id="df8f2-144">Windows Güvenlik Duvarı penceresinin sol sütununda **Gelişmiş ayarlar** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-144">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>

    2. <span data-ttu-id="df8f2-145">Sol sütundaki **gelen kurallar** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-145">Click **Inbound Rules** in the left column.</span></span>

    3. <span data-ttu-id="df8f2-146">Sağ sütundaki **yeni kurallar** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-146">Click **New Rules** in the right column.</span></span>

    4. <span data-ttu-id="df8f2-147">**Bağlantı noktasını** seçin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-147">Select **Port** and click **next**.</span></span>

    5. <span data-ttu-id="df8f2-148">**TCP** ' yi seçin ve `8000, 8001, 8002, 8003, 9000, 80, 443` **belirli yerel bağlantı noktaları** alanına girin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-148">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>

    6. <span data-ttu-id="df8f2-149">**İleri**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-149">Click **Next**.</span></span>

    7. <span data-ttu-id="df8f2-150">**Bağlantıya Izin ver**' i seçin ve **İleri** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-150">Select **Allow the connection**, and click **Next** .</span></span>

    8. <span data-ttu-id="df8f2-151">**Etki alanı** ve **özel**' i seçin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-151">Select **Domain** and **Private**, and click **Next**.</span></span>

    9. <span data-ttu-id="df8f2-152">Bu kuralı adlandırın `WCF-WF 4.0 Samples` ve **son**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-152">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>

    10. <span data-ttu-id="df8f2-153">**Giden kuralları** ' na tıklayın ve adımları c-h olarak tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-153">Click **Outbound Rules** and repeat steps c to h.</span></span>

3. <span data-ttu-id="df8f2-154">Windows Vista veya Windows Server 2008 ' de, aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-154">On Windows Vista or Windows Server 2008, follow these steps.</span></span>

    1. <span data-ttu-id="df8f2-155">**Windows Güvenlik Duvarı üzerinden programa Izin ver**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-155">Click **Allow a program through Windows Firewall**.</span></span>

    2. <span data-ttu-id="df8f2-156">**Özel durumlar** sekmesinde, **bağlantı noktası Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-156">On the **Exceptions** tab, click **Add Port**.</span></span>

    3. <span data-ttu-id="df8f2-157">Bir ad girin, bağlantı noktası numarası olarak 8000 girin ve **TCP** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-157">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>

    4. <span data-ttu-id="df8f2-158">**Kapsamı Değiştir** düğmesine tıklayın, yalnızca ağ (alt ağ) seçeneğini belirleyin ve **Tamam**' **a** tıklayın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-158">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>

    5. <span data-ttu-id="df8f2-159">8001, 8002, 8003, 9000, 80 ve 443 bağlantı noktaları için b ile d arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="df8f2-159">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>

4. <span data-ttu-id="df8f2-160">Güvenlik Duvarı uygulamasını kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-160">Click **OK** to close the firewall applet.</span></span>

> [!NOTE]
> <span data-ttu-id="df8f2-161">Örneklerle çalışmayı bitirdiğinizde tüm güvenlik duvarı özel durumlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-161">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="df8f2-162">Bunu yapmak için, **Windows Güvenlik Duvarı Denetim Masası** uygulamasını açın ve önceki yordamlar tarafından eklenen tüm programları veya bağlantı noktası girişlerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="df8f2-162">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
