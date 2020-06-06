---
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855384"
---
# <a name="endpoint-element"></a>\<endpoint> öğesi
Hizmetleri açığa çıkarmak için kullanılan bir hizmet uç noktası için bağlama, anlaşma ve adres özelliklerini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|adres|Bitiş noktasının adresini içeren bir dize. Adres mutlak veya göreli bir adres olarak belirtilebilir. Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım şemasına uygun bir temel adres sağlaması beklenir. Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.<br /><br /> Varsayılan değer boş bir dizedir.|  
|behaviorConfiguration|Uç noktada kullanılacak davranışın adını içeren bir dize.|  
|bağlama|Kullanılacak bağlamanın türünü belirten gerekli dize özniteliği. Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır. Tür, bağlamanın tür adı değil, Bölüm adı tarafından kaydedilir.|  
|bindingConfiguration|Uç nokta örneği oluşturulurken kullanılacak bağlamanın bağlama adını belirten bir dize. Bağlama adı, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır. Varsayılan değer boş bir dizedir.<br /><br /> Bu öznitelik, `binding` yapılandırma dosyasındaki belirli bir bağlama yapılandırmasına başvurmak için ile birlikte kullanılır. Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın. Aksi takdirde, bir özel durum oluşabilir.|  
|bindingName|WSDL ile tanım dışarı aktarma için bağlamanın benzersiz nitelenmiş adını belirten bir dize. Varsayılan değer boş bir dizedir.|  
|bindingNamespace|WSDL ile tanım dışarı aktarma için bağlama ad alanının nitelenmiş adını belirten bir dize. Varsayılan değer boş bir dizedir.|  
|Sözleşmesi|Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize. Derlemenin anlaşma türünü uygulaması gerekir. Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir. Varsayılan değer boş bir dizedir.|  
|endpointConfiguration|`kind`Bu standart uç noktanın ek yapılandırma bilgilerine başvuran özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize. Bölümünde aynı ad tanımlanmalıdır `<standardEndpoints>` .|  
|isSystemEndpoint|Bir uç noktanın altyapı uç noktası olup olmadığını belirten bir Boolean değer.|  
|denetlenmesi|Uygulanan standart bitiş noktası türünü belirten bir dize. Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse ortak bir hizmet uç noktası oluşturulur.|  
|listenUriMode|Taşımanın `ListenUri` hizmetin dinlemesi için belirtilen şekilde nasıl davrandığını belirtir. Geçerli değerler şunlardır<br /><br /> -Explicit<br />-Benzersiz<br /><br /> Varsayılan değer açıktır.|  
|Öğesini|Hizmet uç noktasının dinlediği URI 'yi belirten bir dize. Varsayılan değer boş bir dizedir.|  
|name|İsteğe bağlı öznitelik. Hizmet uç noktasının adını belirten bir dize. Varsayılan değer, bağlama adı ve anlaşma açıklaması adının bitiştirilmesi olur. Hizmetlerin birden fazla uç noktası olabilir, bu nedenle uç noktanın `name` özniteliği hizmetin adından farklıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Adres üst bilgileri koleksiyonu.|  
|[\<identity>](identity.md)|Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<service>](service.md)|Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.|  
  
## <a name="example"></a>Örnek  
 Bu, hizmet uç noktası yapılandırmasına bir örnektir.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
