---
title: "Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0086e145ca2aab325764467742a4ff2e6e3c0b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="d9ed7-102">Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d9ed7-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="d9ed7-103">İçinde net.tcp:// bağlantı noktası kullanmak için en kolay yolu, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulamasıdır kullanarak hizmet kullanıma sunmak için <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-103">The easiest way to use net.tcp:// port sharing in your [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="d9ed7-104">Bu bağlama sağlayan bir <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> net.tcp:// bağlantı noktası paylaşımı bu bağlama ile yapılandırılan hizmet için etkinleştirilip etkinleştirilmediğini denetler özelliği.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="d9ed7-105">Aşağıdaki yordam nasıl kullanılacağını gösterir <xref:System.ServiceModel.NetTcpBinding> sınıfı bir uç noktada Tekdüzen Kaynak Tanımlayıcısı (URI) net.tcp://localhost/MyService önce kodda ve ardından yapılandırma öğelerini kullanarak açın.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="d9ed7-106">Bir NetTcpBinding üzerinde kodda net.tcp:// bağlantı noktası etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d9ed7-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1.  <span data-ttu-id="d9ed7-107">Adlı bir sözleşme uygulamak için bir hizmet oluşturma `IMyService` ve çağrısından `MyService`,.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <span data-ttu-id="d9ed7-108">Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> sınıfı ve ayarlayın <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <span data-ttu-id="d9ed7-109">Oluşturma bir <xref:System.ServiceModel.ServiceHost> ve bunun için hizmet uç noktası eklemek `MyService` paylaşımı etkin bağlantı noktası kullanan <xref:System.ServiceModel.NetTcpBinding> ve dinlediği uç noktada URI "net.tcp://localhost/MyService" adres.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="d9ed7-110">Bu örnek, uç nokta adresi URI farklı bir bağlantı noktası belirtmediğinden 808 varsayılan TCP bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="d9ed7-111">Bağlantı noktası paylaşımı açıkça aktarım bağlama üzerinde etkin olduğundan, bu hizmet bağlantı noktası 808 diğer işlemlerinde diğer hizmetlerle paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="d9ed7-112">Bu hizmet bağlantı noktası paylaşımı verilmez ve başka bir uygulama 808 numaralı bağlantı noktasını zaten kullanıyor, throw bir <xref:System.ServiceModel.AddressAlreadyInUseException> zaman erişimiyle açıldı.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="d9ed7-113">Bir NetTcpBinding yapılandırmasında net.tcp:// bağlantı noktası etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d9ed7-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1.  <span data-ttu-id="d9ed7-114">Aşağıdaki örnekte, bağlantı noktası paylaşımı etkinleştirme ve yapılandırma öğeleri kullanılarak hizmet uç noktası eklemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9ed7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9ed7-115">See Also</span></span>  
 [<span data-ttu-id="d9ed7-116">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="d9ed7-116">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="d9ed7-117">Nasıl yapılır: Net.TCP Bağlantı Noktası Paylaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d9ed7-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
