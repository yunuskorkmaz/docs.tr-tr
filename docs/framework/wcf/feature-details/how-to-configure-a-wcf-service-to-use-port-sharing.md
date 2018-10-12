---
title: 'Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 19f61e6e38a5eeb477833b0d5ea94c1b1a8447b4
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121924"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="54912-102">Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="54912-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="54912-103">Kullanarak bir hizmeti kullanıma sunmak için Windows Communication Foundation (WCF) uygulamanızda net.tcp:// bağlantı noktası kullanmak için en kolay yolu olan <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="54912-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="54912-104">Bu bağlama sağlayan bir <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliği net.tcp:// bağlantı noktası paylaşımı için bu bağlama ile yapılandırılan hizmetin etkin olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="54912-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="54912-105">Aşağıdaki yordam nasıl kullanılacağını gösterir <xref:System.ServiceModel.NetTcpBinding> kodda ve yapılandırma öğelerini kullanarak ardından bir uç noktada Tekdüzen Kaynak Tanımlayıcısı (URI) net.tcp://localhost/MyService ilk açmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="54912-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="54912-106">Bir NetTcpBinding üzerinde kod paylaşımı net.tcp:// bağlantı noktasını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="54912-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1.  <span data-ttu-id="54912-107">Adlı bir sözleşme uygulamak için bir hizmet oluşturma `IMyService` ve onu çağırmak `MyService`,.</span><span class="sxs-lookup"><span data-stu-id="54912-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <span data-ttu-id="54912-108">Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="54912-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <span data-ttu-id="54912-109">Oluşturma bir <xref:System.ServiceModel.ServiceHost> ve bunun için hizmet uç noktası ekleme `MyService` paylaşımı etkin bağlantı noktası kullanan <xref:System.ServiceModel.NetTcpBinding> ve uç noktasında dinleyen net.tcp://localhost/MyService"URI" adresi.</span><span class="sxs-lookup"><span data-stu-id="54912-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="54912-110">Bu örnek, uç nokta adresini URI farklı bir bağlantı noktası belirtmediğinden 808 varsayılan TCP bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="54912-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="54912-111">Bağlantı noktası paylaşımı açıkça aktarım bağlama üzerinde etkin olmadığından, bu hizmet bağlantı noktası 808 diğer işlemlerde diğer hizmetlerle paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54912-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="54912-112">Bu hizmet bağlantı noktası paylaşımı izin ve başka bir uygulama bağlantı noktası 808 zaten kullanıyor alanlarına bir <xref:System.ServiceModel.AddressAlreadyInUseException> zaman erişimiyle açıldı.</span><span class="sxs-lookup"><span data-stu-id="54912-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="54912-113">Bir NetTcpBinding üzerinde yapılandırmada net.tcp:// bağlantı noktası etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="54912-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1.  <span data-ttu-id="54912-114">Aşağıdaki örnekte, bağlantı noktası paylaşımı etkinleştirme ve yapılandırma öğeleri kullanılarak hizmet uç noktası eklemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="54912-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54912-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54912-115">See Also</span></span>  
* [<span data-ttu-id="54912-116">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="54912-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
* [<span data-ttu-id="54912-117">Nasıl yapılır: Net.TCP Bağlantı Noktası Paylaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="54912-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
