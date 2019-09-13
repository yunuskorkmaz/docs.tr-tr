---
title: 'Öğretici: Windows Communication Foundation istemcisi oluşturma'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928900"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Öğretici: Windows Communication Foundation istemcisi oluşturma

Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken dördüncü beş görev açıklanmaktadır. Öğreticilere genel bakış için bkz [. Öğretici: Windows Communication Foundation uygulamaları](getting-started-tutorial.md)ile çalışmaya başlayın.

WCF uygulaması oluşturmaya yönelik sonraki görev, bir WCF hizmetinden meta verileri alarak istemci oluşturmaktır. Hizmetin MEX uç noktasından meta verileri alan bir hizmet başvurusu eklemek için Visual Studio 'Yu kullanırsınız. Daha sonra Visual Studio, seçtiğiniz dilde istemci proxy 'si için bir yönetilen kaynak kodu dosyası oluşturur. Ayrıca, bir istemci yapılandırma dosyası (*app. config*) oluşturur. Bu dosya, istemci uygulamasının bir uç noktada hizmete bağlanmasını sağlar. 

> [!NOTE]
> Visual Studio 'da bir sınıf kitaplığı projesinden bir WCF hizmeti çağırırsanız, otomatik olarak bir proxy ve ilişkili yapılandırma dosyası oluşturmak için **hizmet başvurusu Ekle** özelliğini kullanın. Ancak, sınıf kitaplığı projeleri bu yapılandırma dosyasını kullanmadığından, oluşturulan yapılandırma dosyasındaki ayarları, sınıf kitaplığını çağıran yürütülebilir dosya için *app. config* dosyasına eklemeniz gerekir.

> [!NOTE]
> Alternatif olarak, proxy sınıfını ve yapılandırma dosyasını oluşturmak için Visual Studio yerine [ServiceModel meta veri yardımcı programı aracını](#servicemodel-metadata-utility-tool) kullanın.

İstemci uygulaması, hizmetle iletişim kurmak için oluşturulan proxy sınıfını kullanır. Bu yordam öğretici 'de [açıklanmaktadır: İstemci](how-to-use-a-wcf-client.md)kullanın.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - Proxy sınıfı ve yapılandırma dosyalarını oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.

## <a name="create-a-windows-communication-foundation-client"></a>Windows Communication Foundation istemcisi oluşturma

1. Visual Studio 'da bir konsol uygulaması projesi oluşturun: 

    1. **Dosya** menüsünde**Proje/çözüm** **Aç** > ' ı seçin ve daha önce oluşturduğunuz **gettingstarted** çözümüne (*gettingstarted. sln*) gidin. **Aç**'ı seçin.

    2. **Görünüm** menüsünden **Çözüm Gezgini**' yi seçin.

    3. **Çözüm Gezgini** penceresinde, **gettingstarted** çözümünü (üst düğüm) seçin ve sonra kısayol menüsünden**Yeni proje** **Ekle** > ' yi seçin. 
    
    4. **Yeni Proje Ekle** penceresinde, sol taraftaki **Visual C#**  veya **Visual Basic**altında **Windows Masaüstü** kategorisini seçin. 

    5. **Konsol uygulaması (.NET Framework)** şablonunu seçin ve **ad**Için *GettingStartedClient* yazın. **Tamam**’ı seçin.

2. **GettingStartedClient** projesinde <xref:System.ServiceModel> derlemeye bir başvuru ekleyin: 

    1. **Çözüm Gezgini** penceresinde, **GettingStartedClient** projesi altındaki **Başvurular** klasörünü seçin ve kısayol menüsünden **Başvuru Ekle** ' yi seçin. 

    2. **Başvuru Ekle** penceresinde pencerenin sol tarafındaki **derlemeler** altında **Framework**' ü seçin.
    
    3. **System. ServiceModel**bulun ve seçin ve ardından **Tamam**' ı seçin. 

    4. **Dosya** > **Tümünü Kaydet**' i seçerek çözümü kaydedin.

3. Hesaplayıcı hizmetine bir hizmet başvurusu ekleyin:

   1. **Çözüm Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **References** klasörünü seçin ve sonra kısayol menüsünden **hizmet başvurusu Ekle** öğesini seçin.

   2. **Hizmet başvurusu Ekle** penceresinde **bul**' u seçin.

      Hesaplatorservice hizmeti başlatılır ve Visual Studio bunu **Hizmetler** kutusunda görüntüler.

   3. Hesap ve hizmet tarafından uygulanan hizmet sözleşmelerini göstermek için **Hesaplatorservice** ' i seçin. Varsayılan **ad alanını** bırakın ve **Tamam**' ı seçin.

      Visual Studio, **GettingStartedClient** projesindeki **bağlı hizmetler** klasörü altına yeni bir öğe ekler. 

### <a name="servicemodel-metadata-utility-tool"></a>ServiceModel meta veri yardımcı programı Aracı

Aşağıdaki örneklerde, proxy sınıfı dosyasını oluşturmak için isteğe bağlı olarak [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) nasıl kullanılacağı gösterilmektedir. Bu araç, proxy sınıfı dosyasını ve *app. config* dosyasını oluşturur. Aşağıdaki örneklerde, C# ve sırasıyla Visual Basic proxy 'nin nasıl oluşturulacağı gösterilmektedir:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>İstemci yapılandırma dosyası

İstemciyi oluşturduktan sonra, Visual Studio, **GettingStartedClient** projesinde **app. config** yapılandırma dosyasını oluşturur; Bu, aşağıdaki örneğe benzer olmalıdır:

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

[System. ServiceModel > bölümünde uç nokta > öğesine dikkat edin. \<](../configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) Endpoint öğesi istemcinin hizmete erişmek için kullandığı uç noktayı şu şekilde tanımlar: **&lt;&gt;**

- Adres: `http://localhost:8000/GettingStarted/CalculatorService`. Uç noktanın adresi.
- Hizmet Sözleşmesi: `ServiceReference1.ICalculator`. Hizmet sözleşmesi, WCF istemcisiyle hizmet arasındaki iletişimi işler. Visual Studio, **hizmet başvurusu Ekle** işlevini kullandığınızda bu sözleşmeyi oluşturdu. Bu aslında, GettingStartedLib projesinde tanımladığınız sözleşmenin bir kopyasıdır. 
- Bağlama: <xref:System.ServiceModel.WSHttpBinding>. Bağlama, aktarım, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntıları olarak HTTP 'yi belirtir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - İstemci uygulaması için proxy sınıfı ve yapılandırma dosyalarını oluşturmak üzere WCF hizmetine bir hizmet başvurusu ekleyin.

Oluşturulan istemciyi nasıl kullanacağınızı öğrenmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF istemcisi kullanma](how-to-use-a-wcf-client.md)
