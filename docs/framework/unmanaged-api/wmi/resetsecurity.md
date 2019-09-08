---
title: ResetSecurity işlevi (yönetilmeyen API Başvurusu)
description: ResetSecurity işlevi, geçerli iş parçacığına bir kimliğe bürünme belirteci atar.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798260"
---
# <a name="resetsecurity-function"></a>ResetSecurity işlevi
Sağlanan kimliğe bürünme belirtecini geçerli iş parçacığına atar.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>Parametreler

`token`  
'ndaki Geçerli iş parçacığıyla ilişkilendirilecek kimliğe bürünme belirteci. Değeri olabilir `null`. 

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri (0) `S_OK` olur.

İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur. Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini çağırın.
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
