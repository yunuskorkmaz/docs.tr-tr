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
ms.openlocfilehash: 1e6c42d8e74d2d3e7925c657c67832f662416e64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673879"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId Arabirimi

Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Bu nesnedeki kodu temsil eden biçimli bir dize alır `IDefinitionAppId` .|  
|`IDefinitionAppId::put_Codebase`|Bu `IDefinitionAppId` nesnenin kodunu belirtilen biçimli dize değerine ayarlar.|  
|`IDefinitionAppId::EnumAppPath`|Geçerli uygulama yolundaki derlemeleri içeren bir [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.|  
|`IDefinitionAppId::SetAppPath`|Geçerli kapsamdaki derleme için uygulama yolunu, belirtilen [IDefinitionIdentity](idefinitionidentity-interface.md) nesnesinin başvurduğu değere ayarlar.|  
|`IDefinitionAppId::get_SubscriptionId`|Bu nesne için bir abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IDefinitionAppId` .|  
|`IDefinitionAppId::put_SubscriptionId`|Bu nesne için bir aboneliğin Belirteç tanımlayıcısını `IDefinitionAppId` belirtilen dize değerine ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
