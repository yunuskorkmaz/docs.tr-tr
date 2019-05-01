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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9be512bab30e08ddeb7deadf8a29263e928549a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000382"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW İşlevi
Unicode dizesi tarafından belirtilen dosyanın içeriğini üzerinden bir karma oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 [in] Karma dosyayı Unicode adı.  
  
 `piHashAlg`  
 [out içinde] Karma oluşturulurken kullanılacak algoritma. Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir. Varsa `piHashAlg` CALG_SHA 1 kullanılan varsayılan algoritma 0 olarak ayarlanır.  
  
 `pbHash`  
 [out] Oluşturulan karma içeren bir bayt dizisi.  
  
 `cchHash`  
 [in] En büyük arabellek boyutunu tarafından işaret edilen `pbHash`.  
  
 `pchHash`  
 [out] Bayt cinsinden boyutu, `pbHash`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev aynı şekilde, [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), dosya adı belirtimi yerine ANSI Unicode olması dışında.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
