---
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855384"
---
# <a name="endpoint-element"></a>\<uç nokta > öğesi
Hizmetleri açığa çıkarmak için kullanılan bir hizmet uç noktası için bağlama, anlaşma ve adres özelliklerini belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<hizmet >** ](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<uç nokta >**  
  
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
|bindingConfiguration|Uç nokta örneği oluşturulurken kullanılacak bağlamanın bağlama adını belirten bir dize. Bağlama adı, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır. Varsayılan değer boş bir dizedir.<br /><br /> Bu öznitelik, yapılandırma dosyasındaki belirli bir `binding` bağlama yapılandırmasına başvurmak için ile birlikte kullanılır. Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın. Aksi takdirde, bir özel durum oluşabilir.|  
|bindingName|WSDL ile tanım dışarı aktarma için bağlamanın benzersiz nitelenmiş adını belirten bir dize. Varsayılan değer boş bir dizedir.|  
|bindingNamespace|WSDL ile tanım dışarı aktarma için bağlama ad alanının nitelenmiş adını belirten bir dize. Varsayılan değer boş bir dizedir.|  
|contract|Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize. Derlemenin anlaşma türünü uygulaması gerekir. Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir. Varsayılan değer boş bir dizedir.|  
|endpointConfiguration|Bu standart uç noktanın ek yapılandırma bilgilerine başvuran `kind` özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize. `<standardEndpoints>` Bölümünde aynı ad tanımlanmalıdır.|  
|isSystemEndpoint|Bir uç noktanın altyapı uç noktası olup olmadığını belirten bir Boolean değer.|  
|kind|Uygulanan standart bitiş noktası türünü belirten bir dize. Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse ortak bir hizmet uç noktası oluşturulur.|  
|listenUriMode|Taşımanın hizmetin dinlemesi için `ListenUri` belirtilen şekilde nasıl davrandığını belirtir. Geçerli değerler şunlardır<br /><br /> -Explicit<br />-Benzersiz<br /><br /> Varsayılan değer açıktır.|  
|Öğesini|Hizmet uç noktasının dinlediği URI 'yi belirten bir dize. Varsayılan değer boş bir dizedir.|  
|name|İsteğe bağlı öznitelik. Hizmet uç noktasının adını belirten bir dize. Varsayılan değer, bağlama adı ve anlaşma açıklaması adının bitiştirilmesi olur. Hizmetlerin birden fazla uç noktası olabilir, bu nedenle uç `name` noktanın özniteliği hizmetin adından farklıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<üst bilgiler >](headers.md)|Adres üst bilgileri koleksiyonu.|  
|[\<kimlik >](identity.md)|Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<hizmet >](service.md)|Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.|  
  
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
- [Noktalarının Adresler, bağlamalar ve sözleşmeler](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Nasıl yapılır: Yapılandırmada bir hizmet uç noktası oluşturma](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
