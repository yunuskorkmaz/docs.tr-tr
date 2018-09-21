---
title: 'Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma'
ms.date: 09/14/2018
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 1eadb5008575a1a53d685db14d68e42d0dce1360
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478298"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a>Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma

Dördüncü altı görev bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur. Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.

Bu konuda, bir WCF hizmetinden meta verileri alma ve hizmete erişmek bir WCF proxy oluşturulacağı açıklanmaktadır. Bu görevi kullanılarak tamamlanır **hizmet Başvurusu Ekle** Visual Studio tarafından sağlanan işlevsellik. Bu araç, hizmetin MEX uç noktasından meta verileri alır ve yönetilen kaynak kodu dosyası oluşturur bir istemci proxy dilde (C# varsayılan olarak) seçtiniz. İstemci proxy oluşturma, ek araç ayrıca oluşturur veya kendi uç birinde hizmetine bağlanmak istemci uygulamasını etkinleştiren istemci yapılandırma dosyasını güncelleştirir.

> [!NOTE]
> Ayrıca [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanmak yerine, yapılandırma ve proxy sınıfı oluşturmak için **hizmet Başvurusu Ekle** Visual Studio'da.

> [!NOTE]
> Bir WCF hizmeti bir sınıf kitaplığı projesi Visual Studio'da çağrılırken kullanabileceğiniz **hizmet Başvurusu Ekle** otomatik olarak bir ara sunucu ve ilişkili yapılandırma dosyasını oluşturmak için özellik. Yapılandırma dosyasını sınıf kitaplığı projesi tarafından kullanılmıyor. Sınıf kitaplığı çağıran yürütülebilir dosyası için app.config dosyasına oluşturulan yapılandırma dosyasında ayarları eklemeniz gerekir.

İstemci uygulama hizmeti ile iletişim kurmak için oluşturulan proxy sınıfını kullanır. Bu yordamda açıklanan [nasıl yapılır: istemci kullanma](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).

## <a name="to-create-a-windows-communication-foundation-client"></a>Bir Windows Communication Foundation istemcisi oluşturmak için

1. Visual Studio'da yeni bir konsol uygulama projesi oluşturun. Başlarken çözüme sağ **Çözüm Gezgini** seçip **Ekle** > **yeni proje**. İçinde **Yeni Proje Ekle** seçin sol taraftaki iletişim **Windows Masaüstü** kategorisi altında **Visual C#** veya **Visual Basic**. Seçin **konsol uygulaması (.NET Framework)** şablonu ve ardından ad proje **GettingStartedClient**.

2. System.ServiceModel başvuru GettingStartedClient projeye ekleyin. Sağ **başvuruları** klasörü altında GettingStartedClient projede **Çözüm Gezgini**ve ardından **Başvuru Ekle**. İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki **derlemeleri**. Bulmak ve seçmek **System.ServiceModel**ve ardından **Tamam**. Çözüm seçerek Kaydet **dosya** > **Tümünü Kaydet**.

3. Bir hesap makinesi hizmetine hizmet başvurusu ekleyin.

   1. İlk olarak, GettingStartedHost konsol uygulamasını başlatın.

   2. Konak çalıştırıldıktan sonra sağ **başvuruları** klasörü altında GettingStartedClient projede **Çözüm Gezgini** seçip **Ekle**  >   **Hizmet başvurusu**.

   3. Adres kutusuna aşağıdaki URL'yi girin **hizmet Başvurusu Ekle** iletişim: [http://localhost:8000/GettingStartedClient/Service](http://localhost:8000/GettingStartedClient/Service)

   4. Seçin **Git**.

   CalculatorService görüntülenen **Hizmetleri** liste kutusu. CalculatorService genişletmek ve hizmeti tarafından uygulanan hizmet sözleşmelerini görüntülemek için çift tıklayın. Varsayılan ad alanı olarak bırakın- ve **Tamam**.

    Visual Studio kullanarak bir hizmet için bir başvuru eklediğinizde, yeni bir öğe görünür **Çözüm Gezgini** altında **hizmet başvuruları** GettingStartedClient projesi altındaki klasör. Kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı, bir kaynak kodu dosyası ve app.config dosyası oluşturulur.

    Komut satırı aracını da kullanabilirsiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci kodu oluşturmak için uygun anahtarlara sahip. Aşağıdaki örnek, bir kod dosyası ve hizmet için bir yapılandırma dosyası oluşturur. İlk örnek VB proxy oluşturma işlemini gösterir ve ikinci proxy C# içinde oluşturma adımları anlatılmaktadır:

    ```shell
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```shell
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

## <a name="next-steps"></a>Sonraki adımlar

İstemci uygulaması hesaplayıcı hizmeti çağırmak için kullanacağı proxy oluşturmuş oldunuz. Serideki sonraki konuya geçin.

> [!div class="nextstepaction"]
> [Nasıl yapılır: İstemci Yapılandırma](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Nasıl yapılır: Meta Veri Belgelerini İndirmek için Svcutil.exe Kullanma](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
