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
ms.openlocfilehash: 8038d0abc93e058e6bde897bbf2261d8f1df885a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732332"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW İşlevi

Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde bir karma oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Karma olacak dosyanın Unicode adı.  
  
 `piHashAlg`  
 [in, out] Karma oluşturulurken kullanılacak algoritma. Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır. `piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.  
  
 `pbHash`  
 dışı Oluşturulan karmayı içeren bir bayt dizisi.  
  
 `cchHash`  
 'ndaki Tarafından işaret edilen arabelleğin en büyük boyutu `pbHash` .  
  
 `pchHash`  
 dışı Bayt cinsinden boyutu `pbHash` .  
  
## <a name="remarks"></a>Açıklamalar  

 Bu işlev, [GetHashFromFile](gethashfromfile-function.md)ile aynıdır, ancak dosya adı belirtimi ANSI yerine Unicode olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFileW Yöntemi](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile Yöntemi](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
