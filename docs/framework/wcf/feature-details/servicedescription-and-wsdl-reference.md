---
title: ServiceDescription ve WSDL Başvurusu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7eadfaaae920071092f569fe2b8882875ed9497f
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription ve WSDL Başvurusu
Bu konuda açıklanmaktadır nasıl [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web Hizmetleri Açıklama Dili (WSDL) belgeleri ve ondan eşlemeleri <xref:System.ServiceModel.Description.ServiceDescription> örnekleri.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>ServiceDescription WSDL 1.1 nasıl eşlendiğini  
 Kullanabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL belgelerden dışarı aktarmak için bir <xref:System.ServiceModel.Description.ServiceDescription> hizmetiniz için örneği. Meta veri uç noktalarını yayımladığınızda WSDL belgeleri hizmetiniz için otomatik olarak oluşturulur.  
  
 Ayrıca içeri aktarabilirsiniz <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri, <xref:System.ServiceModel.Description.ContractDescription> örnekleri ve <xref:System.ServiceModel.Channels.Binding> kullanarak WSDL belgeleri örneklerden `WsdlImporter` türü.  
  
 WSDL belgeler, dışa aktarılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], dış XML Şeması belgelerden kullanılan tüm XML şema tanımını içeri aktarın. Veri türleri hizmetinde kullanmak her hedef ad alanı için ayrı bir XML Şeması belgesi aktarılır. Benzer şekilde, ayrı bir WSDL belge dışarı her hedef ad alanı için kullanım hizmeti sözleşme.  
  
### <a name="servicedescription"></a>ServiceDescription  
 A <xref:System.ServiceModel.Description.ServiceDescription> örneği eşlendiğini bir `wsdl:service` öğesi. A <xref:System.ServiceModel.Description.ServiceDescription> örneğini içeren koleksiyonu <xref:System.ServiceModel.Description.ServiceEndpoint> örnekleri her eşleme, bağımsız `wsdl:port` öğeleri.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Hizmet için değer.|  
|`Namespace`|İçin hedefAdboşluğu `wsdl:service` hizmet tanımı.|  
|`Endpoints`|`wsdl:port` Hizmet için tanımlar.|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  
 A <xref:System.ServiceModel.Description.ServiceEndpoint> örneği eşlendiğini bir `wsdl:port` öğesi. A <xref:System.ServiceModel.Description.ServiceEndpoint> örneği içeren bir adresi, bağlama ve bir sözleşme.  
  
 Uygulama uç noktası davranışları <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi değiştirebilirsiniz `wsdl:port` bağlı oldukları için uç nokta için öğesi.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name Uç noktası için değer ve `wsdl:binding` /@name endpoint bağlama için değer.|  
|`Address`|Adresini `wsdl:port` uç nokta tanımı.<br /><br /> Uç nokta için taşıma adresinin biçimi belirler. Örneğin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-bunu olabilir bir SOAP adresi veya bir uç nokta başvuru taşımaları desteklenir.|  
|`Binding`|`wsdl:binding` Uç nokta tanımı.<br /><br /> Farklı `wsdl:binding` tanımları, bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] herhangi bir sözleşmesine bağlı değil.|  
|`Contract`|`wsdl:portType` Uç nokta tanımı.|  
|`Behaviors`|Uygulama uç noktası davranışları <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi değiştirebilirsiniz `wsdl:port` uç noktası için.|  
  
### <a name="bindings"></a>Bağlamalar  
 Bağlama örneği için bir `ServiceEndpoint` örneği eşlendiğini bir `wsdl:binding` tanımı. Farklı `wsdl:binding` belirli bir ile ilişkilendirilmelidir tanımları `wsdl:portType` tanımı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamaları herhangi bir sözleşme bağımsız.  
  
 Bir bağlama bağlama öğelerinin koleksiyonu yapılır. Her uç nokta istemcileri ile nasıl iletişim kurduğu, bazı yönlerinin açıklar. Ayrıca, bir bağlama sahip bir <xref:System.ServiceModel.Channels.MessageVersion> belirten <xref:System.ServiceModel.EnvelopeVersion> ve <xref:System.ServiceModel.Channels.AddressingVersion> uç noktası için.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|Bir uç nokta varsayılan adını kullanılan, eklenmiş sözleşme adı bağlama adıyla olduğu bir çizgiyle ayrılmış.|  
