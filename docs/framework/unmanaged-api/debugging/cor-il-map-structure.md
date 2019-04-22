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
ms.openlocfilehash: e6d8023c7ac6d917c9df40fb18316ddc12df5ec1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190437"
---
# <a name="corilmap-structure"></a>COR_IL_MAP Yapısı
Değişiklikleri, bir işlevin göreli uzaklığı belirtir.  
  
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
|`oldOffset`|İşlevin başlangıcına göre uzaklığı eski Microsoft Ara dilini (MSIL).|  
|`newOffset`|İşlevin başlangıcına göre yeni MSIL uzaklık.|  
|`fAccurate`|`true` eşleme doğru olarak bilinir Aksi takdirde, `false`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Eşleme biçimi aşağıdaki gibidir: Hata ayıklayıcı varsayar `oldOffset` özgün, değiştirilmemiş MSIL kodu içinde bir MSIL uzaklığı ifade eder. `newOffset` Yeni, izleme eklenmiş kod içinde karşılık gelen MSIL uzaklık parametresi başvurur.  
  
 Düzgün çalışması için atlamak için aşağıdaki gereksinimlerin karşılanması:  
  
-   Harita, artan düzende sıralanmalıdır.  
  
-   İzleme eklenmiş MSIL kodu edilip edilmemesi gerektiğini değil.  
  
-   Özgün MSIL kodu kaldırılmamalıdır.  
  
-   Eşleme girişleri program veritabanı (PDB) dosyasındaki dizi noktalarını eşlemek için içermelidir.  
  
 Harita eksik girdiler enterpolasyon değil. Aşağıdaki örnek, bir harita ve sonuçları gösterir.  
  
 Eşleme:  
  
-   0 eski uzaklığı, 0 yeni uzaklık  
  
-   5 eski uzaklığı, 10 yeni uzaklık  
  
-   9 eski uzaklığı, 20 yeni uzaklık  
  
 Sonuçları:  
  
-   0, 1, 2, 3 veya 4 eski uzaklığı 0'ın yeni bir uzaklık eşleştirilir.  
  
-   Eski bir uzaklık 5, 6, 7 veya 8, 10 yeni uzaklık eşleştirilir.  
  
-   9 veya daha eski bir uzaklık yeni uzaklık 20 eşleştirilir.  
  
-   Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleştirilir.  
  
-   Yeni bir uzaklık 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklığı 5 eşleştirilir.  
  
-   20 veya üzeri bir yeni uzaklığı eski uzaklığı 9 eşleştirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
