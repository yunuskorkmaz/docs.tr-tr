---
title: IEnumReferenceIdentity Arabirimi
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
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d1af31c72770947c33f358a9689bac6fd95ef53c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity Arabirimi
Bir koleksiyonu için bir numaralandırıcı görevi gören `IReferenceIdentity` nesneleri.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Arabirim işaretçisi yeni bir alır `IEnumReferenceIdentity` bu aynı üyeleri içeren `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Belirtilen sayıda alır `IReferenceIdentity` geçerli konumdan başlayarak nesneleri.|  
|`IEnumReferenceIdentity::Reset`|Yönerge işaretçisi başlangıcına bu taşır `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Öğeler, geçerli konumdan başlayarak belirtilen sayıda tarafından yönerge işaretçisi İleri taşınır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IReferenceIdentity Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
