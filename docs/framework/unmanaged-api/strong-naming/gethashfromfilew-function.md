---
title: GetHashFromFileW İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175089"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW İşlevi
Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde karma oluşturur.  
  
 Bu işlev amortismana kaldırıldı. Bunun yerine [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 [içinde] Karma dosyanın Unicode adı.  
  
 `piHashAlg`  
 [içinde, dışarı] Karma oluştururken kullanılacak algoritma. Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlanan algoritmalardır. 0 `piHashAlg` olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.  
  
 `pbHash`  
 [çıkış] Oluşturulan karma içeren bir bayt dizisi.  
  
 `cchHash`  
 [içinde] Tarafından işaret edilen arabelleğe `pbHash`işaret edilen maksimum boyutu.  
  
 `pchHash`  
 [çıkış] Boyutu, bayt, ve. `pbHash`  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev [GetHashFromFile](gethashfromfile-function.md)ile aynıdır , ancak dosya adı belirtimi ANSI yerine Unicode'dur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFileW Yöntemi](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile Yöntemi](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
