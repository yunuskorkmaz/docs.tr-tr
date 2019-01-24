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
ms.openlocfilehash: bb8686342b20bd6afe0a4c4803d64428ed95c98b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665779"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity Arabirimi
Kod nesnesi benzersiz imzası bir başvuruyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Yeni bir arabirim işaretçisi alır `IReferenceIdentity` için aynı olan örneği `IReferenceIdentity`, belirtilen öznitelik değişiklikleri dışında.|  
|`IReferenceIdentity::EnumAttributes`|Bir arabirim işaretçisi alır bir `IEnumIDENTITY_ATTRIBUTE` bununla ilişkili öznitelikleri içeren örneğini `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Belirtilen ada sahip belirtilen ad alanı özniteliğinin değerini alır.|  
|`IReferenceIdentity::SetAttribute`|Belirtilen ad alanı ve belirtilen değere belirtilen ada sahip özniteliğini ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
