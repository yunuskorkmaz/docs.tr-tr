---
title: GetErrorInfo işlevi (Yönetilmeyen API Başvurusu)
description: GetErrorInfo işlevi önceki işlev çağrısından hata bilgilerini alır.
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
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176818"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo fonksiyonu
Önceki işlev çağrısından hata bilgilerini alır.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a>Döndürülen değer

İşlev çağrısı başarılı olursa veya `null` başarısız olursa [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) nesnesine işaretçi.
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemine bir çağrı yıkıyor.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.def  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
