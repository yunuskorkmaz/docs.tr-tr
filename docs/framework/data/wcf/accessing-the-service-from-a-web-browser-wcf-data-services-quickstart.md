---
title: "Bir Web tarayıcısından hizmetine erişim (WCF Veri Hizmetleri Hızlı Başlangıç)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71beb254bf258da97207f14afca73cd68c6927ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="8ff8a-102">Bir Web tarayıcısından hizmetine erişim (WCF Veri Hizmetleri Hızlı Başlangıç)</span><span class="sxs-lookup"><span data-stu-id="8ff8a-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="8ff8a-103">Bu görevde, başlayacak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] gelen [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] ve isteğe bağlı olarak devre dışı bırak akışı okuma Web tarayıcısında.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-103">In this task, you will start the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="8ff8a-104">Sonra hizmet tanımı belge almak yanı sıra HTTP GET isteklerini sunulan kaynakları için bir Web tarayıcısı aracılığıyla göndererek veri hizmeti kaynaklara erişim.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-104">You will then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ff8a-105">Varsayılan olarak, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] otomatik atar bir bağlantı noktası numarası `localhost` bilgisayarınızda URI.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-105">By default, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="8ff8a-106">Bu görev bağlantı noktası numarasını kullanır `12345` URI örneklerde.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-106">This task uses the port number `12345` in the URI examples.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8ff8a-107">belirli bir bağlantı noktası numarasını ayarlama, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] proje bakın [veri hizmeti oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="8ff8a-107"> how to set a specific port number in your [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="8ff8a-108">Internet Explorer kullanarak varsayılan hizmet belgesini istemek için</span><span class="sxs-lookup"><span data-stu-id="8ff8a-108">To request the default service document by using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="8ff8a-109">Internet Explorer'da, gelen **Araçları** menüsünde, select **Internet Seçenekleri**, tıklatın **içerik** sekmesini tıklatın, **ayarları**ve temizleyin **Akış görüntülemek kapatma**.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-109">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>  
  
     <span data-ttu-id="8ff8a-110">Bu, okuma akışı devre dışı bırakıldığından emin hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-110">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="8ff8a-111">Bu işlev devre dışı değil, Web tarayıcısı ham XML verileri görüntüleme yerine akışı XML olarak döndürülen AtomPub kodlanmış belge değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-111">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ff8a-112">Tarayıcınız akışa ham XML verileri olarak görüntüleyemiyor, hala sayfası için kaynak kodunu olarak akış görüntüleyebiliyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-112">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>  
  
2.  <span data-ttu-id="8ff8a-113">İçinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], uygulamanın hata ayıklamayı başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-113">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], press the F5 key to start debugging the application.</span></span>  
  
3.  <span data-ttu-id="8ff8a-114">Yerel bilgisayarda Web tarayıcısını açın.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-114">Open a Web browser on the local computer.</span></span> <span data-ttu-id="8ff8a-115">Adres çubuğunda aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="8ff8a-115">In the address bar, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     <span data-ttu-id="8ff8a-116">Bu, bu veri hizmeti tarafından sunulan varlık kümeleri listesi içeren varsayılan hizmet belgesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-116">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="8ff8a-117">Varlık erişmek için bir Web tarayıcısından kaynakları ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ff8a-117">To access entity set resources from a Web browser</span></span>  
  
1.  <span data-ttu-id="8ff8a-118">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="8ff8a-118">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     <span data-ttu-id="8ff8a-119">Bu, Northwind örnek veritabanındaki tüm müşteriler kümesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-119">This returns a set of all customers in the Northwind sample database.</span></span>  
  
2.  <span data-ttu-id="8ff8a-120">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="8ff8a-120">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     <span data-ttu-id="8ff8a-121">Belirli bir müşteri için bu varlık örneğini döndürür `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-121">This returns an entity instance for the specific customer, `ALFKI`.</span></span>  
  
3.  <span data-ttu-id="8ff8a-122">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="8ff8a-122">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     <span data-ttu-id="8ff8a-123">Bu müşteriler ve tüm siparişleri belirli bir müşteri için bir dizi döndürülecek siparişler arasındaki ilişkiyi geçtiğini `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-123">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>  
  
4.  <span data-ttu-id="8ff8a-124">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="8ff8a-124">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     <span data-ttu-id="8ff8a-125">Bu belirli bir müşteriye ait siparişleri filtreler `ALFKI` böylece yalnızca belirli bir sırada sağlanan üzerinde tabanlı döndürülen `OrderID` değeri.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-125">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8ff8a-126">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="8ff8a-126">Next Steps</span></span>  
 <span data-ttu-id="8ff8a-127">Başarıyla eriştiğiniz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir Web tarayıcısından HTTP GET veren tarayıcı ile belirtilen kaynaklara ister.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-127">You have successfully accessed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="8ff8a-128">Bir Web tarayıcısı istekleri adresleme söz dizimi ile denemek ve sonuçları görüntülemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-128">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="8ff8a-129">Ancak, bir üretim veri hizmeti genellikle bu yöntem tarafından erişilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-129">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="8ff8a-130">Genellikle, uygulamaların veri hizmeti uygulaması aracılığıyla etkileşim kodu veya komut dosyası dili.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-130">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="8ff8a-131">Ardından, ortak dil çalışma zamanı (CLR) nesneleri değilmiş gibi veri hizmeti kaynaklara erişmek için istemci kitaplıkları kullanan bir istemci uygulaması oluşturacak:</span><span class="sxs-lookup"><span data-stu-id="8ff8a-131">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>  
  
 [<span data-ttu-id="8ff8a-132">.NET Framework İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ff8a-132">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ff8a-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ff8a-133">See Also</span></span>  
 [<span data-ttu-id="8ff8a-134">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="8ff8a-134">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
