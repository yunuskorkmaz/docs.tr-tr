---
title: NetHttpBinding Kullanma
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: cd4a50798ff709c32db056c6aa7289993431f40e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696748"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="8eb43-102">NetHttpBinding Kullanma</span><span class="sxs-lookup"><span data-stu-id="8eb43-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="8eb43-103"><xref:System.ServiceModel.NetHttpBinding> HTTP veya WebSocket hizmetlerini kullanma için tasarlanmış bir bağlama ve ikili kodlama varsayılan olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="8eb43-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="8eb43-104"><xref:System.ServiceModel.NetHttpBinding> İstek-yanıt anlaşması veya çift yönlü sözleşme ile kullanılan olup olmadığını algılar ve davranışını eşleşecek şekilde değiştirmesine - HTTP istek-yanıt sözleşmeleriyle ve WebSockets için çift yönlü sözleşmeler için kullanır.</span><span class="sxs-lookup"><span data-stu-id="8eb43-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="8eb43-105">Bu davranış kullanılarak geçersiz kılınabilir <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ayarı:</span><span class="sxs-lookup"><span data-stu-id="8eb43-105">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="8eb43-106">`Always` -Bu, hatta istek-yanıt sözleşmeleriyle için kullanılacak WebSockets zorlar.</span><span class="sxs-lookup"><span data-stu-id="8eb43-106">`Always` - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="8eb43-107">`Never` -Bu, WebSockets kullanılmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="8eb43-107">`Never` - This prevents WebSockets from being used.</span></span> <span data-ttu-id="8eb43-108">Bu ayar ile çift yönlü sözleşme kullanılmaya çalışılırsa, bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="8eb43-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="8eb43-109">`WhenDuplex` -Bu, varsayılan değerdir ve yukarıda açıklandığı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="8eb43-109">`WhenDuplex` - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="8eb43-110"><xref:System.ServiceModel.NetHttpBinding> güvenilir oturumlar, hem HTTP modu hem de WebSocket modu destekler.</span><span class="sxs-lookup"><span data-stu-id="8eb43-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="8eb43-111">WebSocket içinde modu oturumları taşıma tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8eb43-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8eb43-112">Kullanırken <xref:System.ServiceModel.NetHttpBinding> ve bağlamanın TransferMode TransferMode.Streamed için ayarlanır, kilitlenme ve çağrı zaman aşımı büyük akışlarını neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eb43-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="8eb43-113">Bu sorunu Gönder küçük ileti çalışma veya TransferMode.Buffered kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="8eb43-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="8eb43-114">NetHttpBinding bir hizmetin yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8eb43-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="8eb43-115"><xref:System.ServiceModel.NetHttpBinding> Olabilir aynı yapılandırılmış diğer bağlama.</span><span class="sxs-lookup"><span data-stu-id="8eb43-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="8eb43-116">Bir WCF Hizmeti ile yapılandırma aşağıdaki yapılandırma parçacığı göstermektedir <xref:System.ServiceModel.NetHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8eb43-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 <span data-ttu-id="8eb43-117">Aşağıdaki kod parçacığını nasıl ekleneceğini gösterir <xref:System.ServiceModel.NetHttpBinding> kod.</span><span class="sxs-lookup"><span data-stu-id="8eb43-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="8eb43-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8eb43-118">See Also</span></span>  
 [<span data-ttu-id="8eb43-119">Hizmetler için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8eb43-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="8eb43-120">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8eb43-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="8eb43-121">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8eb43-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="8eb43-122">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="8eb43-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
