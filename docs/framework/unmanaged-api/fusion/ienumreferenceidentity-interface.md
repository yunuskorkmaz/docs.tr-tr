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
ms.openlocfilehash: 1305b9ebe3cd87ba002ee87610ff309d015a44e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131741"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity Arabirimi
`IReferenceIdentity` nesnelerinin bir koleksiyonu için bir Numaralandırıcı işlevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Bu `IEnumReferenceIdentity`aynı üyeleri içeren yeni bir `IEnumReferenceIdentity` yönelik bir arabirim işaretçisi alır.|  
|`IEnumReferenceIdentity::Next`|Geçerli konumdan başlayarak belirtilen sayıda `IReferenceIdentity` nesnesini alır.|  
|`IEnumReferenceIdentity::Reset`|Yönerge işaretçisini bu `IEnumReferenceIdentity`başına kaydırır.|  
|`IEnumReferenceIdentity::Skip`|Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IReferenceIdentity Arabirimi](ireferenceidentity-interface.md)
