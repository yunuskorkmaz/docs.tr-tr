---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143570"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Örneği
Bu örnek, yeni içerik türlerinin Windows Communication Foundation (WCF) ileti gövdesi biçimleriyle nasıl eşlendirilebildiğini gösterir.  
  
 WCF'nin <xref:System.ServiceModel.Description.WebHttpEndpoint> aynı uç noktada JSON, XML veya ham ikili iletiler almasını sağlayan Web iletisi kodlayıcısındaki öğe takılır. Kodlayıcı, isteğin HTTP içerik türüne bakarak iletinin gövde biçimini belirler. Bu örnek, <xref:System.ServiceModel.Channels.WebContentTypeMapper> kullanıcının içerik türü ve gövde biçimi arasındaki eşlemi denetlemesini sağlayan sınıfı tanıtır.  
  
 WCF, içerik türleri için varsayılan eşlemeler kümesi sağlar. Örneğin, `application/json` JSON haritaları `text/xml` ve XML eşler. JSON veya XML'e eşlenmemiş herhangi bir içerik türü ham ikili biçime eşlenir.  
  
 Bazı senaryolarda (örneğin, push-style API'ler), hizmet geliştiricisi istemci tarafından döndürülen içerik türünü denetlemez. Örneğin, istemciler JSON `text/javascript` yerine `application/json`döndürebilir. Bu durumda, hizmet geliştiricisi, aşağıdaki örnek <xref:System.ServiceModel.Channels.WebContentTypeMapper> kodda gösterildiği gibi, verilen içerik türünü doğru şekilde işlemek için türetilen bir tür sağlamalıdır.  
  
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
  
 Tür <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi geçersiz kılmalı. Yöntem `contentType` bağımsız değişkeni değerlendirmeli ve aşağıdaki <xref:System.ServiceModel.Channels.WebContentFormat.Json>değerlerden birini döndürmelidir: , , <xref:System.ServiceModel.Channels.WebContentFormat.Xml> <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Varsayılan <xref:System.ServiceModel.Channels.WebContentFormat.Default> Web iletisi kodlayıcı eşlemelerine ertelemeler. Önceki örnek kodda `text/javascript` içerik türü JSON'a eşlenir ve diğer tüm eşlemeler değişmeden kalır.  
  
 `JsonContentTypeMapper` Sınıfı kullanmak için Web.config'inizde aşağıdakileri kullanın:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper'ı kullanma gereksinimini doğrulamak için yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın. İstemci sayfası JSON içeriğini `text/javascript` göndermeye çalışırken yüklenmez.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. [Windows İletişim Temel Örnekleri Bina](../../../../docs/framework/wcf/samples/building-the-samples.md)açıklandığı gibi çözüm WebContentTypeMapperSample.sln oluşturun.  
  
3. Gidin `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (proje dizininin içinden tarayıcıda JCTMClientPage.htm'yi açmayın).  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
