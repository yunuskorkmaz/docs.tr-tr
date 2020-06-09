---
title: ServiceModel Öznitelikleri ve ServiceDescription Başvurusu
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: 5e39a63d399edccc580b27ad4bfbc9ab05015ef9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600354"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>ServiceModel Öznitelikleri ve ServiceDescription Başvurusu
*Açıklama ağacı* , <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> bir hizmetin her yönüyle birlikte betimleyen türlerin (sınıfıyla başlayarak) hiyerarşisidir. Windows Communication Foundation (WCF), Web Hizmetleri Açıklama Dili (WSDL), XML şeması tanım dili (XSD) ve istemcilerin hizmete bağlanmak ve bu hizmeti kullanmak ve açıklama ağacı değerlerinin çeşitli kod ve yapılandırma dosyası temsillerini oluşturmak için kullanabileceği hizmetle ilgili olarak, geçerli bir hizmet çalışma zamanı oluşturmak için bir açıklama ağacı kullanır.  
  
 Bu konu başlığı altında, sözleşmeyle ilgili özelliklerin hizmet sözleşmesinden nasıl alındığı ve nasıl uygulandığı ve açıklama ağacına eklendiği açıklanmaktadır. Bazı durumlarda, öznitelik değerleri davranış özelliklerine dönüştürülür ve davranış daha sonra açıklama ağacına eklenir. Açıklama ağacı değerlerinin meta verilere nasıl dönüştürüldüğü hakkında daha fazla bilgi için bkz. [ServiceDescription ve WSDL başvurusu](servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Işlemleri açıklama ağacına eşleme  
 WCF uygulamalarında, hizmet sözleşmeleri arabirim veya sınıfı ve yöntemlerini bir işlem gruplandırması olarak işaretlemek için öznitelikler kullanan arabirimlere (veya sınıflara) göre modellenir. Bir <xref:System.ServiceModel.ServiceHost> sınıf açıldığında, tüm hizmet sözleşmeleri ve uygulamalar, bir açıklama ağacı ile birlikte yansıtılır ve yapılandırma bilgileriyle birleştirilir.  
  
 İki tür işlem modeli vardır: *parametre* modeli ve *ileti sözleşmesi* modeli. Parametre modeli, sınıfı tarafından işaretlenen bir parametre veya dönüş değeri türü olmayan yönetilen yöntemler kullanır <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> . Bu modelde, geliştiriciler parametrelerin ve dönüş değerlerinin serileştirmesini denetler, ancak WCF, hizmet ve sözleşmesinin açıklama ağacını doldurmak için kullanılan değerleri oluşturur.  
  
 Yapılandırma dosyalarında belirtilen bağlamalar doğrudan <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> özelliğine yüklenir.  
  
|ServiceBehaviorAttribute özelliği|Açıklama ağacı değeri etkilendi|  
|---------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A>Tüm işlemler için özelliği ayarlar.|  
|MaxItemsInObjectGraph|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A>Tüm işlemler için özelliği ayarlar.|  
  
|ServiceContractAttribute özelliği|Açıklama ağacı değeri etkilendi|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> tüm işlemlere eklenir <xref:System.ServiceModel.Description.OperationDescription.Messages%2A> .|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A>ve muhtemelen alt koruma düzeyleri. Koruma düzeyi hiyerarşisi hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](../understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute değeri|Açıklama ağacı değeri etkilendi|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|OperationContractAttribute değeri|Açıklama ağacı değeri etkilendi|  
|--------------------------------------|-------------------------------------|  
|Eylem|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>çıkış iletisi veya giriş iletisi için, sözleşme/geri çağırma sözleşmesine bağlı olarak.|  
|Metodundaki AsyncPattern|True ise <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> ve<xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Tek bir ile eşlenir <xref:System.ServiceModel.Description.MessageDescription><xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Name|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A>ve muhtemelen alt koruma düzeyleri. Koruma düzeyi hiyerarşisi hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](../understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A>çıkış iletisi veya giriş iletisi için, sözleşme/geri çağırma sözleşmesine bağlı olarak.|  
  
|FaultContractAttribute değeri|Açıklama ağacı değeri etkilendi|  
|----------------------------------|-------------------------------------|  
|Eylem|<xref:System.ServiceModel.Description.FaultDescription.Action%2A>Sözleşme/geri çağırma sözleşmesine bağlı olarak.|  
|Ayrıntı türü|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Name|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|DataContractFormatAttribute değeri|Açıklama ağacı değeri etkilendi|  
|---------------------------------------|-------------------------------------|  
|Kullanım|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A>Değer, işlem için üzerinde ayarlanır <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> .|  
  
|XmlSerializerFormatAttribute değeri|Açıklama ağacı değeri etkilendi|  
|----------------------------------------|-------------------------------------|  
|Stil|Bu <xref:System.ServiceModel.XmlSerializerFormatAttribute> özellik, <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> işlemi için üzerinde ayarlanır.|  
|Kullanım|, <xref:System.ServiceModel.XmlSerializerFormatAttribute> İşlemi için üzerinde ayarlanır <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> .|  
  
|TransactionFlowAttribute değeri|Açıklama ağacı değeri etkilendi|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|, <xref:System.ServiceModel.TransactionFlowAttribute> Özelliğine bir işlem davranışı olarak eklenir <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> .|  
  
|MessageContractAttribute değeri|Açıklama ağacı değeri etkilendi|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|MessageHeaderAttribute değeri|Açıklama ağacı değeri etkilendi|  
|----------------------------------|-------------------------------------|  
|Aktör|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>içindeki ilgili üst bilgi için<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>içindeki ilgili üst bilgi için<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>içindeki ilgili üst bilgi için<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>içindeki ilgili üst bilgi için<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>içindeki ilgili üst bilgi için<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Geçiş|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>içindeki ilgili üst bilgi için<xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|MessageBodyMemberAttribute değeri|Açıklama ağacı değeri etkilendi|  
|--------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>içindeki ilgili bölüm için<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>içindeki ilgili bölüm için<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Sipariş verme|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A>içindeki ilgili bölüm için<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>içindeki ilgili bölüm için<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|MessageHeaderArrayAttribute değeri|Açıklama ağacı değeri etkilendi|  
|---------------------------------------|-------------------------------------|  
|Aktör|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Geçiş|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|MessagePropertyAttribute değeri|Açıklama ağacı değeri etkilendi|  
|------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|MessageParameterAttribute değeri|Açıklama ağacı değeri etkilendi|  
|-------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>içindeki ilgili bölüm için<xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Açıklama ağacı değerlerinin meta verilere nasıl dönüştürüldüğü hakkında daha fazla bilgi için bkz. [ServiceDescription ve WSDL başvurusu](servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceDescription ve WSDL Başvurusu](servicedescription-and-wsdl-reference.md)
