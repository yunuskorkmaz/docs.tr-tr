---
title: StrongNameSignatureSize İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176896"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize İşlevi
Güçlü ad imzasının boyutunu döndürür. `StrongNameSignatureSize`genellikle derleyiciler tarafından, gecikme imzalı bir derleme oluştururken dosyada ne kadar alan ayırılabildiğini belirlemek için kullanılır.  
  
 Bu işlev amortismana kaldırıldı. Bunun yerine [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>Parametreler  
 `pbPublicKeyBlob`  
 [içinde] Güçlü ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](publickeyblob-structure.md) türünden bir yapı.  
  
 `cbPublicKeyBlob`  
 [içinde] Boyutu, bayt, ve. `pbPublicKeyBlob`  
  
 `pcbSize`  
 [içinde] Güçlü ad imzasını depolamak için gereken bayt sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarılı bir şekilde tamamlandığında; aksi `false`takdirde, .  
  
## <a name="remarks"></a>Açıklamalar  
 `StrongNameSignatureSize` İşlev başarıyla tamamlanmamışsa, oluşturulan son hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini arayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** StrongName.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameSignatureSize Yöntemi](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
