---
title: ICLRStrongName::StrongNameKeyGenEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 9ba50616b25f9c7c592f19947c82a890ae6b5a4a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671687"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a>ICLRStrongName::StrongNameKeyGenEx Yöntemi

Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `wszKeyContainer`  
 'ndaki İstenen anahtar kapsayıcısı adı. `wszKeyContainer` geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.  
  
 `dwFlags`  
 'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer. Aşağıdaki değerler desteklenir:  
  
- 0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.  
  
- 0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.  
  
 `dwKeySize`  
 'ndaki Anahtarın bit cinsinden istenen boyutu.  
  
 `ppbKeyBlob`  
 dışı Döndürülen ortak/özel anahtar çifti.  
  
 `pcbKeyBlob`  
 dışı Bayt cinsinden boyutu `ppbKeyBlob` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  

 1,0 ve 1,1 .NET Framework sürümleri, bir `dwKeySize` derlemeyi güçlü bir adla imzalamak için 1024 bit gerektirir; sürüm 2,0, 2048 bit anahtarlar için destekler.  
  
 Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyGen Yöntemi](iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
