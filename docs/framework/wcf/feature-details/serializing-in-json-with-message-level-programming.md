---
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: a2568c30d34e39aaf1708a9fb3e186f86b17f5b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-in-json-with-message-level-programming"></a>İleti Düzeyi Programlama ile JSON Seri Hale Getirme
WCF JSON biçiminde verilerin serileştirilmesi destekler. Bu konu, kullanarak türlerinizi serileştirmek için WCF bildirmek açıklar <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Yazılı ileti programlama  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Kullanıldığında <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> bir hizmet işlemi uygulanır. Bu özniteliklerin her ikisini de belirlemenizi sağlayan `RequestFormat` ve `ResponseFormat`. JSON istekleri ve yanıtları için kullanmak üzere bu ikisinin ayarlanmış `WebMessageFormat.Json`.  JSON kullanmalısınız kullanmak için <xref:System.ServiceModel.WebHttpBinding> otomatik olarak yapılandıran <xref:System.ServiceModel.Description.WebHttpBehavior>. WCF seri hale getirme hakkında daha fazla bilgi için bkz: [seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Windows Communication Foundation'da serileştirme](http://msdn.microsoft.com/magazine/cc163569.aspx). JSON ve WCF hakkında daha fazla bilgi için bkz: [RESTfull Hizmetleri WCF ile giriş](http://msdn.microsoft.com/magazine/dd315413.aspx), [.NET 3.5 WCF hizmetleri oluşturma JSON etkinleştirilmiş](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), ve [WCF,KALANgenelbakış](http://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  JSON kullanarak kullanılmasını gerektiren <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> SOAP iletişimi desteklemez. İletişim hizmetlerini <xref:System.ServiceModel.WebHttpBinding> istemci-tarafı proxy oluşturmak için Visual Studio'nun hizmet Başvurusu Ekle işlevselliği veya svcutil komut satırı aracını kullanmanız mümkün olmayacak şekilde sunan hizmet meta verilerini desteklemez. Hizmetleri kullanan nasıl programlı olarak çağırabilirsiniz daha fazla bilgi için <xref:System.ServiceModel.WebHttpBinding>, bkz: [REST Hizmetleri WCF ile kullanmak için nasıl](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Türsüz ileti programlama  
 Doğrudan türsüz Message nesneleri ile çalışırken, JSON olarak seri hale getirmek için türsüz iletideki açıkça özelliklerini ayarlamanız gerekir. Aşağıdaki kod parçacığını bunun nasıl yapılacağı gösterilmektedir.  
  
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
