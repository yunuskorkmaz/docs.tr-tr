---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: e37c044e12e015d9f6a5a8e2562d83772cd88a54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569592"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Örneği
Bu örnek, yeni içerik türleri için Windows Communication Foundation (WCF) ileti gövdesi biçimleri eşlemeyle ilgili bilgi gösterir.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Öğesi bağlayacaktır JSON, XML veya aynı uç noktasında ham ikili iletileri almak WCF sağlayan Web ileti Kodlayıcı. Kodlayıcı, HTTP content-type, isteğin bakarak iletinin gövdesi biçimini belirler. Bu örnek tanıtır <xref:System.ServiceModel.Channels.WebContentTypeMapper> içerik türü ve gövde biçimi arasındaki eşlemeyi denetlemek kullanıcının sağlar sınıfını.  
  
 WCF içerik türleri için varsayılan eşlemeleri sunmaktadır. Örneğin, `application/json` JSON değerine eşleyen ve `text/xml` eşleyen XML. JSON veya XML eşlenmemiş herhangi bir içerik türüne ham ikili biçime eşlenir.  
  
 Bazı senaryolarda (örneğin, anında iletme stili API), istemci tarafından döndürülen içerik türü service Geliştirici denetlemez. Örneğin, istemcilerin JSON olarak döndürebilir `text/javascript` yerine `application/json`. Bu durumda, hizmet geliştirici, türetilen bir tür sağlamalısınız <xref:System.ServiceModel.Channels.WebContentTypeMapper> belirtilen içerik türü aşağıdaki örnek kodda gösterildiği gibi doğru şekilde işlemek için.  
  
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
  
 Türü geçersiz kılmanız gerekir <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi. Yöntem değerlendirmelidir `contentType` bağımsız değişkeni ve dönüş aşağıdaki değerlerden biri: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Döndüren <xref:System.ServiceModel.Channels.WebContentFormat.Default> varsayılan Web ileti Kodlayıcı eşlemelere erteler. Önceki örnek kodda `text/javascript` içerik türü için JSON eşlenen ve diğer tüm eşlemeleri değişmeden kalır.  
  
 Kullanılacak `JsonContentTypeMapper` sınıf, uygulamanızın Web.config dosyasında aşağıdakileri kullanın:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper kullanma gereksinimi doğrulamak için yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliği kaldırın. İstemci sayfa kullanmaya çalışırken yüklenemiyordur `text/javascript` JSON içerik göndermek için.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  ' % S'çözüm WebContentTypeMapperSample.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Gidin `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (JCTMClientPage.htm tarayıcıda proje dizininden açmayın).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a>Ayrıca bkz.
