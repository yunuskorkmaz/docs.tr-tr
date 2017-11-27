---
title: IReferenceIdentity Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceIdentity
helpviewer_keywords: IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35c6152836adf02d541bacd149ed9ac053765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity Arabirimi
Bir kod nesnesinin benzersiz imza başvuru temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Arabirim işaretçisi yeni bir alır `IReferenceIdentity` için aynı olan örneği `IReferenceIdentity`, belirtilen öznitelik değişikliklerini dışında.|  
|`IReferenceIdentity::EnumAttributes`|Bir arabirim işaretçisi alır bir `IEnumIDENTITY_ATTRIBUTE` bu ile ilişkili öznitelikleri içeren örneği `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Belirtilen ada sahip belirtilen ad alanında özniteliğinin değerini alır.|  
|`IReferenceIdentity::SetAttribute`|Belirtilen ad ve belirtilen değeri belirtilen ada sahip öznitelik ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Ienumıdentıty_attrıbute arabirimi](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
