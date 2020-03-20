---
title: "Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma"
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 823c3b8452a3fd1c95758d2d09a9effdf02075c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184908"
---
# <a name="how-to-host-a-wcf-service-in-was"></a>Nasıl yapılır: WAS'ta WCF Hizmeti Barındırma
Bu konu, Windows Process Etkinleştirme Hizmetleri (WAS olarak da bilinir) windows communication foundation (WCF) hizmeti barındırılan oluşturmak için gereken temel adımları özetler. WAS, HTTP dışı aktarım protokolleriyle çalışan Internet Bilgi Hizmetleri (IIS) özelliklerinin genelleştirilmesi olan yeni işlem etkinleştirme hizmetidir. WCF, TCP, adlandırılmış borular ve İleti Sıralama gibi WCF tarafından desteklenen HTTP dışı protokoller üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcıarabını kullanır.  
  
 Bu barındırma seçeneği, WAS etkinleştirme bileşenlerinin düzgün şekilde yüklenmesini ve yapılandırılmasını gerektirir, ancak uygulamanın bir parçası olarak herhangi bir barındırma kodunun yazılmasını gerektirmez. WAS'ı yükleme ve yapılandırma hakkında daha fazla bilgi için [bkz: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
  
> [!WARNING]
> Web sunucusunun istek işleme ardışık adı Klasik modda ayarlanmışsa WAS etkinleştirme desteklenmez. WAS etkinleştirme kullanılacaksa, web sunucusunun istek işleme ardışık adı Tümleşik moduna ayarlanmalıdır.  
  
 Bir WCF hizmeti WAS'da barındırıldığında, standart bağlamalar her zamanki gibi kullanılır. Ancak, WAS <xref:System.ServiceModel.NetTcpBinding> barındırılan bir hizmeti <xref:System.ServiceModel.NetNamedPipeBinding> yapılandırmak ve yapılandırmak için kullanırken, bir kısıtlamanın karşılanması gerekir. Farklı uç noktalar aynı aktarımı kullandığında, bağlama ayarlarıaşağıdaki yedi özellikte eşleşir:  
  
- BağlantıBufferSize  
  
- KanalInitializationTimeout  
  
- MaxPendingConnections  
  
- MaxOutputDelay  
  
- MaxPendingAccepts  
  
- BağlantıPoolSettings.IdleTimeout  
  
- BağlantıPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 Aksi takdirde, ilk olarak başlatılır bitiş noktası her zaman bu özelliklerin <xref:System.ServiceModel.ServiceActivationException> değerlerini belirler ve daha sonra eklenen uç noktaları bu ayarlarla eşleşmiyorsa bir atımı yapar.  
  
 Bu örneğin kaynak kopyası için [TCP Etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md)bölümüne bakın.  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>WAS tarafından barındırılan temel bir hizmet oluşturmak için  
  
1. Hizmet türü için bir hizmet sözleşmesi tanımlayın.  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. Hizmet sözleşmesini bir hizmet sınıfında uygulayın. Hizmetin uygulanması içinde adres veya bağlama bilgilerinin belirtilmedigini unutmayın. Ayrıca, yapılandırma dosyasından bu bilgileri almak için kod yazılması gerekmez.  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. Uç noktalartarafından kullanılacak bağlamayı <xref:System.ServiceModel.NetTcpBinding> tanımlamak için bir Web.config dosyası oluşturun. `CalculatorService`  
  
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
  
4. Aşağıdaki kodu içeren bir Service.svc dosyası oluşturun.  
  
   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. Service.svc dosyasını IIS sanal dizininize yerleştirin.  
  
### <a name="to-create-a-client-to-use-the-service"></a>Hizmeti kullanmak için bir istemci oluşturmak için  
  
1. Hizmet meta verilerinden kod oluşturmak için komut satırından [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Oluşturulan istemci, istemci `ICalculator` uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. Oluşturulan istemci uygulaması da uygulanmasını `ClientCalculator`içerir. Adres ve bağlama bilgilerinin hizmetin uygulanması nın herhangi bir yerinde belirtilmemiş olduğunu unutmayın. Ayrıca, yapılandırma dosyasından bu bilgileri almak için kod yazılması gerekmez.  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. Kullanan istemci <xref:System.ServiceModel.NetTcpBinding> için yapılandırma da Svcutil.exe tarafından oluşturulur. Visual Studio'yu kullanırken bu dosya App.config dosyasında adlandırılmalıdır.  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. Bir uygulamadaki `ClientCalculator` nin bir örneğini oluşturun ve ardından servis işlemlerini arayın.  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. İstemciyi derle ve çalıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TCP Etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
