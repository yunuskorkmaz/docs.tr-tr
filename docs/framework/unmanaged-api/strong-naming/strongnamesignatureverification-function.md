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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8943df861b1bff2b28c68d0233fc336d1b5d4579
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798940"
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
  
- `SN_INFLAG_FORCE_VER`(0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.  
  
- `SN_INFLAG_INSTALL`(0x00000002)-bildirimin doğrulandığı ilk zaman olduğunu belirtir.  
  
- `SN_INFLAG_ADMIN_ACCESS`(0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.  
  
- `SN_INFLAG_USER_ACCESS`(0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.  
  
- `SN_INFLAG_ALL_ACCESS`(0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.  
  
- `SN_INFLAG_RUNTIME`(0x80000000)-iç hata ayıklama için ayrılmıştır.  
  
 `pdwOutFlags`  
 dışı Tanımlayıcı ad imzasının doğrulanıp doğrulanmadığını belirten bayraklar. Aşağıdaki değer desteklenir:  
  
- `SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-Bu değer, kayıt defteri `false` ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için olarak ayarlanır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`doğrulama başarılı olduysa, Aksi takdirde `false`,.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureVerification Yöntemi](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx Yöntemi](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
