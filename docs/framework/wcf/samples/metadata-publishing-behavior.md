---
title: Meta Veri Yayımlama Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: c3e26454cc9b29620d80a86df7d7aee131e18200
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618629"
---
# <a name="metadata-publishing-behavior"></a>Meta Veri Yayımlama Davranışı
Meta veri yayımlama davranışı örneği bir hizmet meta verileri yayımlama özelliklerini denetlemek nasıl gösterir. Olası hassas hizmet meta verilerinin yanlışlıkla açığa çıkmasını önlemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı bırakır. Bu varsayılan olarak güvenli, davranıştır ancak ayrıca Aracı (Svcutil.exe gibi) yapılandırmasında hizmetin meta veri yayımlama davranışı açıkça etkinleştirilmediği hizmeti çağırmak için gereken istemci kodu oluşturmak için içeri bir meta veri kullanamayacağı anlamına gelir.  
  
> [!IMPORTANT]
>  Daha anlaşılır olması için bu örnek bir güvenli olmayan meta veri yayımlama uç noktası oluşturma işlemini gösterir. Bu uç noktaları için anonim kimlik doğrulamasız tüketiciler potansiyel olarak kullanılabilir ve bu uç noktaları dağıtmadan önce herkese açık şekilde öğrendiği bir hizmet meta verileri uygun olmasına özen gerekir. Bkz: [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) meta veri uç noktası güvenliğini sağlar. bir örnek için örnek.  
  
 Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), uygulayan `ICalculator` hizmet sözleşmesi. Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmet meta verileri kullanıma sunmak için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmette yapılandırılması gerekir. Bu davranış, mevcut olduğunda, meta verileri kullanıma sunmak için bir uç nokta yapılandırarak yayımlayabilirsiniz <xref:System.ServiceModel.Description.IMetadataExchange> WS-MetadataExchange (MEX) Protokolü uygulaması olarak sözleşme. Kolaylık, bu sözleşmenin "IMetadataExchange" kısaltılmış yapılandırma adı verilmedi. Bu örnekte `mexHttpBinding`, bağlama standart bir kullanışlı olduğu eşdeğer olan `wsHttpBinding` kümesine güvenlik moduyla `None`. Bir "mex" göreli adresini kullanılan uç noktasında olan çözümlenen temel hizmetlerimizi adresi sonuçları bir uç nokta adresi http://localhost/servicemodelsamples/service.svc/mex. Aşağıdaki davranış yapılandırmasını gösterir:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 MEX uç nokta gösterir.  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 Bu örnek ayarlar <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`, hangi de sunan HTTP GET kullanarak hizmet meta verileri. Bir HTTP GET meta veri uç noktası etkinleştirmek için hizmeti bir HTTP temel adresi olmalıdır. Sorgu dizesi `?wsdl` hizmetin taban adresi üzerinde meta verilerine erişmek için kullanılır. Örneğin, bir Web tarayıcısında hizmeti için WSDL görmek için adres kullanırsınız http://localhost/servicemodelsamples/service.svc?wsdl. Alternatif olarak, meta verileri ayarlayarak, HTTPS üzerinden kullanıma sunmak için bu davranışı kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> için `true`. Bu, temel bir HTTPS adresi gerektirir.  
  
 Hizmetin MEX uç noktası kullan erişmeye [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Bu, bir istemci hizmet meta verileri temel alarak oluşturur.  
  
 HTTP GET kullanarak hizmet meta verilerine erişmek için tarayıcınıza noktası http://localhost/servicemodelsamples/service.svc?wsdl.  
  
 Bu davranış kaldırın ve hizmeti ayarlamaya çalıştığınızda bir özel durum alırsınız. Uç nokta davranışı yapılandırılmış olduğundan, bu hata oluştuğunda `IMetadataExchange` sözleşme uygulaması vardır.  
  
 Ayarlarsanız `HttpGetEnabled` için `false`, hizmetin meta verileri görme yerine CalculatorService yardım sayfasına bakın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a>Ayrıca Bkz.
