---
title: SystemWebRouting Tümleştirme Örneği
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: a9f9dc871b92b8cd689234c79b09c98e38a2848d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650995"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="cfbbb-102">SystemWebRouting Tümleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="cfbbb-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="cfbbb-103">Bu örnek, sınıflarda barındırma katmanın tümleştirmesiyle gösterir <xref:System.Web.Routing> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="cfbbb-104">Sınıflarda <xref:System.Web.Routing> ad alanı, doğrudan fiziksel kaynağa karşılık gelmeyen URL'lerini kullanacak şekilde bir uygulama izin verin.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="cfbbb-105">Web yönlendirme kullanarak geri gerçek WCF hizmetleri ardından eşlenen HTTP sanal adresleri oluşturmak Geliştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="cfbbb-106">Bu, bir WCF hizmeti bir fiziksel dosya ya da kaynağa gerek kalmadan barındırılması gerekir veya hizmetleri gibi .html veya .aspx dosyaları içermeyen URL'lerle erişilmesi gerektiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="cfbbb-107">Bu örnek nasıl kullanılacağını gösterir <xref:System.Web.Routing.RouteTable> global.asax dosyasında tanımlanmış hizmetleri çalıştırmak için eşlenen sanal bir URI'leri oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
>  <span data-ttu-id="cfbbb-108">Sınıflarda <xref:System.Web.Routing> ad alanı yalnızca iş için HTTP üzerinden barındırılan hizmetler.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="cfbbb-109">Bu örnek, iki RSS akışlarını oluşturmak için WCF kullanır: bir `movies` akışı ve `channels` akış.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="cfbbb-110">URL'leri, hizmetleri etkinleştirmek için bir uzantı içermiyor ve kayıtlı `Application_Start` yöntemi `Global` türetilmiş sınıf <xref:System.Web.HttpApplication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfbbb-111">Bu örnek yalnızca Internet Information Services (IIS) 7.0 çalışır ve daha sonra IIS 6. 0 ' farklı bir yöntem uzantısız URL'lerin desteklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="cfbbb-112">Bu örneği indirmek için</span><span class="sxs-lookup"><span data-stu-id="cfbbb-112">To download this sample</span></span>
  
<span data-ttu-id="cfbbb-113">Bu örnek, bilgisayarınızda zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="cfbbb-114">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="cfbbb-115">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cfbbb-116">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cfbbb-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="cfbbb-117">To use this sample</span></span>  
  
1. <span data-ttu-id="cfbbb-118">Visual Studio kullanarak, WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="cfbbb-119">Çözümü çalıştırın ve Web geliştirme sunucusunu başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="cfbbb-120">Bir dizin için örnek listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="cfbbb-121">Hiçbir dosya .svc dosya uzantısına sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="cfbbb-122">Adres çubuğuna ekleyin `movies` URL'ye yapılır; bu nedenle BT'nin okur `http://localhost:[port]/movies` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="cfbbb-123">Film akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="cfbbb-124">Adres çubuğuna ekleyin `channels` URL'ye yapılır; bu nedenle olan okuma `http://localhost:[port]/channels` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="cfbbb-125">Kanalları akış tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="cfbbb-126">ALT + F4 tuşuna basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="cfbbb-127">Geliştirme Sunucusu çıkıldı değil, bildirim alanı simgesine sağ tıklayıp **Durdur**.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="cfbbb-128">IIS içinde barındırıldığında Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="cfbbb-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="cfbbb-129">Visual Studio kullanarak, WebRoutingIntegration.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="cfbbb-130">CTRL + SHIFT + B tuşlarına basarak projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="cfbbb-131">Internet Information Services (IIS) Yöneticisi'nde bir Web uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="cfbbb-132">IIS Yöneticisi'nde sağ tıklayın **varsayılan Web sitesi** seçip **uygulama ekleme**.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="cfbbb-133">İçin **diğer**, yazın `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="cfbbb-134">İçin **fiziksel yolu**, projenin içinde hizmet klasörü seçin.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="cfbbb-135">Tuşuna **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="cfbbb-136">Web uygulaması'nı sağ tıklatıp seçerek, uygulamayı başlatmak **uygulamasını Yönet** ardından **Gözat**.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="cfbbb-137">Adres çubuğuna ekleyin `movies` URL'ye yapılır; bu nedenle olan okuma `http://localhost:[port]/movies` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="cfbbb-138">Film akışı tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="cfbbb-139">Adres çubuğuna ekleyin `channels` URL'ye yapılır; bu nedenle olan okuma `http://localhost:[port]/channels` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="cfbbb-140">Kanalları akış tarayıcıda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="cfbbb-141">ALT + F4 tuşuna basarak Web tarayıcısını kapatın.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="cfbbb-142">Bu örnek, barındırma katman sınıfları ile oluşturma kapasitesine sahip olduğunu gösterir. <xref:System.Web.Routing> istekler HTTP üzerinden barındırılan hizmetlerin yönlendirme için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfbbb-143">Varsayılan uygulama havuzu sürüme güncelleştirmelisiniz [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] sürüm 2 ayarlarsanız.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-143">You must update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbbb-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfbbb-144">See also</span></span>

- [<span data-ttu-id="cfbbb-145">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="cfbbb-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
