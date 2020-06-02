---
title: 'Öğretici: temel bir Windows Communication Foundation hizmetini barındırma ve çalıştırma'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 872844487578843492e05dd2abb87b50e0bec91c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291402"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Öğretici: temel bir Windows Communication Foundation hizmetini barındırma ve çalıştırma

Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken üçüncü beş görev açıklanmaktadır. Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

WCF uygulaması oluşturmaya yönelik sonraki görev bir konsol uygulamasında bir WCF hizmeti barındırmanıza yöneliktir. Bir WCF hizmeti, her biri bir veya daha fazla hizmet işlemi sunan bir veya daha fazla *uç nokta*sunar. Hizmet uç noktası aşağıdaki bilgileri belirtir:

- Hizmeti bulabileceğiniz bir adres.
- İstemcinin hizmetle nasıl iletişim kurması gerektiğini açıklayan bilgileri içeren bir bağlama.
- Hizmetin istemcilerine sağladığı işlevselliği tanımlayan bir anlaşma.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> - WCF hizmetini barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - WCF hizmetini barındırmak için kod ekleyin.
> - Yapılandırma dosyasını güncelleştirin.
> - WCF hizmetini başlatın ve çalıştığını doğrulayın.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Hizmeti barındırmak için bir konsol uygulaması projesi oluşturma ve yapılandırma

1. Visual Studio 'da bir konsol uygulaması projesi oluşturun:

    1. **Dosya** menüsünde **Open**  >  **Proje/çözüm** aç ' ı seçin ve daha önce oluşturduğunuz **gettingstarted** çözümüne (*gettingstarted. sln*) gidin. **Aç**'ı seçin.

    2. **Görünüm** menüsünden **Çözüm Gezgini**' yi seçin.

    3. **Çözüm Gezgini** penceresinde, **gettingstarted** çözümünü (üst düğüm) seçin ve sonra **Add**  >  kısayol menüsünden**Yeni proje** Ekle ' yi seçin.

    4. **Yeni Proje Ekle** penceresinde, sol taraftaki **Visual C#** veya **Visual Basic**altındaki **Windows Masaüstü** kategorisini seçin.

    5. **Konsol uygulaması (.NET Framework)** şablonunu seçin ve **ad**Için *GettingStartedHost* yazın. **Tamam**’ı seçin.

2. **GettingStartedHost** projesinde **GettingStartedLib** projesine bir başvuru ekleyin:

    1. **Çözüm Gezgini** penceresinde, **GettingStartedHost** projesi altındaki **Başvurular** klasörünü seçin ve sonra kısayol menüsünden **Başvuru Ekle** ' yi seçin.

    2. **Başvuru Ekle** iletişim kutusunda, pencerenin sol tarafındaki **Projeler** altında **çözüm**' ü seçin.

    3. Pencerenin orta bölümündeki **GettingStartedLib** ' i seçin ve ardından **Tamam**' ı seçin.

       Bu eylem, **GettingStartedLib** projesinde tanımlanan türlerin **GettingStartedHost** projesi için kullanılabilir olmasını sağlar.

3. **GettingStartedHost** projesinde derlemeye bir başvuru ekleyin <xref:System.ServiceModel> :

    1. **Çözüm Gezgini** penceresinde, **GettingStartedHost** projesi altındaki **Başvurular** klasörünü seçin ve sonra kısayol menüsünden **Başvuru Ekle** ' yi seçin.

    2. **Başvuru Ekle** penceresinde pencerenin sol tarafındaki **derlemeler** altında **Framework**' ü seçin.

    3. **System. ServiceModel**' i seçin ve ardından **Tamam**' ı seçin.

    4. **Dosya**  >  **Tümünü Kaydet**' i seçerek çözümü kaydedin.

## <a name="add-code-to-host-the-service"></a>Hizmeti barındırmak için kod ekleme

Hizmeti barındırmak için aşağıdaki adımları uygulamak üzere kod ekleyin:

1. Temel adres için bir URI oluşturun.
2. Hizmeti barındırmak için bir sınıf örneği oluşturun.
3. Hizmet uç noktası oluşturun.
4. Meta veri değişimini etkinleştirin.
5. Gelen iletileri dinlemek için hizmet ana bilgisayarını açın.
  
Kodda aşağıdaki değişiklikleri yapın:

1. **GettingStartedHost** projesinde **program.cs** veya **Module1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:

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
                    selfHost.Description.Behaviors.Add(smb);

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

    Bu kodun nasıl çalıştığı hakkında bilgi için bkz. [hizmet barındırma programı adımları](#service-hosting-program-steps).

2. Proje özelliklerini güncelleştirin:

   1. **Çözüm Gezgini** penceresinde **GettingStartedHost** klasörünü seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

   2. **GettingStartedHost** özellikleri sayfasında **uygulama** sekmesini seçin:

      - C# projeleri için **Başlangıç nesne** listesinden **GettingStartedHost. program** ' ı seçin.

      - Visual Basic projeleri için **Başlangıç nesne** listesinden **Service. program** ' ı seçin.

   3. **Dosya** menüsünde **Tümünü Kaydet**' i seçin.

## <a name="verify-the-service-is-working"></a>Hizmetin çalıştığını doğrulama

1. Çözümü derleyin ve ardından Visual Studio içinden **GettingStartedHost** konsol uygulamasını çalıştırın.

    Hizmetin yönetici ayrıcalıklarıyla çalıştırılması gerekir. Visual Studio 'Yu yönetici ayrıcalıklarıyla açtığınızdan, Visual Studio 'da **GettingStartedHost** çalıştırdığınızda uygulama da yönetici ayrıcalıklarıyla çalıştırılır. Alternatif olarak, yeni bir komut istemi 'ni yönetici olarak açabilirsiniz (kısayol menüsünden **daha fazla**  >  **Çalıştır Yöneticisi** ' ni seçin) ve içinde **GettingStartedHost. exe** ' yi çalıştırın.

