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
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Nasıl yapılır: Bağlantı Noktası Paylaşımı Kullanarak Bir Windows Communication Foundation Hizmetini Yapılandırma
Windows Communication Foundation (WCF) uygulamanızda net.tcp:// bağlantı noktası paylaşımını kullanmanın <xref:System.ServiceModel.NetTcpBinding>en kolay yolu, bir hizmeti kullanarak bir hizmeti ortaya çıkarmaktır.  
  
 Bu bağlama, <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> bu bağlama ile yapılandırılan hizmet için net.tcp:// bağlantı noktası paylaşımının etkin olup olmadığını kontrol eden bir özellik sağlar.  
  
 Aşağıdaki yordam, tekdüzen <xref:System.ServiceModel.NetTcpBinding> kaynak tanımlayıcı (URI) net.tcp://localhost/MyService'te önce kod da sonra yapılandırma öğelerini kullanarak bir bitiş noktası açmak için sınıfın nasıl kullanılacağını gösterir.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>NetTcpBinding kodunda net.tcp:// bağlantı noktası paylaşımını etkinleştirmek için  
  
1. Bir sözleşme uygulamak için `IMyService` bir hizmet `MyService`oluşturun ve onu , .  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Sınıfın bir örneğini <xref:System.ServiceModel.NetTcpBinding> oluşturun <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> ve `true`özelliği 'ne göre ayarlayın.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Bağlantı <xref:System.ServiceModel.ServiceHost> noktası paylaşımını etkinleştiren `MyService` <xref:System.ServiceModel.NetTcpBinding> ve bitiş noktası adresi URI "net.tcp://localhost/MyService"i dinleyen bir nokta oluşturun ve hizmet bitiş noktasını ekleyin.  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > Bu örnek, bitiş noktası adresi URI farklı bir bağlantı noktası numarası belirtmediği için varsayılan TCP 808 bağlantı noktasını kullanır. Bağlantı noktası paylaşımı aktarım bağlamada açıkça etkinleştirildiğinden, bu hizmet bağlantı noktası 808'i diğer işlemlerdeki diğer hizmetlerle paylaşabilir. Bağlantı noktası paylaşımına izin verilmeseydi ve başka bir uygulama zaten <xref:System.ServiceModel.AddressAlreadyInUseException> bağlantı noktası 808'i kullanıyorsa, bu hizmet açıldığında bir hizmet verirdi.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Yapılandırmada netTcpBinding üzerinde net.tcp:// bağlantı noktası paylaşımını etkinleştirmek için  
  
1. Aşağıdaki örnekte, yapılandırma öğelerini kullanarak bağlantı noktası paylaşımını nasıl etkinleştirilir ve hizmet bitiş noktası nın nasıl ekleyeceğini gösterir.  
  
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

- [Net.TCP Bağlantı Noktası Paylaşımı](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Nasıl yapılır: Net.TCP Bağlantı Noktası Paylaşım Hizmetini Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
