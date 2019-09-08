---
title: StrongNameSignatureVerificationEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798920"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx İşlevi
Belirtilen yoldaki Derleme bildiriminin tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: Strongnamesignaturedoğrulamaları Icationex](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. exe veya. dll) dosyasının yolu.  
  
 `fForceVerification`  
 'ndaki doğrulama gerçekleştirmek için, kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile, aksi durumda, `false`. `true`  
  
 `pfWasVerified`  
 dışı tanımlayıcı ad imzası doğrulandıysa, `false`tersi durumda. `true` `pfWasVerified`, kayıt defteri ayarları `false` nedeniyle doğrulama başarılı olduysa olarak da ayarlanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`doğrulama başarılı olduysa, Aksi takdirde `false`,.  
  
## <a name="remarks"></a>Açıklamalar  
 `StrongNameSignatureVerificationEx`[Strongnamesignaturedoğrulama](strongnamesignatureverification-function.md) işlevine benzer bir yetenek sağlar. Ancak, ikinci giriş parametresi ve için `StrongNameSignatureVerificationEx` çıkış parametresi yerine `DWORD`türüdür `BOOLEAN` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** Mscoree. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureVerificationEx Yöntemi](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification Yöntemi](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
