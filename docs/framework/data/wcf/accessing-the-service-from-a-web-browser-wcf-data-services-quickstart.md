---
title: Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri hızlı başlangıç)
description: Visual Studio 'da WCF Veri Hizmetleri başlatmayı ve bir tarayıcıda akış okumayı devre dışı bırakmayı öğrenin. Hizmet tanımı belgesini alın ve veri hizmeti kaynaklarına erişin.
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 27b599b6bf28b2ee0810564a3fb73b14274467ff
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805551"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="2ee63-104">Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri hızlı başlangıç)</span><span class="sxs-lookup"><span data-stu-id="2ee63-104">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="2ee63-105">Bu, WCF Veri Hizmetleri hızlı başlangıç görevinin ikinci görevidir.</span><span class="sxs-lookup"><span data-stu-id="2ee63-105">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="2ee63-106">Bu görevde, Visual Studio 'dan WCF Veri Hizmetleri başlatır ve isteğe bağlı olarak Web tarayıcısında akış okumayı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ee63-106">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="2ee63-107">Daha sonra, sunulan kaynaklara bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek hizmet tanımı belgesini alır ve veri hizmeti kaynaklarına erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ee63-107">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="2ee63-108">Varsayılan olarak, Visual Studio otomatik olarak bilgisayarınızdaki URI 'ye bir bağlantı noktası numarası atar `localhost` .</span><span class="sxs-lookup"><span data-stu-id="2ee63-108">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="2ee63-109">Bu görev, URI örneklerde bağlantı noktası numarasını kullanır `12345` .</span><span class="sxs-lookup"><span data-stu-id="2ee63-109">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="2ee63-110">Visual Studio projenizde belirli bir bağlantı noktası numarasının nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [veri hizmeti oluşturma](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="2ee63-110">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="2ee63-111">Internet Explorer 'ı kullanarak varsayılan hizmet belgesini istemek için</span><span class="sxs-lookup"><span data-stu-id="2ee63-111">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="2ee63-112">Internet Explorer 'da, **Araçlar** menüsünde **Internet seçenekleri**' ni seçin, **içerik** sekmesine tıklayın, **Ayarlar**' a tıklayın ve **akış görüntülemeyi aç**' ı temizleyin.</span><span class="sxs-lookup"><span data-stu-id="2ee63-112">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="2ee63-113">Bu, akış okuma 'nın devre dışı olduğundan emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ee63-113">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="2ee63-114">Bu işlevi devre dışı bırakmayın, Web tarayıcısı ham XML verilerini görüntülemek yerine döndürülen AtomPub kodlu belgeyi bir XML akışı olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2ee63-114">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2ee63-115">Tarayıcınız akışı ham XML verileri olarak görüntüleyemediği takdirde sayfanın kaynak kodu olarak akışı yine de görüntüleyebilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2ee63-115">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="2ee63-116">Visual Studio 'da uygulamada hata ayıklamayı başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2ee63-116">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="2ee63-117">Yerel bilgisayarda bir Web tarayıcısı açın.</span><span class="sxs-lookup"><span data-stu-id="2ee63-117">Open a Web browser on the local computer.</span></span> <span data-ttu-id="2ee63-118">Adres çubuğuna aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="2ee63-118">In the address bar, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="2ee63-119">Bu, bu veri hizmetinin açığa çıkarılan varlık kümelerinin bir listesini içeren varsayılan hizmet belgesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ee63-119">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="2ee63-120">Bir Web tarayıcısından varlık kümesi kaynaklarına erişmek için</span><span class="sxs-lookup"><span data-stu-id="2ee63-120">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="2ee63-121">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="2ee63-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="2ee63-122">Bu, Northwind örnek veritabanındaki tüm müşterilerin bir kümesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ee63-122">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="2ee63-123">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="2ee63-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="2ee63-124">Bu, belirli müşteri için bir varlık örneği döndürür `ALFKI` .</span><span class="sxs-lookup"><span data-stu-id="2ee63-124">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="2ee63-125">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="2ee63-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="2ee63-126">Bu, müşteriler ve siparişler arasındaki ilişkiyi, belirli bir müşteri için tüm siparişlerin bir kümesini döndürecek şekilde inceler `ALFKI` .</span><span class="sxs-lookup"><span data-stu-id="2ee63-126">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="2ee63-127">Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:</span><span class="sxs-lookup"><span data-stu-id="2ee63-127">In the address bar of your Web browser, enter the following URI:</span></span>

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="2ee63-128">Bu, belirtilen `ALFKI` değere göre yalnızca belirli bir sipariş döndürüldüğünden, belirli müşteriye ait olan siparişleri filtreler `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="2ee63-128">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ee63-129">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="2ee63-129">Next Steps</span></span>

<span data-ttu-id="2ee63-130">Bir Web tarayıcısından, belirtilen kaynaklara HTTP GET istekleri veren tarayıcıyla WCF Veri Hizmetleri başarıyla eriştiyseniz.</span><span class="sxs-lookup"><span data-stu-id="2ee63-130">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="2ee63-131">Web tarayıcısı, isteklerin adreslenmesi ve sonuçları görüntülemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ee63-131">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="2ee63-132">Ancak, bu yöntem tarafından genel olarak bir üretim veri hizmetine erişilmez.</span><span class="sxs-lookup"><span data-stu-id="2ee63-132">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="2ee63-133">Uygulamalar genellikle uygulama kodu veya komut dosyası dilleri aracılığıyla veri hizmetiyle etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="2ee63-133">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="2ee63-134">Daha sonra, veri hizmeti kaynaklarına erişmek için, ortak dil çalışma zamanı (CLR) nesneleri gibi istemci kitaplıklarını kullanan bir istemci uygulaması oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="2ee63-134">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ee63-135">.NET Framework İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ee63-135">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="2ee63-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ee63-136">See also</span></span>

- [<span data-ttu-id="2ee63-137">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="2ee63-137">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
