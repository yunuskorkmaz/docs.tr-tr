---
title: 'Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 9e6d75bf8911a3c36e63b3bc108faae823434d1d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510005"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma

Dördüncü altı görev bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur. Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.

Bu konuda, bir WCF hizmetinden meta verileri alma ve hizmete erişmek bir WCF proxy oluşturulacağı açıklanmaktadır. Bu görevi, Visual Studio tarafından sağlanan hizmet Başvurusu Ekle işlevini kullanarak tamamlanır. Bu araç, hizmetin MEX uç noktasından meta verileri alır ve yönetilen kaynak kodu dosyası oluşturur bir istemci proxy dilde (C# varsayılan olarak) seçtiniz. İstemci proxy oluşturma, ek araç ayrıca oluşturur veya kendi uç birinde hizmetine bağlanmak istemci uygulamasını etkinleştiren istemci yapılandırma dosyasını güncelleştirir.

> [!NOTE]
> Ayrıca [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını hizmet Başvurusu Ekle Visual Studio içinde kullanmak yerine, yapılandırma ve proxy sınıfı oluşturmak için.

> [!WARNING]
> Bir WCF hizmeti bir sınıf kitaplığı projesinde çağrılırken [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] otomatik olarak bir ara sunucu ve ilişkili yapılandırma dosyasını oluşturmak için hizmet Başvurusu Ekle özelliğini kullanabilirsiniz.  Yapılandırma dosyasını sınıf kitaplığı projesi tarafından kullanılmıyor. Sınıf kitaplığı çağıran yürütülebilir dosyası için app.config dosyasına, oluşturulan yapılandırma dosyasında ayarları eklemeniz gerekir.

 İstemci uygulama hizmeti ile iletişim kurmak için oluşturulan proxy sınıfını kullanır. Bu yordamda açıklanan [nasıl yapılır: istemci kullanma](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>Bir Windows Communication Foundation istemcisi oluşturmak için

1.  Başlarken çözümü seçerken üzerinde sağ tıklayarak yeni bir konsol uygulama projesi oluşturma **Ekle**, **yeni proje**. İçinde **Yeni Proje Ekle** sol tarafındaki iletişim Seç iletişim **Windows** altında **C#** veya **VB**. İletişim kutusunun orta kısmını seçin **konsol uygulaması**. Projeyi adlandırın `GettingStartedClient`.

2.  GettingStartedClient projenin hedef çerçevesi sağ tıklanarak .NET Framework 4.5 olarak ayarlayın. **GettingStartedClient** Çözüm Gezgini'nde seçerek **özellikleri**. Açılan kutuda yer etiketli **hedef Framework'ü** seçin **.NET Framework 4.5**. Hedef Framework'ü ayarı GettingStartedClient Proje Özellikleri iletişim kutusunda bir VB projesi biraz farklıdır, tıklayın **derleme** sekmesinde ekranın sol tarafındaki ve ardından **Gelişmiş Derleme Seçenekleri** iletişim kutusunun sol alt köşesindeki düğme. Ardından **.NET Framework 4.5** kutuda etiketli **hedef Framework'ü**.

     Hedef Framework'ü ayarlama, çözümü yeniden yüklemek Visual Studio 2011 neden basın **Tamam** istendiğinde.

3.  System.ServiceModel başvuru GettingStartedClient projeye sağ tıklayarak ekleyin **başvuru** klasörü altında Çözüm Gezgini seçip GettingStartedClient proje **Ekle** Başvuru. İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki. Derlemeleri arama metin kutusuna yazın `System.ServiceModel`. İletişim kutusunun orta kısmını seçin **System.ServiceModel**, tıklayın **Ekle** düğmesini **Kapat** düğmesi. Çözüm Kaydet'e tıklayarak **Tümünü Kaydet** aşağıda ana menü düğmesi.

4.  Ardından bir hesap makinesi hizmetine hizmet başvurusu ekleyin. Bunu yapmadan önce GettingStartedHost konsol uygulamasını başlatmanız gerekir. Konak çalıştırıldıktan sonra sağ **başvuruları** klasörü altında GettingStartedClient projede **Çözüm Gezgini** seçip **Ekle**  >   **Hizmet başvurusu**. Adres kutusuna şu URL'yi yazın **hizmet Başvurusu Ekle** iletişim: [ http://localhost:8000/ServiceModelSamples/Service ](http://localhost:8000/ServiceModelSamples/Service) tıklatıp **Git** düğmesi. CalculatorService Hizmetleri liste kutusunda sonra görüntülenmelidir. CalculatorService çift tıklayın ve onu genişletin ve hizmeti tarafından uygulanan hizmet sözleşmelerini gösterir. Varsayılan ad olan ve'ı tıklatın bırakın **Tamam** düğmesi.

     Yeni bir öğe Visual Studio kullanarak bir hizmet başvurusu GettingStartedClient projesi altındaki hizmet başvuruları klasörünün altında Çözüm Gezgini'nde görünür eklerken.  Kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı bir kaynak kodu dosyası ve app.config dosyası oluşturulur.

     Komut satırı aracını da kullanabilirsiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci kodu oluşturmak için uygun anahtarlara sahip. Aşağıdaki örnek, bir kod dosyası ve hizmet için bir yapılandırma dosyası oluşturur. İlk örnek VB proxy oluşturma işlemini gösterir ve ikinci oluşturulan proxy C# ' de gösterilmiştir:

    ```
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service
    ```

    ```csharp
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service
    ```

 İstemci uygulamanızın hesaplayıcı hizmeti çağırmak için kullanacağı Ara oluşturdunuz. Serideki sonraki konuya geçin: [nasıl yapılır: istemci yapılandırma](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Ayrıca Bkz.

- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
