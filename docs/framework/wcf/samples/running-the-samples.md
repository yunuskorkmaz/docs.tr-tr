---
title: "Windows Communication Foundation Örneklerini Çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 603a6dce17d527a3f14e408da19006509514df52
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="running-the-windows-communication-foundation-samples"></a><span data-ttu-id="acf68-102">Windows Communication Foundation Örneklerini Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="acf68-102">Running the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="acf68-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Örnekleri tek makineli veya makine bazındaki bir yapılandırmada çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="acf68-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can be run in a single-machine or cross-machine configuration.</span></span> <span data-ttu-id="acf68-104">Sağlanan gibi örnekleri tek bir makinede çalıştırmak için hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="acf68-104">As supplied, the samples are ready for running on a single machine.</span></span> <span data-ttu-id="acf68-105">Çapraz makine yapılandırması, bir örnek ait yapılandırma dosyası ayarları değiştirmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="acf68-105">In a cross-machine configuration, it is necessary to modify a sample's configuration file settings.</span></span> <span data-ttu-id="acf68-106">Aşağıdaki yordamlarda bir örneği aynı makineye ve çapraz makine yapılandırmalarını çalıştırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="acf68-106">The following procedures explain how to run a sample in same-machine and cross-machine configurations.</span></span> <span data-ttu-id="acf68-107">Internet Information Services (IIS) ve kendi kendini barındıran örnekleri barındırılan hizmetler için adımları Çeşitlemeler olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="acf68-107">Note that there are variations in the steps for services hosted in Internet Information Services (IIS) and the self-hosted samples.</span></span> <span data-ttu-id="acf68-108">Çoğu örnekleri IIS'de barındırılan; nasıl barındırılan belirlemek için örnek Benioku bilgilere bakın.</span><span class="sxs-lookup"><span data-stu-id="acf68-108">Most samples are hosted in IIS; see the sample readme information to determine how it is hosted.</span></span>  
  
 <span data-ttu-id="acf68-109">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], IIS'de barındırılan değil örnekleri bir dinleyici Http.sys ile kaydetmek için yükseltilmiş ayrıcalıklar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="acf68-109">On [!INCLUDE[wv](../../../../includes/wv-md.md)], samples that are not hosted in IIS require elevated privileges to register a listener with Http.sys.</span></span> <span data-ttu-id="acf68-110">Httpcfg.exe hizmetinin altında çalıştığı hesabın ile hizmetin dinleme adreslerini kaydetmek için kullanın ya da yönetici ayrıcalıklarıyla çalışan bir komut isteminden hizmeti başlatın.</span><span class="sxs-lookup"><span data-stu-id="acf68-110">Use Httpcfg.exe to register the service's listening addresses with the account the service is running under, or launch the service from a command prompt running with administrator privileges.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acf68-111">Derleme veya herhangi birini çalıştıran önce [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri, gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="acf68-111">Before building or running any of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples, be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="acf68-112">Aynı makinede örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="acf68-112">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="acf68-113">IIS tarafından barındırılan hizmetindeki, hizmeti aşağıdaki adresini girerek bir tarayıcı kullanarak erişebildiğinden emin olun: http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="acf68-113">If the service is hosted by IIS, ensure that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="acf68-114">Bir onay sayfasına yanıtta görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="acf68-114">A confirmation page should be displayed in response.</span></span> <span data-ttu-id="acf68-115">Onay sayfasında görüntülenmiyorsa bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="acf68-115">If the confirmation page is not displayed, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
2.  <span data-ttu-id="acf68-116">Hizmet kendi kendine barındırılıyorsa Service.exe dile özgü klasörü altında \service\bin çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="acf68-116">If the service is self-hosted, run Service.exe from \service\bin, from under the language-specific folder.</span></span> <span data-ttu-id="acf68-117">Hizmet etkinliğinin hizmet konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="acf68-117">Service activity is displayed on the service console window.</span></span>  
  
3.  <span data-ttu-id="acf68-118">\Client\bin Client.exe çalıştırmak\\, dile özgü klasörü altında.</span><span class="sxs-lookup"><span data-stu-id="acf68-118">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="acf68-119">İstemci etkinliği istemci konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="acf68-119">Client activity is displayed on the client console window.</span></span>  
  
4.  <span data-ttu-id="acf68-120">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="acf68-120">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="acf68-121">Makine genelinde örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="acf68-121">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="acf68-122">IIS'de barındırılan hizmetindeki ise:</span><span class="sxs-lookup"><span data-stu-id="acf68-122">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="acf68-123">Hizmeti makinede ServiceModelSamples adlı bir sanal dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="acf68-123">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="acf68-124">Setupvroot.bat bulunan toplu iş dosyası [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) disk dizini ve sanal dizini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acf68-124">The batch file Setupvroot.bat included with [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="acf68-125">Hizmet program dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti makinede ServiceModelSamples sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="acf68-125">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="acf68-126">\Bin dizindeki dosyaları eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="acf68-126">Ensure that you include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="acf68-127">Test, hizmet bir tarayıcı kullanarak istemci makineden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acf68-127">Test that you can access the service from the client machine using a browser.</span></span>  
  
     <span data-ttu-id="acf68-128">Hizmet kendiliğinden barındırılır ise:</span><span class="sxs-lookup"><span data-stu-id="acf68-128">If the service is self-hosted:</span></span>  
  
    1.  <span data-ttu-id="acf68-129">Hizmeti makinede hizmet dosyalarını barındıracak bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="acf68-129">On the service machine, create a directory to hold the service files.</span></span>  
  
    2.  <span data-ttu-id="acf68-130">Hizmet program dosyalarını \service\bin\ klasöründen dile özgü klasörü altında hizmet makineye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="acf68-130">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service machine.</span></span>  
  
    3.  <span data-ttu-id="acf68-131">Hizmet yapılandırma dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="acf68-131">In the service configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="acf68-132">Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="acf68-132">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    4.  <span data-ttu-id="acf68-133">Bir komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="acf68-133">Launch Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="acf68-134">İstemci makine dile özgü klasörü altındaki \client\bin\ klasöründen istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="acf68-134">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
