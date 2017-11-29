---
title: "StrongNameSignatureVerificationFromImage İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationFromImage
helpviewer_keywords: StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab890451c44b19be6472ae6c7da060ae71612bc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage İşlevi
Bellek zaten eşlendi bütünleştirilmiş ilişkili ortak anahtarı için geçerli olduğunu doğrular.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbBase`  
 [in] Eşlenen derleme bildirimi göreli sanal adresi.  
  
 `dwLength`  
 [in] Eşlenen görüntünün bayt cinsinden boyutu.  
  
 `dwInFlags`  
 [in] Doğrulama davranışını etkilemek bayraklar. Aşağıdaki değerleri desteklenir:  
  
-   `SN_INFLAG_FORCE_VER`(0x00000001) - kayıt defteri ayarlarını geçersiz kılmak gerekli olduğu halde doğrulama zorlar.  
  
-   `SN_INFLAG_INSTALL`(0x00000002) - bu görüntü üzerinde gerçekleştirilen ilk doğrulama olduğunu belirtir.  
  
-   `SN_INFLAG_ADMIN_ACCESS`(0x00000004) - önbelleğe erişimi yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılara izin verip belirtir.  
  
-   `SN_INFLAG_USER_ACCESS`(0x00000008) - derleme yalnızca geçerli kullanıcıya erişilebilir olacağını belirtir.  
  
-   `SN_INFLAG_ALL_ACCESS`(0x00000010) - önbellek garanti erişim kısıtlama sağlayacak belirtir.  
  
-   `SN_INFLAG_RUNTIME`(0x80000000) - iç hata ayıklama için ayrılmış.  
  
 `pdwOutFlags`  
 [out] Ek çıkış bilgileri için bir bayrak. Aşağıdaki değeri desteklenir:  
  
-   `SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - bu değeri ayarı `false` doğrulama kayıt defteri ayarları nedeniyle başarılı olduğunu belirtmek için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarılı tamamlanma; Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `StrongNameSignatureVerificationFromImage` işlevi yok başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) son oluşturulan hata alınacak işlev.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** StrongName.h  
  
 **Kitaplığı:** bir kaynak olarak mscoree.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Strongnamesignatureverificationfromımage yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [Iclrstrongname arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
