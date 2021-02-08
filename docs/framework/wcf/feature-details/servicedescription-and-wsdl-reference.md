---
description: 'Daha fazla bilgi edinin: ServiceDescription ve WSDL başvurusu'
title: ServiceDescription ve WSDL Başvurusu
ms.date: 03/30/2017
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
ms.openlocfilehash: 0ce3dc49d71eda1f9fe36940f153735b43be917b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793525"
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription ve WSDL Başvurusu

Bu konuda, Windows Communication Foundation (WCF) tarafından Web Hizmetleri Açıklama Dili (WSDL) belgelerinin örneklere ve örneklerinden nasıl eşlendiği açıklanmaktadır <xref:System.ServiceModel.Description.ServiceDescription> .  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>ServiceDescription, WSDL 1,1 ile nasıl eşlenir  

 Service için bir örnekten WSDL belgelerini dışarı aktarmak için WCF kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceDescription> . Meta veri uç noktalarını yayımladığınızda hizmetiniz için WSDL belgeleri otomatik olarak oluşturulur.  
  
 Ayrıca, <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Channels.Binding> türü kullanarak WSDL belgelerinden örnekleri, örnekleri ve örnekleri içeri aktarabilirsiniz `WsdlImporter` .  
  
 WCF tarafından dışarı aktarılan WSDL belgeleri, dış XML şeması belgelerinden kullanılan tüm XML şema tanımlarını içeri aktarır. Veri türlerinin hizmette kullanması için her bir hedef ad alanı için ayrı bir XML şeması belgesi verilir. Benzer şekilde, hizmet sözleşmelerinin kullanacağı her bir hedef ad alanı için ayrı bir WSDL belgesi verilir.  
  
### <a name="servicedescription"></a>ServiceDescription  

 Bir <xref:System.ServiceModel.Description.ServiceDescription> örnek bir öğesiyle eşlenir `wsdl:service` . Bir <xref:System.ServiceModel.Description.ServiceDescription> örnek, <xref:System.ServiceModel.Description.ServiceEndpoint> her biri ayrı ayrı öğelerle eşlenen örneklerin bir koleksiyonunu içerir `wsdl:port` .  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Hizmetin değeri.|  
|`Namespace`|Hizmetin tanımı için targetNamespace `wsdl:service` .|  
|`Endpoints`|`wsdl:port`Hizmetin tanımları.|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  

 Bir <xref:System.ServiceModel.Description.ServiceEndpoint> örnek bir öğesiyle eşlenir `wsdl:port` . Bir <xref:System.ServiceModel.Description.ServiceEndpoint> örnek, bir adres, bağlama ve bir sözleşme içerir.  
  
 Arabirimini uygulayan uç nokta davranışları <xref:System.ServiceModel.Description.IWsdlExportExtension> , `wsdl:port` ekli oldukları uç nokta için öğesini değiştirebilir.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|Uç nokta `wsdl:port` /@name `wsdl:binding` /@name bağlaması için değer ve değer.|  
|`Address`|`wsdl:port`Uç nokta tanımının adresi.<br /><br /> Uç nokta için taşıma, adresin biçimini belirler. Örneğin, WCF destekli aktarımlar için bir SOAP adresi veya bir uç nokta başvurusu olabilir.|  
|`Binding`|`wsdl:binding`Uç nokta tanımı.<br /><br /> `wsdl:binding`Tanımlardan farklı olarak, WCF 'deki bağlamalar herhangi bir sözleşmeye bağlı değildir.|  
|`Contract`|`wsdl:portType`Uç nokta tanımı.|  
|`Behaviors`|Arabirimini uygulayan uç nokta davranışları <xref:System.ServiceModel.Description.IWsdlExportExtension> , `wsdl:port` uç nokta için öğesini değiştirebilir.|  
  
### <a name="bindings"></a>Bağlamalar  

 Bir örnek için bağlama örneği `ServiceEndpoint` bir `wsdl:binding` tanıma eşlenir. `wsdl:binding`Belirli bir tanım ile ilişkilendirilmesi gereken tanımlardan farklı olarak `wsdl:portType` , WCF bağlamaları herhangi bir anlaşmada bağımsızdır.  
  
 Bağlama, bağlama öğeleri koleksiyonundan oluşur. Her öğe, uç noktanın istemcilerle nasıl iletişim kuracağını açıklar. Ayrıca, bir bağlama <xref:System.ServiceModel.Channels.MessageVersion> , <xref:System.ServiceModel.EnvelopeVersion> <xref:System.ServiceModel.Channels.AddressingVersion> uç nokta için ve belirtir.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|Bir uç noktanın varsayılan adında kullanılır, bu, anlaşma adı bir alt çizgiyle ayrılmış olan bağlama adıdır.|  