3.  <span data-ttu-id="acf68-135">Uç nokta adresi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="acf68-135">Set the endpoint address.</span></span>  
  
    1.  <span data-ttu-id="acf68-136">Hizmeti bir etki alanı hesabı altında çalışır değilse, istemci yapılandırma dosyasını açın ve yeni adresi hizmetinizin eşleştirmek için uç nokta tanımı adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="acf68-136">If the service is not running under a domain account, open the client configuration file and change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="acf68-137">Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="acf68-137">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    2.  <span data-ttu-id="acf68-138">Hizmeti bir etki alanı hesabı altında çalışıyorsa, istemci yapılandırması karşı hizmet Svcutil.exe çalıştırarak yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="acf68-138">If the service is running under a domain account, regenerate the client configuration by running Svcutil.exe against the service.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="acf68-139">svcutil.exe, çalışıp [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="acf68-139"> running Svcutil.exe, see [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="acf68-140">Örnek yapılandırma dosyasında yerine oluşturulan dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="acf68-140">Use the generated file instead of the configuration file in the sample.</span></span> <span data-ttu-id="acf68-141">Oluşturulan yapılandırma dosyası, ek kimlik bilgileri olan ve varsayılan ayarları olsa bile hizmet uç noktasına bağlanmak gerekli tüm ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="acf68-141">The generated configuration file has additional identity information, and contains all settings necessary to connect to the service endpoint even though they are the default settings.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="acf68-142">kimlik bilgileri bkz [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), ve [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span><span class="sxs-lookup"><span data-stu-id="acf68-142"> identity information, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span></span>  
  
4.  <span data-ttu-id="acf68-143">İstemci makinesinde, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="acf68-143">On the client machine, launch Client.exe from a command prompt.</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="acf68-144">Bir hizmette hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="acf68-144">To debug a service</span></span>  
  
1.  <span data-ttu-id="acf68-145">Yapı Çözümü (istemci ve hizmet) kullanarak **yapı** menüsü veya CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="acf68-145">Build the solution (both client and service) using the **Build** menu or CTRL+SHIFT+B.</span></span>  
  
2.  <span data-ttu-id="acf68-146">IIS'de barındırılan hizmetindeki ise:</span><span class="sxs-lookup"><span data-stu-id="acf68-146">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="acf68-147">Adres http://localhost/servicemodelsamples/service.svc girerek bir tarayıcı kullanarak hizmetini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="acf68-147">Activate the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
    2.  <span data-ttu-id="acf68-148">Çözümde seçin **hata ayıklama** menü ve **ekleme işlemi için** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="acf68-148">In the solution, choose the **Debug** menu and the **Attach to Process** menu item.</span></span>  
  
    3.  <span data-ttu-id="acf68-149">Seçin **işlemleri tüm kullanıcıları göster** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="acf68-149">Select the **Show processes from all users** check box.</span></span>  
  
    4.  <span data-ttu-id="acf68-150">Ana çalışan işlem hatalarını ayıklamak için W3wp.exe seçin (Windows XP ASPNet_wp.exe seçin).</span><span class="sxs-lookup"><span data-stu-id="acf68-150">Select the host worker process W3wp.exe to debug (select ASPNet_wp.exe on Windows XP).</span></span>  
  
3.  <span data-ttu-id="acf68-151">Şimdi hizmet kodunda kesme noktalarını ayarlayın ve özel durumları üzerinde kesme noktaları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="acf68-151">You can now set breakpoints in the service code and enable breakpoints on exceptions.</span></span>  
  
4.  <span data-ttu-id="acf68-152">İstemci proje öğesi sağ tıklatın ve seçin **hata ayıklama**, **başlangıç yeni örnek**.</span><span class="sxs-lookup"><span data-stu-id="acf68-152">Right-click the client project item and choose **Debug**, **Start new instance**.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="acf68-153">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="acf68-153">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="acf68-154">Hizmet güvenlik nedenleriyle IIS'de barındırılıyorsa, sanal dizin tanımı ve örnekleri ile işiniz bittiğinde Kurulum adımlarında'ı izinler kaldırın.</span><span class="sxs-lookup"><span data-stu-id="acf68-154">If the service is hosted in IIS for security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf68-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="acf68-155">See Also</span></span>  
 [<span data-ttu-id="acf68-156">Windows Communication Foundation Örnekleri Derleme</span><span class="sxs-lookup"><span data-stu-id="acf68-156">Building the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [<span data-ttu-id="acf68-157">Bir çalışma grubunda ve makinelerde örneklerini çalıştırma</span><span class="sxs-lookup"><span data-stu-id="acf68-157">Running the Samples in a Workgroup and Across Machines</span></span>](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [<span data-ttu-id="acf68-158">Sorun giderme ipuçları</span><span class="sxs-lookup"><span data-stu-id="acf68-158">Troubleshooting Tips</span></span>](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
