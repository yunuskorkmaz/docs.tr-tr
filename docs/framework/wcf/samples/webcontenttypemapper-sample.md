---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: a259f459606c9745fe10276d967946eb675a7f5e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423792"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Örneği
Bu örnek, yeni içerik türlerinin Windows Communication Foundation (WCF) ileti gövdesi biçimlerine nasıl eşleneceğini gösterir.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> öğesi, WCF 'nin aynı uç noktada JSON, XML veya ham ikili mesajlar almasına izin veren Web ileti Kodlayıcısı 'nı takar. Kodlayıcı, isteğin HTTP içerik türüne bakarak iletinin gövde biçimini belirler. Bu örnek, kullanıcının içerik türü ve gövde biçimi arasındaki eşlemeyi denetlemesine olanak sağlayan <xref:System.ServiceModel.Channels.WebContentTypeMapper> sınıfını tanıtır.  
  
 WCF, içerik türleri için bir varsayılan eşlemeler kümesi sağlar. Örneğin, `application/json` JSON ve `text/xml` Maps for XML ile eşlenir. JSON veya XML ile eşlenmemiş herhangi bir içerik türü ham ikili biçime eşlenir.  
  
 Bazı senaryolarda (örneğin, gönderme stili API 'Leri), hizmet geliştiricisi istemci tarafından döndürülen içerik türünü denetlemez. Örneğin, istemciler `application/json`yerine `text/javascript` olarak JSON döndürebilir. Bu durumda, hizmet geliştiricisi aşağıdaki örnek kodda gösterildiği gibi, verilen içerik türünü doğru şekilde işlemek için <xref:System.ServiceModel.Channels.WebContentTypeMapper> türetilen bir tür sağlamalıdır.  
  
```csharp  
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
  
 Tür <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi geçersiz kılmalıdır. Yöntemin `contentType` bağımsız değişkenini değerlendirmesi ve şu değerlerden birini döndürmesi gerekir: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>. <xref:System.ServiceModel.Channels.WebContentFormat.Default> erteleyiciler varsayılan Web ileti Kodlayıcısı eşlemelerine döndürülüyor. Önceki örnek kodda `text/javascript` içerik türü JSON ile eşlenir ve diğer tüm eşlemeler değişmeden kalır.  
  
 `JsonContentTypeMapper` sınıfını kullanmak için, Web. config ' de aşağıdakileri kullanın:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper kullanma gereksinimini doğrulamak için, yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın. JSON içeriğini göndermek için `text/javascript` kullanılmaya çalışıldığında istemci sayfası yükleme başarısız olur.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi WebContentTypeMapperSample. sln çözümünü oluşturun.  
  
3. `http://localhost/ServiceModelSamples/JCTMClientPage.htm` gidin (bir proje dizininin içinden JCTMClientPage. htm dosyasını tarayıcıda açmayın).  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
