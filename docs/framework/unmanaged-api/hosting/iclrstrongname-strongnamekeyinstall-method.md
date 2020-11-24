---
title: ICLRStrongName::StrongNameKeyInstall Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 7e0c689dad0c288e3af3a3d64ee1bba1c44053c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674534"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a>ICLRStrongName::StrongNameKeyInstall Yöntemi

Bir kapsayıcıya ortak/özel anahtar çifti aktarır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `wszKeyContainer`  
 'ndaki Anahtar kapsayıcısının adı. `wszKeyContainer` boş olmayan bir dize olmalıdır.  
  
 `pbKeyBlob`  
 'ndaki İkili anahtar çifti.  
  
 `cbKeyBlob`  
 'ndaki Bayt cinsinden boyutu `pbKeyBlob` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  

 Anahtar kapsayıcısını silmek için [ICLRStrongName:: StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyDelete Yöntemi](iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
