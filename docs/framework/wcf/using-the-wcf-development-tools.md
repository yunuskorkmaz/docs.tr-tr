---
title: WCF Geliştirme Araçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: adaad28fee5d27976df4bf20bb54f70aec5c2daf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544628"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="8d9a1-102">WCF Geliştirme Araçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8d9a1-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="8d9a1-103">Bu bölümde, WCFservice 'nizi geliştirirken size yardımcı olabilecek Visual Studio geliştirme araçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="8d9a1-104">Kendi hizmetinizi hızlı bir şekilde oluşturmak için Visual Studio şablonlarını temel olarak kullanabilir, sonra da hizmetinize hata ayıklamak ve test etmek için WCF hizmeti otomatik ana bilgisayarı ve WCF test Istemcisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="8d9a1-105">Bu araçlar birlikte hızlı ve sorunsuz bir hata ayıklama ve test çevrimi sağlar ve bir barındırma modeline erken bir aşamada yürütülmesi gereksinimini ortadan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="8d9a1-106">Visual Studio 2017 ' den itibaren, WCF geliştirme araçları varsayılan olarak yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="8d9a1-107">Bu özellikleri kullanabilmeniz için, Visual Studio yükleyicisinde Windows Communication Foundation bileşeninin seçili olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="8d9a1-108">WCF Geliştirici Araçları</span><span class="sxs-lookup"><span data-stu-id="8d9a1-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="8d9a1-109">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="8d9a1-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="8d9a1-110">Visual Studio 'da önceden tanımlanmış Visual Studio projesi ve öğe şablonlarını kullanarak WCF Hizmetleri ve çevreleyen uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="8d9a1-111">WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="8d9a1-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="8d9a1-112">WCF hizmeti otomatik ana makinesi (WcfSvcHost.exe), uyguladık bir hizmeti otomatik olarak barındırmak ve test etmek için Visual Studio hata ayıklayıcısını (F5) başlatmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="8d9a1-113">Ardından, olası hataları bulmak ve onarmak için WCF test Istemcisini (wcfTestClient.exe) veya kendi istemcinizi kullanarak hizmeti test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="8d9a1-114">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="8d9a1-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="8d9a1-115">WCF test Istemcisi (WcfTestClient.exe), rastgele türlerin parametrelerini girmenize, bu girişi hizmete göndermenize ve hizmetin geri gönderdiği yanıtı görüntülemenize olanak tanıyan bir GUI aracıdır.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="8d9a1-116">WCF hizmeti otomatik ana bilgisayarı ile birleştirildiğinde sorunsuz bir hizmet testi deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="8d9a1-117">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d9a1-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="8d9a1-118">Panoda depolanan XML verileri, bir kod sayfasına yapıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="8d9a1-119">Verilerde tanımlanan sınıflar kod türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="8d9a1-120">Araçları yönetici olmadan kullanma ayrıcalığı</span><span class="sxs-lookup"><span data-stu-id="8d9a1-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="8d9a1-121">Yönetici ayrıcalıkları olmayan kullanıcıların WCF Hizmetleri geliştirmesine olanak tanımak için, http://+:8731/Design_Time_Addresses Visual Studio yüklemesi sırasında "" ad alanı için BIR ACL (Access Control listesi) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="8d9a1-122">ACL, makinede oturum açmış tüm etkileşimli kullanıcıları içeren (UI) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="8d9a1-123">Yöneticiler bu ACL 'ye kullanıcı ekleyebilir veya kaldırabilir veya ek bağlantı noktaları açabilir. Bu ACL, WCF veya WF şablonlarının varsayılan yapılandırmasında veri göndermesini ve almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="8d9a1-124">Ayrıca, kullanıcıların, yönetici ayrıcalıkları vermeden WCF hizmeti otomatik ana bilgisayarını (wcfSvcHost.exe) kullanmasına de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="8d9a1-125">Erişimi, yükseltilmiş yönetici hesabı altında Windows Vista 'daki Netsh.exe aracını kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="8d9a1-126">Netsh.exe kullanmanın bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="8d9a1-127">Netsh.exe hakkında daha fazla bilgi için bkz. [Netsh.exe aracını ve komut satırı anahtarlarını kullanma](/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="8d9a1-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d9a1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d9a1-128">See also</span></span>

- [<span data-ttu-id="8d9a1-129">WCF Visual Studio Şablonları</span><span class="sxs-lookup"><span data-stu-id="8d9a1-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="8d9a1-130">WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="8d9a1-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="8d9a1-131">WCF Test İstemcisi (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="8d9a1-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
