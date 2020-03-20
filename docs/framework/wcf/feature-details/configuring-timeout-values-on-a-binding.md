---
title: Bağlamada Zaman Aşımı Değerlerini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185283"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Bağlamada Zaman Aşımı Değerlerini Yapılandırma
WCF bağlamalarında bir dizi zaman sonu ayarı vardır. Bu zaman sonu ayarlarını doğru ayarlamak yalnızca hizmetinizin performansını artırmakla kaynı yoran aynı zamanda hizmetinizin kullanılabilirliği ve güvenliğinde de rol oynayabilir. Aşağıdaki zaman zaman ekmeleri WCF bağlamaları mevcuttur:  
  
1. OpenTimeout  
  
2. Yakın Zaman  
  
3. SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>WCF Bağlama Zaman Dilimleri  
 Bu konuda tartışılan ayarların her biri, kod veya yapılandırma da bağlamanın kendisi üzerinde yapılır. Aşağıdaki kod, kendi barındırılan bir hizmet bağlamında wcf bağlamaüzerinde zaman zaman larını nasıl programla ayarlanacağını gösterir.  
  
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
  
 Aşağıdaki örnek, yapılandırma dosyasındaki bir bağlama üzerinde zaman aşımlarının nasıl yapılandırılabildiğini gösterir.  
  
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
  
 Bu ayarlar hakkında daha fazla bilgi <xref:System.ServiceModel.Channels.Binding> sınıf için belgelerbulunabilir.  
  
### <a name="client-side-timeouts"></a>İstemci tarafı Zaman Ları  
 İstemci tarafında:  
  
1. SendTimeout – bir istek/yanıt hizmeti işlemi için yanıt iletisi almak da dahil olmak üzere, ileti gönderme işleminin tüm sürecini yöneten OperationTimeout'u başlatmada kullanılır. Bu zaman alameti, geri arama sözleşmesi yönteminden yanıt iletileri gönderirken de geçerlidir.  
  
2. OpenTimeout – açık bir zaman aşım değeri belirtilmediğinde kanalları açarken kullanılır.  
  
3. CloseTimeout – açık bir zaman aşım değeri belirtilmediğinde kanalları kapatırken kullanılır.  
  
4. ReceiveTimeout – kullanılmaz.  
  
### <a name="service-side-timeouts"></a>Servis tarafı Zaman Ları  
 Hizmet tarafında:  
  
1. SendTimeout, OpenTimeout, CloseTimeout istemcide aynıdır.  
  
2. ReceiveTimeout – zamanlamadan önce bir oturumun ne kadar süreyle boşta bırakılabildiğini kontrol eden oturum boşta zamanlamasını başlatmayı başlatmak için Hizmet Çerçeve Katmanı tarafından kullanılır.
