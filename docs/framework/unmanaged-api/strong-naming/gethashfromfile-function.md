---
title: "GetHashFromFile İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be7979eb0f7d32e02257cc0b3cb400263350f0bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfile-function"></a>GetHashFromFile İşlevi
Belirtilen dosyanın içeriğini bir karma oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szFilePath`  
 [in] Karma değerini dosyasının adı.  
  
 `piHashAlg`  
 [içinde out] Karma oluşturulurken kullanılacak algoritması. Geçerli algoritmaları Win32 CryptoAPI tarafından tanımlanmış izinlerdir. Varsa `piHashAlg` CALG_SHA-1 kullanılan varsayılan algoritma 0 olarak ayarlanır.  
  
 `pbHash`  
 [out] Üretilen karma içeren bir bayt dizisi.  
  
 `cchHash`  
 [in] Arabelleğin en büyük boyutu, `pbHash` işaret eder.  
  
 `pchHash`  
 [out] Dönen bayt cinsinden boyutu `pbHash`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev aynıdır [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), dosya adı belirtimine Unicode yerine ANSI olması dışında.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetHashFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [GetHashFromFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
