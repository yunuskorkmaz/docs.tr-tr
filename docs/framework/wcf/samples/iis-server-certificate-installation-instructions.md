---
description: 'Hakkında daha fazla bilgi edinin: Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri'
title: Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 1ac5209e9ff82911b0631c190e16ff457fea0db6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631859"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="7e315-103">Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7e315-103">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>

<span data-ttu-id="7e315-104">Internet Information Services (IIS) ile güvenli bir şekilde iletişim kuran örnekleri çalıştırmak için bir sunucu sertifikası oluşturmanız ve kurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e315-104">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="7e315-105">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="7e315-105">Step 1.</span></span> <span data-ttu-id="7e315-106">Sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e315-106">Creating Certificates</span></span>  

 <span data-ttu-id="7e315-107">Bilgisayarınız için bir sertifika oluşturmak üzere, yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve IIS ile güvenli iletişim kullanan her bir örnek için bulunan Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7e315-107">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="7e315-108">Bu toplu iş dosyasını çalıştırmadan önce yolun Makecert.exe içeren klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7e315-108">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="7e315-109">Aşağıdaki komut Setup.bat sertifikayı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e315-109">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="7e315-110">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="7e315-110">Step 2.</span></span> <span data-ttu-id="7e315-111">Sertifikaları yükleme</span><span class="sxs-lookup"><span data-stu-id="7e315-111">Installing Certificates</span></span>  

 <span data-ttu-id="7e315-112">Az önce oluşturduğunuz sertifikaları yüklemek için gereken adımlar kullandığınız IIS sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7e315-112">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="7e315-113">IIS 5,1 (Windows XP) ve IIS 6,0 (Windows Server 2003) üzerinde IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="7e315-113">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="7e315-114">Internet Information Services Manager MMC ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="7e315-114">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="7e315-115">Varsayılan Web sitesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7e315-115">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="7e315-116">**Dizin Güvenliği** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7e315-116">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="7e315-117">**Sunucu sertifikası** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7e315-117">Click the **Server Certificate** button.</span></span> <span data-ttu-id="7e315-118">Web sunucusu sertifikası Sihirbazı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7e315-118">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="7e315-119">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="7e315-119">Complete the wizard.</span></span> <span data-ttu-id="7e315-120">Sertifika atama seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7e315-120">Select the option to assign a certificate.</span></span> <span data-ttu-id="7e315-121">Görüntülenen sertifikalar listesinden ServiceModelSamples-HTTPS-Server sertifikasını seçin.</span><span class="sxs-lookup"><span data-stu-id="7e315-121">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="7e315-122">![IIS sertifikası Sihirbazı](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="7e315-122">![IIS Certificate Wizard](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="7e315-123">HTTPS adresini kullanarak bir tarayıcıda hizmete erişimi test edin `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="7e315-123">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="7e315-124">SSL daha önce Httpcfg.exe kullanılarak yapılandırıldıysa</span><span class="sxs-lookup"><span data-stu-id="7e315-124">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="7e315-125">Sunucu sertifikasını oluşturmak için Makecert.exe kullanın (veya Setup.bat çalıştırın).</span><span class="sxs-lookup"><span data-stu-id="7e315-125">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="7e315-126">IIS Yöneticisi 'ni çalıştırın ve önceki adımlara göre sertifikayı yükler.</span><span class="sxs-lookup"><span data-stu-id="7e315-126">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="7e315-127">Aşağıdaki kod satırını istemci programına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e315-127">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7e315-128">Bu kod yalnızca Makecert.exe tarafından oluşturulanlar gibi test sertifikaları için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7e315-128">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="7e315-129">Üretim kodu için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7e315-129">It is not recommended for production code.</span></span>  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="7e315-130">IIS 7,0 (Windows Vista ve Windows Server 2008) üzerinde IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="7e315-130">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="7e315-131">**Başlat** menüsünde **Çalıştır**' a tıklayın ve ardından Internet INFORMATION SERVICES (IIS) MMC ek bileşenini açmak için **inetmgr** yazın.</span><span class="sxs-lookup"><span data-stu-id="7e315-131">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="7e315-132">**Varsayılan Web sitesine** sağ tıklayın ve **bağlamaları Düzenle...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7e315-132">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="7e315-133">**Site bağlamaları** Iletişim kutusunun **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7e315-133">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="7e315-134">**Tür** açılır listesinden **https** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7e315-134">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="7e315-135">**SSL sertifikası** açılır listesinden **servicemodelsamples-HTTPS-Server** ' ı seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7e315-135">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="7e315-136">HTTPS adresini kullanarak bir tarayıcıda hizmete erişimi test edin `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="7e315-136">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e315-137">Yeni yüklediğiniz test sertifikası güvenilen bir sertifika olmadığından, bu sertifikayla güvenliği sağlanmış yerel web adreslerine gözatarken ek Internet Explorer güvenlik uyarılarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e315-137">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="7e315-138">Sertifikaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="7e315-138">Removing Certificates</span></span>  
  
- <span data-ttu-id="7e315-139">Internet Information Services yöneticisini daha önce yönlendirildiğinden kullanın, ancak bunu eklemek yerine sertifikayı veya bağlamayı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7e315-139">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="7e315-140">Aşağıdaki komutu kullanarak bilgisayar sertifikasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7e315-140">Remove the computer certificate by using the following command.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
