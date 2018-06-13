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
ms.openlocfilehash: 2735355097a1f3f581b3a4bc74f08d8f2ebf3bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430386"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
