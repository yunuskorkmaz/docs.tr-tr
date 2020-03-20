---
title: 'Öğretici: Temel bir Windows Communication Foundation hizmetini barındırın ve çalıştırın'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184077"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Öğretici: Temel bir Windows Communication Foundation hizmetini barındırın ve çalıştırın

Bu öğretici, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin üçüncüsüni açıklar. Öğreticilere genel bir bakış için [Bkz. Öğretici: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)

WCF uygulaması oluşturmak için bir sonraki görev, bir konsol uygulamasında bir WCF hizmetini barındırmaktır. WCF hizmeti, her biri bir veya daha fazla hizmet operasyonunu ortaya çıkaran bir veya daha fazla *uç noktayı*ortaya çıkarır. Hizmet bitiş noktası aşağıdaki bilgileri belirtir:

- Hizmeti bulabileceğiniz bir adres.
- İstemci hizmeti ile nasıl iletişim kurması gerektiğini açıklayan bilgileri içeren bir bağlayıcı.
- Hizmetin istemcilerine sağladığı işlevselliği tanımlayan sözleşme.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - Bir WCF hizmeti barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - WCF hizmetini barındırmak için kod ekleyin.
> - Yapılandırma dosyasını güncelleştirin.
> - WCF hizmetini başlatın ve çalıştığını doğrulayın.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Hizmeti barındırmak için bir konsol uygulaması projesi oluşturma ve yapılandırma

1. Visual Studio'da bir konsol uygulaması projesi oluşturun:

    1. **Dosya** menüsünden**Proje/Çözüm** **Aç'ı** > seçin ve daha önce oluşturduğunuz **Başlangıç** çözümüne göz atın *(GettingStarted.sln).* **Aç**'ı seçin.

    2. **Görünüm** menüsünden **Çözüm Gezgini'ni**seçin.

    3. Çözüm **Gezgini** penceresinde, **Başlangıç** Çözümünü (üst düğüm) seçin ve ardından kısayol menüsünden**Yeni Proje** **Ekle'yi** > seçin.

    4. Yeni **Proje Ekle** penceresinde, sol tarafta, **Visual C#** veya **Visual Basic**altında Windows **Masaüstü** kategorisini seçin.

    5. Konsol **Uygulaması (.NET Framework)** şablonunu seçin ve **Ad**için *GettingStartedHost'u* girin. **Tamam'ı**seçin.

2. **GettingStartedLib** projesine **GettingStartedHost** projesine bir başvuru ekleyin:

    1. Çözüm **Gezgini** penceresinde, **GettingStartedHost** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Başvuru Ekle'yi** seçin.

    2. Başvuru **Ekle** iletişim kutusunda, pencerenin sol tarafındaki **Projeler** altında **Çözüm'ü**seçin.

    3. Pencerenin orta bölümünde **GettingStartedLib'i** seçin ve ardından **Tamam'ı**seçin.

       Bu eylem, **GettingStartedLib** projesinde tanımlanan türleri **GettingStartedHost** projesiiçin kullanılabilir hale getirir.

3. **Derlemeye GettingStartedHost** projesinde <xref:System.ServiceModel> bir başvuru ekleyin:

    1. Çözüm **Gezgini** penceresinde, **GettingStartedHost** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Başvuru Ekle'yi** seçin.

    2. Başvuru **Ekle** penceresinde, pencerenin sol tarafındaki **Derlemeler** altında **Çerçeve'yi**seçin.

    3. **System.ServiceModel'i**seçin ve ardından **Tamam'ı**seçin.

    4. **Tümünü Kaydet'i** > seçerek çözümü**kaydedin.**

## <a name="add-code-to-host-the-service"></a>Hizmeti barındırmak için kod ekleme

Hizmeti barındırmak için aşağıdaki adımları yapmak için kod eklersiniz:

1. Temel adres için bir URI oluşturun.
2. Hizmeti barındırmak için bir sınıf örneği oluşturun.
3. Bir hizmet bitiş noktası oluşturun.
4. Meta veri alışverişini etkinleştirin.
5. Gelen iletileri dinlemek için servis ana bilgisayarını açın.
  
Kodda aşağıdaki değişiklikleri yapın:

1. **GettingStartedHost** projesinde **Program.cs** veya **Module1.vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```

    Bu kodun nasıl çalıştığı hakkında bilgi için [Hizmet barındırma programı adımlarını](#service-hosting-program-steps)görün.

2. Proje özelliklerini güncelleştirin:

   1. Solution **Explorer** penceresinde, **GettingStartedHost** klasörünü seçin ve ardından kısayol menüsünden **Özellikler'i** seçin.

   2. **GettingStartedHost** özellikleri sayfasında **Uygulama** sekmesini seçin:

      - C# projeleri için **Başlangıç nesne** listesinden **GettingStartedHost.Program'ı** seçin.

      - Visual Basic projeleri için **Başlangıç nesne** listesinden **Service.Program'ı** seçin.

   3. **Dosya** menüsünden **Tümünü Kaydet'i**seçin.

## <a name="verify-the-service-is-working"></a>Hizmetin çalıştığını doğrulayın

1. Çözümü oluşturun ve Ardından Visual Studio'nun içinden **GettingStartedHost** konsol uygulamasını çalıştırın.

    Hizmet yönetici ayrıcalıkları ile çalıştırılmalıdır. Visual Studio'yu yönetici ayrıcalıklarıyla açtığınız için, **Visual Studio'da GettingStartedHost'u** çalıştırdığınızda, uygulama yönetici ayrıcalıklarıyla da çalıştırılır. Alternatif olarak, yönetici olarak yeni bir komut istemi açabilir (kısayol menüsünden yönetici olarak **Daha Fazla** > **Çalıştır'ı** seçin) ve içinde **GettingStartedHost.exe'yi** çalıştırabilirsiniz.

2. Bir web tarayıcısı açın ve hizmetin `http://localhost:8000/GettingStarted/CalculatorService`sayfasına 'da göz atın.

   > [!NOTE]
   > Bu gibi hizmetler dinlemek için makineye HTTP adresleri kaydetmek için uygun izni gerektirir. Yönetici hesaplarıbu izne sahiptir, ancak yönetici olmayan hesaplara HTTP ad alanları için izin verilmesi gerekir. Ad alanı rezervasyonlarını yapılandırma hakkında daha fazla bilgi için [http ve HTTPS yapılandırma](feature-details/configuring-http-and-https.md)bölümüne bakın.

