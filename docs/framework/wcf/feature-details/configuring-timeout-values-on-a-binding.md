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
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="a7800-102">Bağlamada Zaman Aşımı Değerlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a7800-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="a7800-103">WCF bağlamaları birtakım zaman aşımı ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="a7800-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="a7800-104">Bu zaman aşımı ayarını ayarları doğru değil yalnızca hizmetinizin performansını aynı zamanda play bir rol kullanılabilirlik ve güvenlik hizmetinizin artırabilir.</span><span class="sxs-lookup"><span data-stu-id="a7800-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="a7800-105">Şu zaman aşımları, WCF bağlamaları üzerinde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a7800-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="a7800-106">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="a7800-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="a7800-107">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a7800-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="a7800-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="a7800-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="a7800-109">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a7800-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="a7800-110">WCF bağlama zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="a7800-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="a7800-111">Bu konuda tartışılan ayarların her biri bağlama üzerinde kendisi, kod veya yapılandırma ya da yapılır.</span><span class="sxs-lookup"><span data-stu-id="a7800-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="a7800-112">Aşağıdaki kod, zaman aşımları şirket içinde barındırılan bir hizmet bağlamı WCF bağlamasında programlanarak nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7800-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="a7800-113">Aşağıdaki örnek bir yapılandırma dosyası bir bağlamada zaman aşımı yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a7800-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="a7800-114">Bu ayarlar hakkında daha fazla bilgi için belgelerinde bulunabilir <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a7800-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="a7800-115">İstemci tarafı zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="a7800-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="a7800-116">İstemci tarafında:</span><span class="sxs-lookup"><span data-stu-id="a7800-116">On the client side:</span></span>  
  
1. <span data-ttu-id="a7800-117">SendTimeout – tüm ileti gönderme işlemini yönetir, OperationTimeout başlatmak için kullanılan bir yanıt iletisi için bir istek/yanıt hizmet işlemi alma dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="a7800-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="a7800-118">Bu zaman aşımı, bir geri çağırma anlaşması yöntemi yanıt iletileri gönderirken de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a7800-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="a7800-119">Opentimeout = – hiçbir açık zaman aşımı değeri belirtildiğinde kanalları açarken kullanılan.</span><span class="sxs-lookup"><span data-stu-id="a7800-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="a7800-120">CloseTimeout – hiçbir açık zaman aşımı değeri belirtildiğinde Kanal kapatılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7800-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="a7800-121">ReceiveTimeout – kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a7800-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="a7800-122">Hizmet tarafı zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="a7800-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="a7800-123">Hizmet tarafında:</span><span class="sxs-lookup"><span data-stu-id="a7800-123">On the service side:</span></span>  
  
1. <span data-ttu-id="a7800-124">SendTimeout opentimeout =, CloseTimeout istemci olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a7800-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="a7800-125">ReceiveTimeout – ne kadar oturum zaman aşımına uğramadan önce boşta kalabileceği denetleyen oturum boşta kalma zaman aşımı başlatmak için hizmet Framework katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7800-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
