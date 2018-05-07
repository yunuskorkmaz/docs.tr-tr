---
title: VerifyClientKey işlevi (yönetilmeyen API Başvurusu)
description: Doğru güvenlik istemci anahtara sahip VerifyClientKey işlevi sağlar.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea8a74633d3e950f6cf7ba87c00a9efa45206545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="verifyclientkey-function"></a>VerifyClientKey işlevi
İstemci anahtar doğru güvenlik sahip olmasını sağlar.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri olan `ERROR_SUCCESS` (0).

İşlev başarısız olursa, dönüş değeri tanımlanan bir sıfır olmayan bir hata kodu *Winerror.h'de*.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.def  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
