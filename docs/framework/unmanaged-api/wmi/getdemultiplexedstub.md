---
title: GetDemultiplexedStub işlevi (yönetilmeyen API Başvurusu)
description: Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için nesne ileticisi havuzu GetDemultiplexedStub işlevi oluşturur.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4311a77c9159428bf7beacc99d4479acb28b91b6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482362"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub işlevi
Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için nesne ileticisi havuzu oluşturur.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>Parametreler

`pObject`  
[in] İstemci işlem içi uygulaması için bir işaretçi [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).

`isLocal`  
[in] Olay yerel olup olmadığını belirten bir bayrak (`true`); Aksi takdirde `false`.

`ppObject`  
[out] Bir istemcinin Windows Yönetimi'nden zaman uyumsuz bir çağrı alma yardımcı olmak için bir nesne ileticisi havuzu.

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri olduğu `S_OK` (0).

İşlev başarısız olursa, dönüş değeri sıfır olmayan hata kodudur. Genişletilmiş hata bilgilerini almak için arama [Geterrorınfo](geterrorinfo.md) işlevi.
    
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
