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
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri hızlı başlangıç)

Bu, WCF Veri Hizmetleri hızlı başlangıç görevinin ikinci görevidir. Bu görevde, Visual Studio 'dan WCF Veri Hizmetleri başlatır ve isteğe bağlı olarak Web tarayıcısında akış okumayı devre dışı bırakabilirsiniz. Daha sonra, sunulan kaynaklara bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek hizmet tanımı belgesini alır ve veri hizmeti kaynaklarına erişebilirsiniz.

> [!NOTE]
> Varsayılan olarak, Visual Studio otomatik olarak bilgisayarınızdaki `localhost` URI 'ye bir bağlantı noktası numarası atar. Bu görev, URI örneklerde bağlantı `12345` noktası numarasını kullanır. Visual Studio projenizde belirli bir bağlantı noktası numarasının nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [veri hizmeti oluşturma](creating-the-data-service.md).

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Internet Explorer 'ı kullanarak varsayılan hizmet belgesini istemek için

1. Internet Explorer 'da, **Araçlar** menüsünde **Internet seçenekleri**' ni seçin, **içerik** sekmesine tıklayın, **Ayarlar**' a tıklayın ve **akış görüntülemeyi aç**' ı temizleyin.

     Bu, akış okuma 'nın devre dışı olduğundan emin olmanızı sağlar. Bu işlevi devre dışı bırakmayın, Web tarayıcısı ham XML verilerini görüntülemek yerine döndürülen AtomPub kodlu belgeyi bir XML akışı olarak değerlendirir.

    > [!NOTE]
    > Tarayıcınız akışı ham XML verileri olarak görüntüleyemediği takdirde sayfanın kaynak kodu olarak akışı yine de görüntüleyebilmelisiniz.

2. Visual Studio 'da uygulamada hata ayıklamayı başlatmak için **F5** tuşuna basın.

3. Yerel bilgisayarda bir Web tarayıcısı açın. Adres çubuğuna aşağıdaki URI 'yi girin:

    ```
    http://localhost:12345/northwind.svc
    ```

     Bu, bu veri hizmetinin açığa çıkarılan varlık kümelerinin bir listesini içeren varsayılan hizmet belgesini döndürür.

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Bir Web tarayıcısından varlık kümesi kaynaklarına erişmek için

1. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     Bu, Northwind örnek veritabanındaki tüm müşterilerin bir kümesini döndürür.

2. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     Bu, `ALFKI`belirli müşteri için bir varlık örneği döndürür.

3. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     Bu, müşteriler ve siparişler arasındaki ilişkiyi, belirli bir müşteri `ALFKI`için tüm siparişlerin bir kümesini döndürecek şekilde inceler.

4. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     Bu, belirtilen `OrderID` değere göre yalnızca belirli bir sipariş `ALFKI` döndürüldüğünden, belirli müşteriye ait olan siparişleri filtreler.

## <a name="next-steps"></a>Sonraki Adımlar

Bir Web tarayıcısından, belirtilen kaynaklara HTTP GET istekleri veren tarayıcıyla WCF Veri Hizmetleri başarıyla eriştiyseniz. Web tarayıcısı, isteklerin adreslenmesi ve sonuçları görüntülemek için kolay bir yol sağlar. Ancak, bu yöntem tarafından genel olarak bir üretim veri hizmetine erişilmez. Uygulamalar genellikle uygulama kodu veya komut dosyası dilleri aracılığıyla veri hizmetiyle etkileşime geçer. Daha sonra, veri hizmeti kaynaklarına erişmek için, ortak dil çalışma zamanı (CLR) nesneleri gibi istemci kitaplıklarını kullanan bir istemci uygulaması oluşturacaksınız:

> [!div class="nextstepaction"]
> [.NET Framework İstemci Uygulaması Oluşturma](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti Kaynaklarına Erişme](accessing-data-service-resources-wcf-data-services.md)
