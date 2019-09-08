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
ms.openlocfilehash: 929909a7f2c4fa1799c8fed94787b8f853c7eac2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796514"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId Arabirimi
Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Bu `IDefinitionAppId` nesnedeki kodu temsil eden biçimli bir dize alır.|  
|`IDefinitionAppId::put_Codebase`|Bu `IDefinitionAppId` nesnenin kodunu belirtilen biçimli dize değerine ayarlar.|  
|`IDefinitionAppId::EnumAppPath`|Geçerli uygulama yolundaki derlemeleri içeren bir [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.|  
|`IDefinitionAppId::SetAppPath`|Geçerli kapsamdaki derleme için uygulama yolunu, belirtilen [IDefinitionIdentity](idefinitionidentity-interface.md) nesnesinin başvurduğu değere ayarlar.|  
|`IDefinitionAppId::get_SubscriptionId`|Bu `IDefinitionAppId` nesne için bir abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.|  
|`IDefinitionAppId::put_SubscriptionId`|Bu `IDefinitionAppId` nesne için bir aboneliğin Belirteç tanımlayıcısını belirtilen dize değerine ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
