---
title: "Nasıl yapılır: Temel Bir Windows Communication Foundation Hizmeti Barındırma ve Çalıştırma"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92aa512a12911913c1d4d7ca1587bb04df0a501d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Nasıl yapılır: Temel Bir Windows Communication Foundation Hizmeti Barındırma ve Çalıştırma
Bu üçüncü altı görev oluşturmak için gerekli olan bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulama. Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.  
  
 Bu konu, barındırmak açıklar bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] bir konsol uygulamasında hizmet. Bu yordam, aşağıdaki adımlardan oluşur:  
  
-   Hizmet barındırmak için bir konsol uygulama projesi oluşturun.  
  
-   Hizmeti için hizmet ana bilgisayarını oluşturun.  
  
-   Meta veri değişimi etkinleştirin.  
  
-   Hizmet ana bilgisayarı açın.  
  
 Bu görevde yazılan kodların tam listesi yordamdan örnekte sağlanır.  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>Hizmet ana bilgisayar için yeni bir konsol uygulaması oluşturmak için  
  
1.  Başlarken çözüm seçerek, üzerinde sağ tıklayarak yeni bir konsol uygulama projesi oluşturma **Ekle**, **yeni proje**. İçinde **Yeni Proje Ekle** iletişim seçin sol tarafındaki iletişim **Windows** altında **C#** veya **VB**. İletişim kutusunun Orta kısım seçin **konsol uygulaması**. Projeyi GettingStartedHost olarak adlandırın.  
  
2.  Sağ tıklayarak GettingStartedHost projenin hedef çerçevesini .NET Framework 4.5 ayarlamak **GettingStartedHost** Çözüm Gezgini'nde seçerek **özellikleri**. Aşağı açılan kutusunda etiketli **hedef Framework** seçin **.NET Framework 4.5**. Hedef Framework'ü GettingStartedHost Proje Özellikleri iletişim kutusunda, biraz farklı VB projedir ayarı, tıklatın **derleme** sekmesinde ekranın sol tarafında ve ardından **Gelişmiş derleme Seçenekler** iletişim kutusunun sol alt köşesindeki düğmesi. Ardından **.NET Framework 4.5** açılır kutusunda etiketli **hedef Framework**.  
  
     Hedef Framework'ü neden olacak ayarı [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] çözümü yeniden yüklemek için basın **Tamam** istendiğinde.  
  
3.  Sağ tıklayarak GettingStartedHost projeye GettingStartedLib projesine bir başvuru ekleyin **başvuruları** klasörü seçin ve Çözüm Gezgini GettingStartedHost projesinde altında **Başvuru Ekle** . İçinde **Başvuru Ekle** iletişim kutusunda **çözüm** tıklayın ve iletişim merkezi bölümünde select GettingStartedLib ve iletişim sol taraftaki **Ekle**. Bu GettingStartedLib GettingStartedHost projesi için kullanılabilir tanımlanan türler sağlar.  
  
