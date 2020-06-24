---
title: Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri hızlı başlangıç)
description: Visual Studio 'da WCF Veri Hizmetleri başlatmayı ve bir tarayıcıda akış okumayı devre dışı bırakmayı öğrenin. Hizmet tanımı belgesini alın ve veri hizmeti kaynaklarına erişin.
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 713436c31bc3f622c4f44a83e33fff3fcbba1c1c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247784"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri hızlı başlangıç)

Bu, WCF Veri Hizmetleri hızlı başlangıç görevinin ikinci görevidir. Bu görevde, Visual Studio 'dan WCF Veri Hizmetleri başlatır ve isteğe bağlı olarak Web tarayıcısında akış okumayı devre dışı bırakabilirsiniz. Daha sonra, sunulan kaynaklara bir Web tarayıcısı aracılığıyla HTTP GET istekleri göndererek hizmet tanımı belgesini alır ve veri hizmeti kaynaklarına erişebilirsiniz.

> [!NOTE]
> Varsayılan olarak, Visual Studio otomatik olarak bilgisayarınızdaki URI 'ye bir bağlantı noktası numarası atar `localhost` . Bu görev, URI örneklerde bağlantı noktası numarasını kullanır `12345` . Visual Studio projenizde belirli bir bağlantı noktası numarasının nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [veri hizmeti oluşturma](creating-the-data-service.md).

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Internet Explorer 'ı kullanarak varsayılan hizmet belgesini istemek için

1. Internet Explorer 'da, **Araçlar** menüsünde **Internet seçenekleri**' ni seçin, **içerik** sekmesine tıklayın, **Ayarlar**' a tıklayın ve **akış görüntülemeyi aç**' ı temizleyin.

     Bu, akış okuma 'nın devre dışı olduğundan emin olmanızı sağlar. Bu işlevi devre dışı bırakmayın, Web tarayıcısı ham XML verilerini görüntülemek yerine döndürülen AtomPub kodlu belgeyi bir XML akışı olarak değerlendirir.

    > [!NOTE]
    > Tarayıcınız akışı ham XML verileri olarak görüntüleyemediği takdirde sayfanın kaynak kodu olarak akışı yine de görüntüleyebilmelisiniz.

2. Visual Studio 'da uygulamada hata ayıklamayı başlatmak için **F5** tuşuna basın.

3. Yerel bilgisayarda bir Web tarayıcısı açın. Adres çubuğuna aşağıdaki URI 'yi girin:

    ```http
    http://localhost:12345/northwind.svc
    ```

     Bu, bu veri hizmetinin açığa çıkarılan varlık kümelerinin bir listesini içeren varsayılan hizmet belgesini döndürür.

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Bir Web tarayıcısından varlık kümesi kaynaklarına erişmek için

1. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     Bu, Northwind örnek veritabanındaki tüm müşterilerin bir kümesini döndürür.

2. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     Bu, belirli müşteri için bir varlık örneği döndürür `ALFKI` .

3. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     Bu, müşteriler ve siparişler arasındaki ilişkiyi, belirli bir müşteri için tüm siparişlerin bir kümesini döndürecek şekilde inceler `ALFKI` .

4. Web tarayıcınızın adres çubuğunda aşağıdaki URI 'yi girin:

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     Bu, belirtilen `ALFKI` değere göre yalnızca belirli bir sipariş döndürüldüğünden, belirli müşteriye ait olan siparişleri filtreler `OrderID` .

## <a name="next-steps"></a>Sonraki Adımlar

Bir Web tarayıcısından, belirtilen kaynaklara HTTP GET istekleri veren tarayıcıyla WCF Veri Hizmetleri başarıyla eriştiyseniz. Web tarayıcısı, isteklerin adreslenmesi ve sonuçları görüntülemek için kolay bir yol sağlar. Ancak, bu yöntem tarafından genel olarak bir üretim veri hizmetine erişilmez. Uygulamalar genellikle uygulama kodu veya komut dosyası dilleri aracılığıyla veri hizmetiyle etkileşime geçer. Daha sonra, veri hizmeti kaynaklarına erişmek için, ortak dil çalışma zamanı (CLR) nesneleri gibi istemci kitaplıklarını kullanan bir istemci uygulaması oluşturacaksınız:

> [!div class="nextstepaction"]
> [.NET Framework İstemci Uygulaması Oluşturma](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti Kaynaklarına Erişme](accessing-data-service-resources-wcf-data-services.md)
