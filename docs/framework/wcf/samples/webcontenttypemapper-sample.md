---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 550e763d30a7fa503f6500dcaa8f9b77ea499bca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283269"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Örneği

Bu örnek, yeni içerik türlerinin Windows Communication Foundation (WCF) ileti gövdesi biçimlerine nasıl eşleneceğini gösterir.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>Öğesi, WCF 'nin aynı uç noktada JSON, XML veya ham ikili mesajlar almasına izin veren Web ileti Kodlayıcısı ' nı takar. Kodlayıcı, isteğin HTTP içerik türüne bakarak iletinin gövde biçimini belirler. Bu örnek <xref:System.ServiceModel.Channels.WebContentTypeMapper> , kullanıcının içerik türü ve gövde biçimi arasındaki eşlemeyi denetlemesine olanak tanıyan sınıfını tanıtır.  
  
 WCF, içerik türleri için bir varsayılan eşlemeler kümesi sağlar. Örneğin, `application/json` JSON ile eşlenir ve `text/xml` XML ile eşlenir. JSON veya XML ile eşlenmemiş herhangi bir içerik türü ham ikili biçime eşlenir.  
  
 Bazı senaryolarda (örneğin, gönderme stili API 'Leri), hizmet geliştiricisi istemci tarafından döndürülen içerik türünü denetlemez. Örneğin, istemciler yerine JSON döndürebilir `text/javascript` `application/json` . Bu durumda, hizmet geliştiricisi <xref:System.ServiceModel.Channels.WebContentTypeMapper> Aşağıdaki örnek kodda gösterildiği gibi, verilen içerik türünü doğru bir şekilde işlemek için öğesinden türetilen bir tür sağlamalıdır.  
  
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
  
 Tür, yöntemi geçersiz kılmalıdır <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> . Yöntemi, `contentType` bağımsız değişkeni değerlendirmeli ve şu değerlerden birini döndürmelidir: <xref:System.ServiceModel.Channels.WebContentFormat.Json> , <xref:System.ServiceModel.Channels.WebContentFormat.Xml> , <xref:System.ServiceModel.Channels.WebContentFormat.Raw> veya <xref:System.ServiceModel.Channels.WebContentFormat.Default> . <xref:System.ServiceModel.Channels.WebContentFormat.Default>Varsayılan Web ileti Kodlayıcısı eşlemelerine erteleyiciler döndürülüyor. Önceki örnek kodda, `text/javascript` içerik türü json ile eşlenir ve diğer tüm eşlemeler değişmeden kalır.  
  
 Sınıfını kullanmak için `JsonContentTypeMapper` Web.config aşağıdakileri kullanın:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper kullanma gereksinimini doğrulamak için, yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın. JSON içeriğini göndermek için kullanılmaya çalışıldığında istemci sayfası yükleme başarısız olur `text/javascript` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi WebContentTypeMapperSample. sln çözümünü oluşturun.  
  
3. ' A gidin `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (tarayıcıda JCTMClientPage.htm proje dizininden açmayın).  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
