---
title: StrongNameGetBlob İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12daac766a09c297bfa129f69342ebad20977e7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780131"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob İşlevi
Belirtilen arabellek, yürütülebilir dosyanın belirtilen adreste ikili gösterimini ile doldurur.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 [in] Yüklenen yürütülebilir dosyanın geçerli bir yol.  
  
 `pbBlob`  
 [in] Arabelleğe yürütülebilir dosyayı yüklemek için.  
  
 `pcbBlob`  
 [out içinde] Bayt cinsinden en büyük boyutu, istenen `pbBlob`. İade, bayt cinsinden gerçek boyutu bağlı, `pbBlob`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` başarıyla tamamlandığında; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `StrongNameGetBlob` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetBlob Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
