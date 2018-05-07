---
title: Bir Web tarayıcısından hizmetine erişim (WCF Veri Hizmetleri Hızlı Başlangıç)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: b7fcead5eed2dd4c0c779d9a881563a39f88d094
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Bir Web tarayıcısından hizmetine erişim (WCF Veri Hizmetleri Hızlı Başlangıç)
Bu görevde, başlayacak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Visual Studio ve isteğe bağlı olarak Web tarayıcısında okuma akışı devre dışı bırakın. Sonra hizmet tanımı belge almak yanı sıra HTTP GET isteklerini sunulan kaynakları için bir Web tarayıcısı aracılığıyla göndererek veri hizmeti kaynaklara erişim.  
  
> [!NOTE]
>  Varsayılan olarak, Visual Studio otomatik-bir bağlantı noktası numarası atar `localhost` bilgisayarınızda URI. Bu görev bağlantı noktası numarasını kullanır `12345` URI örneklerde. Visual Studio projenizde belirli bağlantı noktası numarasını ayarlama hakkında daha fazla bilgi için bkz: [veri hizmeti oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Internet Explorer kullanarak varsayılan hizmet belgesini istemek için  
  
1.  Internet Explorer'da, gelen **Araçları** menüsünde, select **Internet Seçenekleri**, tıklatın **içerik** sekmesini tıklatın, **ayarları**ve temizleyin **Akış görüntülemek kapatma**.  
  
     Bu, okuma akışı devre dışı bırakıldığından emin hale getirir. Bu işlev devre dışı değil, Web tarayıcısı ham XML verileri görüntüleme yerine akışı XML olarak döndürülen AtomPub kodlanmış belge değerlendirir.  
  
    > [!NOTE]
    >  Tarayıcınız akışa ham XML verileri olarak görüntüleyemiyor, hala sayfası için kaynak kodunu olarak akış görüntüleyebiliyor olmalıdır.  
  
2.  Visual Studio'da uygulama hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
3.  Yerel bilgisayarda Web tarayıcısını açın. Adres çubuğunda aşağıdaki URI girin:  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     Bu, bu veri hizmeti tarafından sunulan varlık kümeleri listesi içeren varsayılan hizmet belgesini döndürür.  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a>Varlık erişmek için bir Web tarayıcısından kaynakları ayarlama  
  
1.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     Bu, Northwind örnek veritabanındaki tüm müşteriler kümesini döndürür.  
  
2.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     Belirli bir müşteri için bu varlık örneğini döndürür `ALFKI`.  
  
3.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     Bu müşteriler ve tüm siparişleri belirli bir müşteri için bir dizi döndürülecek siparişler arasındaki ilişkiyi geçtiğini `ALFKI`.  
  
4.  Web tarayıcınızın adres çubuğuna aşağıdaki URI girin:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     Bu belirli bir müşteriye ait siparişleri filtreler `ALFKI` böylece yalnızca belirli bir sırada sağlanan üzerinde tabanlı döndürülen `OrderID` değeri.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Başarıyla eriştiğiniz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir Web tarayıcısından HTTP GET veren tarayıcı ile belirtilen kaynaklara ister. Bir Web tarayıcısı istekleri adresleme söz dizimi ile denemek ve sonuçları görüntülemek için kolay bir yol sağlar. Ancak, bir üretim veri hizmeti genellikle bu yöntem tarafından erişilebilir değil. Genellikle, uygulamaların veri hizmeti uygulaması aracılığıyla etkileşim kodu veya komut dosyası dili. Ardından, ortak dil çalışma zamanı (CLR) nesneleri değilmiş gibi veri hizmeti kaynaklara erişmek için istemci kitaplıkları kullanan bir istemci uygulaması oluşturacak:  
  
 [.NET Framework İstemci Uygulaması Oluşturma](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti Kaynaklarına Erişme](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
