---
title: 'Öğretici: Temel bir Windows Communication Foundation Hizmeti barındırma ve çalıştırma'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: ad9536b1f27ba3945bf76d0474de4825033a1e8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197912"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Öğretici: Temel bir Windows Communication Foundation Hizmeti barındırma ve çalıştırma

Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görev üçüncü açıklanmaktadır. Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

WCF uygulaması oluşturmak için sonraki görev, bir konsol uygulamasında bir WCF Hizmeti barındırma sağlamaktır. Bir WCF hizmeti bir veya daha fazla sunan *uç noktaları*, her biri bir veya daha fazla hizmet işlemleri sunar. Hizmet uç noktası aşağıdaki bilgileri belirtir: 
- Adres hizmetini bulabileceğiniz yerdir.
- Bir istemci hizmeti ile nasıl iletişim kurması gereken açıklayan bilgileri içeren bir bağlama. 
- İstemcilere hizmet sağlayan işlevselliği tanımlayan bir sözleşme.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - Oluşturun ve bir WCF Hizmeti barındırma için bir konsol uygulama projesi yapılandırın.
> - WCF Hizmeti barındırma için kod ekleyin.
> - Yapılandırma dosyasını güncelleştirin.
> - WCF hizmeti başlatın ve doğrulamak çalışıyor.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Oluşturma ve barındırma hizmeti bir konsol uygulama projesi yapılandırma

1. Visual Studio'da konsol uygulaması projesi oluşturun: 
 
    1. Gelen **dosya** menüsünde **açık** > **proje/çözüm** ve **GettingStarted** çözüm, daha önce oluşturduğunuz (*GettingStarted.sln*). **Aç**'ı seçin.

    2. Gelen **görünümü** menüsünde **Çözüm Gezgini**.
    
    3. İçinde **Çözüm Gezgini** penceresinde **GettingStarted** çözüm (üst düğümü) ve ardından **Ekle** > **YeniProje** kısayol menüsünden. 

    4. İçinde **Yeni Proje Ekle** penceresinde, sol tarafta, select **Windows Masaüstü** kategorisi altında **Visual C#**  veya **Visual Basic**. 

    5. Seçin **konsol uygulaması (.NET Framework)** şablon girin *GettingStartedHost* için **adı**. **Tamam**’ı seçin.

2. Başvuru ekleme **GettingStartedHost** için proje **GettingStartedLib** proje: 

    1. İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedHost** proje ve ardından **BaşvuruEkle** kısayol menüsünden. 

    2. İçinde **Başvuru Ekle** iletişim altında **projeleri** penceresinin sol taraftan **çözüm**. 
 
    3. Seçin **GettingStartedLib** penceresi tıklayın ve ardından Merkezi bölümünde **Tamam**. 

       Bu eylem içinde tanımlanmış türlere yapar **GettingStartedLib** proje için kullanılabilir **GettingStartedHost** proje.

3. Başvuru ekleme **GettingStartedHost** için proje <xref:System.ServiceModel> derleme: 

    1. İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedHost** proje ve ardından **BaşvuruEkle** kısayol menüsünden.
    
    2. İçinde **Başvuru Ekle** penceresinin altında **derlemeleri** penceresinin sol taraftan **Framework**. 

    3. Seçin **System.ServiceModel**ve ardından **Tamam**. 
    
    4. Çözüm seçerek Kaydet **dosya** > **Tümünü Kaydet**.

## <a name="add-code-to-host-the-service"></a>Hizmeti barındırmak için kod ekleyin

Hizmeti barındırmak için aşağıdaki adımları uygulamak için kodu ekleyin: 
   1. Temel adres için URI oluşturma.
   2. Barındırma hizmeti için bir sınıf örneği oluşturun.
   3. Hizmet uç noktası oluşturun.
   4. Meta veri değişimi etkinleştirin.
   5. Gelen iletileri dinlemek için hizmet ana bilgisayarı açın.
  
Kodu aşağıdaki değişiklikleri yapın:

1. Açık **Program.cs** veya **Module1.vb** dosyası **GettingStartedHost** proje ve onun kodu aşağıdaki kodla değiştirin:

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
    
    Bu kodu nasıl çalıştığı hakkında daha fazla bilgi için bkz: [hizmet programı adımları barındırma](#service-hosting-program-steps).

2. Proje özelliklerini güncelleştirin:

   1. İçinde **Çözüm Gezgini** penceresinde **GettingStartedHost** klasöre tıklayın ve ardından **özellikleri** kısayol menüsünden.

   2. Üzerinde **GettingStartedHost** özellikleri sayfasında **uygulama** sekmesinde:

      - İçin C# projeleri, select **GettingStartedHost.Program** gelen **Başlangıç nesnesi** listesi.

      - Visual Basic projeleri için seçin **Service.Program** gelen **Başlangıç nesnesi** listesi.

   3. Gelen **dosya** menüsünde **Tümünü Kaydet**.

## <a name="verify-the-service-is-working"></a>Hizmetinin çalıştığını doğrulayın

1. Çözümü derleyin ve çalıştırın **GettingStartedHost** Konsolu Visual Studio içinde uygulama. 

    Hizmet, yönetici ayrıcalıklarıyla çalıştırılmalıdır. Programını çalıştırdığınızda, Visual Studio'nun yönetici ayrıcalıklarıyla açılan çünkü **GettingStartedHost** Visual Studio'da da yönetici ayrıcalıklarına sahip bir uygulama çalıştırılır. Alternatif olarak, yönetici olarak yeni bir komut istemi açın (seçin **daha fazla** > **yönetici olarak çalıştır** kısayol menüsünden) çalıştırıp **GettingStartedHost.exe**  içindeki.

2. Bir web tarayıcısı açın ve hizmetin sayfasına göz atın `http://localhost:8000/GettingStarted/CalculatorService`.
   
   > [!NOTE]
   > Bunun gibi hizmetleri uygun HTTP adresleri dinlemek makinede kaydetme izni gerektirir. Yönetim hesapları, bu izne sahiptir, ancak yönetici olmayan hesapların HTTP ad alanları için izin verilmelidir. Ad alanı ayırmaları yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma HTTP ve HTTPS](feature-details/configuring-http-and-https.md). 