## <a name="service-hosting-program-steps"></a>Hizmet barındırma programı adımları

Hizmeti barındırmak için eklediğiniz koddaki adımlar aşağıdaki gibi açıklanmıştır:

- **Adım 1**: Hizmetin `Uri` temel adresini tutmak için sınıfın bir örneğini oluşturun. Temel adres içeren bir URL'de, hizmeti tanımlayan isteğe bağlı bir URI vardır. Temel adres aşağıdaki gibi biçimlendirilir: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. Hesap makinesi hizmetinin temel adresi HTTP transport, localhost, port 8000 ve URI segmenti Olan GettingStarted'ı kullanır.

- **Adım 2**: Hizmeti <xref:System.ServiceModel.ServiceHost> barındırmak için kullandığınız sınıfın bir örneğini oluşturun. Oluşturucu iki parametre alır: hizmet sözleşmesini uygulayan sınıfın türü ve hizmetin temel adresi.

- **Adım 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Bir örnek oluşturun. Hizmet bitiş noktası bir adres, bağlama ve hizmet sözleşmesinden oluşur. Oluşturucu, <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet sözleşmesi arabirim türü, bir bağlama ve bir adresten oluşur. Hizmet sözleşmesi, `ICalculator`hizmet türünde tanımladığınız ve uyguladığınız sözleşmedir. Bu örnek için <xref:System.ServiceModel.WSHttpBinding>bağlayıcı, yerleşik bir bağlama ve WS-* belirtimlerine uygun uç noktalara bağlanır. WCF ciltleri hakkında daha fazla bilgi için [WCF bağlamalarına genel bakış](bindings-overview.md)alabın. Bitiş noktasını belirlemek için adresi temel adrese eklersiniz. Kod, adresi Hesap Makinesi Hizmeti olarak ve bitiş noktası için `http://localhost:8000/GettingStarted/CalculatorService`tam nitelikli adresi olarak belirtir.

    > [!IMPORTANT]
    > .NET Framework Version 4 ve sonraki sürümler için bir hizmet bitiş noktası eklemek isteğe bağlıdır. Bu sürümler için, kodunuzu veya yapılandırmanızı eklemezseniz, WCF hizmet tarafından uygulanan her temel adres ve sözleşme kombinasyonu için bir varsayılan bitiş noktası ekler. Varsayılan uç noktalar hakkında daha fazla bilgi için [bkz.](specifying-an-endpoint-address.md) Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için WCF hizmetleri için [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş yapılandırmaya](samples/simplified-configuration-for-wcf-services.md)bakın.

- **Adım 4**: Meta veri alışverişini etkinleştirin. İstemciler, hizmet işlemlerini çağırmak için yakınlık oluşturmak için meta veri alışverişini kullanır. Meta veri alışverişini <xref:System.ServiceModel.Description.ServiceMetadataBehavior> etkinleştirmek için, `true`bir örnek `ServiceMetadataBehavior` oluşturun, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> özelliğini <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> <xref:System.ServiceModel.ServiceHost> "" olarak ayarlayın ve nesneyi örnek koleksiyonuna ekleyin.

- **Adım 5** <xref:System.ServiceModel.ServiceHost> : Gelen iletileri dinlemek için açın. Uygulama **Enter**tuşuna basmanızı bekler. Uygulama instantiates <xref:System.ServiceModel.ServiceHost>sonra, bir try /catch bloğu yürütür. Tarafından atılan özel durumları güvenli bir <xref:System.ServiceModel.ServiceHost>şekilde yakalamak hakkında daha fazla bilgi [için WCF istemci kaynaklarını serbest bırakmak için Kapat ve İptal'i kullan'a](samples/use-close-abort-release-wcf-client-resources.md)bakın.

> [!IMPORTANT]
> Bir WCF hizmet kitaplığı eklediğinizde, bir hizmet ana bilgisayar başlatarak hata ayıklama nız durumunda Visual Studio, bu kitap sizin için barındırır. Çakışmaları önlemek için Visual Studio'nun WCF hizmet kitaplığını barındırmasını engelleyebilirsiniz.
>
> 1. **Solution Explorer'da** **GettingStartedLib** projesini seçin ve kısayol menüsünden **Özellikler'i** seçin.
> 2. Aynı çözümde başka bir projehataayıklarken **WCF Seçenekleri'ni** seçin ve **WCF Hizmet Ana Bilgisayarını Başlat'ın denetimini**kaldırın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Bir WCF hizmeti barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - WCF hizmetini barındırmak için kod ekleyin.
> - Yapılandırma dosyasını güncelleştirin.
> - WCF hizmetini başlatın ve çalıştığını doğrulayın.

WCF istemcisi oluşturmayı öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF istemcisi oluşturma](how-to-create-a-wcf-client.md)
