---
title: Bağlamada Zaman Aşımı Değerlerini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: f323dfff338f8a3ba24caab6df3b3916d3ae0d13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773252"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Bağlamada Zaman Aşımı Değerlerini Yapılandırma
WCF bağlamaları birtakım zaman aşımı ayarları vardır. Bu zaman aşımı ayarını ayarları doğru değil yalnızca hizmetinizin performansını aynı zamanda play bir rol kullanılabilirlik ve güvenlik hizmetinizin artırabilir. Şu zaman aşımları, WCF bağlamaları üzerinde kullanılabilir:  
  
1. opentimeout =  
  
2. closeTimeout  
  
3. SendTimeout  
  
4. receiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>WCF bağlama zaman aşımları  
 Bu konuda tartışılan ayarların her biri bağlama üzerinde kendisi, kod veya yapılandırma ya da yapılır. Aşağıdaki kod, zaman aşımları şirket içinde barındırılan bir hizmet bağlamı WCF bağlamasında programlanarak nasıl ayarlanacağını gösterir.  
  
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
  
 Aşağıdaki örnek bir yapılandırma dosyası bir bağlamada zaman aşımı yapılandırma gösterilmektedir.  
  
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
  
 Bu ayarlar hakkında daha fazla bilgi için belgelerinde bulunabilir <xref:System.ServiceModel.Channels.Binding> sınıfı.  
  
### <a name="client-side-timeouts"></a>İstemci tarafı zaman aşımları  
 İstemci tarafında:  
  
1. SendTimeout – tüm ileti gönderme işlemini yönetir, OperationTimeout başlatmak için kullanılan bir yanıt iletisi için bir istek/yanıt hizmet işlemi alma dahil olmak üzere. Bu zaman aşımı, bir geri çağırma anlaşması yöntemi yanıt iletileri gönderirken de geçerlidir.  
  
2. Opentimeout = – hiçbir açık zaman aşımı değeri belirtildiğinde kanalları açarken kullanılan.  
  
3. CloseTimeout – hiçbir açık zaman aşımı değeri belirtildiğinde Kanal kapatılırken kullanılır.  
  
4. ReceiveTimeout – kullanılmaz.  
  
### <a name="service-side-timeouts"></a>Hizmet tarafı zaman aşımları  
 Hizmet tarafında:  
  
1. SendTimeout opentimeout =, CloseTimeout istemci olarak aynıdır.  
  
2. ReceiveTimeout – ne kadar oturum zaman aşımına uğramadan önce boşta kalabileceği denetleyen oturum boşta kalma zaman aşımı başlatmak için hizmet Framework katmanı tarafından kullanılır.
