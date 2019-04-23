---
title: ServiceDescription ve WSDL Başvurusu
ms.date: 03/30/2017
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
ms.openlocfilehash: 6690bea3d3df0f39a5581c3a6c14723c0f30f40c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182890"
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription ve WSDL Başvurusu
Bu konuda ve ondan Windows Communication Foundation (WCF) Web Hizmetleri Açıklama Dili (WSDL) belgeleri nasıl eşlendiğini açıklayan <xref:System.ServiceModel.Description.ServiceDescription> örnekleri.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>ServiceDescription için WSDL 1.1 nasıl eşlendiğini  
 WCF WSDL belgelerini dışarı aktarmak için kullanabileceğiniz bir <xref:System.ServiceModel.Description.ServiceDescription> hizmet örneği. Meta veri uç noktalarını yayımlama, WSDL belgeleri, hizmetiniz için otomatik olarak üretilir.  
  
 Ayrıca Al <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri <xref:System.ServiceModel.Description.ContractDescription> örnekleri ve <xref:System.ServiceModel.Channels.Binding> WSDL belgeleri kullanarak örneklerden `WsdlImporter` türü.  
  
 WCF tarafından dışarı aktarılan WSDL belgeleri, dış XML şema belgelerden kullanılan herhangi bir XML şema tanımı içeri aktarın. Hizmete veri türlerini kullanma her bir hedef ad alanı için ayrı bir XML Şeması belge aktarılır. Benzer şekilde, ayrı bir WSDL belgesi dışarı aktarılan her hedef ad alanı için hizmet kullanım sözleşme.  
  
### <a name="servicedescription"></a>ServiceDescription  
 A <xref:System.ServiceModel.Description.ServiceDescription> örneği eşlenen bir `wsdl:service` öğesi. A <xref:System.ServiceModel.Description.ServiceDescription> örneği oluşan bir koleksiyon içeren <xref:System.ServiceModel.Description.ServiceEndpoint> her eşleme, ayrı ayrı örnekleri `wsdl:port` öğeleri.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Hizmeti için değer.|  
|`Namespace`|TargetNamespace için `wsdl:service` hizmet tanımı.|  
|`Endpoints`|`wsdl:port` Hizmet tanımları.|  
  
### <a name="serviceendpoint"></a>serviceEndpoint  
 A <xref:System.ServiceModel.Description.ServiceEndpoint> örneği eşlenen bir `wsdl:port` öğesi. A <xref:System.ServiceModel.Description.ServiceEndpoint> örneği bir adresi, bağlama ve bir sözleşme içeriyor.  
  
 Uygulama uç nokta davranışları <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi değiştirebilirsiniz `wsdl:port` bağlı oldukları için uç nokta için öğesi.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name Uç noktası için değer ve `wsdl:binding` /@name uç nokta bağlaması için değer.|  
|`Address`|Adresi `wsdl:port` uç nokta tanımı.<br /><br /> Taşıma için uç nokta adresi biçimini belirler. Örneğin, WCF tarafından desteklenen aktarmalar için bir SOAP adresi veya bir uç nokta başvurusu olabilir.|  
|`Binding`|`wsdl:binding` Uç nokta tanımı.<br /><br /> Farklı `wsdl:binding` tanımları, WCF bağlamaları için herhangi bir sözleşme bağlı değil.|  
|`Contract`|`wsdl:portType` Uç nokta tanımı.|  
|`Behaviors`|Uygulama uç nokta davranışları <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi değiştirebilirsiniz `wsdl:port` uç noktası için.|  
  
### <a name="bindings"></a>Bağlamalar  
 Bağlama örneği için bir `ServiceEndpoint` örneği eşlenen bir `wsdl:binding` tanımı. Farklı `wsdl:binding` belirli bir ile ilişkili olması gereken tanımları `wsdl:portType` tanımı, WCF bağlamaları herhangi bir sözleşme bağımsız.  
  
 Bir bağlama bağlama öğelerinin bir koleksiyonunu oluşur. Her öğe endpoint istemcilerin ile nasıl iletişim kurar, bazı yönleri açıklanmaktadır. Ek olarak, bir bağlama sahip bir <xref:System.ServiceModel.Channels.MessageVersion> belirten <xref:System.ServiceModel.EnvelopeVersion> ve <xref:System.ServiceModel.Channels.AddressingVersion> uç noktası için.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|Bağlama adı eklenmiş anlaşması adına sahip olan bir uç nokta varsayılan adını kullanıldığında, bir alt çizgi ile ayrılmış.|  
