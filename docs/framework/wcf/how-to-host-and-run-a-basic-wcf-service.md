---
title: Nasıl temel bir Windows Communication Foundation Hizmeti barındırma ve çalıştırma
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 73633c2c6119204f2fb608b32ae794a2e07b27d0
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747080"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Nasıl temel bir Windows Communication Foundation Hizmeti barındırma ve çalıştırma

Üçüncü altı görev bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur. Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](getting-started-tutorial.md) konu.

Bu konu, bir Windows Communication Foundation (WCF) hizmeti bir konsol uygulamasında barındırma açıklar. Bu yordam, aşağıdaki adımlardan oluşur:

- Hizmeti barındırmak için bir konsol uygulama projesi oluşturun.

- Hizmet konak hizmeti oluşturun.

- Meta veri değişimi etkinleştirin.

- Hizmet ana bilgisayarı açın.

Bu görevde yazılan kodların tam listesi yordamdan örnekte sağlanır.

## <a name="create-a-new-console-application-to-host-the-service"></a>Hizmeti barındırmak için yeni bir konsol uygulaması oluşturun

1. Başlarken çözüm üzerinde sağ tıklatıp seçerek Visual Studio'da yeni bir konsol uygulaması projesi oluşturma **Ekle** > **yeni proje**. İçinde **Yeni Proje Ekle** seçin sol taraftaki iletişim **Windows Masaüstü** kategorisi altında **Visual C#** veya **Visual Basic**. Seçin **konsol uygulaması (.NET Framework)** şablonu ve ardından ad proje **GettingStartedHost**.

2. GettingStartedHost projeye GettingStartedLib projeye bir başvuru ekleyin. Sağ **başvuruları** klasörü altında GettingStartedHost projede **Çözüm Gezgini**ve ardından **Başvuru Ekle**. İçinde **Başvuru Ekle** iletişim kutusunda **çözüm** iletişim kutusunun sol taraftaki GettingStartedLib iletişim kutusunun orta kısmını seçin ve ardından **Ekle**. Bu, GettingStartedLib GettingStartedHost projesi için tanımlanan türleri sağlar.

3. System.ServiceModel başvuru GettingStartedHost projeye ekleyin. Sağ **başvuruları** klasörü altında GettingStartedHost projede **Çözüm Gezgini** seçip **Başvuru Ekle**. İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki **derlemeleri**. Bulmak ve seçmek **System.ServiceModel**ve ardından **Tamam**. Çözüm seçerek Kaydet **dosya** > **Tümünü Kaydet**.

## <a name="host-the-service"></a>Hizmeti barındırma

Program.cs veya Module.vb dosyasını açın ve aşağıdaki kodu girin:

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
            // Step 1 Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 Create a ServiceHost instance
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 Start the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
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
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 Create a URI to serve as the base address
            Dim baseAddress As New Uri("http://localhost:8000/GettingStarted")

            ' Step 2 Create a ServiceHost instance
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
           Try

                ' Step 3 Add a service endpoint
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 Enable metadata exchange.
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 Start the service
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

**1. adım** -hizmetin taban adresi için URI sınıf örneği oluşturur. Hizmetleri, bir taban adresi içeren bir URL ve isteğe bağlı bir URI tarafından tanımlanır. Temel adres gibi biçimlendirilir: [aktarım] :// [makine adı veya etki alanı] [: isteğe bağlı bağlantı noktası #] / [isteğe bağlı URI segmenti] HTTP aktarımı hesaplayıcı hizmeti temel adresi kullanır, segment "GettingStarted" localhost, 8000 numaralı bağlantı noktasını ve URI

**2. adım** – bir örneğini oluşturur <xref:System.ServiceModel.ServiceHost> Hizmeti'ni barındıracak şekilde sınıfı. Oluşturucu, iki parametre, hizmet sözleşmesi uygulayan sınıf türünü ve hizmetin taban adresi alır.

**3. adım** – oluşturur bir <xref:System.ServiceModel.Description.ServiceEndpoint> örneği. Hizmet uç noktası bir adresi, bağlama ve hizmet sözleşmesi oluşur. <xref:System.ServiceModel.Description.ServiceEndpoint> Oluşturucusu bu nedenle hizmet sözleşme arabirimi türü, bağlama ve bir adresi alır. Hizmet sözleşme `ICalculator`, tanımlanan ve hizmet türüne uygulayın. Bu örnekte kullanılan bağlamanın <xref:System.ServiceModel.WSHttpBinding> WS - için uygun uç noktalarına bağlamak için kullanılan yerleşik bir bağlama olduğu * belirtimleri. WCF bağlamaları hakkında daha fazla bilgi için bkz: [WCF bağlamaları genel bakış](bindings-overview.md). Adres, uç noktayı tanımlamak için taban adresi olarak eklenir. Tam uç nokta adresi "CalculatorService" Bu kodu belirtilen adresi olduğundan `"http://localhost:8000/GettingStarted/CalculatorService"`.

