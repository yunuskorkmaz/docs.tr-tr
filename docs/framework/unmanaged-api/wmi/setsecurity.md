---
title: SetSecurity işlevi (yönetilmeyen API Başvurusu)
description: SetSecurity işlevi, geçerli iş parçacığının kimliğe bürünme belirtecini alır.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b3e8ddb34849611daae4dfa1d2762a25ac5cf82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721151"
---
# <a name="setsecurity-function"></a>SetSecurity işlevi
Geçerli iş parçacığıyla ilişkilendirilmiş kimliğe bürünme belirtecini alır.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a>Parametreler

`pNeedToReset` [out] İşlevi döndüğünde, bir işaretçi içeren bir `boolean` belirten belirteç çağırarak sıfırlama olmadığını [ResetSecurity](resetsecurity.md) işlevi.  

`token`  
[out] İşlevi döndüğünde, geçerli iş parçacığıyla ilişkilendirilmiş kimliğe bürünme belirtecini işlemek için bir işaretçi içerir. Değeri olabilir `null` geçerli iş parçacığıyla ilişkilendirilmiş hiçbir belirteç olup olmadığını. 

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri olduğu `S_OK` (0).

İşlev başarısız olursa, dönüş değeri sıfır olmayan hata kodudur. Genişletilmiş hata bilgilerini almak için arama [Geterrorınfo](geterrorinfo.md) işlevi.
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