|`Namespace`|`targetNamespace` İçin `wsdl:binding` tanımı.<br /><br /> Bir ilke WSDL bağlantı noktasına bağlıysa içeri aktarma işlemi sırasında içeri aktarılan bağlama ad alanı eşlendiği `targetNamespace` için `wsdl:port` tanımı.|  
|`BindingElementCollection`, tarafından döndürülen `CreateBindingElements`() yöntemi|Çeşitli etki alanına özgü Uzantılar `wsdl:binding` tanımı, genellikle ilkeyi onaylar.|  
|`MessageVersion`|`EnvelopeVersion` Ve `AddressingVersion` uç noktası için.<br /><br /> Zaman `MessageVersion.None` belirtilirse, WSDL bağlama SOAP bağlama içermiyor ve WS adresleme içeriği WSDL bağlantı noktası içermiyor. Bu ayar genellikle düz eski XML (POX) uç noktaları için kullanılır.|  
  
#### <a name="bindingelements"></a>BindingElements  
 Bağlama öğeleri bir uç nokta bağlama için çeşitli WSDL uzantılarında eşlemeniz `wsdl:binding`, ilke onaylamalarını gibi.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement> SOAP bağlama için Tekdüzen Kaynak Tanımlayıcısı (URI) aktarım bağlama belirler.  
  
#### <a name="addressingversion"></a>AddressingVersion değerini  
 `AddressingVersion` Bağlamada eşler sürüme kullanılan adresleme `wsd:port`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP 1.1 ve SOAP 1.2 adresleri ve WS adresleme destekleyen 08/2004 ve WS adresleme 1.0 uç nokta başvuruları.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 `EnvelopeVersion` SOAP sürümünü eşlenir bağlamada kullanılan `wsdl:binding`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SOAP 1.1 ve SOAP 1.2 bağlamaları destekler.  
  
### <a name="contracts"></a>Sözleşmeler  
 <xref:System.ServiceModel.Description.ContractDescription> İçin örnek bir `ServiceEndpoint` örneği eşlendiğini bir `wsdl:portType`. A `ContractDescription` örneği tüm verilen sözleşme işlemlerini açıklar.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Sözleşme değeri.|  
|`Namespace`|İçin hedefAdboşluğu `wsdl:portType` tanımı.|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Sözleşme değeri. Bu öznitelik bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL 1.1 uzantısı.|  
|`Operations`|`wsdl:operation` Sözleşme tanımı.|  
  
### <a name="operations"></a>İşlemler  
 Bir <xref:System.ServiceModel.Description.OperationDescription> örneği eşlendiğini bir `wsdl:portType` / `wsdl:operation`. Bir `OperationDescription` oluşan bir koleksiyon içeren `MessageDescription` işlemi iletilerde açıklamak örnekleri.  
  
 İki işlem davranışları katılmak yoğun bir şekilde nasıl bir `OperationDescription` WSDL belgeye eşlenen: `DataContractSerializerOperationBehavior` ve `XmlSerializerOperationBehavior`.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name İşlemi için değer.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:binding/wsdl:operation` bu işlem için iletileri.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating İşlemi için değer. Bu öznitelik bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL 1.1 uzantısı.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating İşlemi için değer. Bu öznitelik bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL 1.1 uzantısı.|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input` Ve `wsdl:portType` / `wsdl:operation` / `wsdl:output` iletileri işlemi için.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` İşlemi için tanımlar.|  
|`Behaviors`|`DataContractSerializerOperationBehavior` Ve `XmlSerializerOperationBehavior` işlemi bağlama ve işlem iletileri ile ilgilidir.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>The DataContractSerializerOperationBehavior  
 `DataContractSerializerOperationBehavior` Bir işlem için bir `IWsdlExportExtension` WSDL iletileri ve bu işlem için bağlama aktarır uygulama. XML Şeması türleri kullanılarak verilmiş `XsdDataContractExporter`. `DataContractSerializerOperationBehavior` Kullanın, stil ve şema dışarı aktarma ve alma için bu işlemi kullanmak için de belirler.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style` Bu öznitelik için özellik eşlemeleri için `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style işlemi için değer.<br /><br /> `DataContractSerializerOperationBehavior` WSDL içinde şema türleri yalnızca değişmez değer kullanımını destekler.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>The XmlSerializerOperationBehavior  
 `XmlSerializerOperationBehavior` Bir işlem için bir `IWsdlExportExtension` WSDL iletileri ve bu işlem için bağlama aktarır uygulama. XML Şeması türleri kullanılarak verilmiş `XmlSchemaExporter`. `XmlSerializerOperationBehavior` Kullanın, stil ve şema dışarı aktarma ve alma için bu işlemi kullanmak için de belirler.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style` Bu öznitelik için özellik eşlemeleri için `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style işlemi için değer.<br /><br /> `Use` Bu öznitelik için özellik eşlemeleri için `wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use işlemi tüm iletiler için değerleri.|  
  
