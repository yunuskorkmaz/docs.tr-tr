---
title: Bir Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri Hızlı Başlangıç)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: 01184969b7bfcc0f68351db7c8daeebe79be583c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086119"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Bir Web tarayıcısından hizmete erişme (WCF Veri Hizmetleri Hızlı Başlangıç)

Bu, WCF Veri Hizmetleri hızlı başlangıç ikinci görevdir. Bu görevde, Visual Studio'da WCF veri hizmetlerini başlatın ve isteğe bağlı olarak Web tarayıcısında akış okuma devre dışı bırakın. Ardından hizmet tanımı belgesi almak yanı sıra HTTP GET isteklerini sunulan kaynakları için bir Web tarayıcısı üzerinden göndererek veri hizmeti kaynaklarına erişim.

> [!NOTE]
> Varsayılan olarak, Visual Studio otomatik-için bir bağlantı noktası numarası atar `localhost` bilgisayarınızda URI. Bu görev, bağlantı noktası numarası kullanır `12345` URI örneklerde. Visual Studio projenize bir özel bağlantı noktası numarasını ayarlama hakkında daha fazla bilgi için bkz. [veri hizmeti oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md).

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Internet Explorer'ı kullanarak varsayılan hizmet belgesi istemek için

1.  Internet Explorer'da gelen **Araçları** menüsünde **Internet Seçenekleri**, tıklayın **içerik** sekmesinde **ayarları**, temizleyin **Akış görüntülenirken kapatma**.

     Bu, okuma akışı devre dışı bırakıldığından emin sağlar. Bu işlev devre dışı bırakabilirim, Web tarayıcısı akışı ham XML verileri yerine XML olarak döndürülen AtomPub kodlanmış belge değerlendirir.

    > [!NOTE]
    > Ham XML verileri olarak akışa tarayıcınızın görüntüleyemiyorsanız yine de sayfası için kaynak kodu olarak akış görüntüleyebilir olmalıdır.

2.  Visual Studio'da **F5** anahtar uygulamada hata ayıklamaya başlayın.

3.  Yerel bilgisayarda Web tarayıcısını açın. Adres çubuğunda, aşağıdaki URI girin:

    ```
    http://localhost:12345/northwind.svc
    ```

     Bu, bu veri hizmeti tarafından kullanıma sunulan varlık kümeleri listesini içeren varsayılan hizmet belgesini döndürür.

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Varlık erişmek için bir Web tarayıcısından kaynakları ayarlayın

1.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     Bu, Northwind örnek veritabanındaki tüm müşteriler bir dizi döndürür.

2.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     Belirli bir müşteri için bu varlık örneğini döndürür `ALFKI`.

3.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     Bu müşteriler ve siparişler bir dizi belirli bir müşteri için tüm siparişleri döndürmek için arasındaki ilişkiyi erişir `ALFKI`.

4.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     Bu belirli bir müşteriye ait siparişler filtreler `ALFKI` böylece belirli bir sırada sağlanan üzerinde göre döndürülen `OrderID` değeri.

## <a name="next-steps"></a>Sonraki Adımlar

WCF Veri Hizmetleri, tarayıcı veren HTTP GET istekleri için belirtilen kaynaklara ile bir Web tarayıcısından başarıyla eriştiğiniz. Bir Web tarayıcısı, isteği adresleme söz dizimi ile denemeler yapın ve sonuçları görüntülemek için kolay bir yol sağlar. Ancak, bir üretim veri hizmeti, bu yöntem tarafından genellikle erişilmez. Genellikle, uygulamaların veri hizmeti uygulaması aracılığıyla etkileşim kodu veya komut dosyası dili. Ardından, ortak dil çalışma zamanı (CLR) nesneleri değilmiş gibi veri hizmeti kaynaklarına erişmek için istemci kitaplıkları kullanan bir istemci uygulaması oluşturacak:

> [!div class="nextstepaction"]
> [.NET Framework İstemci Uygulaması Oluşturma](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Ayrıca Bkz.

- [Veri Hizmeti Kaynaklarına Erişme](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