2. Bir Web tarayıcısı açın ve konumundaki hizmetin sayfasına gidin `http://localhost:8000/GettingStarted/CalculatorService` .

   > [!NOTE]
   > Bu gibi hizmetler, dinlemek üzere makineye HTTP adreslerini kaydetmek için uygun izni gerektirir. Yönetici hesaplarında bu izin vardır ancak yönetici olmayan hesaplara HTTP ad alanları için izin verilmesi gerekir. Ad alanı ayırmalarını yapılandırma hakkında daha fazla bilgi için bkz. [http ve https yapılandırma](feature-details/configuring-http-and-https.md).

## <a name="service-hosting-program-steps"></a>Hizmet barındırma programı adımları

Hizmeti barındırmak için eklediğiniz koddaki adımlar aşağıdaki gibi açıklanmıştır:

- **1. adım**: `Uri` hizmetin temel adresini tutmak için sınıfın bir örneğini oluşturun. Temel adresi içeren bir URL 'nin bir hizmeti tanımlayan isteğe bağlı bir URI 'SI vardır. Taban adresi şu şekilde biçimlendirilir: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` . Hesaplayıcı hizmeti için temel adres HTTP taşıması, localhost, bağlantı noktası 8000 ve URI segmentini, GettingStarted kullanır.

- **2. adım**: <xref:System.ServiceModel.ServiceHost> hizmeti barındırmak için kullandığınız sınıfının bir örneğini oluşturun. Oluşturucu iki parametre alır: hizmet sözleşmesini uygulayan sınıfın türü ve hizmetin taban adresi.

- **3. adım**: bir <xref:System.ServiceModel.Description.ServiceEndpoint> örnek oluşturun. Hizmet uç noktası bir adresten, bağlamaya ve hizmet sözleşmesinden oluşur. <xref:System.ServiceModel.Description.ServiceEndpoint>Oluşturucu, hizmet sözleşmesi arabirim türünden, bağlamalardan ve bir adresten oluşur. Hizmet sözleşmesi, `ICalculator` hizmet türünde tanımladığınız ve uyguladığınız hizmet sözleşmedir. Bu örnek için bağlama, <xref:System.ServiceModel.WSHttpBinding> yerleşik bir bağlama ve WS-* belirtimlerine uygun uç noktalara bağlanır. WCF bağlamaları hakkında daha fazla bilgi için bkz. [WCF bağlamalarına genel bakış](bindings-overview.md). Uç noktayı tanımlamak için adresi temel adrese ekleyin. Kod, adresi Hesaplatorservice olarak ve uç noktanın tam adresini olarak belirtir `http://localhost:8000/GettingStarted/CalculatorService` .

    > [!IMPORTANT]
    > .NET Framework sürüm 4 ve üzeri için bir hizmet uç noktası eklemek isteğe bağlıdır. Bu sürümler için, kodunuzu veya yapılandırmanızı eklememeniz durumunda WCF, hizmet tarafından uygulanan her temel adres ve sözleşmenin birleşimi için bir varsayılan uç nokta ekler. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [bir uç nokta adresi belirtme](specifying-an-endpoint-address.md). Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

- **4. adım**: meta veri değişimini etkinleştirin. İstemciler, hizmet işlemlerini çağırmak için proxy oluşturmak üzere meta veri değişimi kullanır. Meta veri değişimini etkinleştirmek için bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek oluşturun, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> özelliğini olarak ayarlayın `true` ve `ServiceMetadataBehavior` nesneyi <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> örnek koleksiyonuna ekleyin <xref:System.ServiceModel.ServiceHost> .

- **5. adım**: <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için açın. Uygulama, **ENTER**tuşuna basmanız için bekler. Uygulama başlatıldıktan sonra <xref:System.ServiceModel.ServiceHost> bir try/catch bloğu yürütür. Tarafından oluşturulan özel durumları güvenli bir şekilde yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost> bkz. [Close ve Abort kullanarak WCF istemci kaynaklarını serbest bırakma](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Bir WCF hizmet kitaplığı eklediğinizde, bir hizmet ana bilgisayarı başlatarak hata ayıklaması yaparsanız, Visual Studio bunu sizin için barındırır. Çakışmaları önlemek için, Visual Studio 'Nun WCF hizmeti kitaplığını barındırmasını engelleyebilirsiniz.
>
> 1. **Çözüm Gezgini** ' de **GettingStartedLib** projesini seçin ve kısayol menüsünden **Özellikler** ' i seçin.
> 2. **WCF seçeneklerini** belirleyin ve **aynı çözümdeki başka bir projede hata ayıklarken WCF hizmeti ana bilgisayarının Başlat**seçimini kaldırın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - WCF hizmetini barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.
> - WCF hizmetini barındırmak için kod ekleyin.
> - Yapılandırma dosyasını güncelleştirin.
> - WCF hizmetini başlatın ve çalıştığını doğrulayın.

Bir WCF istemcisi oluşturmayı öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF istemcisi oluşturma](how-to-create-a-wcf-client.md)
