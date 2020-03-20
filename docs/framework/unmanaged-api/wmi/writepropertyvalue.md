---
title: WritePropertyValue işlevi (Yönetilmeyen API Başvurusu)
description: WritePropertyValue işlevi bir özelliğe bayt yazar.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174842"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue fonksiyonu
Özellik tutamacı tarafından tanımlanan bir özelliğe belirli sayıda bayt yazar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneğine işaretçi.

`lHandle`  
[içinde] Bu özelliği tanımlayan tutamacı içeren bir tamsayı. Tanıtıcı [GetPropertyHandle](getpropertyhandle.md) işlevini arayarak alınabilir.

`lNumBytes`  
[içinde] Tesise yazılan bayt sayısı. Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.

`pHandle`[çıkış] Verileri içeren bayt dizisiiçin bir işaretçi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değildir. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Bir tür uyuşmazlığı oluştu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) yöntemine bir çağrı yıkıyor.

Dize ve diğer tüm`DWORD` `QWORD` veri olmayan veya olmayan ayarlamak için bu işlevi kullanın.

Non string özellik `lNumBytes` değerleri için, belirtilen özellik türünün doğru veri boyutu olmalıdır. Dize özellik `lNumBytes` değerleri için, baytlarda belirtilen dize uzunluğu olmalıdır ve dize kendisi bayt eşit uzunlukta olmalı ve bir null-sonlandırma karakteri ile takip edilmelidir.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
