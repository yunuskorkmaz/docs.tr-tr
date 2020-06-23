---
title: 'Öğretici: Windows Communication Foundation istemci oluşturma'
description: WCF uygulaması oluşturmaya başlamanıza yardımcı olan bir makale serisinin parçası olarak bir WCF hizmetinden meta verileri alarak istemci oluşturmayı öğrenin.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246330"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Öğretici: Windows Communication Foundation istemci oluşturma

Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken dördüncü beş görev açıklanmaktadır. Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

WCF uygulaması oluşturmaya yönelik sonraki görev, bir WCF hizmetinden meta verileri alarak istemci oluşturmaktır. Hizmetin MEX uç noktasından meta verileri alan bir hizmet başvurusu eklemek için Visual Studio 'Yu kullanırsınız. Daha sonra Visual Studio, seçtiğiniz dilde istemci proxy 'si için bir yönetilen kaynak kodu dosyası oluşturur. Ayrıca, bir istemci yapılandırma dosyası (*App.config*) oluşturur. Bu dosya, istemci uygulamasının bir uç noktada hizmete bağlanmasını sağlar.

> [!NOTE]
> Visual Studio 'da bir sınıf kitaplığı projesinden bir WCF hizmeti çağırırsanız, otomatik olarak bir proxy ve ilişkili yapılandırma dosyası oluşturmak için **hizmet başvurusu Ekle** özelliğini kullanın. Ancak, sınıf kitaplığı projeleri bu yapılandırma dosyasını kullanmadığından, oluşturulan yapılandırma dosyasındaki ayarları, sınıf kitaplığını çağıran yürütülebilir dosyanın *App.config* dosyasına eklemeniz gerekir.

> [!NOTE]
> Alternatif olarak, proxy sınıfını ve yapılandırma dosyasını oluşturmak için Visual Studio yerine [ServiceModel meta veri yardımcı programı aracını](#servicemodel-metadata-utility-tool) kullanın.

İstemci uygulaması, hizmetle iletişim kurmak için oluşturulan proxy sınıfını kullanır. Bu yordam [öğretici: Istemci kullanma](how-to-use-a-wcf-client.md)' da açıklanmaktadır.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:
> [!div class="checklist"]
>
> - WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - Proxy sınıfı ve yapılandırma dosyalarını oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.

## <a name="create-a-windows-communication-foundation-client"></a>Windows Communication Foundation istemcisi oluşturma

1. Visual Studio 'da bir konsol uygulaması projesi oluşturun:

    1. **Dosya** menüsünde **Open**  >  **Proje/çözüm** aç ' ı seçin ve daha önce oluşturduğunuz **gettingstarted** çözümüne (*gettingstarted. sln*) gidin. **Aç**'ı seçin.

    2. **Görünüm** menüsünden **Çözüm Gezgini**' yi seçin.

    3. **Çözüm Gezgini** penceresinde, **gettingstarted** çözümünü (üst düğüm) seçin ve sonra **Add**  >  kısayol menüsünden**Yeni proje** Ekle ' yi seçin.

    4. **Yeni Proje Ekle** penceresinde, sol taraftaki **Visual C#** veya **Visual Basic**altındaki **Windows Masaüstü** kategorisini seçin.

    5. **Konsol uygulaması (.NET Framework)** şablonunu seçin ve **ad**Için *GettingStartedClient* yazın. **Tamam**’ı seçin.

2. **GettingStartedClient** projesinde derlemeye bir başvuru ekleyin <xref:System.ServiceModel> :

    1. **Çözüm Gezgini** penceresinde, **GettingStartedClient** projesi altındaki **Başvurular** klasörünü seçin ve kısayol menüsünden **Başvuru Ekle** ' yi seçin.

    2. **Başvuru Ekle** penceresinde pencerenin sol tarafındaki **derlemeler** altında **Framework**' ü seçin.

    3. **System. ServiceModel**bulun ve seçin ve ardından **Tamam**' ı seçin.

    4. **Dosya**  >  **Tümünü Kaydet**' i seçerek çözümü kaydedin.

3. Hesaplayıcı hizmetine bir hizmet başvurusu ekleyin:

   1. **Çözüm Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **References** klasörünü seçin ve sonra kısayol menüsünden **hizmet başvurusu Ekle** öğesini seçin.

   2. **Hizmet başvurusu Ekle** penceresinde **bul**' u seçin.

      Hesaplatorservice hizmeti başlatılır ve Visual Studio bunu **Hizmetler** kutusunda görüntüler.

   3. Hesap ve hizmet tarafından uygulanan hizmet sözleşmelerini göstermek için **Hesaplatorservice** ' i seçin. Varsayılan **ad alanını** bırakın ve **Tamam**' ı seçin.

      Visual Studio, **GettingStartedClient** projesindeki **bağlı hizmetler** klasörü altına yeni bir öğe ekler.

### <a name="servicemodel-metadata-utility-tool"></a>ServiceModel meta veri yardımcı programı Aracı

Aşağıdaki örneklerde, proxy sınıfı dosyasını oluşturmak için isteğe bağlı olarak [ServiceModel meta veri yardımcı programı aracının (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) nasıl kullanılacağı gösterilmektedir. Bu araç, proxy sınıfı dosyasını ve *App.config* dosyasını oluşturur. Aşağıdaki örneklerde, sırasıyla C# ve Visual Basic proxy 'nin nasıl oluşturulacağı gösterilmektedir:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>İstemci yapılandırma dosyası

İstemciyi oluşturduktan sonra, Visual Studio, aşağıdaki örneğe benzer olması gereken **GettingStartedClient** projesinde **App.config** yapılandırma dosyasını oluşturur:

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

Bölümünün altında, [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) öğesine dikkat edin [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) . ** &lt; Endpoint &gt; ** öğesi istemcinin hizmete erişmek için kullandığı uç noktayı şu şekilde tanımlar:

- Adres: `http://localhost:8000/GettingStarted/CalculatorService` . Uç noktanın adresi.
- Hizmet Sözleşmesi: `ServiceReference1.ICalculator` . Hizmet sözleşmesi, WCF istemcisiyle hizmet arasındaki iletişimi işler. Visual Studio, **hizmet başvurusu Ekle** işlevini kullandığınızda bu sözleşmeyi oluşturdu. Bu aslında, GettingStartedLib projesinde tanımladığınız sözleşmenin bir kopyasıdır.
- Bağlama: <xref:System.ServiceModel.WSHttpBinding> . Bağlama, aktarım, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntıları olarak HTTP 'yi belirtir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - İstemci uygulaması için proxy sınıfı ve yapılandırma dosyalarını oluşturmak üzere WCF hizmetine bir hizmet başvurusu ekleyin.

Oluşturulan istemciyi nasıl kullanacağınızı öğrenmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF istemcisi kullanma](how-to-use-a-wcf-client.md)