|`Namespace`|`targetNamespace` İçin `wsdl:binding` tanımı.<br /><br /> Bir ilke WSDL bağlantı noktasına bağlıysa içeri aktarma işlemi sırasında içeri aktarılan bağlama ad alanı eşlendiği `targetNamespace` için `wsdl:port` tanımı.|  
|`BindingElementCollection`, tarafından döndürülen `CreateBindingElements`() yöntemi|Çeşitli etki alanına özgü Uzantılar `wsdl:binding` tanımı, genellikle ilkeyi onaylar.|  
|`MessageVersion`|`EnvelopeVersion` Ve `AddressingVersion` uç noktası için.<br /><br /> Zaman `MessageVersion.None` belirtilirse, WSDL bağlama bir SOAP bağlama içermiyor ve WS-Addressing içerik WSDL bağlantı noktası içermiyor. Bu ayar genellikle düz eski XML (POX) uç noktaları için kullanılır.|  
  
#### <a name="bindingelements"></a>BindingElements  
 Bir uç nokta bağlaması için bağlama öğeleri eşleme çeşitli WSDL uzantılarında `wsdl:binding`, ilke onaylamalarını gibi.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement> SOAP bağlama için Tekdüzen Kaynak Tanımlayıcısı (URI) aktarım bağlama belirler.  
  
#### <a name="addressingversion"></a>AddressingVersion değerini  
 `AddressingVersion` Bağlamada kullanılan adresleme sürümü eşlendiğini `wsd:port`. WCF SOAP 1.1 ve SOAP 1.2 adresleri ve WS-Addressing destekler 08/2004 ve WS-Addressing 1.0 uç nokta başvuruları.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 `EnvelopeVersion` SOAP sürümünü eşlenir bağlamada kullanılan `wsdl:binding`. WCF SOAP 1.1 ve SOAP 1.2 bağlamaları destekler.  
  
### <a name="contracts"></a>Sözleşmeler  
 <xref:System.ServiceModel.Description.ContractDescription> Örnek bir `ServiceEndpoint` örneği eşlenen bir `wsdl:portType`. A `ContractDescription` örneği tüm işlemler için verilen bir sözleşme açıklar.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Sözleşme için değer.|  
|`Namespace`|TargetNamespace için `wsdl:portType` tanımı.|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Sözleşme için değer. WCF uzantısı için WSDL 1.1 özniteliğidir.|  
|`Operations`|`wsdl:operation` Sözleşme tanımları.|  
  
### <a name="operations"></a>İşlemler  
 Bir <xref:System.ServiceModel.Description.OperationDescription> örneği eşlenen bir `wsdl:portType` / `wsdl:operation`. Bir `OperationDescription` koleksiyonunu içeren `MessageDescription` açıklayan işlemi için iletileri örnekleri.  
  
 İki işlem davranışları katılmak yoğun bir şekilde nasıl bir `OperationDescription` bir WSDL belgesi eşlendi: `DataContractSerializerOperationBehavior` ve `XmlSerializerOperationBehavior`.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name İşlemi için değer.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:binding/wsdl:operation` bu işlem için iletileri.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating İşlemi için değer. WCF uzantısı için WSDL 1.1 özniteliğidir.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating İşlemi için değer. WCF uzantısı için WSDL 1.1 özniteliğidir.|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input` Ve `wsdl:portType` / `wsdl:operation` / `wsdl:output` işlem iletileri.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` İşlemi için tanımlar.|  
|`Behaviors`|`DataContractSerializerOperationBehavior` Ve `XmlSerializerOperationBehavior` işlemi bağlama ve işlem iletileri ile Dağıt.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  
 `DataContractSerializerOperationBehavior` Bir işlem için bir `IWsdlExportExtension` uygulamasında, bu işlem için bağlama ve WSDL iletileri dışarı aktarır. XML Şeması türleri kullanarak verilen `XsdDataContractExporter`. `DataContractSerializerOperationBehavior` Ayrıca kullanım ve stil şema verici ve içeri Aktarıcı bu işlem için kullanılacak belirler.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style` Özelliği bu öznitelik için eşlenen `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style işlemi için değer.<br /><br /> `DataContractSerializerOperationBehavior` WSDL içinde şema türleri yalnızca literal kullanımını destekler.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>The XmlSerializerOperationBehavior  
 `XmlSerializerOperationBehavior` Bir işlem için bir `IWsdlExportExtension` uygulamasında, bu işlem için bağlama ve WSDL iletileri dışarı aktarır. XML Şeması türleri kullanarak verilen `XmlSchemaExporter`. `XmlSerializerOperationBehavior` Ayrıca kullanım ve stil şema verici ve içeri Aktarıcı bu işlem için kullanılacak belirler.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style` Özelliği bu öznitelik için eşlenen `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style işlemi için değer.<br /><br /> `Use` Özelliği bu öznitelik için eşlenen `wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use işlemdeki tüm iletiler için değerler.|  
  
