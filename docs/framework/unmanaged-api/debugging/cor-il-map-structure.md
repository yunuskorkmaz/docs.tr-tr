---
title: COR_IL_MAP Yapısı
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179299"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP Yapısı
Bir işlevin göreli mahsup değişiklikleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`oldOffset`|Eski Microsoft ara dili (MSIL) işlevin başına göre ofset.|  
|`newOffset`|Yeni MSIL ofset fonksiyonun başına göre.|  
|`fAccurate`|`true`haritalamanın doğru olduğu biliniyorsa; aksi `false`takdirde, .|  
  
## <a name="remarks"></a>Açıklamalar  
 Haritanın biçimi aşağıdaki gibidir: Hata ayıklayıcı, `oldOffset` özgün, değiştirilmemiş MSIL kodu içinde bir MSIL mahsup anlamına gelir varsayar. Parametre, `newOffset` yeni, araçlı kod içinde ilgili MSIL mahsup anlamına gelir.  
  
 Düzgün çalışmaya adım atmak için aşağıdaki gereksinimlerin karşılanması gerekir:  
  
- Harita artan sırada sıralanmalıdır.  
  
- İşletilmiş MSIL kodu yeniden sıralanmamalıdır.  
  
- Özgün MSIL kodu kaldırılmamalıdır.  
  
- Harita, program veritabanı (PDB) dosyasındaki tüm sıra noktalarını eşlemek için girişleri içermelidir.  
  
 Harita, eksik girişleri interpolate etmez. Aşağıdaki örnekte bir harita ve sonuçları gösterilmektedir.  
  
 Harita:  
  
- 0 eski ofset, 0 yeni ofset  
  
- 5 eski ofset, 10 yeni ofset  
  
- 9 eski ofset, 20 yeni ofset  
  
 Sonuçlar:  
  
- 0, 1, 2, 3 veya 4'lü eski bir ofset, 0'ın yeni bir mahsup'una eşlenir.  
  
- 5, 6, 7 veya 8'lik eski bir ofset, yeni ofset 10'a eşlenir.  
  
- 9 veya daha yüksek eski bir ofset yeni ofset 20 eşlenir.  
  
- 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9'un yeni bir mahsup hakkı eski ofset 0'a eşlenir.  
  
- 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19'luk yeni bir ofset, eski ofset 5'e eşlenir.  
  
- 20 veya daha yüksek yeni bir ofset eski ofset 9 eşlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorProf.idl  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata ayıklama](index.md)
