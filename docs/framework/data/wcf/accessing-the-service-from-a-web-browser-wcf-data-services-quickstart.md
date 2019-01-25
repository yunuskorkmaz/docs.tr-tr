---
title: Bir Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri Hızlı Başlangıç)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 15a74e47774c532e75eca8a60a1af3a3e4f03f58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591649"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="b8ecd-102">Bir Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri Hızlı Başlangıç)</span><span class="sxs-lookup"><span data-stu-id="b8ecd-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="b8ecd-103">Bu, WCF Veri Hizmetleri hızlı başlangıç ikinci görevdir.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="b8ecd-104">Bu görevde, Visual Studio'da WCF veri hizmetlerini başlatın ve isteğe bağlı olarak Web tarayıcısında akış okuma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="b8ecd-105">Ardından hizmet tanımı belgesi almak yanı sıra HTTP GET isteklerini sunulan kaynakları için bir Web tarayıcısı üzerinden göndererek veri hizmeti kaynaklarına erişim.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="b8ecd-106">Varsayılan olarak, Visual Studio otomatik-için bir bağlantı noktası numarası atar `localhost` bilgisayarınızda URI.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="b8ecd-107">Bu görev, bağlantı noktası numarası kullanır `12345` URI örneklerde.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="b8ecd-108">Visual Studio projenize bir özel bağlantı noktası numarasını ayarlama hakkında daha fazla bilgi için bkz. [veri hizmeti oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="b8ecd-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="b8ecd-109">Internet Explorer'ı kullanarak varsayılan hizmet belgesi istemek için</span><span class="sxs-lookup"><span data-stu-id="b8ecd-109">To request the default service document by using Internet Explorer</span></span>

1.  <span data-ttu-id="b8ecd-110">Internet Explorer'da gelen **Araçları** menüsünde **Internet Seçenekleri**, tıklayın **içerik** sekmesinde **ayarları**, temizleyin **Akış görüntülenirken kapatma**.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="b8ecd-111">Bu, okuma akışı devre dışı bırakıldığından emin sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="b8ecd-112">Bu işlev devre dışı bırakabilirim, Web tarayıcısı akışı ham XML verileri yerine XML olarak döndürülen AtomPub kodlanmış belge değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b8ecd-113">Ham XML verileri olarak akışa tarayıcınızın görüntüleyemiyorsanız yine de sayfası için kaynak kodu olarak akış görüntüleyebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2.  <span data-ttu-id="b8ecd-114">Visual Studio'da **F5** anahtar uygulamada hata ayıklamaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3.  <span data-ttu-id="b8ecd-115">Yerel bilgisayarda Web tarayıcısını açın.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="b8ecd-116">Adres çubuğunda, aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="b8ecd-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="b8ecd-117">Bu, bu veri hizmeti tarafından kullanıma sunulan varlık kümeleri listesini içeren varsayılan hizmet belgesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="b8ecd-118">Varlık erişmek için bir Web tarayıcısından kaynakları ayarlayın</span><span class="sxs-lookup"><span data-stu-id="b8ecd-118">To access entity set resources from a Web browser</span></span>

1.  <span data-ttu-id="b8ecd-119">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="b8ecd-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="b8ecd-120">Bu, Northwind örnek veritabanındaki tüm müşteriler bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-120">This returns a set of all customers in the Northwind sample database.</span></span>

2.  <span data-ttu-id="b8ecd-121">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="b8ecd-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="b8ecd-122">Belirli bir müşteri için bu varlık örneğini döndürür `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3.  <span data-ttu-id="b8ecd-123">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="b8ecd-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="b8ecd-124">Bu müşteriler ve siparişler bir dizi belirli bir müşteri için tüm siparişleri döndürmek için arasındaki ilişkiyi erişir `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4.  <span data-ttu-id="b8ecd-125">Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:</span><span class="sxs-lookup"><span data-stu-id="b8ecd-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="b8ecd-126">Bu belirli bir müşteriye ait siparişler filtreler `ALFKI` böylece belirli bir sırada sağlanan üzerinde göre döndürülen `OrderID` değeri.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b8ecd-127">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b8ecd-127">Next Steps</span></span>

<span data-ttu-id="b8ecd-128">WCF Veri Hizmetleri, tarayıcı veren HTTP GET istekleri için belirtilen kaynaklara ile bir Web tarayıcısından başarıyla eriştiğiniz.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="b8ecd-129">Bir Web tarayıcısı, isteği adresleme söz dizimi ile denemeler yapın ve sonuçları görüntülemek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="b8ecd-130">Ancak, bir üretim veri hizmeti, bu yöntem tarafından genellikle erişilmez.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="b8ecd-131">Genellikle, uygulamaların veri hizmeti uygulaması aracılığıyla etkileşim kodu veya komut dosyası dili.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="b8ecd-132">Ardından, ortak dil çalışma zamanı (CLR) nesneleri değilmiş gibi veri hizmeti kaynaklarına erişmek için istemci kitaplıkları kullanan bir istemci uygulaması oluşturacak:</span><span class="sxs-lookup"><span data-stu-id="b8ecd-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8ecd-133">.NET Framework İstemci Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8ecd-133">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="b8ecd-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8ecd-134">See also</span></span>

- [<span data-ttu-id="b8ecd-135">Veri Hizmeti Kaynaklarına Erişme</span><span class="sxs-lookup"><span data-stu-id="b8ecd-135">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
