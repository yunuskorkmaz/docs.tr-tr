---
title: IDefinitionAppId Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 247edbe300bbb93ddbdd4260109999fd33b08006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId Arabirimi
Uygulama geçerli kapsamda tanımlar kodu için benzersiz bir tanımlayıcıyı temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Bu kodda temsil eden biçimlendirilmiş bir dize alır `IDefinitionAppId` nesnesi.|  
|`IDefinitionAppId::put_Codebase`|Bu kod ayarlar `IDefinitionAppId` belirtilen nesneye biçimlendirilmiş bir dize değeri.|  
|`IDefinitionAppId::EnumAppPath`|Bir arabirim işaretçisi alır bir [Ienumdefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) geçerli uygulama yolu derlemelerde içeren nesne.|  
|`IDefinitionAppId::SetAppPath`|Uygulama yolu, belirtilen tarafından başvurulan değer için geçerli kapsamdaki derleme için ayarlar [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) nesnesi.|  
|`IDefinitionAppId::get_SubscriptionId`|Bu abonelik için bir işaretçi belirteç tanımlayıcı bir dize gösterimini alır `IDefinitionAppId` nesnesi.|  
|`IDefinitionAppId::put_SubscriptionId`|Bir abonelik için belirteç tanımlayıcı için ayarlar `IDefinitionAppId` nesne için belirtilen dize değeri.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
