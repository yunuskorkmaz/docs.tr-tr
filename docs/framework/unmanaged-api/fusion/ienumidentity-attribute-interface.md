---
title: IEnumIDENTITY_ATTRIBUTE Arabirimi
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: 71a6ea9f593da093985a4420e690f1bdd7f9d139
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728998"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE Arabirimi

Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir Numaralandırıcı işlevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|İle aynı üyeleri içeren yeni bir arabirim işaretçisi alır `IEnumIDENTITY_ATTRIBUTE` `IEnumIDENTITY_ATTRIBUTE` .|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Bu öğelerin içerdiği verileri `IEnumIDENTITY_ATTRIBUTE` belirtilen veri arabelleğine yazar.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Geçerli konumdan başlayarak belirtilen sayıda öznitelik alır.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumIDENTITY_ATTRIBUTE` .|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
