---
title: GetFileVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 2dd004a44b20d48dafc72711ac23abcb55739224
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617206"
---
# <a name="getfileversion-function"></a>GetFileVersion İşlevi
Belirtilen arabelleği kullanarak belirtilen dosyanın ortak dil çalışma zamanı (CLR) sürüm bilgilerini alır.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `szFilename`  
 'ndaki İnceedilecek dosyanın yolu.  
  
 `szBuffer`  
 [in, out] Döndürülen sürüm bilgileri için ayrılan arabellek.  
  
 `cchBuffer`  
 'ndaki Öğesinin geniş karakterdeki boyutu `szBuffer` .  
  
 `dwLength`  
 dışı Döndürülen bayt cinsinden boyutu `szBuffer` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
