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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799222"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile İşlevi
Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 [in, out] Karma oluşturulurken kullanılacak algoritma. Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır. `piHashAlg` 0 olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.  
  
 `pbHash`  
 dışı Oluşturulan karmayı içeren bir bayt dizisi.  
  
 `cchHash`  
 'ndaki İşaret eden `pbHash` arabelleğin en büyük boyutu.  
  
 `pchHash`  
 dışı Döndürülen `pbHash`bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, [GetHashFromFileW](gethashfromfilew-function.md)ile aynıdır, ancak dosya adı belirtimi UNICODE yerine ANSI olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFile Yöntemi](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW Yöntemi](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
