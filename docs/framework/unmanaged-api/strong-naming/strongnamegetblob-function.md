---
title: StrongNameGetBlob İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d5b3d1d39b5d4c5b7d4db073b3ffaf1c6b88373
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799107"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob İşlevi
Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wszFilePath`  
 'ndaki Yüklenecek yürütülebilir dosyanın geçerli yolu.  
  
 `pbBlob`  
 'ndaki Yürütülebilir dosyanın yükleneceği arabellek.  
  
 `pcbBlob`  
 [in, out] İstenen en büyük boyut ( `pbBlob`bayt). Dönüş sonrasında, bayt `pbBlob`cinsinden gerçek boyut.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarıyla tamamlandığında; Aksi takdirde `false`,.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameGetBlob`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetBlob Yöntemi](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage Yöntemi](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
