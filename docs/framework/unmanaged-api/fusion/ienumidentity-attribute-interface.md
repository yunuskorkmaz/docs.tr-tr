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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ae940946c56cbc858690cccce61597d0016e40c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571814"
---
# <a name="ienumidentityattribute-interface"></a>IEnumIDENTITY_ATTRIBUTE Arabirimi
Geçerli kapsam içinde kod nesnesinin öznitelikleri için bir numaralandırıcı olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Yeni bir arabirim işaretçisi alır `IEnumIDENTITY_ATTRIBUTE` bu aynı üyeleri içeren `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Bu öğe içinde yer alan verileri Yazar `IEnumIDENTITY_ATTRIBUTE` belirtilen veri arabelleği için.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Öznitelikler, geçerli konumdan başlayarak belirtilen sayıda alır.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Yönerge işaretçisini bu başlangıcına taşır `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Öğe, geçerli konumdan başlayarak belirtilen sayıda yönerge işaretçisini ileriye taşır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
