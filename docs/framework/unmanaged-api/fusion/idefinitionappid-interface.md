---
title: IDefinitionAppId Arabirimi
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd705ef549de3a8018efe731ef8735ef7b6b915
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083185"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId Arabirimi
Uygulama geçerli kapsamda tanımlar kod için benzersiz bir tanımlayıcı temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Bu kod temsil eden bir biçimlendirilmiş dize alır `IDefinitionAppId` nesne.|  
|`IDefinitionAppId::put_Codebase`|Bu kod ayarlar `IDefinitionAppId` belirtilen nesneye biçimlendirilmiş dize değeri.|  
|`IDefinitionAppId::EnumAppPath`|Bir arabirim işaretçisi alır bir [Ienumdefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) geçerli uygulama yolu derlemeleri içeren nesne.|  
|`IDefinitionAppId::SetAppPath`|Uygulama yolu geçerli kapsamda belirtilen tarafından başvurulan değer derleme için ayarlar [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) nesne.|  
|`IDefinitionAppId::get_SubscriptionId`|Abonelik için bu belirteci tanımlayıcı bir dize gösterimini bir işaretçi alır `IDefinitionAppId` nesne.|  
|`IDefinitionAppId::put_SubscriptionId`|Bir abonelik için belirteç tanımlayıcısı için ayarlar `IDefinitionAppId` nesne belirtilen dize değeri.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
