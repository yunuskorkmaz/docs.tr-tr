---
title: '&lt;baseAddresses&gt; &lt;eklemesi&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 31edf570a7374a4b4fe31760d35ec196ecfcb3c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553574"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a>&lt;baseAddresses&gt; &lt;eklemesi&gt;
Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten bir yapılandırma öğesini temsil eder.  
  
 \<system.ServiceModel>  
\<İstemci >  
\<uç noktası >  
\<konak >  
\<baseAddresses >  
\<baseAddress >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`baseAddress`|Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Bir koleksiyonu `baseAddress` öğeleri.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [Barındırma](../../../../../docs/framework/wcf/feature-details/hosting.md)
