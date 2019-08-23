---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926417"
---
# <a name="baseaddresses"></a>\<baseAddresses >
Şirket içinde barındırılan bir `baseAddress` ortamdaki hizmet ana bilgisayarı için temel adres olan bir öğe koleksiyonunu temsil eder. Bir temel adres varsa, uç noktalar temel adrese göre adreslerle yapılandırılabilir.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç nokta >  
\<Ana bilgisayar >  
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
|[\<> Ekle](add-of-baseaddresses.md)|Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesi.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ana bilgisayar >](host.md)|Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [Barındırma](../../../wcf/feature-details/hosting.md)
