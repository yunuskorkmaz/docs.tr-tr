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
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796438"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity Arabirimi
Bir `IReferenceIdentity` nesne koleksiyonu için bir Numaralandırıcı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|İle aynı üyeleri `IEnumReferenceIdentity` `IEnumReferenceIdentity`içeren yeni bir arabirim işaretçisi alır.|  
|`IEnumReferenceIdentity::Next`|Geçerli konumdan başlayarak belirtilen sayıda `IReferenceIdentity` nesneyi alır.|  
|`IEnumReferenceIdentity::Reset`|Yönerge işaretçisini bunun `IEnumReferenceIdentity`başlangıcına taşıdır.|  
|`IEnumReferenceIdentity::Skip`|Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IReferenceIdentity Arabirimi](ireferenceidentity-interface.md)
