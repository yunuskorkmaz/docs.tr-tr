---
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 854f03e94510b7f02bb1b7660f1e5108fd8faed8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600406"
---
# <a name="serializing-in-json-with-message-level-programming"></a>İleti Düzeyi Programlama ile JSON Seri Hale Getirme
WCF, JSON biçimindeki verilerin serileştirilmesinin kullanılmasını destekler. Bu konuda, WCF 'yi kullanarak türlerinizi serileştirmek için nasıl söyleyeceğinizi açıklanmaktadır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .  
  
## <a name="typed-message-programming"></a>Yazılan Ileti programlama  
 , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.ServiceModel.Web.WebGetAttribute> Veya <xref:System.ServiceModel.Web.WebInvokeAttribute> bir hizmet işlemine uygulandığında kullanılır. Bu özniteliklerin her ikisi de belirtmenizi sağlar `RequestFormat` `ResponseFormat` . İstekleri ve yanıtları için JSON kullanmak. her ikisini de olarak ayarlayın `WebMessageFormat.Json` .  JSON kullanmak için, <xref:System.ServiceModel.WebHttpBinding> ' yi otomatik olarak yapılandıran öğesini kullanmanız gerekir <xref:System.ServiceModel.Description.WebHttpBehavior> . WCF serileştirme hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md). JSON ve WCF hakkında daha fazla bilgi için bkz. [hizmet istasyonu-WCF Ile yeniden hizmet vermek Için bir giriş](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> JSON kullanımı, <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> SOAP iletişimini desteklemeyen ve kullanımını gerektirir. İle iletişim kuran hizmetler, <xref:System.ServiceModel.WebHttpBinding> hizmet meta verilerinin sunulmasını desteklemez; böylece, istemci tarafı proxy oluşturmak Için Visual Studio 'nun hizmet başvurusu Ekle işlevselliğini veya Svcutil komut satırı aracını kullanamazsınız. Tarafından kullanılan Hizmetleri programlı olarak nasıl çağırabilmeniz hakkında daha fazla bilgi için <xref:System.ServiceModel.WebHttpBinding> bkz. [WCF Ile Rest hizmetlerini kullanma](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
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

- [AJAX Tümleştirme ve JSON Desteği](ajax-integration-and-json-support.md)
- [Bağımsız JSON Seri Hale Getirme](stand-alone-json-serialization.md)
- [JSON serileştirme](../samples/json-serialization.md)
