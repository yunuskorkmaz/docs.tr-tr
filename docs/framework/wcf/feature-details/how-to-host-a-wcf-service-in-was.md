---
title: "Nasıl yapılır: Was'ta WCF Hizmeti barındırma"
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 9094cf04ed1bc9fabe8d9df11b876007f322679a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651181"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Nasıl yapılır: Was'ta WCF Hizmeti barındırma
Bu konuda anahatları Windows İşlem Etkinleştirme Hizmetleri (WAS olarak da bilinir) oluşturmak için gereken temel adımlarda barındırılan Windows Communication Foundation (WCF) hizmet. OLAN HTTP olmayan aktarım kurallarıyla çalışma Internet Information Services (IIS) özellikleri genelleştirilmiş olduğundan yeni işlem Etkinleştirme hizmeti. WCF dinleyici bağdaştırıcı arabirimi gibi TCP ve adlandırılmış kanallar ve Message Queuing, WCF tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletişim kurmak için kullanır.  
  
 WAS etkinleştirme bileşenleri düzgün şekilde yüklenir ve yapılandırılır, ancak uygulamanın bir parçası yazılması için herhangi bir barındırma kod gerektirmeyen bu barındırma seçeneği gerektirir. Yükleme ve WAS'ta yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF etkinleştirme bileşenlerini yükleme ve yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
>  OLUŞTU. web sunucusunun istek işleme ardışık düzeni için Klasik modu olarak ayarlanmışsa etkinleştirme desteklenmiyor. WAS etkinleştirme kullanılacak ise ardışık düzen işleme, web sunucusu isteği tümleşik moduna ayarlanmalıdır.  
  
 WAS içinde barındırılan bir WCF hizmeti, standart bağlamaları normal şekilde kullanılır. Ancak, kullanırken <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> WAS barındırılan hizmeti yapılandırmak için bir kısıtlama yerine getirilmesi gerekir. Farklı uç noktalar aynı taşıma kullandığınızda, aşağıdaki yedi özellikleri eşleştirilecek bağlama ayarları vardır:  
  
-   ConnectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   maxPendingConnections  
  
-   MaxOutputDelay  
  
-   maxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Aksi durumda, başlatılmış olan bir uç nokta önce her zaman bu özelliklerin değerlerini belirler ve daha sonra eklenen uç noktaları throw bir <xref:System.ServiceModel.ServiceActivationException> bu ayarları eşleşmiyorsa.  
  
 Bu örnekte kaynak kopyası için bkz: [TCP Etkinleştirmesi](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>WAS tarafından barındırılan bir temel hizmet oluşturmak için  
  
1.  Hizmet türü için bir hizmet anlaşmasını tanımlar.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  Hizmet sözleşmesi bir hizmet sınıfında uygulayın. Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın. Ayrıca, yapılandırma dosyasından bu bilgileri almak için yazılacak kod yok.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  Tanımlamak için bir Web.config dosyası oluşturma <xref:System.ServiceModel.NetTcpBinding> tarafından kullanılacak bağlama `CalculatorService` uç noktaları.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Aşağıdaki kodu içeren bir Service.svc dosyası oluşturun.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  IIS sanal dizininde Service.svc dosyası yerleştirin.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Hizmeti kullanmak için bir istemci oluşturmak için  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  Oluşturulan istemci uygulaması da uygulamasını içerir `ClientCalculator`. Adres ve bağlama bilgilerini herhangi bir uygulama hizmetinin içinde belirtilmemiş unutmayın. Ayrıca, yapılandırma dosyasından bu bilgileri almak için yazılacak kod yok.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  Kullanan istemci yapılandırmasını <xref:System.ServiceModel.NetTcpBinding> svcutil.exe'yi da oluşturulur. Bu dosya, Visual Studio kullanırken App.config dosyasında adlandırılmalıdır.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırma.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  Derleyin ve istemci çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TCP Etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
