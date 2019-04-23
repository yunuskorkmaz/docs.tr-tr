---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 1ffa3be4a6b8976ab978ea995e8b2c1faaacf0ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144644"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="ede05-102">WCF Geliştirme Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ede05-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="ede05-103">Bu bölümde, WCFservice geliştirmenize yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ede05-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="ede05-104">Visual Studio şablonları, kendi hizmetinizi hızla oluşturmak için bir temel kullanın. sonra hizmeti test etmek ve hata ayıklama için WCF hizmet otomatik konağı ve WCF Test İstemcisi'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ede05-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="ede05-105">Bu araçlar birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsünü sağlamak ve bir barındırma modeli için erken bir aşamada işleme gerek kullanımını.</span><span class="sxs-lookup"><span data-stu-id="ede05-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="ede05-106">WCF geliştirici araçları</span><span class="sxs-lookup"><span data-stu-id="ede05-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="ede05-107">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="ede05-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="ede05-108">WCF hizmetleri ve kapsayıcı uygulamaları hızlıca oluşturmak için Visual Studio'da önceden tanımlanmış Visual Studio'nun proje ve öğe şablonlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ede05-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="ede05-109">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="ede05-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="ede05-110">WCF hizmet otomatik ana bilgisayarı (WcfSvcHost.exe), Visual Studio hata ayıklayıcıyı otomatik olarak ana bilgisayar ve uyguladıysanız bir hizmeti test etmek için (F5) başlatmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ede05-110">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="ede05-111">Sonra hizmeti bulun ve olası hataları düzeltmek için WCF Test İstemcisi (wcfTestClient.exe) veya kendi istemci kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ede05-111">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="ede05-112">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="ede05-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="ede05-113">WCF Test İstemcisi (WcfTestClient.exe) giriş parametreleri rastgele türler, hizmet ve hizmet yanıtı geri gönderir görünümü girdi gönderme olanak tanıyan bir GUI aracıdır.</span><span class="sxs-lookup"><span data-stu-id="ede05-113">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="ede05-114">Bu test WCF hizmet otomatik konağı ile birleştirildiğinde deneyimi sorunsuz bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="ede05-114">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="ede05-115">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ede05-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="ede05-116">XML verileri Pano'ya depolanan bir kod sayfasına yapıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ede05-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="ede05-117">Verilerde tanımlanan sınıflar için kod türleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ede05-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="ede05-118">Yönetici ayrıcalığı olmayan araçları kullanarak</span><span class="sxs-lookup"><span data-stu-id="ede05-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="ede05-119">WCF hizmetleri geliştirmek yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için bir ACL (erişim denetim listesi) için ad alanı oluşturulan "http://+:8731/Design_Time_Addresses" Visual Studio yüklemesi sırasında.</span><span class="sxs-lookup"><span data-stu-id="ede05-119">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="ede05-120">ACL makinede oturum açan tüm etkileşimli kullanıcılar içerir (UI) için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ede05-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="ede05-121">Yöneticiler ekleyin veya bu ACL'SİNDEN kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL, varsayılan yapılandırmasında veri alıp göndermek WCF veya WF şablonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ede05-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="ede05-122">Ayrıca, kullanıcıların yönetici ayrıcalıkları vermeden WCF hizmet otomatik ana bilgisayarı (wcfSvcHost.exe) kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ede05-122">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="ede05-123">İçinde Netsh.exe aracını kullanarak erişimi değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında.</span><span class="sxs-lookup"><span data-stu-id="ede05-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="ede05-124">Netsh.exe kullanmaya bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ede05-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="ede05-125">Netsh.exe hakkında daha fazla bilgi için bkz: [Netsh.exe aracı ve komut satırı anahtarları nasıl kullanılacağını](https://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="ede05-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede05-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ede05-126">See also</span></span>

- [<span data-ttu-id="ede05-127">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="ede05-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)
- [<span data-ttu-id="ede05-128">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="ede05-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="ede05-129">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="ede05-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