## <a name="service-hosting-program-steps"></a>Hizmet barındırma program adımları

Hizmet aşağıdaki gibi açıklandığı gibi ana bilgisayar için eklenen kodu adımları:

- **1. adım**: Bir örneğini oluşturmak `Uri` hizmetin taban adresi için sınıf. Temel adres içeren bir URL, bir hizmeti tanımlayan bir isteğe bağlı bir URI'ya sahip. Temel adres gibi biçimlendirilir: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. HTTP taşıma, localhost, 8000 numaralı bağlantı noktasını ve GettingStarted URI segmenti hesaplayıcı hizmeti temel adresi kullanır.

- **2. adım**: Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> hizmeti barındırmak için kullanılan sınıf. Oluşturucu iki parametre alır: Hizmet sözleşmesi ve hizmetin taban adresi uygulayan sınıf türü.

- **3. adım**: Oluşturma bir <xref:System.ServiceModel.Description.ServiceEndpoint> örneği. Hizmet uç noktası bir adresi, bağlama ve hizmet sözleşmesi oluşur. <xref:System.ServiceModel.Description.ServiceEndpoint> Oluşturucusu hizmet sözleşme arabirimi türü, bağlama ve bir adresi oluşur. Hizmet sözleşme `ICalculator`, tanımlanan ve hizmet türüne uygulayın. Bu örnek için bağlama <xref:System.ServiceModel.WSHttpBinding>, yerleşik bir bağlamadır ve WS - için uygun uç noktalarına bağlayan * belirtimleri. WCF bağlamaları hakkında daha fazla bilgi için bkz: [WCF bağlamaları genel bakış](bindings-overview.md). Uç noktayı tanımlamak için temel adres bir adres sonuna ekleyin. Kod CalculatorService ve tam uç nokta adresi olarak adresini belirten `http://localhost:8000/GettingStarted/CalculatorService`.

    > [!IMPORTANT]
    > .NET Framework sürüm 4 ve sonraki sürümlerinde, bir hizmet uç noktası eklemek isteğe bağlıdır. Kod veya yapılandırma, eklemezseniz bu sürümleri için WCF taban adresini ve sözleşme hizmeti tarafından uygulanan her bir birleşimi için bir varsayılan uç nokta ekler. Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [bir uç nokta adresi belirtme](specifying-an-endpoint-address.md). Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](samples/simplified-configuration-for-wcf-services.md).

- **4. adım**: Meta veri değişimi etkinleştirin. İstemcileri, hizmet işlemleri çağırmak için proxy oluşturmak için meta veri değişimi kullanın. Meta veri değişimi etkinleştirmek için oluşturun bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek olarak ayarlayın, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> özelliğini `true`ve ekleme `ServiceMetadataBehavior` nesnesini <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonunu <xref:System.ServiceModel.ServiceHost> örneği.

- **5. adım**: Açık <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için. Uygulama, basmanızı bekler **Enter**. Uygulama örneğini oluşturur sonra <xref:System.ServiceModel.ServiceHost>, try/catch bloğu yürütür. Güvenli bir şekilde tarafından oluşturulan özel durumları yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost>, bkz: [kullanım Kapat ve iptal WCF istemci kaynaklar serbest bırakılacaksa](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Bir WCF hizmet kitaplığı eklediğinizde, hizmet ana bilgisayarı yeniden başlatarak hatalarını ayıklıyorsanız Visual Studio bunu sizin için barındırır. Çakışmaları önlemek için Visual Studio WCF hizmet kitaplığı barındırma veritabanından engelleyebilirsiniz. 
> 1. Seçin **GettingStartedLib** projesi **Çözüm Gezgini** ve **özellikleri** kısayol menüsünden.
> 2. Seçin **WCF seçenekleri** kaldırın **Başlat WCF hizmet aynı çözümdeki başka bir proje hata ayıklama konağı**.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> - Oluşturun ve bir WCF Hizmeti barındırma için bir konsol uygulama projesi yapılandırın.
> - WCF Hizmeti barındırma için kod ekleyin.
> - Yapılandırma dosyasını güncelleştirin.
> - WCF hizmeti başlatın ve doğrulamak çalışıyor.

Bir WCF istemcisi oluşturma hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: Bir WCF istemcisi oluşturma](how-to-create-a-wcf-client.md)
