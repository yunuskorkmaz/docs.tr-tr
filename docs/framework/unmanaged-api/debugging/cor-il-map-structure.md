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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9676730a4f11ed77996b7a4aab4e538aba9b53c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="corilmap-structure"></a>COR_IL_MAP Yapısı
Değişiklikler bir işlev göreli uzaklığı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`oldOffset`|İşlev başına göreli uzaklığı eski Microsoft Ara dili (MSIL).|  
|`newOffset`|İşlev başlangıcını göre yeni MSIL uzaklığı.|  
|`fAccurate`|`true` doğru olması için eşleme biliniyorsa; Aksi takdirde `false`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Harita biçimi aşağıdaki gibidir: hata ayıklayıcı varsayar `oldOffset` özgün, değiştirilmemiş MSIL kodundaki MSIL uzaklığı ifade eder. `newOffset` Yeni, Araçlı kod içinde karşılık gelen MSIL uzaklık parametresi başvurur.  
  
 Atlama için düzgün çalışması için aşağıdaki gereksinimlerin karşılanması:  
  
-   Harita artan sırada sıralanması.  
  
-   İzleme eklenmiş MSIL kod edilip edilmemesi gerektiğini değil.  
  
-   Özgün MSIL kod kaldırılmaması gerekir.  
  
-   Harita program veritabanı (PDB) dosyasından tüm sıralama noktaları eşlemek için girişleri içermelidir.  
  
 Harita eksik girdiler kesinti değil. Aşağıdaki örnek, bir harita ve sonuçları gösterir.  
  
 Eşleyin:  
  
-   eski uzaklığı 0, 0 yeni uzaklığı  
  
-   5 eski uzaklığı, 10 yeni uzaklığı  
  
-   9 eski uzaklığı, 20 yeni uzaklığı  
  
 Sonuçları:  
  
-   0, 1, 2, 3 veya 4 eski uzaklığı yeni uzaklığı 0 eşleşecektir.  
  
-   5, 6, 7 veya 8 eski uzaklığı yeni uzaklık 10 eşleşecektir.  
  
-   9 veya üzeri eski uzaklığı yeni uzaklık 20 eşleşecektir.  
  
-   Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleşecektir.  
  
-   Yeni uzaklığını 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklık 5 eşleşecektir.  
  
-   Yeni bir uzaklık 20 veya daha yüksek eski uzaklık 9 eşleşecektir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
