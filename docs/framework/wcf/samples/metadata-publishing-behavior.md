---
title: "Meta Veri Yayımlama Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fbccca0bb5db7fa12b5237d19b833e9fe11da0e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-publishing-behavior"></a>Meta Veri Yayımlama Davranışı
Meta veri yayımlama davranışı örneği, bir hizmetin meta veri yayımlama özelliklerini denetlemek gösterilmiştir. Olası hassas hizmeti meta verileri, için varsayılan yapılandırma, yanlışlıkla açığa çıkmasını önlemek amacıyla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri, meta veri yayımlama devre dışı bırakır. Bu davranışı varsayılan olarak güvenlidir, ancak ayrıca bir meta veri kullanamayacağı anlamına gelir (örneğin, Svcutil.exe) aracı hizmetin meta veri yayımlama davranışı açıkça yapılandırmasında etkinleştirilmediği sürece hizmetini çağırmak için gerekli istemci kodu oluşturmak üzere, içe.  
  
> [!IMPORTANT]
>  Daha anlaşılır olması için bu örnek nasıl güvenli meta veri yayımlama uç noktası oluşturulacağını gösterir. Bu tür uç noktaları anonim kimlik doğrulamasız tüketicilere potansiyel olarak kullanılabilir ve bakım gibi uç noktaları dağıtmadan önce genel olarak disclosing bir hizmetin meta veri uygun olduğundan emin olmak için izlenmelidir. Bkz: [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) bir meta veri uç noktası güvenli hale getiren bir örnek için örnek.  
  
 Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme. Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Meta veri, kullanıma sunmak bir hizmet için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmette yapılandırılması gerekir. Bu davranış bulunduğunda kullanıma sunmak için bir uç nokta yapılandırarak meta verileri yayımlayabilirsiniz <xref:System.ServiceModel.Description.IMetadataExchange> WS-MetadataExchange (MEX) Protokolü uygulaması olarak sözleşme. Kolaylık, bu sözleşme "IMetadataExchange" kısaltılmış yapılandırma adı verilmedi. Bu örnekte `mexHttpBinding`, kolaylık sağlamak amacıyla bağlaması standart olduğu eşdeğerdir `wsHttpBinding` kümesine güvenlik moduyla `None`. "Mex" göreli adresidir kullanılan uç, hangi olduğunda çözülmüş temel Hizmetleri karşı adresi bir uç nokta adresi http://localhost/servicemodelsamples/service.svc/mex sonuçlanır. Aşağıdaki davranış yapılandırmasını gösterir:  
  
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
  
 Aşağıdaki MEX bitiş noktası gösterir.  
  
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
  
 Bu örnek ayarlar <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğine `true`, hangi ayrıca sunan HTTP GET kullanarak hizmetin meta verileri. Bir HTTP GET meta veri uç noktasının etkinleştirmek için hizmeti bir HTTP temel adresi olması gerekir. Sorgu dizesi `?wsdl` hizmetinin temel adresini meta verilerine erişmek için kullanılır. Örneğin, bir Web tarayıcısı hizmetinde WSDL görmek için adres http://localhost/servicemodelsamples/service.svc?wsdl kullanırsınız. Alternatif olarak, meta veri ayarlayarak HTTPS üzerinden kullanıma sunmak için bu davranış kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> için `true`. Bu bir HTTPS temel adresi gerektirir.  
  
 Hizmetin MEX uç noktası kullan erişmek için [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Bu hizmetin meta verileri temel alarak istemci oluşturur.  
  
 HTTP GET kullanarak hizmetin meta verilerine erişmek için http://localhost/servicemodelsamples/service.svc?wsdl tarayıcınız işaret.  
  
 Bu davranış kaldırırsanız ve hizmet açmaya çalıştığınızda bir özel durum alın. Davranış uç nokta ile yapılandırılmış. Bu hata oluşur `IMetadataExchange` sözleşme hiçbir uygulama vardır.  
  
 Ayarlarsanız `HttpGetEnabled` için `false`, hizmetin meta verileri görmesini yerine CalculatorService yardım sayfasına bakın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a>Ayrıca Bkz.
