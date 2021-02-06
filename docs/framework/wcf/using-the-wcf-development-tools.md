---
description: 'Hakkında daha fazla bilgi edinin: WCF geliştirme araçlarını kullanma'
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: c96644fb66006447f6a05f6c08ea84fe2ed99ce8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631703"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="e91f2-103">WCF Geliştirme Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e91f2-103">Using the WCF Development Tools</span></span>

<span data-ttu-id="e91f2-104">Bu bölümde, WCFservice 'nizi geliştirirken size yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e91f2-104">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="e91f2-105">Kendi hizmetinizi hızlı bir şekilde oluşturmak için Visual Studio şablonlarını temel olarak kullanabilir, sonra da hizmetinize hata ayıklamak ve test etmek için WCF hizmeti otomatik ana bilgisayarı ve WCF test Istemcisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e91f2-105">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="e91f2-106">Bu araçlar birlikte hızlı ve sorunsuz bir hata ayıklama ve test çevrimi sağlar ve bir barındırma modeline erken bir aşamada yürütülmesi gereksinimini ortadan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e91f2-106">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="e91f2-107">Visual Studio 2017 ' den itibaren, WCF geliştirme araçları varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="e91f2-107">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="e91f2-108">Bu özellikleri kullanabilmeniz için, Visual Studio yükleyicisinde Windows Communication Foundation bileşeninin seçili olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e91f2-108">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="e91f2-109">WCF Geliştirici Araçları</span><span class="sxs-lookup"><span data-stu-id="e91f2-109">The WCF Developer Tools</span></span>  

 [<span data-ttu-id="e91f2-110">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="e91f2-110">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="e91f2-111">Visual Studio 'da önceden tanımlanmış Visual Studio projesi ve öğe şablonlarını kullanarak WCF Hizmetleri ve çevreleyen uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e91f2-111">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="e91f2-112">WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e91f2-112">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="e91f2-113">WCF hizmeti otomatik ana makinesi (WcfSvcHost.exe), uyguladık bir hizmeti otomatik olarak barındırmak ve test etmek için Visual Studio hata ayıklayıcısını (F5) başlatmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e91f2-113">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="e91f2-114">Ardından, olası hataları bulmak ve onarmak için WCF test Istemcisini (wcfTestClient.exe) veya kendi istemcinizi kullanarak hizmeti test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e91f2-114">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="e91f2-115">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e91f2-115">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="e91f2-116">WCF test Istemcisi (WcfTestClient.exe), rastgele türlerin parametrelerini girmenize, bu girişi hizmete göndermenize ve hizmetin geri gönderdiği yanıtı görüntülemenize olanak tanıyan bir GUI aracıdır.</span><span class="sxs-lookup"><span data-stu-id="e91f2-116">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="e91f2-117">WCF hizmeti otomatik ana bilgisayarı ile birleştirildiğinde sorunsuz bir hizmet testi deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e91f2-117">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="e91f2-118">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e91f2-118">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="e91f2-119">Panoda depolanan XML verileri, bir kod sayfasına yapıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e91f2-119">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="e91f2-120">Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e91f2-120">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="e91f2-121">Araçları yönetici olmadan kullanma ayrıcalığı</span><span class="sxs-lookup"><span data-stu-id="e91f2-121">Using the Tools without Administrator privilege</span></span>  

 <span data-ttu-id="e91f2-122">Yönetici ayrıcalıkları olmayan kullanıcıların WCF Hizmetleri geliştirmesine olanak tanımak için, http://+:8731/Design_Time_Addresses Visual Studio yüklemesi sırasında "" ad alanı için BIR ACL (Access Control listesi) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e91f2-122">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="e91f2-123">ACL, makinede oturum açmış tüm etkileşimli kullanıcıları içeren (UI) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e91f2-123">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="e91f2-124">Yöneticiler bu ACL 'ye kullanıcı ekleyebilir veya kaldırabilir veya ek bağlantı noktaları açabilir. Bu ACL, WCF veya WF şablonlarının varsayılan yapılandırmasında veri göndermesini ve almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e91f2-124">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="e91f2-125">Ayrıca, kullanıcıların, yönetici ayrıcalıkları vermeden WCF hizmeti otomatik ana bilgisayarını (wcfSvcHost.exe) kullanmasına de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e91f2-125">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="e91f2-126">Erişimi, yükseltilmiş yönetici hesabı altında Windows Vista 'daki Netsh.exe aracını kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e91f2-126">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="e91f2-127">Netsh.exe kullanmanın bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e91f2-127">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="e91f2-128">Netsh.exe hakkında daha fazla bilgi için bkz. [Netsh.exe aracını ve Command-Line anahtarlarını kullanma](/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="e91f2-128">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91f2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e91f2-129">See also</span></span>

- [<span data-ttu-id="e91f2-130">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="e91f2-130">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="e91f2-131">WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e91f2-131">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="e91f2-132">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e91f2-132">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
