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
ms.openlocfilehash: 7e6bc57fb470a5c12549bb5f9445ecf1551425a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107836"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE Arabirimi
Geçerli kapsamdaki kod nesnesinin öznitelikleri için bir Numaralandırıcı işlevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Bu `IEnumIDENTITY_ATTRIBUTE`aynı üyeleri içeren yeni bir `IEnumIDENTITY_ATTRIBUTE` yönelik bir arabirim işaretçisi alır.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Bu `IEnumIDENTITY_ATTRIBUTE` öğelerinde içerilen verileri belirtilen veri arabelleğine yazar.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Geçerli konumdan başlayarak belirtilen sayıda öznitelik alır.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Yönerge işaretçisini bu `IEnumIDENTITY_ATTRIBUTE`başına kaydırır.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
