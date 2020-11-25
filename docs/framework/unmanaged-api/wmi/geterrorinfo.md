---
title: GetErrorInfo işlevi (yönetilmeyen API Başvurusu)
description: GetErrorInfo işlevi, önceki işlev çağrısından hata bilgilerini alır.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5da4eaa459c515689b822e4cb537380245e800e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722771"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo işlevi

Önceki işlev çağrısından hata bilgilerini alır.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a>Döndürülen değer

İşlev çağrısı başarılı olursa veya başarısız olursa bir [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) nesnesine yönelik bir işaretçi `null` .
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [ICommandText Threadingınfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemine bir çağrı kaydırır.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. def  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
