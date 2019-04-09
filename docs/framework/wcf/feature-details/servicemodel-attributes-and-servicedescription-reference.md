---
title: ServiceModel Öznitelikleri ve ServiceDescription Başvurusu
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: 022731d7d6e60d36c5f4a595edc90aaff0586a79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195351"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>ServiceModel Öznitelikleri ve ServiceDescription Başvurusu
*Açıklama ağaç* türlerin hiyerarşisi olan (başlayarak <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> sınıfı) bir hizmet her yönüyle birlikte açıklar. Windows Communication Foundation (WCF) Web Hizmetleri Açıklama Dili (WSDL), XML Şeması Tanım Dili (XSD) ve istemciler için kullanabileceğiniz hizmetiyle ilgili ilke onaylamalarını (meta veriler) yayımlamak için bir geçerli hizmet çalışma zamanı oluşturmak için bir açıklama ağaç kullanır. bağlanmak ve bu hizmeti kullanmak ve çeşitli kod ve yapılandırma dosyası açıklaması ağaç değerlerinin temsillerini oluşturmak için.  
  
 Bu konu, nasıl sözleşme ile ilgili özellikleri açıklar. hizmet sözleşmesi ve nasıl bunlar uygulanan ve açıklama ağacına elde edilir. Bazı durumlarda, öznitelik değerleri davranış özelliklerini dönüştürülür ve davranışı ardından açıklama ağacına eklenir. Açıklama ağaç değerleri meta verilere nasıl dönüştürüldüğünü hakkında daha fazla bilgi için bkz. [ServiceDescription ve WSDL başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Açıklama ağaç eşleme işlemleri  
 WCF uygulamalarda, hizmet sözleşmelerini arabirimleri (veya sınıfları) tarafından modellenir arabirim veya sınıf ve metotlarını işlemlerinin bir gruplandırma olarak işaretlemek için öznitelikler kullanan. Olduğunda bir <xref:System.ServiceModel.ServiceHost> sınıfı açıldığında, herhangi bir hizmet sözleşmeleri ve uygulamalar üzerinden yansıtılır ve yapılandırma bilgilerini bir açıklama ağacında ile birleştirilir.  
  
 İşlem modelleri iki tür vardır: *parametre* modeli ve *ileti anlaşması* modeli. Bir parametre veya olarak işaretlenmiş dönüş değeri türüne sahip değil, yönetilen yöntemleri parametresi modelini kullanan <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> sınıfı. Bu modelde, geliştiricilerin parametreleri serileştirmek denetlemek ve dönüş değerleri, ancak WCF hizmet sözleşmesi için açıklama ağacını doldurmak için kullanılan değerleri oluşturur.  
  
 Yapılandırma dosyalarında belirtilen bağlamaları doğrudan yüklenir <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> özelliği.  
  
|ServiceBehaviorAttribute özelliği|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|Kümeleri <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> tüm işlemler için özellik.|  
|MaxItemsInObjectGraph|Kümeleri <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> tüm işlemler için özellik.|  
  
|ServiceContractAttribute özelliği|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> tüm işlemler için eklenen <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> ve büyük olasılıkla alt koruma düzeyleri. Koruma düzeyi hiyerarşisi hakkında daha fazla bilgi için bkz. [anlama koruma düzeyi](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|Sessionmode'u|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute değeri|Etkilenen açıklama ağaç değeri|  
|--------------------------------------|-------------------------------------|  
|methodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|OperationContractAttribute değeri|Etkilenen açıklama ağaç değeri|  
|--------------------------------------|-------------------------------------|  
|Eylem|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> çıkış iletisi veya sözleşme/geri çağırma anlaşması sırasında bağlı olarak giriş iletisi için.|  
|AsyncPattern|TRUE ise <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> ve <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Tek bir eşlenir <xref:System.ServiceModel.Description.MessageDescription> içinde <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Ad|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> ve büyük olasılıkla alt koruma düzeyleri. Koruma düzeyi hiyerarşisi hakkında daha fazla bilgi için bkz. [anlama koruma düzeyi](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> çıkış iletisi veya sözleşme/geri çağırma anlaşması sırasında bağlı olarak giriş iletisi için.|  
  
|FaultContractAttribute değeri|Etkilenen açıklama ağaç değeri|  
|----------------------------------|-------------------------------------|  
|Eylem|<xref:System.ServiceModel.Description.FaultDescription.Action%2A> Sözleşme/geri çağırma anlaşması sırasında bağlı olarak.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Ad|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|DataContractFormatAttribute değeri|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Değeri ayarı <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> işlemi için.|  
  
|XmlSerializerFormatAttribute değeri|Etkilenen açıklama ağaç değeri|  
|----------------------------------------|-------------------------------------|  
|Stil|Bu <xref:System.ServiceModel.XmlSerializerFormatAttribute> özelliği ayarlanmış <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> işlemi için.|  
|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|<xref:System.ServiceModel.XmlSerializerFormatAttribute> Ayarlanır <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> işlemi için.|  
  
|TransactionFlowAttribute değeri|Etkilenen açıklama ağaç değeri|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> İçin bir işlem davranışı olarak eklenen <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> özelliği.|  
  
|MessageContractAttribute değeri|Etkilenen açıklama ağaç değeri|  
|------------------------------------|-------------------------------------|  
|protectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|MessageHeaderAttribute değeri|Etkilenen açıklama ağaç değeri|  
|----------------------------------|-------------------------------------|  
|Aktör|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A> karşılık gelen üst bilgisinde <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A> karşılık gelen üst bilgisinde <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> karşılık gelen üst bilgisinde <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> karşılık gelen üst bilgisinde <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> karşılık gelen üst bilgisinde <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Geçiş|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A> karşılık gelen üst bilgisinde <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|Da MessageBodyMemberAttribute değeri|Etkilenen açıklama ağaç değeri|  
|--------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Sipariş verme|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|MessageHeaderArrayAttribute değeri|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|Aktör|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|protectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Geçiş|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|MessagePropertyAttribute değeri|Etkilenen açıklama ağaç değeri|  
|------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|MessageParameterAttribute değeri|Etkilenen açıklama ağaç değeri|  
|-------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Açıklama ağaç değerleri meta verilere nasıl dönüştürüldüğünü hakkında daha fazla bilgi için bkz. [ServiceDescription ve WSDL başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceDescription ve WSDL Başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
