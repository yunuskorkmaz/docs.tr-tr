---
title: GetDemultiplexedStub fonksiyonu (Yönetilmeyen API Başvurusu)
description: GetDemultiplexedStub işlevi, istemcinin Windows Yönetimi'nden eşzamanlı çağrılar almasına yardımcı olmak için bir nesne iletme lavabosu oluşturur.
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
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174972"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub fonksiyonu
Windows Yönetimi'nden eşzamanlı çağrılar almada istemciye yardımcı olmak için bir nesne ilemör lavabosu oluşturur.
  
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
[içinde] [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)istemcinin süreç içinde uygulanması için bir işaretçi.

`isLocal`  
[içinde] Olayın yerel olup olmadığını belirten`true`bir bayrak ( ); aksi `false`takdirde, .

`ppObject`  
[çıkış] Windows Yönetimi'nden eşzamanlı çağrılar almada istemciye yardımcı olmak için bir nesne iletme lavabosu.

## <a name="return-value"></a>Döndürülen değer

İşlev başarılı olursa, iade `S_OK` değeri (0) olur.

İşlev başarısız olursa, iade değeri sıfır olmayan bir hata kodudur. Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini arayın.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
