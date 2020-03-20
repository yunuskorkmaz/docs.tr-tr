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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176987"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile İşlevi
Belirtilen dosyanın içeriği üzerinde karma oluşturur.  
  
 Bu işlev amortismana kaldırıldı. Bunun yerine [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) yöntemini kullanın.  
  
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
 [içinde] Karma dosyanın adı.  
  
 `piHashAlg`  
 [içinde, dışarı] Karma oluştururken kullanılacak algoritma. Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlanan algoritmalardır. 0 `piHashAlg` olarak ayarlanırsa, varsayılan algoritma CALG_SHA-1 kullanılır.  
  
 `pbHash`  
 [çıkış] Oluşturulan karma içeren bir bayt dizisi.  
  
 `cchHash`  
 [içinde] Tamponun işaret eden `pbHash` maksimum boyutu.  
  
 `pchHash`  
 [çıkış] Döndürülen baytların `pbHash`boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev [GetHashFromFileW](gethashfromfilew-function.md)ile aynıdır, ancak dosya adı belirtimi Unicode yerine ANSI'dir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFile Yöntemi](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW Yöntemi](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
