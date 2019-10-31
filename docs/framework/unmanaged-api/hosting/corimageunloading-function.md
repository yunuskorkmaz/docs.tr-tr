---
title: _CorImageUnloading İşlevi
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
ms.openlocfilehash: 30e3a88140c8a438001e8428df4c5ee879c83376
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136917"
---
# <a name="_corimageunloading-function"></a>_CorImageUnloading İşlevi
Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.  
  
 Bu işlev uygulanmadı. Çağrılırsa, E_NOTIMPL döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ImageBase`  
 'ndaki Boşaltılacak görüntünün başlangıç konumuna yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
