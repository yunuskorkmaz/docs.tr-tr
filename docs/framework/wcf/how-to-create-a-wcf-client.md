---
title: 'Öğretici: Windows Communication Foundation istemcisi oluşturma'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184110"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Öğretici: Windows Communication Foundation istemcisi oluşturma

Bu öğretici, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin dördüncüsünün açıklanmaktadır. Öğreticilere genel bir bakış için [Bkz. Öğretici: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)

WCF uygulaması oluşturmak için bir sonraki görev, bir WCF hizmetinden meta veri alarak bir istemci oluşturmaktır. Hizmetin MEX bitiş noktasından meta verileri alan bir hizmet başvurusu eklemek için Visual Studio'yu kullanırsınız. Visual Studio daha sonra seçtiğiniz dilde bir istemci proxy için yönetilen bir kaynak kodu dosyası oluşturur. Ayrıca bir istemci yapılandırma dosyası *(App.config)* oluşturur. Bu dosya, istemci uygulamasının hizmete bitiş noktasında bağlanmasını sağlar.

> [!NOTE]
> Visual Studio'daki bir sınıf kitaplığı projesinden wcf hizmeti çağırırsanız, proxy ve ilişkili yapılandırma dosyası oluşturmak için **Hizmet Başvurusu Ekle** özelliğini kullanın. Ancak, sınıf kitaplığı projeleri bu yapılandırma dosyasını kullanmadığından, sınıf kitaplığını çağıran yürütülebilir dosya için oluşturulan yapılandırma dosyasındaki ayarları *App.config* dosyasına eklemeniz gerekir.

> [!NOTE]
> Alternatif olarak, proxy sınıfı ve yapılandırma dosyasını oluşturmak için Visual Studio yerine [ServiceModel Metadata Utility aracını](#servicemodel-metadata-utility-tool) kullanın.

İstemci uygulaması, hizmetle iletişim kurmak için oluşturulan proxy sınıfını kullanır. Bu yordam [Tutorial açıklanmıştır: Bir istemci kullanın.](how-to-use-a-wcf-client.md)

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırır.
> - Proxy sınıfı ve yapılandırma dosyalarını oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.

## <a name="create-a-windows-communication-foundation-client"></a>Windows Communication Foundation istemcisi oluşturma

1. Visual Studio'da bir konsol uygulaması projesi oluşturun:

    1. **Dosya** menüsünden**Proje/Çözüm** **Aç'ı** > seçin ve daha önce oluşturduğunuz **Başlangıç** çözümüne göz atın *(GettingStarted.sln).* **Aç**'ı seçin.

    2. **Görünüm** menüsünden **Çözüm Gezgini'ni**seçin.

    3. Çözüm **Gezgini** penceresinde, **Başlangıç** Çözümünü (üst düğüm) seçin ve ardından kısayol menüsünden**Yeni Proje** **Ekle'yi** > seçin.

    4. Yeni **Proje Ekle** penceresinde, sol tarafta, **Visual C#** veya **Visual Basic**altında Windows **Masaüstü** kategorisini seçin.

    5. Konsol **Uygulaması (.NET Framework)** şablonunu seçin ve **Ad**için *GettingStartedClient'ı* girin. **Tamam'ı**seçin.

2. **Derlemeye Başlangıç İstemci** projesinde <xref:System.ServiceModel> bir başvuru ekleyin:

    1. Çözüm **Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Başvuru Ekle'yi** seçin.

    2. Başvuru **Ekle** penceresinde, pencerenin sol tarafındaki **Derlemeler** altında **Çerçeve'yi**seçin.

    3. **System.ServiceModel'i**bulun ve seçin ve ardından **Tamam'ı**seçin.

    4. **Tümünü Kaydet'i** > seçerek çözümü**kaydedin.**

3. Hesap makinesi hizmetine bir hizmet başvurusu ekleyin:

   1. Çözüm **Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Hizmet Başvurusu Ekle'yi** seçin.

   2. Hizmet Başvurusu Ekle penceresinde **Keşfet'i**seçin. **Add Service Reference**

      CalculatorService hizmeti başlar ve Visual Studio bunu **Hizmetler** kutusunda görüntüler.

   3. Genişletmek ve hizmet tarafından uygulanan hizmet sözleşmelerini görüntülemek için **Hesap Makinesi Hizmetini** seçin. Varsayılan **Ad alanını** bırakın ve **Tamam'ı**seçin.

      Visual **Studio, GettingStartedClient** projesinde **Bağlı Hizmetler** klasörüne yeni bir öğe ekler.

### <a name="servicemodel-metadata-utility-tool"></a>ServiceModel Metadata Yardımcı araç

Aşağıdaki örnekler, proxy sınıfı dosyasını oluşturmak için [ServiceModel Metadata Utility aracının (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) isteğe bağlı olarak nasıl kullanılacağını gösterir. Bu araç proxy sınıf dosyası ve *App.config* dosyasını oluşturur. Aşağıdaki örnekler, sırasıyla C# ve Visual Basic'te proxy'nin nasıl oluşturacağımı gösterir:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>İstemci yapılandırma dosyası

İstemciyi oluşturduktan sonra Visual Studio, **GettingStartedClient** projesinde aşağıdaki örneğe benzer olması gereken **App.config** yapılandırma dosyasını oluşturur:

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

System.serviceModel>bölümünde, [ \<bitiş noktası>](../configure-apps/file-schema/wcf/endpoint-element.md) öğesine dikkat edin. [ \<](../configure-apps/file-schema/wcf/system-servicemodel.md) ** &lt;Uç nokta&gt; ** öğesi, istemcinin hizmete erişmek için kullandığı bitiş noktasını aşağıdaki gibi tanımlar:

- Adres: `http://localhost:8000/GettingStarted/CalculatorService`. Bitiş noktasının adresi.
- Hizmet sözleşmesi: `ServiceReference1.ICalculator`. Hizmet sözleşmesi, WCF istemcisi ile hizmet arasındaki iletişimi işler. Visual Studio, Hizmet Başvurusu **Ekle** işlevini kullandığınızda bu sözleşmeyi oluşturdu. Bu aslında GettingStartedLib projesinde tanımladığınız sözleşmenin bir kopyasıdır.
- Bağlama: <xref:System.ServiceModel.WSHttpBinding>. Bağlama, HTTP'yi aktarım, birlikte çalışabilir güvenlik ve diğer yapılandırma ayrıntıları olarak belirtir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırır.
> - İstemci uygulaması için proxy sınıfı ve yapılandırma dosyaları oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.

Oluşturulan istemciyi nasıl kullanacağınızı öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF istemcisi kullanma](how-to-use-a-wcf-client.md)
