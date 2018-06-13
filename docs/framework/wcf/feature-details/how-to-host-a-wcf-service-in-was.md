---
title: "Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma"
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 7050d866233b248c7c8f9f41337ce451b5510c30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492674"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma
Bu konuda anahatları Windows İşlem Etkinleştirme Hizmetleri (WAS olarak da bilinir) oluşturmak için gereken temel adımlarda Windows Communication Foundation (WCF) hizmetini barındırılan. EDİLDİ Genelleştirme HTTP olmayan aktarım protokolleri ile iş Internet Information Services (IIS) özellikleri olan yeni işlem Etkinleştirme hizmeti. WCF TCP ve adlandırılmış kanallar ve Message Queuing gibi WCF tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletmek için Dinleyici Bağdaştırıcısı arabirimini kullanır.  
  
 Bu barındırma seçeneği WAS etkinleştirme bileşenleri düzgün bir şekilde yüklenir ve yapılandırılır, ancak uygulamanın bir parçası yazılması için herhangi bir barındırma kod gerektirmeyen gerektirir. Yükleme ve WAS yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve yapılandırma WCF etkinleştirme bileşenlerini](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
>  Web sunucunuzun istek işleme ardışık Klasik moda ayarladıysanız etkinleştirme desteklenmeyen OLUŞTU. WAS etkinleştirme kullanılacak ise web sunucusunun istek işleme ardışık tümleşik moduna ayarlamanız gerekir.  
  
 Bir WCF Hizmeti WAS içinde barındırıldığında, standart bağlamaları normal şekilde kullanılır. Ancak, kullanırken <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> WAS barındırılan hizmeti yapılandırmak için bir kısıtlama yerine getirilmesi gerekir. Farklı uç noktalar aynı aktarım kullandığınızda, aşağıdaki yedi özellikleri eşleştirilecek bağlama ayarları vardır:  
  
-   ConnectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   maxPendingConnections  
  
-   maxOutputDelay  
  
-   maxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Aksi takdirde başlatılmış uç nokta önce her zaman bu özelliklerin değerlerini belirler ve daha sonra eklenen uç noktaları throw bir <xref:System.ServiceModel.ServiceActivationException> bu ayarları eşleşmiyorsa.  
  
 Bu örnekte kaynak kopyası için bkz: [TCP etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>WAS tarafından barındırılan temel bir hizmet oluşturmak için  
  
1.  Hizmet türü için bir hizmet sözleşmesini tanımlama.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  Bir hizmet sınıfında Hizmet sözleşmesini uygulama. Adres veya bağlama bilgisi hizmet uygulaması içinde belirtilmemiş unutmayın. Ayrıca, bu bilgileri yapılandırma dosyasından almak için yazılacak kodu yok.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  Tanımlamak için bir Web.config dosyası oluşturmak <xref:System.ServiceModel.NetTcpBinding> tarafından kullanılmak üzere bağlama `CalculatorService` uç noktaları.  
  
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
  
5.  Service.svc dosyasını, IIS sanal dizininde yerleştirin.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Hizmeti kullanmak için bir istemci oluşturmak için  
  
1.  Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  Oluşturulan istemci uygulaması da uyarlamasını içeren `ClientCalculator`. Adres ve bağlama bilgilerini hizmet uygulaması içinde herhangi bir yerde belirtilmemiş unutmayın. Ayrıca, bu bilgileri yapılandırma dosyasından almak için yazılacak kodu yok.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  Kullanan istemci yapılandırması <xref:System.ServiceModel.NetTcpBinding> Svcutil.exe tarafından da oluşturulur. Bu dosya App.config dosyasında Visual Studio kullanırken adlı olmalıdır.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]   
  
5.  Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemleri çağırın.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  Derleme ve istemci çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TCP Etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
