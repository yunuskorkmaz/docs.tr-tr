---
description: 'Daha fazla bilgi edinin: COR_IL_MAP yapısı'
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
ms.openlocfilehash: ff3d636429f51119342baea5d71163eb9d764e03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712330"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP Yapısı

Bir işlevin göreli uzaklığının değişikliklerini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`oldOffset`|İşlevin başlangıcına göre eski Microsoft ara dili (MSIL) uzaklıkları.|  
|`newOffset`|İşlevin başlangıcına göre yeni MSIL fark.|  
|`fAccurate`|`true` eşlemenin doğru olduğu bilinmektedir; Aksi takdirde, `false` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Haritanın biçimi şu şekildedir: hata ayıklayıcı, `oldOffset` orijinal, DEĞIŞTIRILMEMIŞ MSIL kodu içindeki BIR MSIL sapmasını ifade eden kabul edilir. `newOffset`Parametresi, yeni ve belgelenmiş kod içindeki karşılık gelen MSIL sapmasını ifade eder.  
  
 Adımların düzgün çalışması için aşağıdaki gereksinimlerin karşılanması gerekir:  
  
- Haritanın artan sırada sıralanması gerekir.  
  
- Belgelenmiş MSIL kodu yeniden sıralanmaz.  
  
- Orijinal MSIL kodu kaldırılmamalıdır.  
  
- Map, program veritabanı (PDB) dosyasındaki tüm sıra noktalarını eşlemek için girdiler içermelidir.  
  
 Eşleme, eksik girişleri enterpolamıyor. Aşağıdaki örnek bir eşlemeyi ve sonuçlarını gösterir.  
  
 Harita  
  
- 0 eski fark, 0 yeni fark  
  
- 5 eski fark, 10 yeni fark  
  
- 9 eski fark, 20 yeni fark  
  
 Sonuçlar:  
  
- 0, 1, 2, 3 veya 4 ' ün eski bir kayması, 0 ' ın yeni bir uzaklığa eşlenir.  
  
- 5, 6, 7 veya 8 ' in eski bir kayması, yeni %10 ' a eşlenir.  
  
- Daha eski bir 9 veya üzeri fark, 20. yeni uzaklığa eşlenir.  
  
- 0, 1, 2, 3, 4, 5, 6, 7, 8 ya da 9 ' un yeni bir kayması, 0 ' dan eski uzaklığa eşlenir.  
  
- 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 ' un yeni bir kayması, 5 eski uzaklığa eşlenir.  
  
- 20 veya üzeri yeni bir konum, eski konum 9 ' A eşlenir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
