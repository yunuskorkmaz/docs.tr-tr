---
title: "Bağlamada Zaman Aşımı Değerlerini Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce70b8bca923645ea1e00a55ec4d41903d828a99
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2018
---
# <a name="configuring-timeout-values-on-a-binding"></a>Bağlamada Zaman Aşımı Değerlerini Yapılandırma
WCF bağlamaları birtakım zaman aşımı ayarları yok. Bu zaman aşımı ayarını ayarları doğru değil yalnızca hizmetinizin performans aynı zamanda play bir rol kullanılabilirlik ve güvenlik hizmetinizin artırabilir. WCF bağlamaları üzerinde aşağıdaki zaman aşımları kullanılabilir:  
  
1.  openTimeout  
  
2.  closeTimeout  
  
3.  SendTimeout  
  
4.  ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>WCF bağlama zaman aşımları  
 Bu konuda tartışılan ayarların her biri bağlama, kendisini, kod veya yapılandırma üzerinde yapılır. Aşağıdaki kod programlı olarak zaman aşımı kendini barındıran hizmet bağlamında WCF bağlamasında nasıl ayarlanacağını gösterir.  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");
    
    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));
        
        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);
        
        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();
        
        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 Aşağıdaki örnek bir yapılandırma dosyasına bağlama zaman aşımları yapılandırma gösterir.  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00" 
                 closeTimeout="00:10:00" 
                 sendTimeout="00:10:00" 
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 Bu ayarlar hakkında daha fazla bilgi için belgelere bulunabilir <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
### <a name="client-side-timeouts"></a>İstemci tarafı zaman aşımları  
 İstemci tarafında:  
  
1.  SendTimeout – tam bir ileti gönderme işlemini yönetir, OperationTimeout başlatmak için kullanılan bir istek/yanıt hizmet işlemi için bir yanıt iletisi alma dahil olmak üzere. Bu zaman aşımı yanıt iletileri bir geri çağırma sözleşme yönteminden gönderirken de geçerlidir.  
  
2.  OpenTimeout – hiçbir açık zaman aşımı değeri belirtildiğinde kanalları açarken kullanılan.  
  
3.  CloseTimeout – hiçbir açık zaman aşımı değeri belirtildiğinde kanalları kapatırken kullanılır.  
  
4.  ReceiveTimeout – kullanılmaz.  
  
### <a name="service-side-timeouts"></a>Hizmet tarafı zaman aşımları  
 Hizmet tarafında:  
  
1.  SendTimeout, OpenTimeout, CloseTimeout gibi istemcide aynıdır.  
  
2.  ReceiveTimeout – ne kadar oturum zaman aşımına uğramadan önce boşta kalabileceği denetleyen oturum boşta kalma zaman aşımı başlatmak için hizmet Framework katman tarafından kullanılan.
