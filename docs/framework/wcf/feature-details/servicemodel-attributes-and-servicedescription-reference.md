---
title: ServiceModel Öznitelikleri ve ServiceDescription Başvurusu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ba8888c2a1bd3c16ab6d216c365870c0df0e499a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>ServiceModel Öznitelikleri ve ServiceDescription Başvurusu
*Açıklama ağaç* türleri hiyerarşisidir (ile başlayan <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> sınıfı), bir hizmetin her açıdan birlikte açıklanmaktadır. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web Hizmetleri Açıklama Dili (WSDL), XML Şeması Tanım Dili (XSD) ve ilke onaylamalarını (meta verileri) ve istemcilerin bağlanmak ve hizmeti kullanmak için kullandığı hizmet hakkında yayımlamak için geçerli bir hizmet çalışma zamanı oluşturmak için kullandığı bir açıklama ağacı çeşitli kod ve yapılandırma dosyası gösterimlerini açıklama ağaç değerleri oluşturur.  
  
 Bu konuda, nasıl sözleşme ilgili özellikler açıklanmaktadır. hizmet sözleşmesi ve nasıl uygulanan ve açıklama ağacına eklenen elde edilir. Bazı durumlarda, öznitelik değerleri davranış özelliklerine dönüştürülür ve davranışı ardından açıklama ağacına eklenir. Açıklama ağaç değerler meta verileri nasıl dönüştürülür hakkında daha fazla bilgi için bkz: [ServiceDescription ve WSDL başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="mapping-operations-to-the-description-tree"></a>Açıklama ağacına işlemleri eşleme  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar, hizmet sözleşmelerini Modellenen arabirimlerine (veya sınıflar), öznitelikler arabirimi veya sınıf ve yöntemlerinden işlemleri gruplandırması olarak işaretlemek için kullanın. Zaman bir <xref:System.ServiceModel.ServiceHost> sınıfı açıldığında, hizmet sözleşmeleri ve uygulamaları üzerinden yansıtılır ve yapılandırma bilgilerini bir açıklama ağacında birleştirilen.  
  
 İşlem modelleri iki tür vardır: *parametresi* modeli ve *ileti sözleşmesi* modeli. Bir parametre veya tarafından işaretlenen dönüş değeri türü olmayan yönetilen yöntemleri parametresi modelini kullanan <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> sınıfı. Bu model, geliştiriciler, parametreleri serileştirmek denetlemek ve dönüş değerleri, ancak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti ve sözleşmesi için açıklama ağacı doldurmak için kullanılan değerleri oluşturur.  
  
 Yapılandırma dosyalarında belirtilen bağlamaları yüklenirler doğrudan <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> özelliği.  
  
|ServiceBehaviorAttribute özelliği|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|ignoreExtensionDataObject|Ayarlar <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> özelliği tüm işlemler için.|  
|MaxItemsInObjectGraph|Ayarlar <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> özelliği tüm işlemler için.|  
  
|ServiceContractAttribute özelliği|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>, <xref:System.ServiceModel.Description.MessageDescription> tüm işlemler için eklenen <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> ve büyük olasılıkla alt koruma düzeyleri. Koruma düzeyi hiyerarşisi hakkında daha fazla bilgi için bkz: [anlama koruma düzeyi](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute değeri|Etkilenen açıklama ağaç değeri|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|OperationContractAttribute değeri|Etkilenen açıklama ağaç değeri|  
|--------------------------------------|-------------------------------------|  
|Eylem|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> çıktı iletisi veya sözleşme/geri çağırma sözleşme bağlı olarak giriş iletisi için.|  
|Başlatıcıda|TRUE ise, <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> ve <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|Tek bir eşlenir <xref:System.ServiceModel.Description.MessageDescription> içinde <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|Ad|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> ve büyük olasılıkla alt koruma düzeyleri. Koruma düzeyi hiyerarşisi hakkında daha fazla bilgi için bkz: [anlama koruma düzeyi](../../../../docs/framework/wcf/understanding-protection-level.md).|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> çıktı iletisi veya sözleşme/geri çağırma sözleşme bağlı olarak giriş iletisi için.|  
  
|FaultContractAttribute değeri|Etkilenen açıklama ağaç değeri|  
|----------------------------------|-------------------------------------|  
|Eylem|<xref:System.ServiceModel.Description.FaultDescription.Action%2A> Sözleşme/geri çağırma sözleşme bağlı olarak.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Ad|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|DataContractFormatAttribute değeri|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Değeri ayarı <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> işlemi için.|  
  
|XmlSerializerFormatAttribute değeri|Etkilenen açıklama ağaç değeri|  
|----------------------------------------|-------------------------------------|  
|Stil|Bu <xref:System.ServiceModel.XmlSerializerFormatAttribute> özelliği ayarlanmış <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> işlemi için.|  
|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|<xref:System.ServiceModel.XmlSerializerFormatAttribute> Ayarlanan <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> işlemi için.|  
  
|TransactionFlowAttribute değeri|Etkilenen açıklama ağaç değeri|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> Bir işlemi davranışı eklenen <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> özelliği.|  
  
|MessageContractAttribute değeri|Etkilenen açıklama ağaç değeri|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|MessageHeaderAttribute değeri|Etkilenen açıklama ağaç değeri|  
|----------------------------------|-------------------------------------|  
|Aktör|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A> karşılık gelen üst bilgi için <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A> karşılık gelen üst bilgi için <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> karşılık gelen üst bilgi için <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> karşılık gelen üst bilgi için <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> karşılık gelen üst bilgi için <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Geçiş|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A> karşılık gelen üst bilgi için <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|MessageBodyMemberAttribute değeri|Etkilenen açıklama ağaç değeri|  
|--------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|Sırası|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|MessageHeaderArrayAttribute değeri|Etkilenen açıklama ağaç değeri|  
|---------------------------------------|-------------------------------------|  
|Aktör|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|Ad Alanı|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Geçiş|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|MessagePropertyAttribute değeri|Etkilenen açıklama ağaç değeri|  
|------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|MessageParameterAttribute değeri|Etkilenen açıklama ağaç değeri|  
|-------------------------------------|-------------------------------------|  
|Ad|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> karşılık gelen bir parçası <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 Açıklama ağaç değerler meta verileri nasıl dönüştürülür hakkında daha fazla bilgi için bkz: [ServiceDescription ve WSDL başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ServiceDescription ve WSDL Başvurusu](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
