---
title: StrongNameKeyGen İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: 79b2235e3645c89c2cd9ebcce079d5eb7efdd162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128745"
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen İşlevi
Tanımlayıcı ad kullanımı için yeni bir ortak/özel anahtar çifti oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszKeyContainer`  
 'ndaki İstenen anahtar kapsayıcısı adı. `wszKeyContainer`, boş olmayan bir dize veya geçici bir ad oluşturmak için null olmalıdır.  
  
 `dwFlags`  
 'ndaki Anahtarın kaydedilip edilmeyeceğini belirtir. Aşağıdaki değerler desteklenir:  
  
- 0x00000000-`wszKeyContainer` bir geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.  
  
- 0x00000001 (`SN_LEAVE_KEY`)-anahtarın kayıtlı olması gerektiğini belirtir.  
  
 `ppbKeyBlob`  
 dışı Döndürülen ortak/özel anahtar çifti.  
  
 `pcbKeyBlob`  
 dışı `ppbKeyBlob`bayt cinsinden boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 başarılı tamamlamada `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 `StrongNameKeyGen` işlevi 1024 bitlik bir anahtar oluşturur. Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.  
  
 `StrongNameKeyGen` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyGen Yöntemi](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [StrongNameKeyGenEx Yöntemi](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
