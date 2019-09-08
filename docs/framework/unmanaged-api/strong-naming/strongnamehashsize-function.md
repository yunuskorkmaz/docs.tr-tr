---
title: StrongNameHashSize İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53384a5aa7f8d11f868057f892f7b60aac2e9f02
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799031"
---
# <a name="strongnamehashsize-function"></a>StrongNameHashSize İşlevi
Belirtilen karma algoritmasını kullanarak bir karma için gereken arabellek boyutunu alır.  
  
 Bu işlev kullanım dışı bırakıldı. Bunun yerine [ICLRStrongName:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ulHashAlg`  
 'ndaki Arabellek boyutunu hesaplamak için kullanılan karma algoritması.  
  
 `pcbSize`  
 dışı Bayt cinsinden döndürülen arabellek boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`başarıyla tamamlandığında; Aksi takdirde `false`,.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo işlevini çağırın.](strongnameerrorinfo-function.md) `StrongNameHashSize`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** StrongName. h  
  
 **Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [StrongNameHashSize Yöntemi](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [ICLRStrongName Arabirimi](../hosting/iclrstrongname-interface.md)
