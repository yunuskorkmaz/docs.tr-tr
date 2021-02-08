---
description: 'Daha fazla bilgi edinin: temel örnek'
title: Temel Örnek
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 064c3d616a911f789050ccd5da433ed10fcfb596
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778847"
---
# <a name="basic-sample"></a>Temel Örnek

Bu örnek, bir hizmetin bulunabilir hale getirme ve keşfedilebilir bir hizmeti nasıl arayılacağını gösterir. Bu örnek iki projeden oluşur: hizmet ve istemci.

> [!NOTE]
> Bu örnek kodda bulma işlemini uygular.  Yapılandırmada bulmayı uygulayan bir örnek için bkz. [yapılandırma](configuration-sample.md).

## <a name="service"></a>Hizmet

Bu, basit bir Hesaplayıcı hizmet uygulamasıdır. Bulma ile ilgili kod, `Main` <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına eklenen ve <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki kodda gösterildiği gibi eklenen yerlerde bulunabilir.

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

İstemci <xref:System.ServiceModel.Discovery.DynamicEndpoint> , hizmetini bulmak için bir kullanır. <xref:System.ServiceModel.Discovery.DynamicEndpoint>Standart bir uç nokta, istemci açıldığında hizmetin uç noktasını çözer. Bu durumda, hizmet <xref:System.ServiceModel.Discovery.DynamicEndpoint> sözleşmesini temel alan hizmeti arar. <xref:System.ServiceModel.Discovery.DynamicEndpoint>Aramayı <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Varsayılan olarak bir olarak yapar. Bir hizmet uç noktası bulduktan sonra istemci, belirtilen bağlama üzerinden bu hizmete bağlanır.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

İstemci, `InvokeCalculatorService` <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri aramak için sınıfını kullanan adlı bir yöntemi tanımlar. , <xref:System.ServiceModel.Discovery.DynamicEndpoint> Öğesinden devralır <xref:System.ServiceModel.Description.ServiceEndpoint> , bu nedenle yöntemine geçirilebilirler `InvokeCalculatorService` . Örnek daha sonra <xref:System.ServiceModel.Discovery.DynamicEndpoint> örneğini oluşturmak için öğesini kullanır `CalculatorServiceClient` ve hesap makinesi hizmetinin çeşitli işlemlerini çağırır.

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

1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md). Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Visual Studio 2012 kullanarak, Basic. sln ' yi açın ve örneği derleyin.

3. service.exe uygulamasını çalıştırın.

4. Hizmet başladıktan sonra client.exe çalıştırın.

5. İstemcinin adresini bilmeden hizmeti bulabildiğinin gözlemleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
