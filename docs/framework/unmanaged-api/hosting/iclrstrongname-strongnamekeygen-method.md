---
title: ICLRStrongName::StrongNameKeyGen Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: db5c0dbe57607c7a3bf8b97cee734415aa934336
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763091"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen Yöntemi
Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszKeyContainer`  
 'ndaki İstenen anahtar kapsayıcısı adı. `wszKeyContainer`geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.  
  
 `dwFlags`  
 'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer. Aşağıdaki değerler desteklenir:  
  
- 0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.  
  
- 0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.  
  
 `ppbKeyBlob`  
 dışı Döndürülen ortak/özel anahtar çifti.  
  
 `pcbKeyBlob`  
 dışı Bayt cinsinden boyutu `ppbKeyBlob` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRStrongName:: StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) yöntemi 1024 bitlik bir anahtar oluşturur. Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyGenEx Yöntemi](iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName Arabirimi](iclrstrongname-interface.md)
