---
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 36459dbc0ddee883678a98a27f9abb74fde78e86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184492"
---
# <a name="serializing-in-json-with-message-level-programming"></a>İleti Düzeyi Programlama ile JSON Seri Hale Getirme
WCF, JSON formatında verileri seri hale getirmeyi destekler. Bu konu, WCF'ye türlerinizi seri <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>hale getirmek için nasıl söyleyeceğiniz açıklanır.  
  
## <a name="typed-message-programming"></a>Yazılı İleti Programlama  
 Bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> hizmet işlemine <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> uygulandığında kullanılır. Bu özniteliklerin her ikisi `RequestFormat` `ResponseFormat`de belirtmek için izin verir ve . İstek ler ve yanıtlar için JSON'u kullanmak için. her ikisini de `WebMessageFormat.Json`.  JSON'u kullanmak <xref:System.ServiceModel.WebHttpBinding>için, otomatik olarak yapılandırılan <xref:System.ServiceModel.Description.WebHttpBehavior>. WCF serileştirme hakkında daha fazla bilgi için [serileştirme ve deserialization'a](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)bakın. JSON ve WCF hakkında daha fazla bilgi için Service [Station - WCF ile RESTful Hizmetlere Giriş](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf)' e bakın.  
  
> [!IMPORTANT]
> JSON'un kullanılması, SOAP iletişiminin <xref:System.ServiceModel.WebHttpBinding> kullanılmasını gerektirir ve <xref:System.ServiceModel.Description.WebHttpBehavior> bu iletişimi desteklemez. Hizmet <xref:System.ServiceModel.WebHttpBinding> meta verilerini açığa çıkarmakla iletişim kuramayan hizmetler, istemci tarafı proxy'si oluşturmak için Visual Studio'nun Hizmet Başvurusu Ekle işlevini veya svcutil komut satırı aracını kullanamazsınız. Kullanan hizmetleri programlı olarak nasıl arayabilirsiniz <xref:System.ServiceModel.WebHttpBinding>hakkında daha fazla bilgi için [WCF ile REST Hizmetlerinin Nasıl Tüketilir'e](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf)bakınız.  
  
## <a name="untyped-message-programming"></a>Yazılmamış İleti Programlama  
 Doğrudan yazılmamış İleti nesneleri ile çalışırken, json olarak serihale getirmek için yazılmamış iletideki özellikleri açıkça ayarlamanız gerekir. Aşağıdaki kod parçacığı bunun nasıl yapılacağını gösterir.  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AJAX Tümleştirme ve JSON Desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Bağımsız JSON Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [JSON Seri Hale Getirme](../../../../docs/framework/wcf/samples/json-serialization.md)
