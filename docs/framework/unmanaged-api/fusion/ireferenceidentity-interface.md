---
title: IReferenceIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796361"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity Arabirimi
Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Belirtilen öznitelik değişiklikleri dışında, bu `IReferenceIdentity` `IReferenceIdentity`ile özdeş olan yeni bir örneğe bir arabirim işaretçisi alır.|  
|`IReferenceIdentity::EnumAttributes`|`IEnumIDENTITY_ATTRIBUTE` Bu`IReferenceIdentity`ile ilişkili öznitelikleri içeren bir örneğe bir arabirim işaretçisi alır.|  
|`IReferenceIdentity::GetAttribute`|Belirtilen ad alanındaki özniteliğin değerini belirtilen adla alır.|  
|`IReferenceIdentity::SetAttribute`|Belirtilen ad alanına ve belirtilen ada sahip olan özniteliği belirtilen değere ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE Arabirimi](ienumidentity-attribute-interface.md)
