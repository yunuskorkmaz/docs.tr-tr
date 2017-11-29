---
title: IEnumReferenceIdentity Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Fusion arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Ireferenceıdentity arabirimi](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
