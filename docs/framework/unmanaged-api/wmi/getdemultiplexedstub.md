---
title: GetDemultiplexedStub işlevi (yönetilmeyen API Başvurusu)
description: GetDemultiplexedStub işlevi, bir istemcinin Windows yönetiminden zaman uyumsuz çağrılar almasına yardımcı olmak için bir nesne iletici havuzu oluşturur.
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
ms.openlocfilehash: 9cc028b3300b43f8a0fb3e29f8b5ac6e1817b8c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127466"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub işlevi
Bir istemciye Windows yönetiminden zaman uyumsuz çağrılar alma konusunda yardımcı olmak için bir nesne iletici havuzu oluşturur.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>Parametreler

`pObject`  
'ndaki İstemcinin işlem içi [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)uygulamasına yönelik bir işaretçi.

`isLocal`  
'ndaki Olayın yerel olup olmadığını belirten bayrak (`true`); Aksi takdirde, `false`.

`ppObject`  
dışı Windows yönetiminden zaman uyumsuz çağrılar alırken bir istemciye yardımcı olmak için bir nesne ileticisi Havuzu.

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri `S_OK` (0).

İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur. Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini çağırın.
    
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