4.  System.ServiceModel başvuru GettingStartedHost projeye sağ tıklayarak ekleyin **başvuru** klasörü altında Çözüm Gezgini'nde ve select GettingStartedHost proje **Ekle** Başvuru. İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki. Arama derlemeleri metin kutusuna yazın `System.ServiceModel`. İletişim kutusunun Orta kısım seçin **System.ServiceModel**, tıklatın **Ekle** düğmesine tıklayın ve **Kapat** düğmesi. Ana menü aşağıdaki Tümünü Kaydet düğmesine tıklayarak çözümü kaydedin.  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
-   Program.cs veya Module.vb dosyasını açın ve aşağıdaki kodu girin:  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
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
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
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
  
    1.  1. adım - hizmetin taban adresi tutmak için URI sınıfının bir örneğini oluşturur. Hizmetleri, bir taban adresi içeren bir URL ve isteğe bağlı bir URI tarafından tanımlanır. Temel adres şekilde biçimlendirilmiş: [aktarım] :// [makine adı veya etki alanı] [: isteğe bağlı bağlantı noktası #] / [isteğe bağlı URI segmenti] localhost, bağlantı noktası 8000 ve URI segmentlere "GettingStarted", hesap makinesi hizmetinin temel adres HTTP aktarımı kullanır.  
  
    2.  Adım 2 – bir örnek oluşturur / <xref:System.ServiceModel.ServiceHost> hizmet barındırmak için sınıf. Oluşturucusu iki parametre, hizmet sözleşmesi uygulayan sınıf türü ve hizmetin taban adresi alır.  
  
    3.  Adım 3 – oluşturur bir <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` örneği. Hizmet uç noktası bir adresi, bağlama ve hizmet sözleşmesini oluşur. <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` Oluşturucusu bu nedenle hizmet sözleşme arabirimi türü, bir bağlama ve bir adresi alır. Hizmet sözleşme `ICalculator`, tanımlı ve hizmet türü uygulayın. Bu örnekte kullanılan bağlama <xref:System.ServiceModel.WSHttpBinding> WS - için uygun Uç noktalara bağlanmak için kullanılan yerleşik bir bağlama olduğu * belirtimleri. WCF bağlamaları hakkında daha fazla bilgi için bkz: [WCF bağlamaları genel bakış](../../../docs/framework/wcf/bindings-overview.md). Adres uç noktayı tanımlamak için taban adresi eklenir. Uç nokta için tam adresi "CalculatorService" Bu kodda belirtilen adresi olduğundan `"http://localhost:8000/GettingStarted/CalculatorService"` .NET Framework 4.0 kullanırken, isteğe bağlı ya da daha yeni bir hizmet uç noktası ekleniyor. Uç nokta yok, kod veya yapılandırma, eklenirse, bu sürümlerde WCF her taban adresi ve hizmet tarafından uygulanan anlaşmanın bileşimi için bir varsayılan uç nokta ekler. Uç noktaları varsayılan hakkında daha fazla bilgi için bkz: [bir uç noktası adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
        > [!IMPORTANT]
        >  Hizmet uç noktası ekleme, .NET Framework 4 kullanırken, isteğe bağlı veya üzeri. Uç nokta yok, kod veya yapılandırma, eklenirse, bu sürümlerde WCF her taban adresi ve hizmet tarafından uygulanan anlaşmanın bileşimi için bir varsayılan uç nokta ekler. Uç noktaları varsayılan hakkında daha fazla bilgi için bkz: [bir uç noktası adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
    4.  4. adım – etkinleştir meta veri değişimi. İstemciler, hizmet işlemlerini çağırma için kullanılacak proxy oluşturmak için meta veri değişimi kullanır. Etkinleştirmek için meta verileri exchange oluşturması bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği, ayarlayın 's <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğine `true`ve davranış eklemek <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` koleksiyonu <xref:System.ServiceModel.ServiceHost> örneği.  
  
    5.  5. adım – açık <xref:System.ServiceModel.ServiceHost> gelen iletiler için dinleme için. İsabet kullanıcının kodu bekler bildirimi girin. Bunu yaparsanız, uygulama hemen kapatılacak ve hizmet kapanacak. Try/catch bloğu kullanılan de dikkat edin. Sonra <xref:System.ServiceModel.ServiceHost> bırakıldı örneği, diğer tüm kod bir try/catch bloğu içinde yerleştirilir. Güvenli bir şekilde tarafından oluşturulan özel durumları yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost>, bkz: [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
### <a name="to-verify-the-service-is-working"></a>Hizmetin çalıştığını doğrulamak için  
  
1.  İçinde gelen GettingStartedHost konsol uygulamasını çalıştırın [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]. Çalışırken [!INCLUDE[wv](../../../includes/wv-md.md)] ve sonraki işletim sistemleri, hizmet yönetici ayrıcalıklarıyla çalıştırılmalıdır. Çünkü [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] yönetici ayrıcalıklarıyla çalıştırın, GettingStartedHost da yönetici ayrıcalıklarıyla çalıştırın. Ayrıca, yönetici ayrıcalıklarıyla çalıştıran yeni bir komut istemi başlatın ve içerdiği service.exe çalıştırın.  
  
2.  Açık Internet Explorer ve hizmetin hata ayıklama sayfası adresindeki `http://localhost:8000/GettingStarted/CalculatorService`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek hizmet sözleşmesini ve önceki kısımlarında öğreticide içerir ve hizmeti bir konsol uygulamasında barındırır.  
  
 Bu komut satırı derleyicisi ile derlemek için IService1.cs ve service1.cs dosyasını bir sınıf kitaplığı başvuran içine derleme `System.ServiceModel.dll`. Ve Program.cs bir konsol uygulaması derleyin.  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
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
'IService1.vb  
Imports System  
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
'Service1.vb  
Imports System  
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
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
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
>  Bunun gibi hizmetleri HTTP adreslerini dinleme için makinede Kaydet izni gerektirir. Yönetici hesapları, bu izne sahip, ancak yönetici olmayan bir hesap HTTP ad alanları için izin verilmelidir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]ad alanı ayırmaları yapılandırma hakkında [yapılandırma HTTP ve HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Altında çalışırken [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], service.exe yönetici ayrıcalıklarıyla çalıştırılmalıdır.  
  
 Şimdi hizmeti çalışıyor. İle devam [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Sorun giderme bilgileri için bkz: [Başlarken Öğreticisi sorun giderme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Kendini barındırma](../../../docs/framework/wcf/samples/self-host.md)
