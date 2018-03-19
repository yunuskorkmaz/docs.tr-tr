---
title: "Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2591cad6354ec40f1fb6ead265c84a67adf3eec8
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma
Bu dördüncü altı görev oluşturmak için gerekli olan bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulama. Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.  
  
 Bu konu, meta verilerini almak açıklar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oluşturmak için kullanın ve hizmeti bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmete erişim proxy. Bu görev, Visual Studio tarafından sağlanan hizmet Başvurusu Ekle işlevini kullanarak tamamlanır. Bu araç hizmetin MEX uç noktasından meta verileri alır ve yönetilen kaynak kodu dosyasının oluşturur istemci proxy dilinde (C# varsayılan olarak) seçtiniz. İstemci proxy oluşturma, yanı sıra aracı ayrıca oluşturur veya kendi uç noktaları birinde hizmetine bağlanmak için istemci uygulaması sağlayan istemci yapılandırma dosyası güncelleştirir.  
  
> [!NOTE]
>  Aynı zamanda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy sınıfı ve Visual Studio içinde hizmet Başvurusu Ekle kullanmak yerine yapılandırması oluşturmak için aracı.  
  
> [!WARNING]
>  Çağrılırken bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] öğesinden bir sınıf kitaplığı projesinde hizmet [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] otomatik olarak bir proxy ve ilişkili yapılandırma dosyası oluşturmak için hizmet Başvurusu Ekle özelliğini kullanabilirsiniz.  Yapılandırma dosyası sınıf kitaplığı proje tarafından kullanılmaz. Sınıf kitaplığı çağıracak yürütülebilir dosyası için app.config dosyasına oluşturulan yapılandırma dosyasında ayarları eklemeniz gerekir.  
  
 İstemci uygulaması hizmetiyle iletişim kurmak için oluşturulan proxy sınıfını kullanır. Bu yordamda açıklanan [nasıl yapılır: bir istemci kullanın](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
### <a name="to-create-a-windows-communication-foundation-client"></a>Bir Windows Communication Foundation istemcisi oluşturmak için  
  
1.  Başlarken çözüm seçerek, üzerinde sağ tıklayarak yeni bir konsol uygulama projesi oluşturma **Ekle**, **yeni proje**. İçinde **Yeni Proje Ekle** iletişim seçin sol tarafındaki iletişim **Windows** altında **C#** veya **VB**. İletişim kutusunun Orta kısım seçin **konsol uygulaması**. Proje adı `GettingStartedClient`.  
  
2.  Sağ tıklayarak GettingStartedClient projenin hedef çerçevesini .NET Framework 4.5 ayarlamak **GettingStartedClient** Çözüm Gezgini'nde seçerek **özellikleri**. Aşağı açılan kutusunda etiketli **hedef Framework** seçin **.NET Framework 4.5**. Hedef Framework'ü GettingStartedClient Proje Özellikleri iletişim kutusunda, biraz farklı VB projedir ayarı, tıklatın **derleme** sekmesinde ekranın sol tarafında ve ardından **Gelişmiş Derleme Seçenekleri** iletişim kutusunun sol alt köşesindeki düğmesi. Ardından **.NET Framework 4.5** açılır kutusunda etiketli **hedef Framework**.  
  
     Hedef Framework'ü ayarlanırsa, çözümü yeniden yüklemek Visual Studio 2011'e basın **Tamam** istendiğinde.  
  
3.  System.ServiceModel başvuru GettingStartedClient projeye sağ tıklayarak ekleyin **başvuru** klasörü altında Çözüm Gezgini'nde ve select GettingStartedClient proje **Ekle** Başvuru. İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki. Arama derlemeleri metin kutusuna yazın `System.ServiceModel`. İletişim kutusunun Orta kısım seçin **System.ServiceModel**, tıklatın **Ekle** düğmesine tıklayın ve **Kapat** düğmesi. Tıklayarak çözümü kaydetmek **Tümünü Kaydet** aşağıda ana menü düğmesi.  
  
4.  Sonraki wlll hesaplayıcı hizmetine hizmet başvurusu ekleyin. Bunu yapmadan önce GettingStartedHost konsol uygulamasını başlatmanız gerekir. Ana bilgisayar çalışmaya başladıktan sonra başvuruları klasörü altında Çözüm Gezgini'nde GettingStartedClient projeye sağ tıklayın ve hizmet Başvurusu Ekle iletişim kutusunun adres kutusuna aşağıdaki URL'de hizmet Başvurusu Ekle ve türünü seçin: HYPERLINK "http:/ / localhost:8000/ServiceModelSamples/hizmet "ServiceModelSamples/8000/hizmet ve tıklatın **Git** düğmesi. CalculatorService sonra hizmetleri liste kutusunda çift tıklatın CalculatorService görüntülenmesi gerekir ve onu genişletin ve hizmeti tarafından uygulanan Hizmet sözleşmeleri göster. Varsayılan ad olan ve'ı tıklatın bırakın **Tamam** düğmesi.  
  
     Visual Studio yeni bir öğe kullanarak bir hizmet için bir başvuru GettingStartedClient projesinin altındaki hizmeti başvuruları klasörü altında Çözüm Gezgini'nde görünecektir eklediğinizde.  Kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı bir kaynak kodu dosyasının ve app.config dosyası oluşturulur.  
  
     Komut satırı aracı kullanabilirsiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci kodu oluşturmak için uygun anahtarlara sahip. Aşağıdaki örnek kod dosyası ve hizmet için bir yapılandırma dosyası oluşturur. İlk örnek içinde VB proxy oluşturmak nasıl gösterir ve ikinci oluşturulan proxy C# ' ta gösterilmektedir:  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
 İstemci uygulaması hesaplayıcı hizmetini çağırmak için kullanacağı proxy oluşturdunuz. Serideki sonraki bölümüne geçin: [nasıl yapılır: bir istemci yapılandırma](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
