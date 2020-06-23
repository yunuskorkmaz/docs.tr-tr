---
title: Bağlamada Zaman Aşımı Değerlerini Yapılandırma
description: Hizmetinizin performansını, kullanılabilirliğini ve güvenliğini geliştirmek üzere WCF bağlamaları için zaman aşımı ayarlarını yönetmeyi öğrenin.
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: c41824a242d9b42290183cd70b9acf5b8ee59e6b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245121"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Bağlamada Zaman Aşımı Değerlerini Yapılandırma
WCF bağlamalarında kullanılabilir bir dizi zaman aşımı ayarı vardır. Bu zaman aşımı ayarlarının doğru ayarlanması yalnızca hizmetinizin performansını değil, hizmetinizin kullanılabilirliği ve güvenliğine ilişkin bir rol de yürütebilir. Aşağıdaki zaman aşımları WCF bağlamaları üzerinde kullanılabilir:  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. Binding üstündeki SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>WCF bağlama zaman aşımları  
 Bu konu başlığında ele alınan ayarların her biri, kodda veya yapılandırmada bağlama sırasında yapılır. Aşağıdaki kod, şirket içinde barındırılan bir hizmet bağlamında bir WCF bağlamasında zaman aşımlarını programlı bir şekilde ayarlamayı gösterir.  
  
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
  
 Aşağıdaki örnek, bir yapılandırma dosyasındaki bağlamadaki zaman aşımlarının nasıl yapılandırılacağını gösterir.  
  
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
  
 Bu ayarlar hakkında daha fazla bilgi, sınıfının belgelerinde bulunabilir <xref:System.ServiceModel.Channels.Binding> .  
  
### <a name="client-side-timeouts"></a>İstemci tarafı zaman aşımları  
 İstemci tarafında:  
  
1. SendTimeout – bir istek/yanıt hizmeti işlemi için yanıt iletisi alma da dahil olmak üzere bir ileti gönderme işlemini yöneten OperationTimeout 'u başlatmak için kullanılır. Bu zaman aşımı Ayrıca, bir geri çağırma sözleşmesi yönteminden yanıt iletileri gönderilirken de geçerlidir.  
  
2. OpenTimeout: açık bir zaman aşımı değeri belirtilmediğinde kanallar açılırken kullanılır.  
  
3. CloseTimeout: açık bir zaman aşımı değeri belirtilmediğinde kanallar kapatılırken kullanılır.  
  
4. ReceiveTimeout – kullanılmaz.  
  
### <a name="service-side-timeouts"></a>Hizmet tarafı zaman aşımları  
 Hizmet tarafında:  
  
1. SendTimeout, OpenTimeout, CloseTimeout, istemci ile aynıdır.  
  
2. ReceiveTimeout: bir oturumun zaman aşımından önce ne kadar süreyle boşta kalabileceğini denetleyen oturum boşta kalma zaman aşımını başlatmak için Service Framework katmanı tarafından kullanılır.
