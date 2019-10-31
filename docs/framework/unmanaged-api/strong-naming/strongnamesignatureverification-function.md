---
title: StrongNameSignatureVerification İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: 7dd61be008ba08ca2b28ae3e7e8ff6326f8a41d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129242"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification İşlevi
Belirtilen bayrağa göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: Strongnamesignaturedoğrulaması](../hosting/iclrstrongname-strongnamesignatureverification-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 'ndaki Doğrulanacak derleme için taşınabilir yürütülebilir (. dll veya. exe) dosyasının yolu.  
  
 `dwInFlags`  
 'ndaki Doğrulama davranışını değiştirecek bayraklar. Aşağıdaki değerler desteklenir:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.  
  
- `SN_INFLAG_INSTALL` (0x00000002)-bildirimin doğrulandığı ilk zaman olduğunu belirtir.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.  
  
- `SN_INFLAG_RUNTIME` (0x80000000)-iç hata ayıklama için ayrılmıştır.  
  
 `pdwOutFlags`  
 dışı Tanımlayıcı ad imzasının doğrulanıp doğrulanmadığını belirten bayraklar. Aşağıdaki değer desteklenir:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-Bu değer, kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için `false` olarak ayarlanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 doğrulama başarılı olduysa `true`; Aksi takdirde, `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureVerification Yöntemi](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx Yöntemi](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