### <a name="messages"></a>İletiler  
 A `MessageDescription` örneği eşlendiğini bir `wsdl:message` tarafından başvurulan bir `wsdl:portType` / `wsdl:operation` / `wsdl:input` veya `wsdl:portType` / `wsdl:operation` / `wsdl:output`bir işlemde ileti. A `MessageDescription` gövde ile üst bilgilerine sahiptir.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Action`|İletinin SOAP veya WS adresleme eylem.<br /><br /> Not eylem dizesi kullanan bu işlemler "*" WSDL içinde temsil edilmez.|  
|`Direction`|`MessageDirection.Input` eşlendiği `wsdl:input`.<br /><br /> `MessageDirection.Output` eşlendiği `wsdl:output`.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:message` bu ileti tanımı.|  
|`Body`|İleti için ileti gövdesi.|  
|`Headers`|İleti için üstbilgiler.|  
|`ContractDescription.Name`, `OperationContract.Name`|Türetilen için kullanılan, dışa `wsdl:message` /@name değeri.|  
  
#### <a name="message-body"></a>İleti gövdesi  
 A `MessageBodyDescription` örneği eşlendiğini `wsdl:message` / `wsdl:part` bir ileti gövdesi için tanımlar. İleti gövdesi kaydırılmış olabilir veya tam.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`WrapperName`|Stil RPC değilse sonra `WrapperName` haritalar tarafından başvuruda bulunulan öğe adı için `wsdl:message` / `wsdl:part` ile @name "parametreleri" ayarlayın.|  
|`WrapperNamespace`|Stil RPC değilse sonra `WrapperNamespace` öğesinin ad alanı için eşlendiğini `wsdl:message` / `wsdl:part` ile @name "parametreleri" ayarlayın.|  
|`Parts`|Bu ileti gövdesi ileti bölümleri.|  
|`ReturnValue`|Bir kapsayıcı öğe (Sarmalanan belge stili veya RPC stili), yoksa sarmalayıcı öğesinin alt öğesi ilk `wsdl:message` / `wsdl:part` iletisi.|  
  
#### <a name="message-parts"></a>İleti bölümleri  
 A `MessagePartDescription` örneği eşlendiğini bir `wsdl:message` / `wsdl:part` ve XML Şeması tür ya da ileti bölümü işaret öğe.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name İleti bölümü ve ileti bölümü işaret öğesinin adı için değer.|  
|`Namespace`|İleti bölümü işaret öğesinin ad alanı.|  
|`Index`|Dizini `wsdl:message` / `wsdl:part` ileti.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:message` bu ileti bölümü tanımı. İlkenin belirli bir ileti bölümü işaret edecek şekilde parametreli.|  
|`MessageType`|İleti bölümü işaret öğesi XML Şeması türü.|  
  
#### <a name="message-headers"></a>İleti üstbilgileri  
 A `MessageHeaderDescription` örneği de eşleyen bir ileti parçası olan bir `soap:header` ileti bölümü için bağlama.  
  
### <a name="faults"></a>Hataları  
 A `FaultDescription` örneği eşlendiğini bir `wsdl:portType` / `wsdl:operation` / `wsdl:fault` tanımı ve onun ilişkili `wsdl:message` tanımı. `wsdl:message` İlişkili WSDL bağlantı noktası türünü aynı hedef ad alanına eklenir. `wsdl:message` Sahip noktalarını karşılık gelen XML Schema öğesi için "ayrıntı" adlı bir tek ileti bölümü `DefaultType` için özellik değeri `FaultDescription` örneği.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Arızanın değeri.|  
|`Namespace`|Hata ayrıntı iletisi bölümü işaret XML Şeması öğesinin ad alanı.|  
|`Action`|Hataya SOAP veya WS adresleme eylem.|  
|`ProtectionLevel`|Güvenlik İlkesi'nde koruma onaylar iliştirilmiş `wsdl:message` bu hata için tanımı.|  
|`DetailType`|Ayrıntılı ileti bölümü işaret öğesi XML Şeması türü.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Türetilen için kullanılan `wsdl:message` /@name hata iletisi için değer.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description>
