---
description: 'Daha fazla bilgi edinin: CorNativeLinkFlags numaralandırması'
title: CorNativeLinkFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 9025d192ca92c1160c1b072b0dcfe045fa3ceab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784359"
---
# <a name="cornativelinkflags-enumeration"></a>CorNativeLinkFlags Numaralandırması

Yerel kod bağlanırken bağlayıcı tarafından kullanılan bayrak değerlerini sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`nlfNone`|Bayrak olmadığını gösterir.|  
|`nlfLastError`|Bir `setLastError` anahtar sözcüğü gösterir.|  
|`nlfNoMangle`|Bir `nomangle` anahtar sözcüğü gösterir.|  
|`nlfMaxValue`|Kullanılmadı.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
