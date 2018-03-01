---
title: "GetDemultiplexedStub işlevi (yönetilmeyen API Başvurusu)"
description: "GetDemultiplexedStub işlevi bir istemci zaman uyumsuz çağrılar Windows Yönetimi'nden alma yardımcı olması için bir nesne iletici havuz oluşturur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f53ee18345347f506a404a22bf5bfea6af037463
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub işlevi
Windows Yönetimi'nden zaman uyumsuz çağrılar alırken bir istemci yardımcı olması için bir nesne iletici havuz oluşturur.
  
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
[in] İstemcinin işlemdeki uygulaması için bir işaretçi [IWbemObjectSink](https://msdn.microsoft.com/library/aa391787(v=vs.85).aspx).

`isLocal`  
[in] Olay yerel olup olmadığını belirten bir bayrak (`true`); Aksi halde, `false`.

`ppObject`  
[out] Windows Yönetimi'nden zaman uyumsuz çağrılar alırken bir istemci yardımcı olması için bir nesne iletici havuzu.

## <a name="return-value"></a>Dönüş değeri

İşlev başarılı olursa, dönüş değeri olan `S_OK` (0).

İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur. Genişletilmiş hata bilgilerini için arama [Geterrorınfo](geterrorinfo.md) işlevi.
    
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
