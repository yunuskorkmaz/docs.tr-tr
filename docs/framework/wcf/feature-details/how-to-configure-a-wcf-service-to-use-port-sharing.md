---
title: 'Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: cd8d76137ac195e452a7d66fb6ddbeda405a922f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185096"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="d735b-102">Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d735b-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="d735b-103">Windows Communication Foundation (WCF) uygulamanızda net.tcp:// bağlantı noktası paylaşımını kullanmanın <xref:System.ServiceModel.NetTcpBinding>en kolay yolu, bir hizmeti kullanarak bir hizmeti ortaya çıkarmaktır.</span><span class="sxs-lookup"><span data-stu-id="d735b-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="d735b-104">Bu bağlama, <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> bu bağlama ile yapılandırılan hizmet için net.tcp:// bağlantı noktası paylaşımının etkin olup olmadığını kontrol eden bir özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d735b-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="d735b-105">Aşağıdaki yordam, tekdüzen <xref:System.ServiceModel.NetTcpBinding> kaynak tanımlayıcı (URI) net.tcp://localhost/MyService'te önce kod da sonra yapılandırma öğelerini kullanarak bir bitiş noktası açmak için sınıfın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d735b-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="d735b-106">NetTcpBinding kodunda net.tcp:// bağlantı noktası paylaşımını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d735b-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="d735b-107">Bir sözleşme uygulamak için `IMyService` bir hizmet `MyService`oluşturun ve onu , .</span><span class="sxs-lookup"><span data-stu-id="d735b-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="d735b-108">Sınıfın bir örneğini <xref:System.ServiceModel.NetTcpBinding> oluşturun <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> ve `true`özelliği 'ne göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d735b-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="d735b-109">Bağlantı <xref:System.ServiceModel.ServiceHost> noktası paylaşımını etkinleştiren `MyService` <xref:System.ServiceModel.NetTcpBinding> ve bitiş noktası adresi URI "net.tcp://localhost/MyService"i dinleyen bir nokta oluşturun ve hizmet bitiş noktasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d735b-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="d735b-110">Bu örnek, bitiş noktası adresi URI farklı bir bağlantı noktası numarası belirtmediği için varsayılan TCP 808 bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d735b-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="d735b-111">Bağlantı noktası paylaşımı aktarım bağlamada açıkça etkinleştirildiğinden, bu hizmet bağlantı noktası 808'i diğer işlemlerdeki diğer hizmetlerle paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="d735b-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="d735b-112">Bağlantı noktası paylaşımına izin verilmeseydi ve başka bir uygulama zaten <xref:System.ServiceModel.AddressAlreadyInUseException> bağlantı noktası 808'i kullanıyorsa, bu hizmet açıldığında bir hizmet verirdi.</span><span class="sxs-lookup"><span data-stu-id="d735b-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="d735b-113">Yapılandırmada netTcpBinding üzerinde net.tcp:// bağlantı noktası paylaşımını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d735b-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="d735b-114">Aşağıdaki örnekte, yapılandırma öğelerini kullanarak bağlantı noktası paylaşımını nasıl etkinleştirilir ve hizmet bitiş noktası nın nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d735b-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d735b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d735b-115">See also</span></span>

- [<span data-ttu-id="d735b-116">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="d735b-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="d735b-117">Nasıl yapılır: Net.TCP Bağlantı Noktası Paylaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d735b-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
