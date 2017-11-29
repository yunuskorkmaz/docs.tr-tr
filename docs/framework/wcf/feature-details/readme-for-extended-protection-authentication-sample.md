---
title: "Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3981a0d0c82b8bc35536a9afd702e753fcf07db5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="7798d-102">Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek</span><span class="sxs-lookup"><span data-stu-id="7798d-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="7798d-103">Genişletilmiş koruma, bir saldırgan ("man-in--middle") istemci kimlik bilgilerini yakalar ve bunları istemcinin hedeflenen sunucuda güvenlikli kaynaklara erişmek için kullandığı man-in--middle (MITM) saldırılarına karşı korumak için bir güvenlik girişimidir.</span><span class="sxs-lookup"><span data-stu-id="7798d-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="7798d-104">Daha fazla bilgi için bkz: [kimlik doğrulamasına genel bakış için genişletilmiş koruma](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7798d-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7798d-105">Bu örnek yalnızca IIS üzerinde barındırıldığında çalışır.</span><span class="sxs-lookup"><span data-stu-id="7798d-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="7798d-106">HTTPS desteklemediği için Visual Studio geliştirme sunucusu üzerinde çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="7798d-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7798d-107">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="7798d-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="7798d-108">Program Ekle/Kaldır makinede yükleme IIS -> Windows özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="7798d-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="7798d-109">Windows özelliklerinde Windows kimlik doğrulamasını etkinleştirmek: Internet Information Services World Wide Web Hizmetleri -> Güvenlik -> Windows kimlik doğrulaması ->.</span><span class="sxs-lookup"><span data-stu-id="7798d-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="7798d-110">HTTP etkinleştirme Windows özelliklerini aç: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="7798d-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="7798d-111">Bu örnek sunucu ile güvenli bir kanal oluşturmak için istemcinin gerektirir ve bu nedenle, Internet Information Services (IIS) Yöneticisi'nden yüklenebilecek bir sunucu sertifikası varlığını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7798d-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="7798d-112">Açık IIS Yöneticisi'ni -> sunucu sertifikaları (sekmesinden özelliği Görünüm).</span><span class="sxs-lookup"><span data-stu-id="7798d-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="7798d-113">Bu örnek test amacıyla, otomatik olarak imzalanan sertifika oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7798d-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="7798d-114">(Internet Explorer'ı güvenli olmadığı sertifika hakkında soracak şekilde istemiyorsanız, güvenilen kök sertifika yetkilisi depolarında yükleyebilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="7798d-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="7798d-115">Varsayılan Web sitesi için Eylemler bölmesine gidin.</span><span class="sxs-lookup"><span data-stu-id="7798d-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="7798d-116">Düzenle'yi tıklatın Site bağlamaları ->.</span><span class="sxs-lookup"><span data-stu-id="7798d-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="7798d-117">HTTPS türü olarak zaten değilse, bağlantı noktası numarası 443 sunmak ve Yukarıdaki adımda oluşturulan SSL sertifika atama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7798d-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="7798d-118">Hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7798d-118">Build the service.</span></span> <span data-ttu-id="7798d-119">Bu sanal dizin IIS'de sizin için (eylemden proje özelliklerinde belirtilen post yapı) oluşturur ve barındırılan Web olması için bir hizmet için gerektiği şekilde dll, .svc ve yapılandırma dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7798d-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="7798d-120">IIS Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="7798d-120">Open the IIS Manager.</span></span> <span data-ttu-id="7798d-121">Önceki adımda oluşturduğunuz sanal dizinini (ExtendedProtection) sağ tıklatın ve uygulama Dönüştür seçin.</span><span class="sxs-lookup"><span data-stu-id="7798d-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="7798d-122">Kimlik doğrulama modülü bu sanal dizin için IIS Yöneticisi'nde açın ve Windows kimlik doğrulamasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7798d-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="7798d-123">Gelişmiş ayarlar için Windows kimlik doğrulaması için bu sanal dizin açın ve aşağıdaki örnekte, her zaman karşılık gelen ExtendedProtection ayarı ayarlandığından, gerekli ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7798d-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="7798d-124">Hizmet URL'sini bir tarayıcı penceresinde erişerek test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7798d-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="7798d-125">Bu URL çapraz bir makineden erişmek Güvenlik Duvarı tüm gelen HTTP ve HTTPS bağlantıları için açıldığında emin olun.</span><span class="sxs-lookup"><span data-stu-id="7798d-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="7798d-126">İstemci yapılandırma dosyasını açın ve için tam makine ad \<istemci >- \<uç noktası >-adresi özniteliğinin, << full_machine_name >> değiştirme.</span><span class="sxs-lookup"><span data-stu-id="7798d-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="7798d-127">İstemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7798d-127">Run the client.</span></span> <span data-ttu-id="7798d-128">İstemci hizmete güvenli bir kanal oluşturma ve genişletilmiş koruma kapsar altında kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="7798d-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
