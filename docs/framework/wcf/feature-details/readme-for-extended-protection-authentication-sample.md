---
title: Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 19fe961e346874346485442bd0ba90badab5f79f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192479"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="36506-102">Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek</span><span class="sxs-lookup"><span data-stu-id="36506-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="36506-103">Genişletilmiş koruma, bir saldırgan ("adam-in--middle") istemci kimlik bilgileri yakalar ve bunları istemcinin hedeflenen sunucusundaki güvenli kaynaklara erişmek için kullandığı adam-de-adam (MITM) saldırılarına karşı korumak için bir güvenlik girişimidir.</span><span class="sxs-lookup"><span data-stu-id="36506-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="36506-104">Daha fazla bilgi için [kimlik doğrulamasına genel bakış için genişletilmiş koruma](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36506-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36506-105">Bu örnek yalnızca IIS üzerinde barındırıldığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="36506-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="36506-106">HTTPS desteklemediği için Visual Studio geliştirme sunucusu üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="36506-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="36506-107">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="36506-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="36506-108">IIS üzerinde Program Ekle/Kaldır makineden yükleme -> Windows özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="36506-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="36506-109">Windows kimlik doğrulamasını Windows özelliklerini aç: Internet Information Services World Wide Web Hizmetleri -> -> Güvenlik Windows kimlik doğrulaması ->.</span><span class="sxs-lookup"><span data-stu-id="36506-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="36506-110">HTTP etkinleştirmesini Windows özelliklerini aç: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="36506-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="36506-111">İstemcinin sunucuyla güvenli bir kanal oluşturmak için bu örneği gerektirir ve bu nedenle, Internet Information Services (IIS) Yöneticisi'nden yüklenebilecek bir sunucu sertifikası varlığını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="36506-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="36506-112">Açık IIS Yöneticisi -> sunucu sertifikaları (sekmesinden özelliği Görünüm).</span><span class="sxs-lookup"><span data-stu-id="36506-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="36506-113">Bu örnek sınama amacıyla bir otomatik olarak imzalanan sertifika oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36506-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="36506-114">(Internet Explorer'ı güvenli olmadığı hakkında sertifika istemek için istemiyorsanız, güvenilen kök sertifika yetkilisi depolarında yükleyebilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="36506-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="36506-115">Varsayılan Web sitesi için Eylemler bölmesine gidin.</span><span class="sxs-lookup"><span data-stu-id="36506-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="36506-116">Düzenle düğmesine Site bağlamaları ->.</span><span class="sxs-lookup"><span data-stu-id="36506-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="36506-117">Bir tür olarak HTTPS henüz varsa, bağlantı noktası numarası 443 ve Yukarıdaki adımda oluşturulan SSL sertifika atama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="36506-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="36506-118">Derleme hizmeti.</span><span class="sxs-lookup"><span data-stu-id="36506-118">Build the service.</span></span> <span data-ttu-id="36506-119">Bu sanal dizini IIS içinde sizin için (post yapı eylemi proje özelliklerinde belirtilen) oluşturur ve barındırılan Web olması için bir hizmet için gerektiği şekilde dll, .svc ve yapılandırma dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="36506-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="36506-120">IIS Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="36506-120">Open the IIS Manager.</span></span> <span data-ttu-id="36506-121">Önceki adımda oluşturduğunuz sanal dizini (ExtendedProtection) sağ tıklayın ve uygulama Dönüştür'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="36506-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="36506-122">Kimlik doğrulama modülünü, bu sanal dizin için IIS Yöneticisi'nde açın ve Windows kimlik doğrulamasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="36506-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="36506-123">Gelişmiş ayarları için Windows kimlik doğrulaması için bu sanal dizin açın ve aşağıdaki örnekte, her zaman ilgili ExtendedProtection ayarı ayarlandığından, gerekli ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="36506-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="36506-124">Hizmet URL'sini bir tarayıcı penceresinden erişerek test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36506-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="36506-125">Bu URL'yi bir çapraz makineden erişmek istiyorsanız, güvenlik duvarı tüm gelen HTTP ve HTTPS bağlantıları için açık olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="36506-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="36506-126">İstemci yapılandırma dosyasını açın ve sağlamak için tam makine adı \<istemci >- \<uç noktası >-<< full_machine_name >> değiştirerek, adresi özniteliği.</span><span class="sxs-lookup"><span data-stu-id="36506-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="36506-127">İstemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="36506-127">Run the client.</span></span> <span data-ttu-id="36506-128">İstemci hizmete güvenli bir kanal oluşturma ve arka planda altında genişletilmiş koruma kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="36506-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
