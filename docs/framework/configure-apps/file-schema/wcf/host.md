---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 8a8f9db96281d8d775ff5c2923018228b3a9c1e5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269035"
---
# <a name="host"></a>\<konak >
Hizmet konak makinesi ayarlarını belirler.  
  
 \<system.ServiceModel>  
\<Hizmetleri >  
\<Hizmet >  
\<konak >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Bir koleksiyonu `baseAddress` hizmet ana bilgisayarı tarafından kullanılan tabanı belirten öğeleri.|  
|[\<zaman aşımı >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Hizmet >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
