---
title: "VerifyClientKey işlevi (yönetilmeyen API Başvurusu)"
description: "Doğru güvenlik istemci anahtara sahip VerifyClientKey işlevi sağlar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: VerifyClientKey
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: VerifyClientKey
helpviewer_keywords: VerifyClientKey function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cce10e3dd5536a85b4dee62cc7f6e9e8e73929cb
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
