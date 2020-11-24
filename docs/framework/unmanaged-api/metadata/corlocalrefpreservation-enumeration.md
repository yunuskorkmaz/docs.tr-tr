---
title: CorLocalRefPreservation Sabit Listesi
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
ms.openlocfilehash: 49b0298f4fa776c93f89ac380ce65568b493379b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677121"
---
# <a name="corlocalrefpreservation-enumeration"></a>CorLocalRefPreservation Sabit Listesi

Yerel başvuruların işleme için bayrak değerlerini içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|Yerel başvuruları koru.|  
|`MDPreserveLocalTypeRef`|Yerel tür başvurularını koru.|  
|`MDPreserveLocalMemberRef`|Yerel üye başvurularını koruma.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
