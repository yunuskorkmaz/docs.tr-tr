---
title: Temel Örnek
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 07015c61ccab303d0fe38e65077d984ff40ce357
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045716"
---
# <a name="basic-sample"></a>Temel Örnek

Bu örnek, bir hizmetin bulunabilir hale getirme ve keşfedilebilir bir hizmeti nasıl arayılacağını gösterir. Bu örnek iki projeden oluşur: hizmet ve istemci.

> [!NOTE]
> Bu örnek kodda bulma işlemini uygular.  Yapılandırmada bulmayı uygulayan bir örnek için bkz. [yapılandırma](../../../../docs/framework/wcf/samples/configuration-sample.md).

## <a name="service"></a>Hizmet

Bu, basit bir Hesaplayıcı hizmet uygulamasıdır. Bulma ile ilgili kod, hizmet ana bilgisayarına `Main` eklenen ve <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki kodda gösterildiği gibi eklenen yerlerde bulunabilir.

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

İstemci, hizmetini bulmak <xref:System.ServiceModel.Discovery.DynamicEndpoint> için bir kullanır. <xref:System.ServiceModel.Discovery.DynamicEndpoint>Standart bir uç nokta, istemci açıldığında hizmetin uç noktasını çözer. Bu durumda <xref:System.ServiceModel.Discovery.DynamicEndpoint> , hizmet sözleşmesini temel alan hizmeti arar. Aramayı varsayılan olarak bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> olarak yapar. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Bir hizmet uç noktası bulduktan sonra istemci, belirtilen bağlama üzerinden bu hizmete bağlanır.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

İstemci, hizmetleri aramak için `InvokeCalculatorService` <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfını kullanan adlı bir yöntemi tanımlar. , <xref:System.ServiceModel.Discovery.DynamicEndpoint> `InvokeCalculatorService` Öğesinden <xref:System.ServiceModel.Description.ServiceEndpoint>devralır, bu nedenle yöntemine geçirilebilirler. Örnek daha sonra `CalculatorServiceClient` örneğini oluşturmak <xref:System.ServiceModel.Discovery.DynamicEndpoint> için öğesini kullanır ve hesap makinesi hizmetinin çeşitli işlemlerini çağırır.

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

1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Daha fazla bilgi için bkz. [http ve https yapılandırma](https://go.microsoft.com/fwlink/?LinkId=70353). Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Visual Studio 2012 kullanarak, Basic. sln ' yi açın ve örneği derleyin.

3. Service. exe uygulamasını çalıştırın.

4. Hizmet başladıktan sonra Client. exe ' yi çalıştırın.

5. İstemcinin adresini bilmeden hizmeti bulabildiğinin gözlemleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
