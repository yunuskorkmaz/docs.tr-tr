---
title: Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 597af9873b4a5c042aec817ac0d26a86bac9ea82
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253797"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="fa718-102">Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fa718-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>

<span data-ttu-id="fa718-103">Internet Information Services (IIS) ile güvenli bir şekilde iletişim kuran örnekleri çalıştırmak için bir sunucu sertifikası oluşturmanız ve kurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa718-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="fa718-104">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="fa718-104">Step 1.</span></span> <span data-ttu-id="fa718-105">Sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa718-105">Creating Certificates</span></span>  

 <span data-ttu-id="fa718-106">Bilgisayarınız için bir sertifika oluşturmak üzere, yönetici ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve IIS ile güvenli iletişim kullanan her bir örnek için bulunan Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa718-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="fa718-107">Bu toplu iş dosyasını çalıştırmadan önce yolun Makecert.exe içeren klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa718-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="fa718-108">Aşağıdaki komut Setup.bat sertifikayı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa718-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="fa718-109">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="fa718-109">Step 2.</span></span> <span data-ttu-id="fa718-110">Sertifikaları yükleme</span><span class="sxs-lookup"><span data-stu-id="fa718-110">Installing Certificates</span></span>  

 <span data-ttu-id="fa718-111">Az önce oluşturduğunuz sertifikaları yüklemek için gereken adımlar kullandığınız IIS sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fa718-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="fa718-112">IIS 5,1 (Windows XP) ve IIS 6,0 (Windows Server 2003) üzerinde IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="fa718-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="fa718-113">Internet Information Services Manager MMC ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="fa718-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="fa718-114">Varsayılan Web sitesine sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="fa718-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="fa718-115">**Dizin Güvenliği** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="fa718-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="fa718-116">**Sunucu sertifikası** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fa718-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="fa718-117">Web sunucusu sertifikası Sihirbazı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="fa718-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="fa718-118">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="fa718-118">Complete the wizard.</span></span> <span data-ttu-id="fa718-119">Sertifika atama seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="fa718-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="fa718-120">Görüntülenen sertifikalar listesinden ServiceModelSamples-HTTPS-Server sertifikasını seçin.</span><span class="sxs-lookup"><span data-stu-id="fa718-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="fa718-121">![IIS sertifikası Sihirbazı](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="fa718-121">![IIS Certificate Wizard](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="fa718-122">HTTPS adresini kullanarak bir tarayıcıda hizmete erişimi test edin `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="fa718-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="fa718-123">SSL daha önce Httpcfg.exe kullanılarak yapılandırıldıysa</span><span class="sxs-lookup"><span data-stu-id="fa718-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="fa718-124">Sunucu sertifikasını oluşturmak için Makecert.exe kullanın (veya Setup.bat çalıştırın).</span><span class="sxs-lookup"><span data-stu-id="fa718-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="fa718-125">IIS Yöneticisi 'ni çalıştırın ve önceki adımlara göre sertifikayı yükler.</span><span class="sxs-lookup"><span data-stu-id="fa718-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="fa718-126">Aşağıdaki kod satırını istemci programına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa718-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fa718-127">Bu kod yalnızca Makecert.exe tarafından oluşturulanlar gibi test sertifikaları için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fa718-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="fa718-128">Üretim kodu için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="fa718-128">It is not recommended for production code.</span></span>  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="fa718-129">IIS 7,0 (Windows Vista ve Windows Server 2008) üzerinde IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="fa718-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="fa718-130">**Başlat** menüsünde **Çalıştır**' a tıklayın ve ardından Internet INFORMATION SERVICES (IIS) MMC ek bileşenini açmak için **inetmgr** yazın.</span><span class="sxs-lookup"><span data-stu-id="fa718-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="fa718-131">**Varsayılan Web sitesine** sağ tıklayın ve **bağlamaları Düzenle...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="fa718-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="fa718-132">**Site bağlamaları** Iletişim kutusunun **Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fa718-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="fa718-133">**Tür** açılır listesinden **https** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="fa718-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="fa718-134">**SSL sertifikası** açılır listesinden **servicemodelsamples-HTTPS-Server** ' ı seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="fa718-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="fa718-135">HTTPS adresini kullanarak bir tarayıcıda hizmete erişimi test edin `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="fa718-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa718-136">Yeni yüklediğiniz test sertifikası güvenilen bir sertifika olmadığından, bu sertifikayla güvenliği sağlanmış yerel web adreslerine gözatarken ek Internet Explorer güvenlik uyarılarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa718-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="fa718-137">Sertifikaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="fa718-137">Removing Certificates</span></span>  
  
- <span data-ttu-id="fa718-138">Internet Information Services yöneticisini daha önce yönlendirildiğinden kullanın, ancak bunu eklemek yerine sertifikayı veya bağlamayı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fa718-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="fa718-139">Aşağıdaki komutu kullanarak bilgisayar sertifikasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fa718-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
