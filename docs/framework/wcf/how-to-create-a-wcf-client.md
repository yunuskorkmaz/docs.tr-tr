---
title: 'Öğretici: Bir Windows Communication Foundation istemcisi oluşturma'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 39f63b22257fb67d9caa5f84c886ead161508a33
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625830"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Öğretici: Bir Windows Communication Foundation istemcisi oluşturma

Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görev dördüncü açıklanmaktadır. Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

WCF uygulaması oluşturmak için sonraki görev, bir WCF hizmetinden meta verileri alarak bir istemci oluşturmaktır. Meta verileri alır bu hizmetin MEX uç noktasından bir hizmet başvurusu eklemek için Visual Studio'yu kullanın. Visual Studio ardından seçtiğiniz dilde bir istemci proxy'si için bir yönetilen kaynak kodu dosyası oluşturur. Ayrıca bir istemci yapılandırma dosyası oluşturur (*App.config*). Bu dosya, istemci uygulamanın, bir uç nokta adresindeki hizmet bağlanmasını sağlar. 

> [!NOTE]
> Visual Studio'da bir sınıf kitaplığı projesi bir WCF Hizmeti çağırmanıza kullanırsanız **hizmet Başvurusu Ekle** otomatik olarak bir ara sunucu ve ilişkili yapılandırma dosyasını oluşturmak için özellik. Bu yapılandırma dosyasını sınıf kitaplığı projeleri kullanmayın çünkü Bununla birlikte, oluşturulan yapılandırma dosyasındaki ayarları eklemek ihtiyacınız *App.config* sınıf kitaplığı çağıran yürütülebilir dosyası için dosya.

> [!NOTE]
> Alternatif olarak, kullanın [ServiceModel meta veri yardımcı programracı](#servicemodel-metadata-utility-tool) proxy sınıfı ve yapılandırma dosyası oluşturmak için Visual Studio yerine.

İstemci uygulama hizmeti ile iletişim kurmak için oluşturulan proxy sınıfını kullanır. Bu yordamda açıklanan [Öğreticisi: Bir istemci kullanın](how-to-use-a-wcf-client.md).

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - Oluşturun ve bir konsol uygulama projesi için WCF istemcisini yapılandırın.
> - Bir proxy sınıfı ve yapılandırma dosyaları oluşturmak için WCF hizmetine hizmet başvurusu ekleyin.

## <a name="create-a-windows-communication-foundation-client"></a>Bir Windows Communication Foundation istemcisi oluşturma

1. Visual Studio'da konsol uygulaması projesi oluşturun: 

    1. Gelen **dosya** menüsünde **açık** > **proje/çözüm** ve **GettingStarted** çözüm, daha önce oluşturduğunuz (*GettingStarted.sln*). **Aç**'ı seçin.

    2. Gelen **görünümü** menüsünde **Çözüm Gezgini**.

    3. İçinde **Çözüm Gezgini** penceresinde **GettingStarted** çözüm (üst düğümü) ve ardından **Ekle** > **YeniProje** kısayol menüsünden. 
    
    4. İçinde **Yeni Proje Ekle** penceresinde, sol tarafta, select **Windows Masaüstü** kategorisi altında **Visual C#**  veya **Visual Basic**. 

    5. Seçin **konsol uygulaması (.NET Framework)** şablon girin *GettingStartedClient* için **adı**. **Tamam**’ı seçin.

2. Başvuru ekleme **GettingStartedClient** için proje <xref:System.ServiceModel> derleme: 

    1. İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedClient** proje ve ardından **BaşvuruEkle** kısayol menüsünden. 

    2. İçinde **Başvuru Ekle** penceresinin altında **derlemeleri** penceresinin sol taraftan **Framework**.
    
    3. Bulmak ve seçmek **System.ServiceModel**ve ardından **Tamam**. 

    4. Çözüm seçerek Kaydet **dosya** > **Tümünü Kaydet**.

3. Bir hesap makinesi hizmetine hizmet Başvurusu Ekle:

   1. İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedClient** proje ve ardından **hizmet Başvurusu Ekle**  kısayol menüsünden.

   2. İçinde **hizmet Başvurusu Ekle** penceresinde **bulma**.

      CalculatorService hizmeti başlatır ve Visual Studio içinde görüntüler **Hizmetleri** kutusu.

   3. Seçin **CalculatorService** genişletmek ve hizmeti tarafından uygulanan hizmet sözleşmelerini görüntülemek için. Varsayılan değeri bırakın **Namespace** ve **Tamam**.

      Visual Studio altında yeni bir öğe ekler **bağlı hizmetler** klasöründe **GettingStartedClient** proje. 

### <a name="servicemodel-metadata-utility-tool"></a>ServiceModel meta veri yardımcı programracı

Aşağıdaki örnekler, isteğe bağlı olarak kullanmayı göstermektedir [ServiceModel meta veri yardımcı programracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) proxy sınıfı dosyası oluşturmak için. Bu araç proxy sınıfı dosyası oluşturur ve *App.config* dosya. Aşağıdaki örnekler proxy oluşturma C# ve Visual Basic, sırasıyla:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>İstemci yapılandırma dosyası

İstemci oluşturduktan sonra Visual Studio oluşturur **App.config** yapılandırma dosyasında **GettingStartedClient** proje, aşağıdaki örneğe benzer olmalıdır:

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

Altında [ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, fark [ \<uç noktası >](../configure-apps/file-schema/wcf/endpoint-element.md) öğesi. **&lt;Uç nokta&gt;** öğe istemcinin gibi hizmete erişmek için kullandığı uç nokta tanımlar:
- Adres: `http://localhost:8000/GettingStarted/CalculatorService`. Uç nokta adresi.
- Hizmet sözleşmesi: `ServiceReference1.ICalculator`. Hizmet sözleşmesi WCF İstemcisi hizmeti arasındaki iletişimi gerçekleştirir. Visual Studio, bu sözleşme, kullanıldığında oluşturulan kendi **hizmet Başvurusu Ekle** işlevi. Bu temelde GettingStartedLib projede tanımlanan sözleşme bir kopyasıdır. 
- Bağlama: <xref:System.ServiceModel.WSHttpBinding>. Bağlama HTTP taşıma, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntılarını belirtir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> - Oluşturun ve bir konsol uygulama projesi için WCF istemcisini yapılandırın.
> - Bir istemci uygulaması proxy sınıfı ve yapılandırma dosyaları oluşturmak için WCF hizmetine hizmet başvurusu ekleyin.

Oluşturulan istemciyi kullanma hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF istemci kullanma](how-to-use-a-wcf-client.md)
