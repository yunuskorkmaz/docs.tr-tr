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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff64be47802a46979818ab54cc3efb4112dd05e0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798620"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType işlevi
Çağıranın yürütüldüğü grup türünü alır.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
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

## <a name="return-value"></a>Dönüş değeri

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `S_OK` | 0 | İşlev başarıyla tamamlandı. |
| `E_FAIL` | 0x80000008 | Arayan bir grupta yürütülmüyor. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [ICommandText Threadingınfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metoduna bir çağrıyı sarmalanmış.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
