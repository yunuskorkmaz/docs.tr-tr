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
ms.openlocfilehash: 4f3574e282d24fa11ffa2f85463f682c42098ae7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135047"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen Yöntemi
Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 'ndaki İstenen anahtar kapsayıcısı adı. `wszKeyContainer`, geçici bir ad oluşturmak için boş olmayan bir dize ya da null olmalıdır.  
  
 `dwFlags`  
 'ndaki Anahtarın kaydedilip edilmeyeceğini belirten bir değer. Aşağıdaki değerler desteklenir:  
  
- 0x00000000-`wszKeyContainer` bir geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.  
  
- 0x00000001 (`SN_LEAVE_KEY`)-anahtarın kayıtlı olması gerektiğini belirtir.  
  
 `ppbKeyBlob`  
 dışı Döndürülen ortak/özel anahtar çifti.  
  
 `pcbKeyBlob`  
 dışı `ppbKeyBlob`bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRStrongName:: StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) yöntemi 1024 bitlik bir anahtar oluşturur. Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyGenEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
