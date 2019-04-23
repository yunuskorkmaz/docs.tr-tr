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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f968d84ae695eb1da127538ebdc5e4f55d6ebf39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183163"
---
# <a name="corexemain2-function"></a>_CorExeMain2 İşlevi
Belirtilen bellek eşlemeli kod içinde giriş noktasını yürütür. Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Bellek eşlemeli kod için bir işaretçi.  
  
 `cUnmappedPE`  
 [in] Öğe sayısı `pUnmappedPE` basılı tutabilirsiniz.  
  
 `pImageNameIn`  
 [in] Yürütülebilir resmin adı için bir işaretçi.  
  
 `pLoadersFileName`  
 [in] Yükleyici dosyasının adı.  
  
 `pCmdLine`  
 [in] Komut satırı parametreleri, varsa.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
