---
title: "WCF Geliştirme Araçlarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9532363adafd492ca35e10e6d20c788ddf5b1d17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="cef0d-102">WCF Geliştirme Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="cef0d-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="cef0d-103">Bu bölümde açıklanmıştır [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] geliştirmeye yardımcı olabilecek geliştirme araçları, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]hizmeti.</span><span class="sxs-lookup"><span data-stu-id="cef0d-103">This section describes the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[indigo1](../../../includes/indigo1-md.md)] development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="cef0d-104">Kullanabilirsiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hızlı bir şekilde kendi hizmet oluşturmak için bir temel olarak şablonları kullanın. ardından [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti otomatik ana bilgisayarı ve [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci hata ayıklama ve hizmetinizi test etmek için Test.</span><span class="sxs-lookup"><span data-stu-id="cef0d-104">You can use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="cef0d-105">Bu araçları birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsü sağlar ve barındırma modeli için erken bir aşamada yürütmek için gereken engellemek.</span><span class="sxs-lookup"><span data-stu-id="cef0d-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="cef0d-106">WCF geliştirici araçları</span><span class="sxs-lookup"><span data-stu-id="cef0d-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="cef0d-107">WCF Visual Studio şablonları</span><span class="sxs-lookup"><span data-stu-id="cef0d-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="cef0d-108">Kullanabileceğiniz önceden tanımlanmış [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] proje ve öğe şablonlarını [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hızlı bir şekilde oluşturmak için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetler ve çevresindeki uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="cef0d-108">You can use the predefined [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project and item templates in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="cef0d-109">WCF hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="cef0d-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="cef0d-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmeti otomatik ana bilgisayarı (WcfSvcHost.exe) başlatmak verir [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] hata ayıklayıcı otomatik olarak ana bilgisayar ve uygulanan bir hizmeti test (F5).</span><span class="sxs-lookup"><span data-stu-id="cef0d-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="cef0d-111">Hizmetini kullanarak sınayabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test İstemcisi (wcfTestClient.exe) veya kendi istemci bulmak ve olası hataları düzeltmek için.</span><span class="sxs-lookup"><span data-stu-id="cef0d-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="cef0d-112">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="cef0d-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="cef0d-113">Test İstemcisi (WcfTestClient.exe) giriş parametreleri rastgele türler, hizmet ve hizmet yanıtı geri gönderir görünümü için giriş göndermek izin veren bir GUI aracıdır.</span><span class="sxs-lookup"><span data-stu-id="cef0d-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="cef0d-114">İle birleştirildiğinde deneyimi sınama sorunsuz bir hizmet sunar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti otomatik ana bilgisayarı.</span><span class="sxs-lookup"><span data-stu-id="cef0d-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="cef0d-115">XML'den veri türü sınıfları oluşturma</span><span class="sxs-lookup"><span data-stu-id="cef0d-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="cef0d-116">XML verileri Pano'ya depolanan bir kod sayfasına yapıştırılabilmesi için.</span><span class="sxs-lookup"><span data-stu-id="cef0d-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="cef0d-117">Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="cef0d-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="cef0d-118">Yönetici ayrıcalığı olmadan araçlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="cef0d-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="cef0d-119">Geliştirmek için yönetici ayrıcalığı olmayan kullanıcıların etkinleştirmek için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmetleri, bir ACL (erişim denetim listesi) oluşturulur "http://+:8731/Design_Time_Addresses" ad alanı için yüklemesi sırasında [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cef0d-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="cef0d-120">ACL hangi makineye oturum açmış etkileşimli kullanıcıların tümünü içerir (UI) ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cef0d-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="cef0d-121">Yöneticiler eklemek veya bu ACL'den kaldırmasına veya ek bağlantı noktalarını açın. Bu ACL varsayılan yapılandırmalarında veri alıp göndermek WCF veya WF şablonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="cef0d-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="cef0d-122">Ayrıca, kullanıcıların kullanmasını sağlar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet otomatik yönetici ayrıcalıklarını verme olmadan Konağı (wcfSvcHost.exe).</span><span class="sxs-lookup"><span data-stu-id="cef0d-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="cef0d-123">Erişim Netsh.exe aracını kullanarak değiştirebilirsiniz [!INCLUDE[wv](../../../includes/wv-md.md)] yükseltilmiş yönetici hesabı altında.</span><span class="sxs-lookup"><span data-stu-id="cef0d-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="cef0d-124">Netsh.exe kullanmaya ilişkin bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cef0d-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="cef0d-125">Netsh.exe, bkz: [Netsh.exe aracı ve komut satırı anahtarları kullanmayı](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="cef0d-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef0d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cef0d-126">See Also</span></span>  
 [<span data-ttu-id="cef0d-127">WCF Visual Studio şablonları</span><span class="sxs-lookup"><span data-stu-id="cef0d-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="cef0d-128">WCF hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="cef0d-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="cef0d-129">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="cef0d-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
