---
title: GetHashFromFile İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ee9f9cd9a9f35c6c54497ad382bb6f9817d186bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732378"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile İşlevi

Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szFilePath`  
 'ndaki Karma yapılacak dosyanın adı.  
  
 `piHashAlg`  
 [in, out] Karma oluşturulurken kullanılacak algoritma. Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır. `piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.  
  
 `pbHash`  
 dışı Oluşturulan karmayı içeren bir bayt dizisi.  
  
 `cchHash`  
 'ndaki İşaret eden arabelleğin en büyük boyutu `pbHash` .  
  
 `pchHash`  
 dışı Döndürülen bayt cinsinden boyutu `pbHash` .  
  
## <a name="remarks"></a>Açıklamalar  

 Bu işlev, [GetHashFromFileW](gethashfromfilew-function.md)ile aynıdır, ancak dosya adı belirtimi UNICODE yerine ANSI olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFile Yöntemi](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW Yöntemi](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
