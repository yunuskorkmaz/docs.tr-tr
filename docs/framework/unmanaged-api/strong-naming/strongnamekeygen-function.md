---
description: 'Daha fazla bilgi edinin: StrongNameKeyGen Işlevi'
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
ms.openlocfilehash: c5f4cfcfa9030ae856acf5fd59ab34a2b8338670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636276"
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
 'ndaki İstenen anahtar kapsayıcısı adı. `wszKeyContainer` geçici bir ad oluşturmak için boş olmayan bir dize veya null olmalıdır.  
  
 `dwFlags`  
 'ndaki Anahtarın kaydedilip edilmeyeceğini belirtir. Aşağıdaki değerler desteklenir:  
  
- 0x00000000- `wszKeyContainer` geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.  
  
- 0x00000001 ( `SN_LEAVE_KEY` )-anahtarın kayıtlı olması gerektiğini belirtir.  
  
 `ppbKeyBlob`  
 dışı Döndürülen ortak/özel anahtar çifti.  
  
 `pcbKeyBlob`  
 dışı Bayt cinsinden boyutu `ppbKeyBlob` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` başarıyla tamamlandığında; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 `StrongNameKeyGen`İşlevi 1024 bitlik bir anahtar oluşturur. Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.  
  
 `StrongNameKeyGen`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameKeyGen Yöntemi](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [StrongNameKeyGenEx Yöntemi](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
