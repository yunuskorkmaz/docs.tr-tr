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
ms.openlocfilehash: c398663b84637d2551b0d94bd59b9e0994721ba5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124773"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification İşlevi
Sağlanan yol, derleme bildirimi belirtilen bayraklar göre doğrulanan bir tanımlayıcı ad imzası içerip içermediğini gösteren bir değer alır.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 [in] Taşınabilir yürütülebilir (.dll veya .exe) dosyayı doğrulamak derleme yolu.  
  
 `dwInFlags`  
 [in] Doğrulama davranışını değiştirmek için işaretler. Aşağıdaki değerleri desteklenir:  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulama zorlar.  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - Bu bildirimi doğrulanır ilk kez olduğunu belirtir.  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) - önbellek yönetici ayrıcalıklarına sahip kullanıcılara erişimi sağlayacak belirtir.  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) - derleme yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - iç hata ayıklama için ayrılmış.  
  
 `pdwOutFlags`  
 [out] Tanımlayıcı ad imzası doğrulandı olup olmadığını belirten bayrak. Aşağıdaki değeri desteklenir:  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` doğrulama başarılı olduysa; Aksi takdirde, `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureVerification Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
