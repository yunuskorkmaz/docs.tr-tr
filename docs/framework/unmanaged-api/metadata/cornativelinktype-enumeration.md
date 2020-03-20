---
title: CorNativeLinkType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: 0b613ebacdff82a29fdbc3f4caa0f2b8bb5d3f6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176168"
---
# <a name="cornativelinktype-enumeration"></a>CorNativeLinkType Numaralandırması
Yerel koda bağlı türü gösteren değerler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`nltNone`|Anahtar kelimelerden hiçbirinin belirtilmemiş olduğunu gösterir.|  
|`nltAnsi`|ANSI anahtar kelimesinin belirtildiğini gösterir.|  
|`nltUnicode`|Unicode anahtar kelimesinin belirtildiğini gösterir|  
|`nltAuto`|Otomatik anahtar kelimenin belirtildiğini gösterir.|  
|`nltOle`|OLE anahtar kelimesinin belirtildiğini gösterir.|  
|`nltMaxValue`|Kullanılmadı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
