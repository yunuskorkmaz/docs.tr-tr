---
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: af6c2d726b03fe82f5447bdec25944149b966f2a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938066"
---
# <a name="serializing-in-json-with-message-level-programming"></a>İleti Düzeyi Programlama ile JSON Seri Hale Getirme
WCF, JSON biçimindeki verilerin serileştirilmesinin kullanılmasını destekler. Bu konuda, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanarak, WCF 'nin türlerinizi serileştirmek için nasıl anlamakta olduğu açıklanır.  
  
## <a name="typed-message-programming"></a>Yazılan Ileti programlama  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, bir hizmet işlemine <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> uygulandığında kullanılır. Bu özniteliklerin her ikisi de `RequestFormat` ve `ResponseFormat`belirtmenize olanak tanır. İstekleri ve yanıtları için JSON kullanmak. her ikisini de `WebMessageFormat.Json`olarak ayarlayın.  JSON kullanmak için, <xref:System.ServiceModel.Description.WebHttpBehavior>otomatik olarak yapılandıran <xref:System.ServiceModel.WebHttpBinding>kullanmanız gerekir. WCF serileştirme hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). JSON ve WCF hakkında daha fazla bilgi için bkz. [hizmet istasyonu-WCF Ile yeniden hizmet vermek Için bir giriş](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> JSON kullanımı, SOAP iletişimini desteklemeyen <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> kullanılmasını gerektirir. <xref:System.ServiceModel.WebHttpBinding> ile iletişim kuran hizmetler, hizmet meta verilerinin sunulmasını desteklemez, böylece bir istemci tarafı proxy oluşturmak için Visual Studio 'nun Hizmet Başvurusu Ekle işlevselliğini veya Svcutil komut satırı aracını kullanamazsınız. <xref:System.ServiceModel.WebHttpBinding>kullanan Hizmetleri program aracılığıyla nasıl çağırabilmeniz hakkında daha fazla bilgi için bkz. [WCF Ile Rest hizmetlerini kullanma](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
## <a name="untyped-message-programming"></a>Türsüz Ileti programlama  
 Türsüz Ileti nesneleriyle doğrudan çalışırken, türsüz iletideki özellikleri JSON olarak seri hale getirmek için açıkça ayarlamanız gerekir. Aşağıdaki kod parçacığında bunun nasıl yapılacağı gösterilmektedir.  
  
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
- [JSON Serileştirme](../../../../docs/framework/wcf/samples/json-serialization.md)
