---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: eedf0ce6cf75b8fb56daf98f2005e66162ce10d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155661"
---
# <a name="usemanagedpresentation"></a>\<useManagedPresentation >
CardSpace güvenlik belirteci WS-Trust öğesinin CardSpace profilini destekleyen hizmeti ile iletişim kurmak için kullanılan bir bağlama öğesi. Bu öğe yok özniteliği var ve boş bir anahtar vardır.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<useManagedPresentation >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, WS-Trust öğesinin CardSpace profilini destekleyen olgu, ilkede ifade etmek için bir kimlik sağlayıcısı tarafından kullanılır. Bu tür bir ilke onaylama yayımlama kimlik sağlayıcıları, CardSpace profilini temel alan sorunu belirteçleri görüyor olmalısınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
