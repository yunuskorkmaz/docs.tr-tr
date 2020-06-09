---
title: 'Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 28f2858d68de99839d7fec66b0fe4528d7e42325
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579533"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="f2c02-102">Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f2c02-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="f2c02-103">Windows Communication Foundation (WCF) uygulamanızda net. TCP://bağlantı noktası paylaşımını kullanmanın en kolay yolu, hizmetini kullanarak bir hizmeti kullanıma sunmasıdır <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="f2c02-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="f2c02-104">Bu bağlama <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> , bu bağlama ile yapılandırılan hizmet için net. TCP://bağlantı noktası paylaşımının etkinleştirilip etkinleştirilmeyeceğini denetleyen bir özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2c02-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="f2c02-105">Aşağıdaki yordamda, <xref:System.ServiceModel.NetTcpBinding> sınıfının önce kod içinde, sonra yapılandırma öğelerini kullanarak Tekdüzen Kaynak tanımlayıcısı (URI) net. TCP://localhost/MyService içinde bir uç nokta açmak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f2c02-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="f2c02-106">Kodda NetTcpBinding üzerinde net. TCP://bağlantı noktası paylaşımını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f2c02-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="f2c02-107">Adlı bir sözleşmeyi uygulamak ve çağırmak için bir hizmet oluşturun `IMyService` `MyService` .</span><span class="sxs-lookup"><span data-stu-id="f2c02-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="f2c02-108">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="f2c02-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="f2c02-109">Bir oluşturun <xref:System.ServiceModel.ServiceHost> ve bu `MyService` bağlantı noktası, <xref:System.ServiceModel.NetTcpBinding> "net. TCP://localhost/MyService" uç nokta adresi URI 'sini dinler.</span><span class="sxs-lookup"><span data-stu-id="f2c02-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="f2c02-110">Bu örnek, uç nokta adresi URI 'SI farklı bir bağlantı noktası numarası belirtmediğinden, varsayılan TCP bağlantı noktası 808 ' ü kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2c02-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="f2c02-111">Bağlantı noktası Paylaşımı, aktarım bağlamasında açık bir şekilde etkinleştirildiğinden, bu hizmet bağlantı noktası 808 ' i diğer süreçlerdeki diğer hizmetlerle paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="f2c02-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="f2c02-112">Bağlantı noktası paylaşımına izin verilmiyorsa ve başka bir uygulama zaten 808 numaralı bağlantı noktasını kullanıyorsa, bu hizmet açıldığında bir oluşturur <xref:System.ServiceModel.AddressAlreadyInUseException> .</span><span class="sxs-lookup"><span data-stu-id="f2c02-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="f2c02-113">Yapılandırmada NetTcpBinding üzerinde net. TCP://bağlantı noktası paylaşımını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f2c02-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="f2c02-114">Aşağıdaki örnek, bağlantı noktası paylaşımının nasıl etkinleştirileceğini ve yapılandırma öğelerini kullanarak hizmet uç noktasının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2c02-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2c02-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2c02-115">See also</span></span>

- [<span data-ttu-id="f2c02-116">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="f2c02-116">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="f2c02-117">Nasıl yapılır: Net.TCP Bağlantı Noktası Paylaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f2c02-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](how-to-enable-the-net-tcp-port-sharing-service.md)
