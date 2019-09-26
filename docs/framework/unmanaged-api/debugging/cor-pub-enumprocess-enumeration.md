---
title: COR_PUB_ENUMPROCESS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eab5fc13b74d8af4f0baaa3953c5c73ea255bfe6
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274014"
---
# <a name="cor_pub_enumprocess-enumeration"></a>COR_PUB_ENUMPROCESS Numaralandırması
Numaralandırılacak işlemin türünü tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|Yönetilen bir işlem.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen hata ayıklama API 'sinin geçerli sürümü yalnızca yönetilen işlemi numaralandırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorPub. IDL, CorPub. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](debugging-enumerations.md)
