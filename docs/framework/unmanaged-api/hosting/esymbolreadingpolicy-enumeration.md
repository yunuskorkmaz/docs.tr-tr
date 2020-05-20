---
title: ESymbolReadingPolicy Numaralandırması
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 5c3d1d0ebc56ee93c950afb4f015c8e10ec6a0f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616183"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy Numaralandırması
Program veritabanı (PDB) dosyalarını okumaya yönelik ilkeyi belirten değerleri içerir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Hata ayıklayıcının her zaman PDB dosyalarını okuduğunuzu belirtir.|  
|`eSymbolReadingFullTrustOnly`|Hata ayıklayıcının yalnızca tam güven Derlemeleriyle ilişkili PDB dosyalarını okuması gerektiğini belirtir.|  
|`eSymbolReadingNever`|Hata ayıklayıcının PDB dosyalarını asla okumayacağını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ESymbolReadingPolicy`Sabit listesi [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemiyle birlikte kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](hosting-enumerations.md)