|`Namespace`|`targetNamespace` `wsdl:binding` Tanımı için.<br /><br /> İçeri aktarma işleminde, WSDL bağlantı noktasına bir ilke eklenmişse, içeri aktarılan bağlama ad alanı tanım için ile eşlenir `targetNamespace` `wsdl:port` .|  
|`BindingElementCollection`, `CreateBindingElements` () yöntemi tarafından döndürülen|Tanıma yönelik çeşitli etki alanına özgü uzantılar `wsdl:binding` , genellikle ilke onaylamaları.|  
|`MessageVersion`|`EnvelopeVersion` `AddressingVersion` Uç nokta için ve.<br /><br /> Belirtildiğinde `MessageVersion.None` , WSDL bağlaması BIR SOAP bağlaması içermez ve wsdl bağlantı noktası WS-Addressing içerik içermez. Bu ayar genellikle düz eski XML (POX) uç noktaları için kullanılır.|  
  
#### <a name="bindingelements"></a>BindingElements  

 Bir uç nokta bağlamasının bağlama öğeleri, ' de ilke onayları gibi çeşitli WSDL uzantılarına eşlenir `wsdl:binding` .  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement>Bağlama için, BIR SOAP bağlamasının aktarım Tekdüzen Kaynak tanımlayıcısı 'nı (URI) belirler.  
  
#### <a name="addressingversion"></a>AddressingVersion  

 `AddressingVersion`Bağlamadaki ' de kullanılan adresleme sürümüyle eşlenir `wsd:port` . WCF, SOAP 1,1 ve SOAP 1,2 adreslerini ve WS-Addressing 08/2004 ve WS-Addressing 1,0 uç nokta başvurularını destekler.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  

 `EnvelopeVersion`Bir bağlamadaki ' de kullanılan soap sürümüyle eşlenir `wsdl:binding` . WCF, SOAP 1,1 ve SOAP 1,2 bağlamalarını destekler.  
  
### <a name="contracts"></a>Sözleşmeler  

 <xref:System.ServiceModel.Description.ContractDescription>Bir örneğin örneği `ServiceEndpoint` bir ile eşlenir `wsdl:portType` . Bir `ContractDescription` örnek, belirli bir sözleşme için tüm işlemleri açıklar.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Sözleşmenin değeri.|  
|`Namespace`|Tanım için targetNamespace `wsdl:portType` .|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Sözleşmenin değeri. Bu öznitelik, WSDL 1,1 için bir WCF uzantısıdır.|  
|`Operations`|`wsdl:operation`Sözleşmenin tanımları.|  
  
### <a name="operations"></a>Operations  

 Bir <xref:System.ServiceModel.Description.OperationDescription> örnek bir ile eşlenir `wsdl:portType` / `wsdl:operation` . `OperationDescription` `MessageDescription` , İşlemin iletilerini tanımlayan örneklerin bir koleksiyonunu içerir.  
  
 İki işlem davranışı `OperationDescription` , BIR WSDL belgesine nasıl eşlendiğine çok fazla katılır: `DataContractSerializerOperationBehavior` ve `XmlSerializerOperationBehavior` .  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name İşlemin değeri.|  
|`ProtectionLevel`|Güvenlik ilkesinde `wsdl:binding/wsdl:operation` Bu işleme yönelik iletilere eklenen koruma onayları.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating İşlemin değeri. Bu öznitelik, WSDL 1,1 için bir WCF uzantısıdır.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating İşlemin değeri. Bu öznitelik, WSDL 1,1 için bir WCF uzantısıdır.|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input` `wsdl:portType` / `wsdl:operation` / `wsdl:output` İşlem için ve iletileri.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` İşlemin tanımları.|  
|`Behaviors`|`DataContractSerializerOperationBehavior`Ve `XmlSerializerOperationBehavior` işlem bağlamayı ve işlem iletilerini ele.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  

 `DataContractSerializerOperationBehavior`İşlem için, `IWsdlExportExtension` WSDL iletilerini ve bu işlem için bağlamayı dışarı aktaran bir uygulamasıdır. XML şeması türleri kullanılarak verilir `XsdDataContractExporter` . `DataContractSerializerOperationBehavior`Ayrıca, bu işlem için kullanılacak kullanımı, stili ve şema Dışarı Aktarıcı 'yı ve alma işlemini belirler.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style`Bu özniteliğin özelliği, `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style işlem için olan değere eşlenir.<br /><br /> , `DataContractSerializerOperationBehavior` WSDL 'de şema türlerinin yalnızca sabit kullanımını destekler.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  

 `XmlSerializerOperationBehavior`İşlem için, `IWsdlExportExtension` WSDL iletilerini ve bu işlem için bağlamayı dışarı aktaran bir uygulamasıdır. XML şeması türleri kullanılarak verilir `XmlSchemaExporter` . `XmlSerializerOperationBehavior`Ayrıca, bu işlem için kullanılacak kullanımı, stili ve şema Dışarı Aktarıcı 'yı ve alma işlemini belirler.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style`Bu özniteliğin özelliği, `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style işlem için olan değere eşlenir.<br /><br /> `Use`Bu özniteliğin özelliği, `wsdl:binding` / `wsdl:operation` / `soap:operation` /@use işlemdeki tüm iletiler için/* değerleriyle eşlenir.|  
  
