---
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: f50f6a699dff54e3d0950f5ce0e1049217b9dc45
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928738"
---
# <a name="serializing-in-json-with-message-level-programming"></a>İleti Düzeyi Programlama ile JSON Seri Hale Getirme
WCF, JSON biçimindeki verilerin serileştirilmesinin kullanılmasını destekler. Bu konuda, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>WCF 'yi kullanarak türlerinizi serileştirmek için nasıl söyleyeceğinizi açıklanmaktadır.  
  
## <a name="typed-message-programming"></a>Yazılan Ileti programlama  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.ServiceModel.Web.WebGetAttribute> , Veya<xref:System.ServiceModel.Web.WebInvokeAttribute> bir hizmet işlemine uygulandığında kullanılır. Bu özniteliklerin her ikisi de belirtmenizi `RequestFormat` `ResponseFormat`sağlar. İstekleri ve yanıtları için JSON kullanmak. her ikisini de olarak `WebMessageFormat.Json`ayarlayın.  JSON kullanmak için, <xref:System.ServiceModel.WebHttpBinding>' yi otomatik olarak <xref:System.ServiceModel.Description.WebHttpBehavior>yapılandıran öğesini kullanmanız gerekir. WCF serileştirme hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). JSON ve WCF hakkında daha fazla bilgi için bkz. [hizmet istasyonu-WCF Ile yeniden hizmet vermek Için bir giriş](https://msdn.microsoft.com/magazine/dd315413.aspx).  
  
> [!IMPORTANT]
> JSON kullanımı, <xref:System.ServiceModel.WebHttpBinding> SOAP iletişimini desteklemeyen <xref:System.ServiceModel.Description.WebHttpBehavior> ve kullanımını gerektirir. İle iletişim kuran hizmetler, <xref:System.ServiceModel.WebHttpBinding> hizmet meta verilerinin sunulmasını desteklemez; böylece, istemci tarafı proxy oluşturmak için Visual Studio 'nun hizmet başvurusu Ekle işlevselliğini veya Svcutil komut satırı aracını kullanamazsınız. Tarafından <xref:System.ServiceModel.WebHttpBinding>kullanılan Hizmetleri programlı olarak nasıl çağırabilmeniz hakkında daha fazla bilgi için bkz. [WCF ile rest hizmetlerini kullanma](https://blogs.msdn.microsoft.com/pedram/2008/04/21/how-to-consume-rest-services-with-wcf/).  
  
## <a name="untyped-message-programming"></a>Türsüz Ileti programlama  
 Türsüz Ileti nesneleriyle doğrudan çalışırken, türsüz iletideki özellikleri JSON olarak seri hale getirmek için açıkça ayarlamanız gerekir. Aşağıdaki kod parçacığında bunun nasıl yapılacağı gösterilmektedir.  
  
```  
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
