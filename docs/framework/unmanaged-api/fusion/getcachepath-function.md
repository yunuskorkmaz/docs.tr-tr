---
title: GetCachePath İşlevi
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: 13e1468ef5a48f18910c1f8082cdd7c4849da14a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132694"
---
# <a name="getcachepath-function"></a>GetCachePath İşlevi
Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwCacheFlags`  
 'ndaki Önbelleğe alınmış derlemenin kaynağını gösteren bir [asm_cache_flags](asm-cache-flags-enumeration.md) değeri.  
  
 `pwzCachePath`  
 dışı Yolun döndürülen işaretçisi.  
  
 `pcchPath`  
 [in, out] İstenen en büyük `pwzCachePath`uzunluğu ve dönüş sonrasında, `pwzCachePath`gerçek uzunluğu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASM_CACHE_FLAGS Sabit Listesi](asm-cache-flags-enumeration.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
