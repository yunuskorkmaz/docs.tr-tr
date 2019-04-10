---
title: 'Nasıl yapılır: Bağlantı noktası paylaşımı için bir Windows Communication Foundation hizmetini yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: bc0c822659ee57ac8dd87a2adddcd32e934ea4fb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302412"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Nasıl yapılır: Bağlantı noktası paylaşımı için bir Windows Communication Foundation hizmetini yapılandırma
Kullanarak bir hizmeti kullanıma sunmak için Windows Communication Foundation (WCF) uygulamanızda net.tcp:// bağlantı noktası kullanmak için en kolay yolu olan <xref:System.ServiceModel.NetTcpBinding>.  
  
 Bu bağlama sağlayan bir <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliği net.tcp:// bağlantı noktası paylaşımı için bu bağlama ile yapılandırılan hizmetin etkin olup olmadığını denetler.  
  
 Aşağıdaki yordam nasıl kullanılacağını gösterir <xref:System.ServiceModel.NetTcpBinding> kodda ve yapılandırma öğelerini kullanarak ardından bir uç noktada Tekdüzen Kaynak Tanımlayıcısı (URI) net.tcp://localhost/MyService ilk açmak için sınıf.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Bir NetTcpBinding üzerinde kod paylaşımı net.tcp:// bağlantı noktasını etkinleştirmek için  
  
1. Adlı bir sözleşme uygulamak için bir hizmet oluşturma `IMyService` ve onu çağırmak `MyService`,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> özelliğini `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Oluşturma bir <xref:System.ServiceModel.ServiceHost> ve bunun için hizmet uç noktası ekleme `MyService` paylaşımı etkin bağlantı noktası kullanan <xref:System.ServiceModel.NetTcpBinding> ve uç noktasında dinleyen net.tcp://localhost/MyService"URI" adresi.  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  Bu örnek, uç nokta adresini URI farklı bir bağlantı noktası belirtmediğinden 808 varsayılan TCP bağlantı noktasını kullanır. Bağlantı noktası paylaşımı açıkça aktarım bağlama üzerinde etkin olmadığından, bu hizmet bağlantı noktası 808 diğer işlemlerde diğer hizmetlerle paylaşabilirsiniz. Bu hizmet bağlantı noktası paylaşımı izin ve başka bir uygulama bağlantı noktası 808 zaten kullanıyor alanlarına bir <xref:System.ServiceModel.AddressAlreadyInUseException> zaman erişimiyle açıldı.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Bir NetTcpBinding üzerinde yapılandırmada net.tcp:// bağlantı noktası etkinleştirmek için  
  
1. Aşağıdaki örnekte, bağlantı noktası paylaşımı etkinleştirme ve yapılandırma öğeleri kullanılarak hizmet uç noktası eklemek gösterilmektedir.  
  
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
- [Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
