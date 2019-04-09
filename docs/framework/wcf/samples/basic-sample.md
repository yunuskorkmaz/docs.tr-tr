---
title: Temel Örnek
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 22d5428da57b2fc8f9b97d4553b86ac2a918f0e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083030"
---
# <a name="basic-sample"></a>Temel Örnek
Bu örnek, bir hizmet bulunabilir hale getirme ve arayın ve kayıtlı bir bulunabilir hizmet çağırmak nasıl gösterir. Bu örnek iki projeden oluşan: hizmet ve istemci.

> [!NOTE]
>  Bu örnek, kod içinde bulma uygular.  Yapılandırmada bulma uygulayan bir örnek için bkz. [yapılandırma](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Hizmet  
 Bu bir basit hesap makinesi hizmet uygulamasıdır. Kod içinde bulunabilir bulma ilgili `Main` burada bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına eklenir ve <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki kodda gösterildiği gibi eklenir.  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>İstemci  
 İstemcinin kullandığı bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmetini bulamadı. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, Bir standart uç nokta, istemci açıldığında hizmetinin uç noktası giderir. Bu durumda, <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmet sözleşmesine dayalı hizmet arar. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Üzerinden arama yapar bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> varsayılan olarak. Hizmet uç noktası bulduktan sonra istemci bu hizmet için belirtilen bağlama üzerinden bağlanır.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 İstemci adı verilen bir yöntem tanımlar `InvokeCalculatorService` kullanan <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri aramak için sınıf. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Devraldığı <xref:System.ServiceModel.Description.ServiceEndpoint>, bu nedenle, geçirilebilir `InvokeCalculatorService` yöntemi. Ardından örnekte <xref:System.ServiceModel.Discovery.DynamicEndpoint> bir örneğini oluşturmak için `CalculatorServiceClient` ve çeşitli işlemler hesaplayıcı hizmeti çağırır.  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Subtract service operation.  
   result = client.Subtract(value1, value2);  
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Multiply service operation.  
   result = client.Multiply(value1, value2);  
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Divide service operation.  
   result = client.Divide(value1, value2);  
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
   Console.WriteLine();  
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örneği çalıştırmak için doğru URL ACL eklenmesi gerekir. Daha fazla bilgi için [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir. Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler yerine etki alanı ve kullanıcı adı isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Visual Studio 2012 kullanarak Basic.sln açın ve örnek oluşturma.  
  
3.  Service.exe uygulamayı çalıştırın.  
  
4.  Hizmet başlatıldıktan sonra client.exe çalıştırın.  
  
5.  İstemci hizmet adresini bilmeden bulamadı gözlemleyin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
