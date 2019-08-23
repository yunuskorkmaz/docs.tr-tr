---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 13c9400874f1e02fac3ce0c3010153ad7806288c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915184"
---
# <a name="wsdlimporter"></a>\<Wsdlıter >
WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.  
  
\<system.ServiceModel>  
\<İstemci >  
\<meta veri >  
\<wsdlImporters >  
\<Wsdlıter >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`type`|Bu öğenin türü.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<wsdlImporters >](wsdlimporters.md)|WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır. İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz. Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [WCF İstemci Yapılandırması](../../../wcf/feature-details/client-configuration.md)
- [İstemciler](../../../wcf/feature-details/clients.md)
