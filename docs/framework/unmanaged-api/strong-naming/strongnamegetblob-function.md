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
ms.openlocfilehash: 8f5cb89294004dfb1f020627ceb1edb58735f72c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732287"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob İşlevi

Belirtilen adresteki yürütülebilir dosyanın ikili gösterimiyle belirtilen arabelleği doldurur.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [in, out] İstenen en büyük boyut (bayt) `pbBlob` . Dönüş sonrasında, bayt cinsinden gerçek boyut `pbBlob` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 `true` başarıyla tamamlandığında; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 `StrongNameGetBlob`İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak Için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** StrongName. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameGetBlob Yöntemi](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage Yöntemi](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
