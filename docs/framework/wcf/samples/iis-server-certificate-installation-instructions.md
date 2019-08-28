---
title: Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 1bb9c8bb2fedc846f46f665fbfd00178e5c72975
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044904"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="70b9f-102">Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="70b9f-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="70b9f-103">Internet Information Services (IIS) ile güvenli bir şekilde iletişim kuran örnekleri çalıştırmak için bir sunucu sertifikası oluşturmanız ve kurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70b9f-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="70b9f-104">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="70b9f-104">Step 1.</span></span> <span data-ttu-id="70b9f-105">Sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="70b9f-105">Creating Certificates</span></span>  
 <span data-ttu-id="70b9f-106">Bilgisayarınız için bir sertifika oluşturmak üzere, yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve IIS ile güvenli iletişim kullanan her bir örnek için bulunan Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="70b9f-107">Bu toplu iş dosyasını çalıştırmadan önce yolun MakeCert. exe içeren klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="70b9f-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="70b9f-108">Setup. bat ' de sertifikayı oluşturmak için aşağıdaki komut kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70b9f-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="70b9f-109">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="70b9f-109">Step 2.</span></span> <span data-ttu-id="70b9f-110">Sertifikaları yükleme</span><span class="sxs-lookup"><span data-stu-id="70b9f-110">Installing Certificates</span></span>  
 <span data-ttu-id="70b9f-111">Az önce oluşturduğunuz sertifikaları yüklemek için gereken adımlar kullandığınız IIS sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="70b9f-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="70b9f-112">IIS 5,1 (Windows XP) ve IIS 6,0 (Windows Server 2003) üzerinde IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="70b9f-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="70b9f-113">Internet Information Services Manager MMC ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="70b9f-114">Varsayılan Web sitesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="70b9f-115">**Dizin Güvenliği** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="70b9f-116">**Sunucu sertifikası** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="70b9f-117">Web sunucusu sertifikası Sihirbazı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="70b9f-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="70b9f-118">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-118">Complete the wizard.</span></span> <span data-ttu-id="70b9f-119">Sertifika atama seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="70b9f-120">Görüntülenen sertifikalar listesinden ServiceModelSamples-HTTPS-Server sertifikasını seçin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="70b9f-121">![IIS sertifikası Sihirbazı](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="70b9f-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="70b9f-122">HTTPS adresini `https://localhost/servicemodelsamples/service.svc`kullanarak bir tarayıcıda hizmete erişimi test edin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="70b9f-123">SSL daha önce Httpcfg. exe kullanılarak yapılandırıldıysa</span><span class="sxs-lookup"><span data-stu-id="70b9f-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="70b9f-124">Sunucu sertifikasını oluşturmak için MakeCert. exe (veya Setup. bat dosyasını çalıştırın) kullanın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="70b9f-125">IIS Yöneticisi 'ni çalıştırın ve önceki adımlara göre sertifikayı yükler.</span><span class="sxs-lookup"><span data-stu-id="70b9f-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="70b9f-126">Aşağıdaki kod satırını istemci programına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="70b9f-127">Bu kod yalnızca, MakeCert. exe tarafından oluşturulanlar gibi test sertifikaları için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="70b9f-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="70b9f-128">Üretim kodu için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="70b9f-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="70b9f-129">IIS 7,0 (Windows Vista ve Windows Server 2008) üzerinde IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="70b9f-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="70b9f-130">**Başlat** menüsünde **Çalıştır**' a tıklayın ve ardından Internet INFORMATION SERVICES (IIS) MMC ek bileşenini açmak için **inetmgr** yazın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="70b9f-131">**Varsayılan Web sitesine** sağ tıklayın ve **bağlamaları Düzenle...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="70b9f-132">**Site bağlamaları** Iletişim kutusunun **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="70b9f-133">**Tür** açılır listesinden **https** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="70b9f-134">**SSL sertifikası** açılır listesinden **servicemodelsamples-HTTPS-Server** ' ı seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="70b9f-135">HTTPS adresini `https://localhost/servicemodelsamples/service.svc`kullanarak bir tarayıcıda hizmete erişimi test edin.</span><span class="sxs-lookup"><span data-stu-id="70b9f-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70b9f-136">Yeni yüklediğiniz test sertifikası güvenilen bir sertifika olmadığından, bu sertifikayla güvenliği sağlanmış yerel web adreslerine gözatarken ek Internet Explorer güvenlik uyarılarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70b9f-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="70b9f-137">Sertifikaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="70b9f-137">Removing Certificates</span></span>  
  
- <span data-ttu-id="70b9f-138">Internet Information Services yöneticisini daha önce yönlendirildiğinden kullanın, ancak bunu eklemek yerine sertifikayı veya bağlamayı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="70b9f-139">Aşağıdaki komutu kullanarak bilgisayar sertifikasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="70b9f-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
