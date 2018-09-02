---
title: 'Nasıl yapılır: Temel Bir Windows Communication Foundation Hizmeti Barındırma ve Çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: e2bf16bd07c7ac9d918a4ae95d7f4aa185d436ec
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404677"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Nasıl yapılır: Temel Bir Windows Communication Foundation Hizmeti Barındırma ve Çalıştırma
Üçüncü altı görev bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur. Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.  
  
 Bu konu, bir Windows Communication Foundation (WCF) hizmeti bir konsol uygulamasında barındırma açıklar. Bu yordam, aşağıdaki adımlardan oluşur:  
  
-   Hizmeti barındırmak için bir konsol uygulama projesi oluşturun.  
  
-   Hizmet konak hizmeti oluşturun.  
  
-   Meta veri değişimi etkinleştirin.  
  
-   Hizmet ana bilgisayarı açın.  
  
 Bu görevde yazılan kodların tam listesi yordamdan örnekte sağlanır.  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>Hizmeti barındırmak için yeni bir konsol uygulaması oluşturmak için  
  
1.  Başlarken çözümü seçerken üzerinde sağ tıklayarak yeni bir konsol uygulaması projesi oluşturma **Ekle**, **yeni proje**. İçinde **Yeni Proje Ekle** sol tarafındaki iletişim Seç iletişim **Windows** altında **C#** veya **VB**. İletişim kutusunun orta kısmını seçin **konsol uygulaması**. GettingStartedHost projesini adlandırın.  
  
2.  GettingStartedHost projenin hedef çerçevesi sağ tıklanarak .NET Framework 4.5 olarak ayarlayın. **GettingStartedHost** Çözüm Gezgini'nde seçerek **özellikleri**. Açılan kutuda yer etiketli **hedef Framework'ü** seçin **.NET Framework 4.5**. Hedef Framework'ü ayarı GettingStartedHost Proje Özellikleri iletişim kutusunda bir VB projesi biraz farklıdır, tıklayın **derleme** sekmesinde ekranın sol tarafındaki ve ardından **Gelişmiş derleme Seçenekleri** iletişim kutusunun sol alt köşesindeki düğme. Ardından **.NET Framework 4.5** kutuda etiketli **hedef Framework'ü**.  
  
     Hedef Framework'ü neden ayarı [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] çözümü yeniden yüklemek için basın **Tamam** istendiğinde.  
  
3.  Sağ tıklanarak GettingStartedHost projeye GettingStartedLib projeye bir başvuru eklemek **başvuruları** klasörü altında Çözüm Gezgini seçip GettingStartedHost proje **Başvuru Ekle** . İçinde **Başvuru Ekle** iletişim kutusunda **çözüm** iletişim ve select GettingStartedLib tıklayın ve iletişim merkezi bölümünde sol tarafta **Ekle**. Bu, GettingStartedLib GettingStartedHost projesi için tanımlanan türleri sağlar.  
  
