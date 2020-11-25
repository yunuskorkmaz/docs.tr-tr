---
title: GetCurrentApartmentType işlevi (yönetilmeyen API Başvurusu)
description: GetCurrentApartmentType işlevi, çağıranın yürütüldüğü grup türünü alır.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0832867d86b7dda80e037846d9aa66c1d37f87be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726203"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType işlevi

Çağıranın yürütüldüğü grup türünü alır.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [Iomthreadingınfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) örneğine yönelik bir işaretçi.

`aptType`  
dışı Arayanın Apartmanı belirten bir [Apttype](/windows/win32/api/objidlbase/ne-objidlbase-apttype) numaralandırma değeri işaretçisi.

## <a name="return-value"></a>Döndürülen değer

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `S_OK` | 0 | İşlev başarıyla tamamlandı. |
| `E_FAIL` | 0x80000008 | Arayan bir grupta yürütülmüyor. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [ICommandText Threadingınfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metoduna bir çağrıyı sarmalanmış.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
