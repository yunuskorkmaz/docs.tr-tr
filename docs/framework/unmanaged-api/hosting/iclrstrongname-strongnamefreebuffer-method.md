---
title: ICLRStrongName::StrongNameFreeBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504010"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a>ICLRStrongName::StrongNameFreeBuffer Yöntemi
[ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName](iclrstrongname-strongnametokenfrompublickey-method.md):: StrongNameTokenFromPublicKey veya [ICLRStrongName:: StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)gibi tanımlayıcı bir ad yöntemine önceki bir çağrı ile ayrılmış belleği serbest bırakır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbMemory`  
 'ndaki Boşaltılacak belleğin bir işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
