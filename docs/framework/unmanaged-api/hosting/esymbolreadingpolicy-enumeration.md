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
ms.openlocfilehash: 786ff6895383fc18dcfedb26fab344f80f04c1df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138202"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy Numaralandırması
Program veritabanı (PDB) dosyalarını okumaya yönelik ilkeyi belirten değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 `ESymbolReadingPolicy` numaralandırması [ICLRDebugManager:: SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemiyle birlikte kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
