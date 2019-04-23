---
title: Geterrorınfo işlevi (yönetilmeyen API Başvurusu)
description: Geterrorınfo işlevi önceki işlev çağrısında hata bilgilerini alır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2df4b87016394d1998ef90abe2e3eeb911886ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217513"
---
# <a name="geterrorinfo-function"></a>Geterrorınfo işlevi
Önceki işlev çağrısında hata bilgilerini alır.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a>Dönüş değeri

Bir işaretçi bir [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) işlev çağrısı başarılı olursa, nesne veya `null` başarısız olması durumunda.
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.def  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
