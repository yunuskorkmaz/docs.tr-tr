---
title: Temel Örnek
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 5d0470fefff86ee3a88fa290be5f349c38ca8276
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716089"
---
# <a name="basic-sample"></a>Temel Örnek

Bu örnek, bir hizmetin bulunabilir hale getirme ve keşfedilebilir bir hizmeti nasıl arayılacağını gösterir. Bu örnek iki projeden oluşur: hizmet ve istemci.

> [!NOTE]
> Bu örnek kodda bulma işlemini uygular.  Yapılandırmada bulmayı uygulayan bir örnek için bkz. [yapılandırma](../../../../docs/framework/wcf/samples/configuration-sample.md).

## <a name="service"></a>Hizmet

Bu, basit bir Hesaplayıcı hizmet uygulamasıdır. Bulma ile ilgili kod, hizmet ana bilgisayarına bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> eklendiği ve aşağıdaki kodda gösterildiği gibi bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> eklendiği `Main` bulunabilir.

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

İstemci, hizmeti bulmak için bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> kullanır. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, standart bir uç nokta, istemci açıldığında hizmetin uç noktasını çözer. Bu durumda <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmet sözleşmesini temel alan hizmeti arar. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, aramayı varsayılan olarak bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> üzerinden çeker. Bir hizmet uç noktası bulduktan sonra istemci, belirtilen bağlama üzerinden bu hizmete bağlanır.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

İstemci, hizmetleri aramak için <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfını kullanan `InvokeCalculatorService` adlı bir yöntemi tanımlar. <xref:System.ServiceModel.Discovery.DynamicEndpoint> <xref:System.ServiceModel.Description.ServiceEndpoint>devraldığından `InvokeCalculatorService` yöntemine geçirilebilir. Örnek daha sonra bir `CalculatorServiceClient` örneği oluşturmak için <xref:System.ServiceModel.Discovery.DynamicEndpoint> kullanır ve Hesaplayıcı hizmetinin çeşitli işlemlerini çağırır.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
