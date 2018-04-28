---
title: Temel Örnek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d692b33c84f12976e2d1c263ca9d68475667c2a8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="basic-sample"></a>Temel Örnek
Bu örnek, bir hizmet bulunabilirlik yapma ve aramak ve bulunabilirlik hizmetini çağırmak nasıl göstermektedir. Bu örnek iki projeden oluşan: hizmet ve istemci.  
  
> [!NOTE]
>  Bu örnek kodda bulma uygular.  Yapılandırmada bulma uygulayan bir örnek için bkz: [yapılandırma](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Hizmet  
 Bu bir basit hesap makinesi hizmetinin uygulamasıdır. Kod bulunabilir bulma ilgili `Main` burada bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına eklenir ve <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki kodda gösterildiği gibi eklenir.  
  
```  
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
 İstemcinin kullandığı bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmet bulunamadı. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, Standart bir uç noktası, istemci açıldığında hizmet uç noktası giderir. Bu durumda, <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmet sözleşmesini hizmet arar. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Üzerinden arama yapar bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> varsayılan olarak. Hizmet uç noktası bulduğunda, istemci, bu hizmete belirtilen bağlama üzerinden bağlanır.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 İstemci olarak adlandırılan bir yöntem tanımlanır `InvokeCalculatorService` kullanan <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri aramak için sınıf. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Devraldığı <xref:System.ServiceModel.Description.ServiceEndpoint>için geçirilebilir nedenle `InvokeCalculatorService` yöntemi. Bu örnek daha sonra kullanır <xref:System.ServiceModel.Discovery.DynamicEndpoint> bir örneğini oluşturmak için `CalculatorServiceClient` ve hesap makinesi hizmetinin çeşitli işlemler çağırır.  
  
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
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örneği çalıştırmak için doğru URL ACL eklenmesi gerekir. Daha fazla bilgi için bkz: [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir. Komut olduğu gibi çalışmazsa, etki alanı ve kullanıcı adı şu bağımsız değişkenleri yerine isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Basic.sln açın ve örnek oluşturun.  
  
3.  Service.exe uygulamayı çalıştırın.  
  
4.  Hizmeti başlatıldıktan sonra client.exe çalıştırın.  
  
5.  İstemci hizmet adresini bilmeden bulamıyor gözlemleyin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a>Ayrıca Bkz.
