---
title: ICLRStrongName::GetHashFromFileW Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176376"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW Yöntemi
Unicode dizesi tarafından belirtilen dosyanın içeriği üzerinde karma oluşturur.  
  
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
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`yöntem başarıyla tamamlanırsa; aksi takdirde, başarısızlığı gösteren bir HRESULT değeri (liste için [Ortak HRESULT Değerleri'ne](/windows/win32/seccrypto/common-hresult-values) bakın).  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, dosya adı belirtimi NINAnSI yerine Unicode [dışında, ICLRStrongName aynıdır::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MetaHost.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFile Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
