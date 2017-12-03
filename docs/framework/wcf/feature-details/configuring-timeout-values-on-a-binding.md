---
title: "Bağlamada Zaman Aşımı Değerlerini Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd6206d3b9445b321230bf5968891773abcac9c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="fa315-102">Bağlamada Zaman Aşımı Değerlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa315-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="fa315-103">WCF bağlamaları birtakım zaman aşımı ayarları yok.</span><span class="sxs-lookup"><span data-stu-id="fa315-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="fa315-104">Bu zaman aşımı ayarını ayarları doğru değil yalnızca hizmetinizin performans aynı zamanda play bir rol kullanılabilirlik ve güvenlik hizmetinizin artırabilir.</span><span class="sxs-lookup"><span data-stu-id="fa315-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="fa315-105">WCF bağlamaları üzerinde aşağıdaki zaman aşımları kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fa315-105">The following timeouts are available on WCF bindings:</span></span>  
  
1.  <span data-ttu-id="fa315-106">openTimeout</span><span class="sxs-lookup"><span data-stu-id="fa315-106">OpenTimeout</span></span>  
  
2.  <span data-ttu-id="fa315-107">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="fa315-107">CloseTimeout</span></span>  
  
3.  <span data-ttu-id="fa315-108">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="fa315-108">SendTimeout</span></span>  
  
4.  <span data-ttu-id="fa315-109">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="fa315-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="fa315-110">WCF bağlama zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="fa315-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="fa315-111">Bu konuda tartışılan ayarların her biri bağlama, kendisini, kod veya yapılandırma üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="fa315-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="fa315-112">Aşağıdaki kod programlı olarak zaman aşımı kendini barındıran hizmet bağlamında WCF bağlamasında nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa315-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="fa315-113">Aşağıdaki örnek bir yapılandırma dosyasına bağlama zaman aşımları yapılandırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa315-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="fa315-114">Bu ayarlar hakkında daha fazla bilgi için belgelere bulunabilir <xref:System.ServiceModel.Channels.Binding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fa315-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="fa315-115">İstemci tarafı zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="fa315-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="fa315-116">İstemci tarafında:</span><span class="sxs-lookup"><span data-stu-id="fa315-116">On the client side:</span></span>  
  
1.  <span data-ttu-id="fa315-117">SendTimeout – tam bir ileti gönderme işlemini yönetir, OperationTimeout başlatmak için kullanılan bir istek/yanıt hizmet işlemi için bir yanıt iletisi alma dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="fa315-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="fa315-118">Bu zaman aşımı yanıt iletileri bir geri çağırma sözleşme yönteminden gönderirken de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fa315-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2.  <span data-ttu-id="fa315-119">Hiçbir açık zaman aşımı değeri belirtildiğinde kanalları açarken kullanılan OpenTimeout –</span><span class="sxs-lookup"><span data-stu-id="fa315-119">OpenTimeout – used when opening channels when no explicit timeout value is specified</span></span>  
  
3.  <span data-ttu-id="fa315-120">Hiçbir açık zaman aşımı değeri belirtildiğinde kanalları kapatma sırasında kullanılan CloseTimeout –</span><span class="sxs-lookup"><span data-stu-id="fa315-120">CloseTimeout – used when closing channels when no explicit timeout value is specified</span></span>  
  
4.  <span data-ttu-id="fa315-121">ReceiveTimeout – kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="fa315-121">ReceiveTimeout – is not used</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="fa315-122">Hizmet tarafı zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="fa315-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="fa315-123">Hizmet tarafında:</span><span class="sxs-lookup"><span data-stu-id="fa315-123">On the service side:</span></span>  
  
1.  <span data-ttu-id="fa315-124">SendTimeout, OpentTimeout, CloseTimeout gibi istemcide aynıdır</span><span class="sxs-lookup"><span data-stu-id="fa315-124">SendTimeout, OpentTimeout, CloseTimeout are the same as on the client</span></span>  
  
2.  <span data-ttu-id="fa315-125">ReceiveTimeout – ne kadar oturum zaman aşımına uğramadan önce boşta kalabileceği denetleyen oturum boşta kalma zaman aşımı başlatmak için hizmet Framework katman tarafından kullanılan.</span><span class="sxs-lookup"><span data-stu-id="fa315-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
