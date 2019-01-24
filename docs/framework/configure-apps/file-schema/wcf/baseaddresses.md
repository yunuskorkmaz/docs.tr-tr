---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 34d400e74b24e9eb4140d1b43597b0217b23d80c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730132"
---
# <a name="ltbaseaddressesgt"></a>&lt;BaseAddresses&gt;
Bir koleksiyonunu temsil eder `baseAddress` kendiliğinden konak ortamdaki hizmet konak için temel adres olan öğeler. Temel adres varsa, uç noktaları, adresler taban adresi göre ile yapılandırılabilir.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
\<konak >  
\<baseAddresses >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
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
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<konak >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
