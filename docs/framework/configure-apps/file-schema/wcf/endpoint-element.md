---
title: "&lt;uç noktası&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7175cf55df6bb735367effa8f806a472b9ce5ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointgt-element"></a>&lt;uç noktası&gt; öğesi
Bağlama, sözleşme ve Hizmetleri kullanıma sunmak için kullanılan bir hizmet uç noktası adresi özelliklerini belirtir.  
  
 \<Sistem. ServiceModel >  
\<Hizmet >  
\<uç noktası >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Uç nokta adresi içeren bir dize. Adres mutlak veya göreli adresi olarak belirtilebilir. Göreli bir adresi sağlanırsa, konak bağlama kullanılan aktarma düzeni için uygun bir taban adresi sağlaması beklenir. Bir adresi yapılandırılmamışsa, taban adresi Bu uç nokta adresi olduğu varsayılır.<br /><br /> Varsayılan boş bir dizedir.|  
|behaviorConfiguration|Uç kullanılacak davranış adını içeren dize.|  
|bağlama|Kullanılacak bağlama türünü belirten dize özniteliği gerekli. Tür başvuru için kayıtlı yapılandırma bölümü içermelidir. Kayıtlı bölüm adı yerine bağlama türü adını türüdür.|  
|bindingConfiguration|Uç nokta örneği oluşturulduğunda kullanılacak bağlama bağlama adını belirten dize. Bağlama adı uç noktaları kapsamında olması gerekir. Varsayılan boş bir dizedir.<br /><br /> Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki özel bağlama yapılandırma başvurmak için. Özel bağlama kullanmaya çalıştığınız gerekiyorsa, bu öznitelik ayarlanır. Aksi halde, bir özel durum.|  
|bindingName|WSDL aracılığıyla tanımı dışa aktarma için bağlama benzersiz tam adını belirten dize. Varsayılan boş bir dizedir.|  
|bindingNamespace|Ad alanı tanımı için bağlama tam adını belirten dize WSDL dışa aktarın. Varsayılan boş bir dizedir.|  
|Sözleşme|Bu uç noktaya sunduğu sözleşmeyi belirten bir dize. Derleme sözleşme türü uygulamalıdır. Bir hizmet uygulaması tek anlaşma türü uygularsa, bu özellik atlanabilir. Varsayılan boş bir dizedir.|  
|endpointConfiguration|Tarafından belirlenen standart uç noktanın adını belirten dize `kind` standart Bu uç noktanın ek yapılandırma bilgilerini başvuran özniteliği. Aynı adı tanımlanmalıdır `<standardEndpoints>` bölümü.|  
|isSystemEndpoint|Bir uç nokta bir altyapı uç noktası olup olmadığını belirten bir Boole değeri.|  
|türü|Standart uç nokta uygulanan türünü belirten bir dize. Türü kaydedilmelidir `<extensions>` bölüm veya machine.config dosyasındaki. Hiçbir şey belirtilirse, ortak bir hizmet uç noktası oluşturulur.|  
|listenUriMode|Taşıma nasıl işler belirtir `ListenUri` hizmetinin üzerinde dinleme sağlanan. Geçerli değerler:<br /><br /> -Açık<br />-Benzersiz<br /><br /> Explicit varsayılan değerdir.|  
|listenUri|Hizmet uç noktası dinleyen URI belirten bir dize. Varsayılan boş bir dizedir.|  
|name|İsteğe bağlı öznitelik. Hizmet uç noktası adını belirten dize. Bağlama ve sözleşme açıklama adı birleşimini varsayılan değerdir. Hizmetleri olabilir birden çok uç nokta, bu nedenle uç noktanın `name` özniteliktir hizmet adından farklı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üstbilgiler >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Adres üstbilgileri koleksiyonu.|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Hizmet >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar yapılandırma bölümü.|  
  
## <a name="example"></a>Örnek  
 Bu, bir hizmet uç noktası yapılandırması örneğidir.  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