### <a name="messages"></a>İletiler  
 A `MessageDescription` örneği eşlenen bir `wsdl:message` tarafından başvurulan bir `wsdl:portType` / `wsdl:operation` / `wsdl:input` veya `wsdl:portType` / `wsdl:operation` / `wsdl:output`işleminde ileti. A `MessageDescription` gövde ve üstbilgiler vardır.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Action`|İletinin SOAP veya WS-Addressing eylem.<br /><br /> Not, eylem dizesi kullanan bu işlemlere "*" WSDL'de temsil edilmez.|  
|`Direction`|`MessageDirection.Input` eşlendiği `wsdl:input`.<br /><br /> `MessageDirection.Output` eşlendiği `wsdl:output`.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:message` bu ileti tanımı.|  
|`Body`|İleti için ileti gövdesi.|  
|`Headers`|İleti için üstbilgiler.|  
|`ContractDescription.Name`, `OperationContract.Name`|Türetmek için kullanılan, dışa `wsdl:message` /@name değeri.|  
  
#### <a name="message-body"></a>İleti gövdesi  
 A `MessageBodyDescription` örneği eşlendiğini `wsdl:message` / `wsdl:part` iletinin gövdesi için tanımlar. İleti gövdesi, sarmalanmış veya çıplak.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`WrapperName`|RPC stili değilse, ardından `WrapperName` öğe adı tarafından başvurulan eşlenir `wsdl:message` / `wsdl:part` ile @name "parametreleri" ayarlayın.|  
|`WrapperNamespace`|RPC stili değilse, ardından `WrapperNamespace` öğe ad alanı için eşlenen `wsdl:message` / `wsdl:part` ile @name "parametreleri" ayarlayın.|  
|`Parts`|Message bölümleri için bu ileti gövdesi.|  
|`ReturnValue`|Alt öğesi olan bir sarmalayıcı öğe (belge kaydırmalı stili veya RPC stili), yoksa sarmalayıcı öğe ilk `wsdl:message` / `wsdl:part` iletisi.|  
  
#### <a name="message-parts"></a>İleti bölümleri  
 A `MessagePartDescription` örneği eşlenen bir `wsdl:message` / `wsdl:part` ve XML şema türü ya da ileti parçası işaret eden bir öğe.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name İleti parçası ve ileti parçası işaret eden bir öğe adı için değer.|  
|`Namespace`|İleti bölümü işaret eden öğe ad alanı.|  
|`Index`|Dizini `wsdl:message` / `wsdl:part` ileti.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:message` tanımı için bu ileti bölümü. İlke, belirli bir ileti bölümü için işaret edecek şekilde parametreli.|  
|`MessageType`|İleti bölümü işaret öğesi XML şema türü.|  
  
#### <a name="message-headers"></a>İleti üstbilgileri  
 A `MessageHeaderDescription` örneği de eşlenen bir ileti parçası olan bir `soap:header` ileti bölümü için bağlama.  
  
### <a name="faults"></a>Hataları  
 A `FaultDescription` örneği eşlenen bir `wsdl:portType` / `wsdl:operation` / `wsdl:fault` tanımını ve onun ilişkili `wsdl:message` tanımı. `wsdl:message` İlişkili WSDL bağlantı noktası türü olarak aynı hedef ad alanına eklenir. `wsdl:message` Karşılık gelen XML şema öğesini işaret eden "ayrıntılı" adlı bir tek ileti parçası olan `DefaultType` için özellik değeri `FaultDescription` örneği.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Hata için değer.|  
|`Namespace`|Hata ayrıntı iletisi bölümü işaret eden bir XML şema öğesini ad alanı.|  
|`Action`|SOAP veya WS-Addressing eylem hata.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:message` tanımı bu hata için.|  
|`DetailType`|Ayrıntılı ileti bölümü işaret öğesi XML şema türü.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Türetmek için kullanılan `wsdl:message` /@name hata iletisi için değer.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description>
