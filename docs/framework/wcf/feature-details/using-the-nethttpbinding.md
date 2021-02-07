---
description: 'Hakkında daha fazla bilgi edinin: NetHttpBinding Kullanma'
title: NetHttpBinding Kullanma
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 3964c3c3e563d143df1edfcd1f98d3250301c209
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756051"
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="0a356-103">NetHttpBinding Kullanma</span><span class="sxs-lookup"><span data-stu-id="0a356-103">Using the NetHttpBinding</span></span>

<span data-ttu-id="0a356-104"><xref:System.ServiceModel.NetHttpBinding> , HTTP veya WebSocket hizmetlerini kullanmak için tasarlanan bir bağlamadır ve varsayılan olarak ikili kodlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a356-104"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="0a356-105"><xref:System.ServiceModel.NetHttpBinding> , istek-yanıt sözleşmesi veya çift yönlü sözleşmeyle birlikte kullanılıp kullanılmayacağını algılar ve davranışını eşleşecek şekilde değiştirin-bu, istek-yanıt sözleşmeleri için HTTP ve çift yönlü sözleşmeler için WebSockets kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a356-105"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="0a356-106">Bu davranış ayarı kullanılarak geçersiz kılınabilir <xref:System.ServiceModel.Channels.WebSocketTransportUsage> :</span><span class="sxs-lookup"><span data-stu-id="0a356-106">This behavior can be overridden using the <xref:System.ServiceModel.Channels.WebSocketTransportUsage> setting:</span></span>  
  
1. <span data-ttu-id="0a356-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> -Bu WebSockets, istek-yanıt sözleşmeleri için bile kullanılmasına zorlar.</span><span class="sxs-lookup"><span data-stu-id="0a356-107"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2. <span data-ttu-id="0a356-108"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> -Bu, WebSockets kullanılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="0a356-108"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> - This prevents WebSockets from being used.</span></span> <span data-ttu-id="0a356-109">Bu ayarla bir çift yönlü sözleşme kullanılmaya çalışılması bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0a356-109">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3. <span data-ttu-id="0a356-110"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> -Bu varsayılan değerdir ve yukarıda açıklandığı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="0a356-110"><xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="0a356-111"><xref:System.ServiceModel.NetHttpBinding> hem HTTP modunda hem de WebSocket modunda güvenilir oturumları destekler.</span><span class="sxs-lookup"><span data-stu-id="0a356-111"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="0a356-112">WebSocket modundaki oturumlarda, taşıma tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0a356-112">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="0a356-113"><xref:System.ServiceModel.NetHttpBinding>Ve bağlamanın TransferMode değeri TransferMode. akışlı olarak ayarlandığında, büyük akışlar kilitlenmeye neden olabilir ve çağrının zaman aşımına uğrayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0a356-113">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="0a356-114">Bu sorunu geçici olarak çözmek için daha küçük mesajlar gönderin veya TransferMode. arabellekli kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a356-114">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="0a356-115">NetHttpBinding kullanmak için bir hizmet yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0a356-115">Configuring a Service to use NetHttpBinding</span></span>  

 <span data-ttu-id="0a356-116">, <xref:System.ServiceModel.NetHttpBinding> Diğer bağlamalamayla aynı şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a356-116">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="0a356-117">Aşağıdaki yapılandırma kod parçacığında, ile bir WCF hizmetinin nasıl yapılandırılacağı gösterilmektedir <xref:System.ServiceModel.NetHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="0a356-117">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
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
    ...
  </system.serviceModel>  
```  
  
 <span data-ttu-id="0a356-118">Aşağıdaki kod parçacığı, içindeki kodun nasıl ekleneceğini gösterir <xref:System.ServiceModel.NetHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="0a356-118">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a356-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a356-119">See also</span></span>

- [<span data-ttu-id="0a356-120">Hizmetler için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0a356-120">Configuring Bindings for Services</span></span>](../configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="0a356-121">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0a356-121">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="0a356-122">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0a356-122">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="0a356-123">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="0a356-123">Duplex Services</span></span>](duplex-services.md)
