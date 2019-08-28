---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 1b15651859fd17673caf898df02c2b74a85d7612
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038535"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Örneği
Bu örnek, yeni içerik türlerinin Windows Communication Foundation (WCF) ileti gövdesi biçimlerine nasıl eşleneceğini gösterir.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Öğesi, WCF 'nin aynı uç noktada JSON, XML veya ham ikili mesajlar almasına izin veren Web ileti Kodlayıcısı ' nı takar. Kodlayıcı, isteğin HTTP içerik türüne bakarak iletinin gövde biçimini belirler. Bu örnek, kullanıcının <xref:System.ServiceModel.Channels.WebContentTypeMapper> içerik türü ve gövde biçimi arasındaki eşlemeyi denetlemesine olanak tanıyan sınıfını tanıtır.  
  
 WCF, içerik türleri için bir varsayılan eşlemeler kümesi sağlar. Örneğin, `application/json` JSON ile eşlenir ve `text/xml` XML ile eşlenir. JSON veya XML ile eşlenmemiş herhangi bir içerik türü ham ikili biçime eşlenir.  
  
 Bazı senaryolarda (örneğin, gönderme stili API 'Leri), hizmet geliştiricisi istemci tarafından döndürülen içerik türünü denetlemez. Örneğin, istemciler `text/javascript` `application/json`yerine JSON döndürebilir. Bu durumda, hizmet geliştiricisi aşağıdaki örnek kodda gösterildiği gibi, verilen içerik türünü <xref:System.ServiceModel.Channels.WebContentTypeMapper> doğru bir şekilde işlemek için öğesinden türetilen bir tür sağlamalıdır.  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 Tür, <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi geçersiz kılmalıdır. Yöntemi `contentType` , bağımsız değişkeni değerlendirmeli ve şu değerlerden birini döndürmelidir: <xref:System.ServiceModel.Channels.WebContentFormat.Xml> <xref:System.ServiceModel.Channels.WebContentFormat.Json>,, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Varsayılan <xref:System.ServiceModel.Channels.WebContentFormat.Default> Web ileti Kodlayıcısı eşlemelerine erteleyiciler döndürülüyor. Önceki örnek kodda, `text/javascript` içerik türü json ile eşlenir ve diğer tüm eşlemeler değişmeden kalır.  
  
 `JsonContentTypeMapper` Sınıfını kullanmak için, Web. config dosyasında aşağıdakileri kullanın:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper kullanma gereksinimini doğrulamak için, yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın. JSON içeriğini göndermek için kullanılmaya `text/javascript` çalışıldığında istemci sayfası yükleme başarısız olur.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi WebContentTypeMapperSample. sln çözümünü oluşturun.  
  
3. ' A gidin (bir proje dizininin içinden JCTMClientPage. htm dosyasını tarayıcıda açmayın). `http://localhost/ServiceModelSamples/JCTMClientPage.htm`  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
