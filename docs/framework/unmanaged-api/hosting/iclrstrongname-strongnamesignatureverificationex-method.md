---
title: ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: e2003ce78f04b101fe093867e0820f9c3840151a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762714"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a>ICLRStrongName::StrongNameSignatureVerificationEx Yöntemi
Belirtilen yoldaki Derleme bildiriminin bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.  
  
 `fForceVerification`  
 [in] `true` doğrulama gerçekleştirmek için, kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile; Aksi takdirde, `false` .  
  
 `pfWasVerified`  
 [out] `true` tanımlayıcı ad imzası doğrulandıysa; Aksi takdirde, `false` . `pfWasVerified`, `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olduysa olarak da ayarlanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`doğrulama başarılı olduysa, Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi [ICLRStrongName:: Strongnamesignaturedoğrulama](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemine benzer bir yetenek sağlar. Ancak, ikinci giriş parametresi ve [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](iclrstrongname-strongnamesignatureverificationex-method.md) için çıkış parametresi `BOOLEAN` yerine türüdür `DWORD` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureVerification Yöntemi](iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
