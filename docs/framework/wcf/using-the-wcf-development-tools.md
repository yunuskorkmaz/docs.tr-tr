---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 41d2ee2881b79ffb086a931ec6d271d409ac66db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806789"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="dccb2-102">WCF Geliştirme Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="dccb2-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="dccb2-103">Bu bölümde, WCFservice geliştirmeye yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dccb2-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="dccb2-104">Hızlı bir şekilde kendi hizmet oluşturmak için temel olarak Visual Studio şablonları kullanın, sonra WCF hizmeti otomatik ana bilgisayarı ve WCF Test İstemcisi hata ayıklama ve hizmetinizi sınamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dccb2-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="dccb2-105">Bu araçları birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsü sağlar ve barındırma modeli için erken bir aşamada yürütmek için gereken engellemek.</span><span class="sxs-lookup"><span data-stu-id="dccb2-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="dccb2-106">WCF geliştirici araçları</span><span class="sxs-lookup"><span data-stu-id="dccb2-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="dccb2-107">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="dccb2-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="dccb2-108">WCF hizmetleri ve çevresindeki uygulamaları hızlı bir şekilde oluşturmak için Visual Studio içindeki önceden tanımlanmış Visual Studio Proje ve öğe şablonları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dccb2-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="dccb2-109">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="dccb2-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="dccb2-110">WCF hizmeti otomatik ana bilgisayarı (WcfSvcHost.exe), Visual Studio hata ayıklayıcısı (F5) otomatik olarak ana bilgisayar ve uygulamış olan bir hizmeti test başlatma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="dccb2-110">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="dccb2-111">Ardından hizmetini bulun ve olası hataları düzeltmek için WCF Test İstemcisi (wcfTestClient.exe) veya kendi istemci kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dccb2-111">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="dccb2-112">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="dccb2-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="dccb2-113">WCF Test İstemcisi (WcfTestClient.exe) giriş parametreleri rastgele türler, hizmet ve hizmet yanıtı geri gönderir görünümü için giriş göndermek izin veren bir GUI aracıdır.</span><span class="sxs-lookup"><span data-stu-id="dccb2-113">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="dccb2-114">WCF hizmet otomatik ana bilgisayarı ile birleştirildiğinde deneyimi sınama sorunsuz bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="dccb2-114">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="dccb2-115">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dccb2-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="dccb2-116">XML verileri Pano'ya depolanan bir kod sayfasına yapıştırılabilmesi için.</span><span class="sxs-lookup"><span data-stu-id="dccb2-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="dccb2-117">Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dccb2-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="dccb2-118">Yönetici ayrıcalığı olmadan araçlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="dccb2-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="dccb2-119">WCF hizmetlerini geliştirmek yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için bir ACL (erişim denetim listesi) ad alanı için oluşturulan "http://+:8731/Design_Time_Addresses" Visual Studio yüklemesi sırasında.</span><span class="sxs-lookup"><span data-stu-id="dccb2-119">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="dccb2-120">ACL hangi makineye oturum açmış etkileşimli kullanıcıların tümünü içerir (UI) ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dccb2-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="dccb2-121">Yöneticiler eklemek veya bu ACL'den kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL varsayılan yapılandırmalarında veri alıp göndermek WCF veya WF şablonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="dccb2-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="dccb2-122">Ayrıca, kullanıcıların yönetici ayrıcalıklarını verme olmadan WCF hizmeti otomatik ana bilgisayarı (wcfSvcHost.exe) kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dccb2-122">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="dccb2-123">Erişim Netsh.exe aracını kullanarak değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında.</span><span class="sxs-lookup"><span data-stu-id="dccb2-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="dccb2-124">Netsh.exe kullanmaya ilişkin bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dccb2-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="dccb2-125">Netsh.exe hakkında daha fazla bilgi için bkz: [Netsh.exe aracı ve komut satırı anahtarları kullanmayı](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="dccb2-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccb2-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dccb2-126">See Also</span></span>  
 [<span data-ttu-id="dccb2-127">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="dccb2-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="dccb2-128">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="dccb2-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="dccb2-129">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="dccb2-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
