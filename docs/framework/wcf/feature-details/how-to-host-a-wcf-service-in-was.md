---
title: "Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma"
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 40460baeb136345f2532ec6ad5035bd5d3a40254
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051993"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma
Bu konuda, Windows Işlem etkinleştirme Hizmetleri (WAS olarak da bilinir) barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir. , HTTP olmayan taşıma protokolleriyle çalışan Internet Information Services (IIS) özelliklerinin genelleştirilmesi olan yeni işlem etkinleştirme hizmetidir. WCF, TCP, adlandırılmış kanallar ve Message Queuing gibi WCF tarafından desteklenen HTTP olmayan protokoller üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcısı arabirimini kullanır.  
  
 Bu barındırma seçeneği, etkinleştirme bileşenlerinin doğru şekilde yüklenip yapılandırılmasını gerektirir, ancak uygulamanın bir parçası olarak herhangi bir barındırma kodunun yazılmasını gerektirmez. WAS yükleme ve yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF etkinleştirme bileşenlerini yükleme ve yapılandırma](how-to-install-and-configure-wcf-activation-components.md).  
  
> [!WARNING]
> Web sunucusunun istek işleme işlem hattı klasik moda ayarlanmışsa etkinleştirme desteklenmez. WAS etkinleştirme kullanılacaksa Web sunucusunun istek işleme işlem hattının tümleşik moda ayarlanması gerekir.  
  
 ' De bir WCF hizmeti barındırıldığı zaman, standart bağlamalar her zamanki şekilde kullanılır. Ancak, ve ' ı kullanılarak <xref:System.ServiceModel.NetTcpBinding> <xref:System.ServiceModel.NetNamedPipeBinding> bir barındırılan hizmeti yapılandırmak için, bir kısıtlama karşılanması gerekir. Farklı uç noktalar aynı aktarımı kullanırken, bağlama ayarlarının aşağıdaki yedi özelliklerde eşleşmesi gerekir:  
  
- ConnectionBufferSize  
  
- ChannelInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- ConnectionPoolSettings. IdleTimeout  
  
- ConnectionPoolSettings. MaxOutboundConnectionsPerEndpoint  
  
 Aksi takdirde, önce başlatılan bitiş noktası bu özelliklerin değerlerini her zaman belirler ve daha sonra eklenen uç noktalar Bu <xref:System.ServiceModel.ServiceActivationException> ayarlarla eşleşmezse bir oluşturur.  
  
 Bu örneğin kaynak kopyası için bkz. [TCP etkinleştirme](../samples/tcp-activation.md).  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>Tarafından barındırılan temel bir hizmet oluşturmak için  
  
1. Hizmet türü için bir hizmet sözleşmesi tanımlayın.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Hizmet sözleşmesini bir hizmet sınıfına uygulayın. Hizmet uygulamasının içinde adresin veya bağlama bilgilerinin belirtilmediğini unutmayın. Ayrıca, bu bilgileri yapılandırma dosyasından almak için kodun yazılması gerekmez.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <xref:System.ServiceModel.NetTcpBinding>Uç noktalar tarafından kullanılacak bağlamayı tanımlamak için bir Web.config dosyası oluşturun `CalculatorService` .  
  
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
  
4. Aşağıdaki kodu içeren bir Service. svc dosyası oluşturun.  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Service. svc dosyasını IIS sanal dizininize yerleştirin.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Hizmeti kullanmak üzere bir istemci oluşturmak için  
  
1. Hizmet meta verilerinden kod oluşturmak için, komut satırından [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Oluşturulan istemci, `ICalculator` istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Oluşturulan istemci uygulaması, uygulamasının uygulamasını da içerir `ClientCalculator` . Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın. Ayrıca, bu bilgileri yapılandırma dosyasından almak için kodun yazılması gerekmez.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Tarafından kullanılan istemcinin yapılandırması <xref:System.ServiceModel.NetTcpBinding> da Svcutil.exe tarafından oluşturulur. Visual Studio kullanılırken bu dosya App.config dosyasında adlandırılmalıdır.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. Uygulamasının bir örneğini oluşturun `ClientCalculator` ve ardından hizmet işlemlerini çağırın.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. İstemcisini derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TCP Etkinleştirme](../samples/tcp-activation.md)
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
