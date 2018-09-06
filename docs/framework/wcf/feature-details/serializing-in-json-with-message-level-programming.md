---
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 9c5ad29e2ddbdde3ae560c4ff2af224bc3a71ad9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855707"
---
# <a name="serializing-in-json-with-message-level-programming"></a>İleti Düzeyi Programlama ile JSON Seri Hale Getirme
WCF JSON biçiminde verilerin serileştirilmesi destekler. Bu konu, türlerinizi kullanarak seri hale getirmek için WCF bildirmek açıklar <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Yazılı ileti programlama  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Kullanıldığında <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> bir hizmet işlemine uygulanır. Bu özniteliklerin her ikisini de belirtmenizi sağlar `RequestFormat` ve `ResponseFormat`. JSON istekler ve yanıtlar için kullanılacak için bunların her ikisi de ayarlanmış `WebMessageFormat.Json`.  JSON kullanmalısınız kullanmak için <xref:System.ServiceModel.WebHttpBinding> otomatik olarak yapılandıran <xref:System.ServiceModel.Description.WebHttpBehavior>. WCF seri hale getirme hakkında daha fazla bilgi için bkz: [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [serileştirme Windows Communication Foundation'da](https://msdn.microsoft.com/magazine/cc163569.aspx). JSON ve WCF hakkında daha fazla bilgi için bkz. [WCF RESTfull hizmetleriyle giriş](https://msdn.microsoft.com/magazine/dd315413.aspx), [.NET 3.5 WCF hizmetleri oluşturma JSON özellikli](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), ve [WCFRESTgenelbakış](https://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  JSON'ı kullanarak kullanılmasını gerektiren <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> SOAP iletişimi desteklemez. İletişim hizmetlerini <xref:System.ServiceModel.WebHttpBinding> istemci-tarafı proxy oluşturmak için Visual Studio'nun hizmet Başvurusu Ekle işlevselliği veya svcutil komut satırı aracını kullanmanız mümkün olmayacak şekilde sunan hizmet meta verileri desteklemez. Hizmetleri kullanan, program aracılığıyla nasıl çağırabileceğiniz daha fazla bilgi için <xref:System.ServiceModel.WebHttpBinding>, bkz: [WCF ile REST hizmetlerini tüketen](https://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Yazılmamış bir Message programlama  
 Doğrudan yazılmamış ileti nesneleriyle çalışırken, JSON olarak seri hale getirmek için yazılmamış bir message üzerinde açıkça özelliklerini ayarlamanız gerekir. Aşağıdaki kod parçacığı, bunun nasıl yapılacağı gösterilmektedir.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AJAX Tümleştirme ve JSON Desteği](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [Bağımsız JSON Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [JSON Serileştirme](../../../../docs/framework/wcf/samples/json-serialization.md)
