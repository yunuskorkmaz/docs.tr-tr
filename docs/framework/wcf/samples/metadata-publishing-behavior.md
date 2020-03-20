---
title: Meta Veri Yayımlama Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144402"
---
# <a name="metadata-publishing-behavior"></a>Meta Veri Yayımlama Davranışı
Meta veri yayımlama davranışı örneği, bir hizmetin meta veri yayımlama özelliklerinin nasıl denetlenir olduğunu gösterir. Potansiyel olarak hassas hizmet meta verilerinin kasıtsız olarak açıklanmasını önlemek için, Windows Communication Foundation (WCF) hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı kılabilir. Bu davranış varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracını (Svcutil.exe gibi) kullanamayacağınız anlamına da gelir.  
  
> [!IMPORTANT]
> Bu örnek, açıklık için güvenli olmayan bir meta veri yayımlama bitiş noktasının nasıl oluşturulabildiğini gösterir. Bu tür uç noktalar anonim kimliği doğrulanmamış tüketiciler için kullanılabilir ve bir hizmetin meta verilerinin herkese açık olarak ifşa edilmesinin uygun olduğundan emin olmak için bu uç noktaları dağıtmadan önce dikkatli olunmalıdır. Meta [veri](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) bitiş noktasını güvence altına alan bir örnek için Özel Güvenli Meta Veri Bitiş Noktası örneğine bakın.  
  
 Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır. Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bir hizmetin meta verileri <xref:System.ServiceModel.Description.ServiceMetadataBehavior> açığa çıkarabilmesi için, hizmet üzerinde yapılandırılması gerekir. Bu davranış söz konusu olduğunda, <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmeyi ws-MetadataExchange (MEX) protokolünün bir uygulaması olarak ortaya çıkarmak için bir bitiş noktası yapılandırarak meta verileri yayımlayabilirsiniz. Kolaylık sağlamak amacıyla, bu sözleşmeye "IMetadataExchange" kısaltma yapılandırma adı verilmiştir. Bu `mexHttpBinding`örnek, güvenlik modu ile eşdeğer `wsHttpBinding` bir kolaylık standart bağlama `None`kullanır. Uç noktada "mex"in göreceli bir adresi kullanılır ve hizmetler temel adresine karşı çözüldüğünde `http://localhost/servicemodelsamples/service.svc/mex`bir bitiş noktası adresi . Aşağıdaki davranış yapılandırmasını gösterir:  
  
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
  
 Aşağıdaki MEX bitiş noktasını gösterir.  
  
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
  
 Bu örnek <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> `true`özelliği , http GET kullanarak hizmetin meta verilerini de ortaya çıkaran olarak ayarlar. HTTP GET meta veri bitiş noktasını etkinleştirmek için hizmetin bir HTTP temel adresi olması gerekir. Sorgu dizesi, `?wsdl` meta verilere erişmek için hizmetin temel adresinde kullanılır. Örneğin, bir Web tarayıcısında hizmet için WSDL görmek için `http://localhost/servicemodelsamples/service.svc?wsdl`adresi kullanmak istiyorsunuz. Alternatif olarak, bu davranışı, https üzerinden meta <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> verileri `true`' ye ayarlayarak ortaya çıkarmak için kullanabilirsiniz. Bunun için bir HTTPS temel adresi gerektirir.  
  
 Hizmetin MEX bitiş noktasına erişmek için [ServiceModel Metadata Utility Tool 'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanın.  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Bu, hizmetin meta verilerine dayalı bir istemci oluşturur.  
  
 HTTP GET'i kullanarak hizmetin meta verilerine `http://localhost/servicemodelsamples/service.svc?wsdl`erişmek için tarayıcınızı ' a' ya yönlendirin.  
  
 Bu davranışı kaldırır ve hizmeti açmaya çalışırsanız bir özel durum elde elabilirsiniz. Bu hata, davranış olmadan, sözleşmeyle yapılandırılan `IMetadataExchange` bitiş noktasının uygulaması olmadığından oluşur.  
  
 `false`Ayarlarsanız, `HttpGetEnabled` hizmetin meta verilerini görmek yerine Hesap Makinesi Hizmeti yardım sayfasını görürsünüz.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
