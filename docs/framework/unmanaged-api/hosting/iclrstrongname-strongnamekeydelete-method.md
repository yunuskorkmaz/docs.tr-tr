---
description: ': ICLRStrongName:: StrongNameKeyDelete yöntemi hakkında daha fazla bilgi edinin'
title: ICLRStrongName::StrongNameKeyDelete Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 5b782785921eb24394db53d29a66600a3867b489
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799583"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a>ICLRStrongName::StrongNameKeyDelete Yöntemi

Belirtilen anahtar kapsayıcısını siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `wszKeyContainer`  
 'ndaki Silinecek anahtar kapsayıcısının adı.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  

 Bir kapsayıcıya ortak/özel anahtar çifti aktarmak için [ICLRStrongName:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyInstall Yöntemi](iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
