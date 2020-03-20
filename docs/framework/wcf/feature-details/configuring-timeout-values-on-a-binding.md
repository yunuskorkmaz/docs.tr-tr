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
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="c7911-102">Bağlamada Zaman Aşımı Değerlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c7911-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="c7911-103">WCF bağlamalarında bir dizi zaman sonu ayarı vardır.</span><span class="sxs-lookup"><span data-stu-id="c7911-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="c7911-104">Bu zaman sonu ayarlarını doğru ayarlamak yalnızca hizmetinizin performansını artırmakla kaynı yoran aynı zamanda hizmetinizin kullanılabilirliği ve güvenliğinde de rol oynayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7911-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="c7911-105">Aşağıdaki zaman zaman ekmeleri WCF bağlamaları mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="c7911-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="c7911-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="c7911-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="c7911-107">Yakın Zaman</span><span class="sxs-lookup"><span data-stu-id="c7911-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="c7911-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="c7911-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="c7911-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c7911-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="c7911-110">WCF Bağlama Zaman Dilimleri</span><span class="sxs-lookup"><span data-stu-id="c7911-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="c7911-111">Bu konuda tartışılan ayarların her biri, kod veya yapılandırma da bağlamanın kendisi üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="c7911-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="c7911-112">Aşağıdaki kod, kendi barındırılan bir hizmet bağlamında wcf bağlamaüzerinde zaman zaman larını nasıl programla ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7911-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="c7911-113">Aşağıdaki örnek, yapılandırma dosyasındaki bir bağlama üzerinde zaman aşımlarının nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7911-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c7911-114">Bu ayarlar hakkında daha fazla bilgi <xref:System.ServiceModel.Channels.Binding> sınıf için belgelerbulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c7911-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="c7911-115">İstemci tarafı Zaman Ları</span><span class="sxs-lookup"><span data-stu-id="c7911-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="c7911-116">İstemci tarafında:</span><span class="sxs-lookup"><span data-stu-id="c7911-116">On the client side:</span></span>  
  
1. <span data-ttu-id="c7911-117">SendTimeout – bir istek/yanıt hizmeti işlemi için yanıt iletisi almak da dahil olmak üzere, ileti gönderme işleminin tüm sürecini yöneten OperationTimeout'u başlatmada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7911-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="c7911-118">Bu zaman alameti, geri arama sözleşmesi yönteminden yanıt iletileri gönderirken de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c7911-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="c7911-119">OpenTimeout – açık bir zaman aşım değeri belirtilmediğinde kanalları açarken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7911-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="c7911-120">CloseTimeout – açık bir zaman aşım değeri belirtilmediğinde kanalları kapatırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7911-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="c7911-121">ReceiveTimeout – kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c7911-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="c7911-122">Servis tarafı Zaman Ları</span><span class="sxs-lookup"><span data-stu-id="c7911-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="c7911-123">Hizmet tarafında:</span><span class="sxs-lookup"><span data-stu-id="c7911-123">On the service side:</span></span>  
  
1. <span data-ttu-id="c7911-124">SendTimeout, OpenTimeout, CloseTimeout istemcide aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c7911-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="c7911-125">ReceiveTimeout – zamanlamadan önce bir oturumun ne kadar süreyle boşta bırakılabildiğini kontrol eden oturum boşta zamanlamasını başlatmayı başlatmak için Hizmet Çerçeve Katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7911-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
