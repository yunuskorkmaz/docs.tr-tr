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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c28f32a4b24393483241bd2d7d6f550b8b65ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796899"
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
 [in, out] İstenen maksimum uzunluk `pwzCachePath`ve dönüş sonrasında gerçek `pwzCachePath`uzunluğu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASM_CACHE_FLAGS Sabit Listesi](asm-cache-flags-enumeration.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
