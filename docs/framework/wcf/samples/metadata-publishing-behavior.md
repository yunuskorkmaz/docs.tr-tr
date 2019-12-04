---
title: Meta Veri Yayımlama Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 3b3057d845ac37280ff46e6e15415758f1f0ba77
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714788"
---
# <a name="metadata-publishing-behavior"></a>Meta Veri Yayımlama Davranışı
Meta veri yayımlama davranışı örneği, bir hizmetin meta veri yayımlama özelliklerinin nasıl kontrol leceğini gösterir. Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır. Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil. exe gibi) kullanamazsınız.  
  
> [!IMPORTANT]
> Bu örnek, netlik açısından güvenli olmayan bir meta veri yayımlama uç noktasının nasıl oluşturulacağını göstermektedir. Bu uç noktalar, anonim olarak kimliği doğrulanmamış tüketiciler tarafından kullanılabilir ve bir hizmetin meta verilerinin genel olarak kapatılarak emin olmak için bu uç noktaların dağıtılmasından önce gerçekleştirilmelidir. Meta veri uç noktası güvenliğini sağlayan bir örnek için [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) örneğine bakın.  
  
 Örnek, `ICalculator` hizmet sözleşmesini uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bir hizmetin meta verileri kullanıma sunmasına yönelik <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, hizmette yapılandırılması gerekir. Bu davranış mevcut olduğunda, bir uç noktayı, <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmesinin bir WS-MetadataExchange (MEX) protokolünün bir uygulama olarak kullanıma sunulacak şekilde yapılandırarak meta verileri yayımlayabilirsiniz. Kolaylık olması için, bu sözleşmeye "IMetadataExchange" kısaltılmış yapılandırma adı verildi. Bu örnek, güvenlik modu `None`olarak ayarlanan `wsHttpBinding` eşdeğer bir standart bağlama olan `mexHttpBinding`kullanır. Uç noktada "mex" göreli adresi kullanılır ve bu, hizmetler temel adresiyle çözümlenirse, `http://localhost/servicemodelsamples/service.svc/mex`uç nokta adresiyle sonuçlanır. Davranış yapılandırması aşağıda gösterilmiştir:  
  
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
  
 Aşağıda, MEX uç noktası gösterilmektedir.  
  
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
  
 Bu örnek, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`olarak ayarlar ve bu da hizmetin meta verilerini HTTP GET kullanarak gösterir. HTTP GET metaveri uç noktasını etkinleştirmek için hizmetin bir HTTP temel adresi olmalıdır. Sorgu dizesi `?wsdl`, meta verilere erişmek için hizmetin temel adresinde kullanılır. Örneğin, hizmet için WSDL 'yi bir Web tarayıcısında görmek için `http://localhost/servicemodelsamples/service.svc?wsdl`adresini kullanmanız gerekir. Alternatif olarak, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> `true`ayarlayarak HTTPS üzerinden meta verileri açığa çıkarmak için bu davranışı kullanabilirsiniz. Bu bir HTTPS temel adresi gerektirir.  
  
 Hizmetin MEX uç noktasına erişmek için, [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanın.  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Bu, hizmetin meta verilerini temel alan bir istemci oluşturur.  
  
 HTTP GET kullanarak hizmetin meta verilerine erişmek için tarayıcınızı `http://localhost/servicemodelsamples/service.svc?wsdl`üzerine getirin.  
  
 Bu davranışı kaldırır ve hizmeti açmaya çalışırsanız bir özel durum alırsınız. Bu hata, davranışı olmadan, `IMetadataExchange` sözleşmesiyle yapılandırılan uç noktanın hiçbir uygulamayla karşılaşmasından kaynaklanır.  
  
 `HttpGetEnabled` `false`olarak ayarlarsanız, hizmetin meta verilerini görmek yerine Hesaplatorservice yardım sayfasını görürsünüz.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
