---
title: "StrongNameSignatureVerificationEx İşlevi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d00c2f03968e69423da31a336d275c46291d8da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx İşlevi
Sağlanan yol, derleme bildirimi sağlam ad imzası içeren olup olmadığını belirten bir değer alır.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 [in] Taşınabilir yürütülebilir (.exe veya .dll) dosyasını doğrulanacak derleme yolu.  
  
 `fForceVerification`  
 [in] `true` , olsa bile gerekli kayıt defteri ayarlarını geçersiz kılmak, aksi takdirde doğrulama gerçekleştirmek için `false`.  
  
 `pfWasVerified`  
 [out] `true` sağlam ad imzası, doğrulanmış Aksi takdirde `false`. `pfWasVerified`Ayrıca ayarlamak `false` kayıt defteri ayarları nedeniyle doğrulama başarılı olursa.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`doğrulama başarılı olursa; Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 `StrongNameSignatureVerificationEx`benzer bir yetenek sağlar [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) işlevi. Ancak, ikinci parametre hem de çıkış parametresi için bir girdi `StrongNameSignatureVerificationEx` türü `BOOLEAN` yerine `DWORD`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak mscoree.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [StrongNameSignatureVerificationEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [StrongNameSignatureVerification Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
