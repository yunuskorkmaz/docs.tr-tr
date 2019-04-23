---
title: IEnumReferenceIdentity Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 766b17bae0c58d9872ff9c118f330ebc3220257e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123493"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity Arabirimi
Bir koleksiyonu için bir numaralandırıcı görevi gören `IReferenceIdentity` nesneleri.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Yeni bir arabirim işaretçisi alır `IEnumReferenceIdentity` bu aynı üyeleri içeren `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Belirtilen sayıda alır `IReferenceIdentity` nesneleri, geçerli konumdan başlayarak.|  
|`IEnumReferenceIdentity::Reset`|Yönerge işaretçisini bu başlangıcına taşır `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Öğe, geçerli konumdan başlayarak belirtilen sayıda yönerge işaretçisini ileriye taşır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IReferenceIdentity Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
