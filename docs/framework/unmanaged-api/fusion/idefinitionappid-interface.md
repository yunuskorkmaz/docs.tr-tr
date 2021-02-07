---
description: 'Şu konuda daha fazla bilgi edinin: IDefinitionAppId arabirimi'
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
ms.openlocfilehash: 3c68044e7e747521e190fad404e89d6d0a994611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760673"
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
