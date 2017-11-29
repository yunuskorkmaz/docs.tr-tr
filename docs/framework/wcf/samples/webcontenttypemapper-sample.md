---
title: "WebContentTypeMapper Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 994742d0c0d60b9fbe2dd7ed1ea252d1074140f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Örneği
Bu örnek, yeni içerik türlerine eşlemek gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti gövdesi biçimleri.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint> Öğesi takılan sağlayan Web ileti Kodlayıcı içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] JSON, XML veya aynı uç noktada ham ikili iletileri almak için. Kodlayıcı HTTP content-type, isteğin bakarak ileti gövdesinin biçimi belirler. Bu örnek tanıtır <xref:System.ServiceModel.Channels.WebContentTypeMapper> kullanıcının içerik türü ve gövde biçimi arasında eşleme denetlemesine olanak sağlayan sınıf.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]içerik türleri için varsayılan eşlemeleri kümesi sağlar. Örneğin, `application/json` eşler için JSON ve `text/xml` XML eşler. Ham ikili biçime JSON veya XML eşlenmemiş herhangi bir içerik türüne eşlenir.  
  
 Bazı senaryolarda (örneğin, anında iletme stili API), istemci tarafından döndürülen içerik türü hizmet Geliştirici denetlemez. Örneğin, istemcilerin JSON olarak döndürebilir `text/javascript` yerine `application/json`. Bu durumda, hizmet Geliştirici türeyen bir tür sağlamalısınız <xref:System.ServiceModel.Channels.WebContentTypeMapper> belirtilen içerik türü aşağıdaki örnek kodda gösterildiği gibi doğru şekilde işlemek için.  
  
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
  
 Türü geçersiz kılmanız gerekir <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi. Yöntem değerlendirilmelidir `contentType` bağımsız değişkeni ve dönüş aşağıdaki değerlerden biri: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Döndürme <xref:System.ServiceModel.Channels.WebContentFormat.Default> varsayılan Web ileti Kodlayıcı eşlemeleri erteler. Önceki örnek kodda `text/javascript` içerik türü için JSON eşlenen ve diğer tüm eşlemeleri değişmeden kalır.  
  
 Kullanılacak `JsonContentTypeMapper` sınıfı, Web.config dosyasında aşağıdakileri kullanın:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 JsonContentTypeMapper kullanma gereksinimi doğrulamak için yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın. İstemci sayfası kullanmaya çalışırken yüklenemiyordur `text/javascript` JSON içerik göndermek için.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm WebContentTypeMapperSample.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  İçin http://localhost/ServiceModelSamples/JCTMClientPage.htm gidin (JCTMClientPage.htm tarayıcıda proje dizininde açık değil).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a>Ayrıca Bkz.
