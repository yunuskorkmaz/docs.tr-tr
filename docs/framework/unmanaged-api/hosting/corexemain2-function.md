---
title: _CorExeMain2 İşlevi
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: cc5324683daa9a02a6a89b2a3fb57ee9fd5dbe72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136956"
---
# <a name="_corexemain2-function"></a>_CorExeMain2 İşlevi
Giriş noktasını belirtilen bellek eşlemeli kodda yürütür. Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pUnmappedPE`  
 'ndaki Bellek eşlemeli koda yönelik bir işaretçi.  
  
 `cUnmappedPE`  
 'ndaki `pUnmappedPE` öğe sayısı olabilir.  
  
 `pImageNameIn`  
 'ndaki Yürütülebilir görüntünün adı için bir işaretçi.  
  
 `pLoadersFileName`  
 'ndaki Yükleyici dosyasının adı.  
  
 `pCmdLine`  
 'ndaki Varsa komut satırı parametreleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