### <a name="messages"></a>İletiler  

 Bir `MessageDescription` `wsdl:message` `wsdl:portType` / `wsdl:operation` / `wsdl:input` işlemde bir veya `wsdl:portType` / `wsdl:operation` / `wsdl:output` ileti tarafından başvurulan bir örnek ile eşlenir. A `MessageDescription` 'nın gövdesi ve başlıkları vardır.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Action`|İleti için SOAP veya WS-Addressing eylemi.<br /><br /> "*" Eylem dizesini kullanan işlemlerin WSDL içinde temsil edilmediğini unutmayın.|  
|`Direction`|`MessageDirection.Input` ile eşlenir `wsdl:input` .<br /><br /> `MessageDirection.Output` ile eşlenir `wsdl:output` .|  
|`ProtectionLevel`|Güvenlik ilkesinde bu iletinin tanımına bağlı koruma onayları `wsdl:message` .|  
|`Body`|İleti için ileti gövdesi.|  
|`Headers`|İleti için üst bilgiler.|  
|`ContractDescription.Name`, `OperationContract.Name`|Dışarı aktarma sırasında değeri türetmek için kullanılır `wsdl:message` /@name .|  
  
#### <a name="message-body"></a>İleti gövdesi  

 Bir `MessageBodyDescription` örnek, `wsdl:message` / `wsdl:part` ileti gövdesinin tanımına eşlenir. İleti gövdesi kaydırılmış veya çıplak olabilir.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`WrapperName`|Stil RPC değilse, `WrapperName` ile başvurulan öğe adıyla eşlenir ve `wsdl:message` / `wsdl:part` @name "Parameters" olarak ayarlanır.|  
|`WrapperNamespace`|Stil RPC değilse, için `WrapperNamespace` öğesi için öğe ad alanıyla eşlenir ve `wsdl:message` / `wsdl:part` @name "Parameters" olarak ayarlanır.|  
|`Parts`|Bu ileti gövdesinin ileti bölümleri.|  
|`ReturnValue`|Sarmalayıcı öğesi varsa sarmalayıcı öğesinin alt öğesi (belge sarmalanmış stili veya RPC stili), aksi takdirde `wsdl:message` / `wsdl:part` ileti içinde ilk.|  
  
#### <a name="message-parts"></a>İleti parçaları  

 Bir `MessagePartDescription` örnek bir ve bir `wsdl:message` / `wsdl:part` XML şeması türü ya da ileti bölümünün gösterdiği öğesiyle eşlenir.  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|İleti bölümünün `wsd:message` / `wsdl:part` /@name değeri ve ileti bölümünün gösterdiği öğenin adı.|  
|`Namespace`|İleti bölümünün işaret ettiği öğenin ad alanı.|  
|`Index`|`wsdl:message` / `wsdl:part` İletinin dizini.|  
|`ProtectionLevel`|Güvenlik ilkesinde `wsdl:message` Bu ileti bölümünün tanımına eklenen koruma onayları. İlke, belirli bir ileti parçasını işaret etmek üzere parametreleştirilenir.|  
|`MessageType`|İleti bölümünün gösterdiği öğenin XML şeması türü.|  
  
#### <a name="message-headers"></a>İleti üstbilgileri  

 `MessageHeaderDescription`Örnek, `soap:header` ileti bölümü için bağlamaya de eşlenen bir ileti bölümüdür.  
  
### <a name="faults"></a>Hatalar  

 Bir `FaultDescription` örnek, `wsdl:portType` / `wsdl:operation` / `wsdl:fault` tanımıyla ve ilişkili `wsdl:message` tanımıyla eşlenir. , `wsdl:message` ILIŞKILI wsdl bağlantı noktası türüyle aynı hedef ad alanına eklenir. , `wsdl:message` `DefaultType` Örneği için özellik değerine KARŞıLıK gelen XML şema öğesini işaret eden "Detail" adlı tek bir ileti bölümüne sahiptir `FaultDescription` .  
  
|Özellikler|WSDL eşleme|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Hata için değer.|  
|`Namespace`|Hata ayrıntısı ileti bölümünün gösterdiği XML şeması öğesinin ad alanı.|  
|`Action`|Hata için SOAP veya WS-Addressing eylemi.|  
|`ProtectionLevel`|Güvenlik ilkesinde bu hatanın tanımına bağlı koruma onayları `wsdl:message` .|  
|`DetailType`|Ayrıntı iletisi bölümünün gösterdiği öğenin XML şeması türü.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|`wsdl:message` /@name Hata iletisi için değeri türetmek için kullanılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description>