> [!IMPORTANT]
> .NET Framework 4 kullanırken, isteğe bağlı veya üzeri bir hizmet uç noktası ekleniyor. Kod veya yapılandırma, uç nokta eklenirse bu sürümlerde WCF taban adresini ve sözleşme hizmeti tarafından uygulanan her bir birleşimi için bir varsayılan uç nokta ekler. Uç noktaları varsayılan hakkında daha fazla bilgi için bkz: [bir uç nokta adresi belirtme](specifying-an-endpoint-address.md). Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](./samples/simplified-configuration-for-wcf-services.md).

**4. adım** – meta veri değişimi etkinleştirin. İstemciler, meta veri değişimi, hizmet işlemlerini aramak için kullanılacak proxy üretmek için kullanır. Etkinleştirmek için meta veri değişimi oluşturma bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ayarlayın, örnek 's <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`ve davranışların eklenmesi <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonunu <xref:System.ServiceModel.ServiceHost> örneği.

**5. adım** – açık <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için. Uyarı kodunu kullanıcının isabet bekler girin. Bunu yaparsanız, uygulamayı hemen kapatmak ve hizmet kapanır. Bir try/catch bloğu kullanılan dikkat edin. Sonra <xref:System.ServiceModel.ServiceHost> olmuştur örneği, diğer tüm kod bir try/catch bloğu içinde yer alır. Güvenli bir şekilde tarafından oluşturulan özel durumları yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost>, bkz: [kullanım Kapat ve iptal WCF istemci kaynakları serbest bırakmak için](samples/use-close-abort-release-wcf-client-resources.md)

> [!IMPORTANT]
> Bir WCF hizmet kitaplığı eklediğinizde, bir hizmet konağı başlatarak ayıkladığınızda Visual Studio bunu sizin için barındırabilirsiniz. Çakışmaları önlemek için bu devre dışı bırakabilirsiniz. 
> 1. GettingStartedLib için proje özelliklerini açın.
> 2. Git **WCF seçenekleri** kaldırın **Başlat WCF hizmet hata ayıklama konağı**.

## <a name="verify-the-service-is-working"></a>Hizmetinin çalıştığını doğrulayın

1. GettingStartedHost konsolunu çalıştıran Visual Studio içinde uygulama.

   Hizmet, yönetici ayrıcalıklarıyla çalıştırılmalıdır. Visual Studio'yu yönetici ayrıcalıklarıyla açılmış olduğundan GettingStartedHost da yönetici ayrıcalıklarıyla çalıştırın. Yeni bir komut istemi kullanarak da açabilirsiniz **yönetici olarak çalıştır** ve içerdiği service.exe çalıştırın.

2. Bir web tarayıcısı açın ve hizmet hata ayıklama sayfasına göz atın `http://localhost:8000/GettingStarted/`. **Unutmayın! Bitiş eğik çizgi önemlidir.**

## <a name="example"></a>Örnek

Aşağıdaki örnek, hizmet sözleşmesini ve önceki adımdan öğreticide içerir ve hizmeti bir konsol uygulamasında barındırır.

Bu komut satırı derleyicisi ile derlemek için Iservice1.cs ve Service1.cs başvuran bir sınıf kitaplığı derleme `System.ServiceModel.dll`. Program.cs bir konsol uygulaması olarak derleyin.

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
        public interface ICalculator
        {
            [OperationContract]
            double Add(double n1, double n2);
            [OperationContract]
            double Subtract(double n1, double n2);
            [OperationContract]
            double Multiply(double n1, double n2);
            [OperationContract]
            double Divide(double n1, double n2);
        }
}
```

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

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
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 of the hosting procedure: Create ServiceHost
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 of the hosting procedure: Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 of the hosting procedure: Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
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

Namespace GettingStartedLib

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

            ' Step 2 of the hosting procedure: Create ServiceHost
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
            Try

                ' Step 3 of the hosting procedure: Add a service endpoint.
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 of the hosting procedure: Enable metadata exchange.
                ' Enable metadata exchange
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

> [!NOTE]
> Bu gibi hizmetlere HTTP adresleri dinlemek makinede kaydetme izni gerektirir. Yönetim hesapları, bu izne sahiptir, ancak yönetici olmayan hesapların HTTP ad alanları için izin verilmelidir. Ad alanı ayırmaları yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma HTTP ve HTTPS](feature-details/configuring-http-and-https.md). Visual Studio altında çalışırken, service.exe yönetici ayrıcalıklarıyla çalıştırılmalıdır.

## <a name="next-steps"></a>Sonraki adımlar

Artık hizmeti çalışıyor. Sonraki görevde bir WCF istemcisi oluşturma.

> [!div class="nextstepaction"]
> [Nasıl yapılır: Bir WCF istemcisi oluşturma](how-to-create-a-wcf-client.md)

Sorun giderme bilgileri için bkz: [Başlarken Öğreticisi sorun giderme](troubleshooting-the-getting-started-tutorial.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](samples/getting-started-sample.md)
- [Kendini Barındırma](samples/self-host.md)
- [Barındırma Hizmetleri](hosting-services.md)
