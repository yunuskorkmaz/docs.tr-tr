---
title: StrongNameKeyDelete İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3eace88e5034c61b7608a6d777608cc2544b8564
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688486"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete İşlevi
Belirtilen anahtar kapsayıcısında siler.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszKeyContainer`  
 [in] Silinecek anahtar kapsayıcısının adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` başarıyla tamamlandığında; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [Strongnamekeyınstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) importa için bir kapsayıcıya bir ortak/özel anahtar çifti işlev.  
  
 Varsa `StrongNameKeyDelete` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [StrongNameKeyDelete Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