4.  System.ServiceModel başvuru GettingStartedHost projeye sağ tıklayarak ekleyin **başvuru** klasörü altında Çözüm Gezgini seçip GettingStartedHost proje **Ekle** Başvuru. İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki. Derlemeleri arama metin kutusuna yazın `System.ServiceModel`. İletişim kutusunun orta kısmını seçin **System.ServiceModel**, tıklayın **Ekle** düğmesini **Kapat** düğmesi. Ana menü altında Tümünü Kaydet düğmesine tıklayarak çözüm kaydedin.  
  
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
  
    1.  1. adım - hizmet temel adresini tutacak URI sınıfının bir örneğini oluşturur. Hizmetleri, bir taban adresi içeren bir URL ve isteğe bağlı bir URI tarafından tanımlanır. Temel adres gibi biçimlendirilir: [aktarım] :// [makine adı veya etki alanı] [: isteğe bağlı bağlantı noktası #] / [isteğe bağlı URI segmenti] HTTP aktarımı hesaplayıcı hizmeti temel adresi kullanır, segment "GettingStarted" localhost, 8000 numaralı bağlantı noktasını ve URI  
  
    2.  Adım 2 – bir örneğini oluşturur / <xref:System.ServiceModel.ServiceHost> Hizmeti'ni barındıracak şekilde sınıfı. Oluşturucu, iki parametre, hizmet sözleşmesi uygulayan sınıf türünü ve hizmetin taban adresi alır.  
  
    3.  Adım 3 – oluşturur bir <xref:System.ServiceModel.Description.ServiceEndpoint> örneği. Hizmet uç noktası bir adresi, bağlama ve hizmet sözleşmesi oluşur. <xref:System.ServiceModel.Description.ServiceEndpoint> Oluşturucusu bu nedenle hizmet sözleşme arabirimi türü, bağlama ve bir adresi alır. Hizmet sözleşme `ICalculator`, tanımlanan ve hizmet türüne uygulayın. Bu örnekte kullanılan bağlamanın <xref:System.ServiceModel.WSHttpBinding> WS - için uygun uç noktalarına bağlamak için kullanılan yerleşik bir bağlama olduğu * belirtimleri. WCF bağlamaları hakkında daha fazla bilgi için bkz: [WCF bağlamaları genel bakış](../../../docs/framework/wcf/bindings-overview.md). Adres, uç noktayı tanımlamak için taban adresi olarak eklenir. Tam uç nokta adresi "CalculatorService" Bu kodu belirtilen adresi olduğundan `"http://localhost:8000/GettingStarted/CalculatorService"`.  
  
        > [!IMPORTANT]
        >  .NET Framework 4 kullanırken, isteğe bağlı veya üzeri bir hizmet uç noktası ekleniyor. Kod veya yapılandırma, uç nokta eklenirse bu sürümlerde WCF taban adresini ve sözleşme hizmeti tarafından uygulanan her bir birleşimi için bir varsayılan uç nokta ekler. Uç noktaları varsayılan hakkında daha fazla bilgi için bkz: [bir uç nokta adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md). Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
    4.  4. adım – etkin meta veri değişimi. İstemciler, meta veri değişimi, hizmet işlemlerini aramak için kullanılacak proxy üretmek için kullanır. Etkinleştirmek için meta veri değişimi oluşturma bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ayarlayın, örnek 's <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`ve davranışların eklenmesi <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` koleksiyonunu <xref:System.ServiceModel.ServiceHost> örneği.  
  
    5.  Adım 5-açık <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için. Uyarı kodunu kullanıcının isabet bekler girin. Bunu yaparsanız, uygulamayı hemen kapatmak ve hizmet kapanır. Bir try/catch bloğu kullanılan dikkat edin. Sonra <xref:System.ServiceModel.ServiceHost> olmuştur örneği, diğer tüm kod bir try/catch bloğu içinde yer alır. Güvenli bir şekilde tarafından oluşturulan özel durumları yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost>, bkz: [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
> [!IMPORTANT]
> App.config dosyasında GettingStartedLib kodunda yaptığınız değişiklikleri yansıtacak şekilde düzenleyin: 
> 1. 14. satır için değiştirin `<service name="GettingStartedLib.CalculatorService">`
> 2. 17 satırına değiştirme `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. Satır 22 için değiştirin `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`
        
### <a name="to-verify-the-service-is-working"></a>Hizmetin çalıştığını doğrulamak için  
  
1.  GettingStartedHost konsol üzerinden içinde çalışan [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]. Çalışırken [!INCLUDE[wv](../../../includes/wv-md.md)] ve sonraki işletim sistemleri, hizmet yönetici ayrıcalıklarıyla çalıştırılmalıdır. Visual Studio'yu yönetici ayrıcalıklarıyla çalıştığından, GettingStartedHost da yönetici ayrıcalıklarıyla çalıştırın. Ayrıca, yönetici ayrıcalıklarıyla çalışan yeni bir komut istemi başlatın ve içerdiği service.exe çalıştırın.  
  
2.  Açık Internet Explorer ve göz atma hizmetin hata ayıklama sayfasında `http://localhost:8000/GettingStarted/CalculatorService`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, hizmet sözleşmesini ve önceki adımdan öğreticide içerir ve hizmeti bir konsol uygulamasında barındırır.  
  
 Bu komut satırı derleyicisi ile derlemek için Iservice1.cs ve Service1.cs bir sınıf kitaplığı başvuran içine derleme `System.ServiceModel.dll`. Ve Program.cs için bir konsol uygulaması derleme.  
  
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
>  Bu gibi hizmetlere HTTP adresleri dinlemek makinede kaydetme izni gerektirir. Yönetim hesapları, bu izne sahiptir, ancak yönetici olmayan hesapların HTTP ad alanları için izin verilmelidir. Ad alanı ayırmaları yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma HTTP ve HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Visual Studio altında çalışırken, service.exe yönetici ayrıcalıklarıyla çalıştırılmalıdır.  
  
 Artık hizmeti çalışıyor. Devam [nasıl yapılır: istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Sorun giderme bilgileri için bkz: [Başlarken Öğreticisi sorun giderme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
