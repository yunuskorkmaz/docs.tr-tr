---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183074"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="f0cb4-102">WCF Geliştirme Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f0cb4-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="f0cb4-103">Bu bölümde, WCFservice geliştirmede size yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="f0cb4-104">Kendi hizmetinizi hızlı bir şekilde oluşturmak için Visual Studio şablonlarını temel olarak kullanabilir, ardından servisinizi hata ayıklamak ve test etmek için WCF Service Auto Host ve WCF Test İstemci'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="f0cb4-105">Bu araçlar birlikte hızlı ve sorunsuz hata ayıklama ve test döngüsü sağlar ve erken bir aşamada bir barındırma modeline bağlanma gereksinimini önler.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="f0cb4-106">Visual Studio 2017 ile başlayarak, WCF geliştirme araçları varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="f0cb4-107">Bu özellikleri kullanabilmek için Visual Studio yükleyicisinde Windows Communication Foundation bileşeninin seçildiğinden emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="f0cb4-108">WCF Geliştirici Araçları</span><span class="sxs-lookup"><span data-stu-id="f0cb4-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="f0cb4-109">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="f0cb4-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="f0cb4-110">WCF hizmetleri ve çevresindeki uygulamaları hızla oluşturmak için Visual Studio'daki önceden tanımlanmış Visual Studio projesini ve öğe şablonlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="f0cb4-111">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="f0cb4-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="f0cb4-112">WCF Service Auto Host (WcfSvcHost.exe), uyguladığınız bir hizmeti otomatik olarak barındırmak ve test etmek için Visual Studio hata ayıklama (F5) başlatmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="f0cb4-113">Daha sonra olası hataları bulmak ve düzeltmek için WCF Test İstemcisini (wcfTestClient.exe) veya kendi istemcinizi kullanarak hizmeti test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="f0cb4-114">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="f0cb4-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="f0cb4-115">WCF Test İstemci (WcfTestClient.exe), rasgele türlerin parametrelerini gireyapmanızı, bu girişi hizmete göndermenizi ve hizmetin geri gönderdiği yanıtı görüntülemenizi sağlayan bir GUI aracıdır.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="f0cb4-116">WCF Service Auto Host ile birleştirildiğinde sorunsuz bir hizmet testi deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="f0cb4-117">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0cb4-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="f0cb4-118">Panoda depolanan XML verileri bir kod sayfasına yapıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="f0cb4-119">Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="f0cb4-120">Yönetici ayrıcalığı olmadan Araçları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f0cb4-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="f0cb4-121">Yönetici ayrıcalığına sahip olmayan kullanıcıların WCF hizmetlerini geliştirmesini sağlamak için Visual Studio'nun kurulumu sırasında " "http://+:8731/Design_Time_Addressesad alanı için bir ACL (Erişim Denetim Listesi) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="f0cb4-122">ACL, makinede oturum açan tüm etkileşimli kullanıcıları içeren (UI) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="f0cb4-123">Yöneticiler kullanıcıları bu ACL'den ekleyebilir veya kaldırabilir veya ek bağlantı noktaları açabilir. Bu ACL, WCF veya WF şablonlarının varsayılan yapılandırmalarında veri gönderip almalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="f0cb4-124">Ayrıca, kullanıcıların WCF Service Auto Host'u (wcfSvcHost.exe) yönetici ayrıcalıkları vermeden kullanmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="f0cb4-125">Windows Vista'daki Netsh.exe aracını kullanarak erişimi yükseltilmiş yönetici hesabı altında değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="f0cb4-126">Aşağıda Netsh.exe kullanarak bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="f0cb4-127">Netsh.exe hakkında daha fazla bilgi için [Netsh.exe Aracı ve Komut Satırı Anahtarları Nasıl Kullanılır'](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))a bakın.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cb4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0cb4-128">See also</span></span>

- [<span data-ttu-id="f0cb4-129">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="f0cb4-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="f0cb4-130">WCF Hizmet Konağı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="f0cb4-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="f0cb4-131">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="f0cb4-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
