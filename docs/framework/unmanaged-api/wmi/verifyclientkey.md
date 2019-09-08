---
title: VerifyClientKey işlevi (yönetilmeyen API Başvurusu)
description: VerifyClientKey işlevi, istemci anahtarının doğru güvenliğe sahip olmasını sağlar.
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
ms.openlocfilehash: b674e959ab93cf76b84e2af41e875a50b7d115f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798196"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey işlevi
İstemci anahtarının doğru güvenliğe sahip olmasını sağlar.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri (0) `ERROR_SUCCESS` olur.

İşlev başarısız olursa, dönüş değeri, *Winerror. h*içinde tanımlanan sıfır olmayan bir hata kodudur.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. def  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
