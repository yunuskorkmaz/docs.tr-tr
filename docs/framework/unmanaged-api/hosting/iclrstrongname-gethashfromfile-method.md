---
title: ICLRStrongName::GetHashFromFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ff346d8f7ba321904a8d91079298b58039e6eb54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727620"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>ICLRStrongName::GetHashFromFile Yöntemi

Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.  
  
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
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, [ICLRStrongName:: GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) yöntemiyle aynıdır, ancak dosya adı belirtimi UNICODE yerine ANSI olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetHashFromFileW Yöntemi](iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
