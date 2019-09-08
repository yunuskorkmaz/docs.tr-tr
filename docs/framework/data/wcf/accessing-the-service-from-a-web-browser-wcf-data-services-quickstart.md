---
title: Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri hızlı başlangıç)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: eb7f1c97722b45a93c310fb8bcbdb42beece2553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780534"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="676f5-102">Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri hızlı başlangıç)</span><span class="sxs-lookup"><span data-stu-id="676f5-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="676f5-103">Bu, WCF Veri Hizmetleri hızlı başlangıç görevinin ikinci görevidir.</span><span class="sxs-lookup"><span data-stu-id="676f5-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="676f5-104">Bu görevde, Visual Studio 'dan WCF Veri Hizmetleri başlatır ve isteğe bağlı olarak Web tarayıcısında akış okumayı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="676f5-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="676f5-105">Daha sonra, sunulan kaynaklara bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek hizmet tanımı belgesini alır ve veri hizmeti kaynaklarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="676f5-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="676f5-106">Varsayılan olarak, Visual Studio otomatik olarak bilgisayarınızdaki `localhost` URI 'ye bir bağlantı noktası numarası atar.</span><span class="sxs-lookup"><span data-stu-id="676f5-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="676f5-107">Bu görev, URI örneklerde bağlantı `12345` noktası numarasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="676f5-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="676f5-108">Visual Studio projenizde belirli bir bağlantı noktası numarasının nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [veri hizmeti oluşturma](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="676f5-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="676f5-109">Internet Explorer 'ı kullanarak varsayılan hizmet belgesini istemek için</span><span class="sxs-lookup"><span data-stu-id="676f5-109">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="676f5-110">Internet Explorer 'da, **Araçlar** menüsünde **Internet seçenekleri**' ni seçin, **içerik** sekmesine tıklayın, **Ayarlar**' a tıklayın ve **akış görüntülemeyi aç**' ı temizleyin.</span><span class="sxs-lookup"><span data-stu-id="676f5-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="676f5-111">Bu, akış okuma 'nın devre dışı olduğundan emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="676f5-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="676f5-112">Bu işlevi devre dışı bırakmayın, Web tarayıcısı ham XML verilerini görüntülemek yerine döndürülen AtomPub kodlu belgeyi bir XML akışı olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="676f5-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="676f5-113">Tarayıcınız akışı ham XML verileri olarak görüntüleyemediği takdirde sayfanın kaynak kodu olarak akışı yine de görüntüleyebilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="676f5-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="676f5-114">Visual Studio 'da uygulamada hata ayıklamayı başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="676f5-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="676f5-115">Yerel bilgisayarda bir Web tarayıcısı açın.</span><span class="sxs-lookup"><span data-stu-id="676f5-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="676f5-116">Adres çubuğuna aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="676f5-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="676f5-117">Bu, bu veri hizmetinin açığa çıkarılan varlık kümelerinin bir listesini içeren varsayılan hizmet belgesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="676f5-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="676f5-118">Bir Web tarayıcısından varlık kümesi kaynaklarına erişmek için</span><span class="sxs-lookup"><span data-stu-id="676f5-118">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="676f5-119">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="676f5-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="676f5-120">Bu, Northwind örnek veritabanındaki tüm müşterilerin bir kümesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="676f5-120">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="676f5-121">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="676f5-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="676f5-122">Bu, `ALFKI`belirli müşteri için bir varlık örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="676f5-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="676f5-123">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="676f5-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="676f5-124">Bu, müşteriler ve siparişler arasındaki ilişkiyi, belirli bir müşteri `ALFKI`için tüm siparişlerin bir kümesini döndürecek şekilde inceler.</span><span class="sxs-lookup"><span data-stu-id="676f5-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="676f5-125">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="676f5-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="676f5-126">Bu, belirtilen `OrderID` değere göre yalnızca belirli bir sipariş `ALFKI` döndürüldüğünden, belirli müşteriye ait olan siparişleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="676f5-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="676f5-127">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="676f5-127">Next Steps</span></span>

<span data-ttu-id="676f5-128">Bir Web tarayıcısından, belirtilen kaynaklara HTTP GET istekleri veren tarayıcıyla WCF Veri Hizmetleri başarıyla eriştiyseniz.</span><span class="sxs-lookup"><span data-stu-id="676f5-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="676f5-129">Web tarayıcısı, isteklerin adreslenmesi ve sonuçları görüntülemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="676f5-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="676f5-130">Ancak, bu yöntem tarafından genel olarak bir üretim veri hizmetine erişilmez.</span><span class="sxs-lookup"><span data-stu-id="676f5-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="676f5-131">Uygulamalar genellikle uygulama kodu veya komut dosyası dilleri aracılığıyla veri hizmetiyle etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="676f5-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="676f5-132">Daha sonra, veri hizmeti kaynaklarına erişmek için, ortak dil çalışma zamanı (CLR) nesneleri gibi istemci kitaplıklarını kullanan bir istemci uygulaması oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="676f5-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="676f5-133">.NET Framework İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="676f5-133">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="676f5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="676f5-134">See also</span></span>

- [<span data-ttu-id="676f5-135">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="676f5-135">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
