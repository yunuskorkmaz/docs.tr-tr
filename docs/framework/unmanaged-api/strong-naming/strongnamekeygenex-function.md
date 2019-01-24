---
title: StrongNameKeyGenEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77ede995b08aba0822e9d86607e0d1e37bd6f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557337"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx İşlevi
Tanımlayıcı ad kullanmak için belirtilen anahtar boyutu ile yeni bir ortak/özel anahtar çifti oluşturur.  
  
 Bu işlev kullanım dışı bırakıldı. Kullanım [Iclrstrongname::strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wszKeyContainer`  
 [in] İstenen anahtar kapsayıcısı adı. `wszKeyContainer` gereken boş olmayan bir dize olması veya geçici bir ad oluşturmak için null.  
  
 `dwFlags`  
 [in] Kaydedilen anahtar bırakın belirtir. Aşağıdaki değerleri desteklenir:  
  
-   kullanılan 0x00000000 - `wszKeyContainer` geçici bir anahtar kapsayıcısı adını oluşturmak için null.  
  
-   0x00000001 (`SN_LEAVE_KEY`)-anahtar sol kaydedilmesi gerektiğini belirtir.  
  
 `dwKeySize`  
 [in] İstenen bit cinsinden anahtar boyutunu.  
  
 `ppbKeyBlob`  
 [out] Döndürülen ortak/özel anahtar çifti.  
  
 `pcbKeyBlob`  
 [out] Bayt cinsinden boyutu, `ppbKeyBlob`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` başarıyla tamamlandığında; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework sürümleri 1.0 ve 1.1 gerektiren bir `dwKeySize` derlemeyi bir katı adla imzalamak için 1024 bit 2048 bit anahtar için desteklenen sürüm 2.0 ekler.  
  
 Anahtarı aldıktan sonra çağırmalıdır [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) ayrılan belleği serbest bırakmak için işlevi.  
  
 Varsa `StrongNameKeyGenEx` işlevi değil başarıyla tamamlanması, çağrı [Strongnameerrorınfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) oluşturulan son hatayı alması için işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [StrongNameKeyGenEx Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
