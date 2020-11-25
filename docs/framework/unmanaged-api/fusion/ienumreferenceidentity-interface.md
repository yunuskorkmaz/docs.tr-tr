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
ms.openlocfilehash: bea357fe9a154ffb8f69228c7332c026dc2759e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728983"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity Arabirimi

Bir nesne koleksiyonu için bir Numaralandırıcı görevi görür `IReferenceIdentity` .  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|İle aynı üyeleri içeren yeni bir arabirim işaretçisi alır `IEnumReferenceIdentity` `IEnumReferenceIdentity` .|  
|`IEnumReferenceIdentity::Next`|`IReferenceIdentity`Geçerli konumdan başlayarak belirtilen sayıda nesneyi alır.|  
|`IEnumReferenceIdentity::Reset`|Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumReferenceIdentity` .|  
|`IEnumReferenceIdentity::Skip`|Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IReferenceIdentity Arabirimi](ireferenceidentity-interface.md)
