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
ms.openlocfilehash: c22f0701cfda4523f595366a97435ef8da08b0cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724474"
---
# <a name="getcachepath-function"></a>GetCachePath İşlevi

Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwCacheFlags`  
 'ndaki Önbelleğe alınmış derlemenin kaynağını gösteren [asm_cache_flags](asm-cache-flags-enumeration.md) değeri.  
  
 `pwzCachePath`  
 dışı Yolun döndürülen işaretçisi.  
  
 `pcchPath`  
 [in, out] İstenen maksimum uzunluk `pwzCachePath` ve dönüş sonrasında gerçek uzunluğu `pwzCachePath` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASM_CACHE_FLAGS Numaralandırması](asm-cache-flags-enumeration.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
