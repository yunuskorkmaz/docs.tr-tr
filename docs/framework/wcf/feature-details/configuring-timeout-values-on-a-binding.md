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
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="97372-103">Bağlamada Zaman Aşımı Değerlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="97372-103">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="97372-104">WCF bağlamalarında kullanılabilir bir dizi zaman aşımı ayarı vardır.</span><span class="sxs-lookup"><span data-stu-id="97372-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="97372-105">Bu zaman aşımı ayarlarının doğru ayarlanması yalnızca hizmetinizin performansını değil, hizmetinizin kullanılabilirliği ve güvenliğine ilişkin bir rol de yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="97372-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="97372-106">Aşağıdaki zaman aşımları WCF bağlamaları üzerinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="97372-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="97372-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="97372-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="97372-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="97372-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="97372-109">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="97372-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="97372-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="97372-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="97372-111">WCF bağlama zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="97372-111">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="97372-112">Bu konu başlığında ele alınan ayarların her biri, kodda veya yapılandırmada bağlama sırasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="97372-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="97372-113">Aşağıdaki kod, şirket içinde barındırılan bir hizmet bağlamında bir WCF bağlamasında zaman aşımlarını programlı bir şekilde ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="97372-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="97372-114">Aşağıdaki örnek, bir yapılandırma dosyasındaki bağlamadaki zaman aşımlarının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97372-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="97372-115">Bu ayarlar hakkında daha fazla bilgi, sınıfının belgelerinde bulunabilir <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="97372-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="97372-116">İstemci tarafı zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="97372-116">Client-side Timeouts</span></span>  
 <span data-ttu-id="97372-117">İstemci tarafında:</span><span class="sxs-lookup"><span data-stu-id="97372-117">On the client side:</span></span>  
  
1. <span data-ttu-id="97372-118">SendTimeout – bir istek/yanıt hizmeti işlemi için yanıt iletisi alma da dahil olmak üzere bir ileti gönderme işlemini yöneten OperationTimeout 'u başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97372-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="97372-119">Bu zaman aşımı Ayrıca, bir geri çağırma sözleşmesi yönteminden yanıt iletileri gönderilirken de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97372-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="97372-120">OpenTimeout: açık bir zaman aşımı değeri belirtilmediğinde kanallar açılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97372-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="97372-121">CloseTimeout: açık bir zaman aşımı değeri belirtilmediğinde kanallar kapatılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97372-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="97372-122">ReceiveTimeout – kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="97372-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="97372-123">Hizmet tarafı zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="97372-123">Service-side Timeouts</span></span>  
 <span data-ttu-id="97372-124">Hizmet tarafında:</span><span class="sxs-lookup"><span data-stu-id="97372-124">On the service side:</span></span>  
  
1. <span data-ttu-id="97372-125">SendTimeout, OpenTimeout, CloseTimeout, istemci ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="97372-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="97372-126">ReceiveTimeout: bir oturumun zaman aşımından önce ne kadar süreyle boşta kalabileceğini denetleyen oturum boşta kalma zaman aşımını başlatmak için Service Framework katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97372-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
