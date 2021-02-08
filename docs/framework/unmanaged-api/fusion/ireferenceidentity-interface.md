---
description: 'Daha fazla bilgi edinin: IReferenceIdentity Arabirimi'
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
ms.openlocfilehash: a29aaa1f4fb928c136af4168619d27900537c779
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800051"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity Arabirimi

Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|`IReferenceIdentity` `IReferenceIdentity` Belirtilen öznitelik değişiklikleri dışında, bu ile özdeş olan yeni bir örneğe bir arabirim işaretçisi alır.|  
|`IReferenceIdentity::EnumAttributes`|`IEnumIDENTITY_ATTRIBUTE`Bu ile ilişkili öznitelikleri içeren bir örneğe bir arabirim işaretçisi alır `IReferenceIdentity` .|  
|`IReferenceIdentity::GetAttribute`|Belirtilen ad alanındaki özniteliğin değerini belirtilen adla alır.|  
|`IReferenceIdentity::SetAttribute`|Belirtilen ad alanına ve belirtilen ada sahip olan özniteliği belirtilen değere ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE Arabirimi](ienumidentity-attribute-interface.md)
