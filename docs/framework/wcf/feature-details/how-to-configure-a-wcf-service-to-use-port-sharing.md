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
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma
Windows Communication Foundation (WCF) uygulamanızda net. TCP://bağlantı noktası paylaşımını kullanmanın en kolay yolu, hizmetini kullanarak bir hizmeti kullanıma sunmasıdır <xref:System.ServiceModel.NetTcpBinding> .  
  
 Bu bağlama <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> , bu bağlama ile yapılandırılan hizmet için net. TCP://bağlantı noktası paylaşımının etkinleştirilip etkinleştirilmeyeceğini denetleyen bir özellik sağlar.  
  
 Aşağıdaki yordamda, <xref:System.ServiceModel.NetTcpBinding> sınıfının önce kod içinde, sonra yapılandırma öğelerini kullanarak Tekdüzen Kaynak tanımlayıcısı (URI) net. TCP://localhost/MyService içinde bir uç nokta açmak için nasıl kullanılacağı gösterilmektedir.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Kodda NetTcpBinding üzerinde net. TCP://bağlantı noktası paylaşımını etkinleştirmek için  
  
1. Adlı bir sözleşmeyi uygulamak ve çağırmak için bir hizmet oluşturun `IMyService` `MyService` .  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliğini olarak ayarlayın `true` .  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Bir oluşturun <xref:System.ServiceModel.ServiceHost> ve bu `MyService` bağlantı noktası, <xref:System.ServiceModel.NetTcpBinding> "net. TCP://localhost/MyService" uç nokta adresi URI 'sini dinler.  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > Bu örnek, uç nokta adresi URI 'SI farklı bir bağlantı noktası numarası belirtmediğinden, varsayılan TCP bağlantı noktası 808 ' ü kullanır. Bağlantı noktası Paylaşımı, aktarım bağlamasında açık bir şekilde etkinleştirildiğinden, bu hizmet bağlantı noktası 808 ' i diğer süreçlerdeki diğer hizmetlerle paylaşabilir. Bağlantı noktası paylaşımına izin verilmiyorsa ve başka bir uygulama zaten 808 numaralı bağlantı noktasını kullanıyorsa, bu hizmet açıldığında bir oluşturur <xref:System.ServiceModel.AddressAlreadyInUseException> .  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Yapılandırmada NetTcpBinding üzerinde net. TCP://bağlantı noktası paylaşımını etkinleştirmek için  
  
1. Aşağıdaki örnek, bağlantı noktası paylaşımının nasıl etkinleştirileceğini ve yapılandırma öğelerini kullanarak hizmet uç noktasının nasıl ekleneceğini gösterir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Net.TCP Bağlantı Noktası Paylaşımı](net-tcp-port-sharing.md)
- [Nasıl yapılır: Net.TCP Bağlantı Noktası Paylaşım Hizmetini Etkinleştirme](how-to-enable-the-net-tcp-port-sharing-service.md)
