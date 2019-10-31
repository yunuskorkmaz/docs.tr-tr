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
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108209"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId Arabirimi
Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Bu `IDefinitionAppId` nesnesindeki kodu temsil eden biçimli bir dize alır.|  
|`IDefinitionAppId::put_Codebase`|Bu `IDefinitionAppId` nesnesinin kodunu belirtilen biçimli dize değerine ayarlar.|  
|`IDefinitionAppId::EnumAppPath`|Geçerli uygulama yolundaki derlemeleri içeren bir [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.|  
|`IDefinitionAppId::SetAppPath`|Geçerli kapsamdaki derleme için uygulama yolunu, belirtilen [IDefinitionIdentity](idefinitionidentity-interface.md) nesnesinin başvurduğu değere ayarlar.|  
|`IDefinitionAppId::get_SubscriptionId`|Bu `IDefinitionAppId` nesnesine bir abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.|  
|`IDefinitionAppId::put_SubscriptionId`|Bu `IDefinitionAppId` nesnesine yönelik bir aboneliğin Belirteç tanımlayıcısını belirtilen dize değerine ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
