---
title: QualifierSet_Next işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Next işlevi bir Numaralandırmadaki bir sonraki niteleyiciyi alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f97a19f236b87a7f4c5b2014aca6ee4abd338c63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798287"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next işlevi
Bir [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi çağrısıyla başlatılan bir Numaralandırmadaki bir sonraki niteleyiciyi alır.   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
'ndaki Bu parametre kullanılmıyor.

`ptr`   
'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

`lFlags`   
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pstrName`   
dışı Niteleyicinin adı. Bu parametre yok sayılır; Aksi takdirde, `pstrName` geçerli `BSTR` bir veya bir Bellek sızıntısının gerçekleşmemelidir. `null` Null değilse, işlev her zaman döndürüldüğünde `BSTR` `WBEM_S_NO_ERROR`yeni bir değer ayırır.

`pVal`   
dışı Başarılı olduğunda, niteleyicinin değeri. İşlev başarısız olursa, `VARIANT` tarafından `pVal` işaret edilen değiştirilmez. Bu parametre ise `null`parametresi yok sayılır.

`plFlavor`   
dışı Niteleyiciyi alan bir LONG işaretçisi. Flavor bilgileri istenmiyorsa, bu parametre olabilir `null`. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_UNEXPECTED` | 0x8004101D | Çağıran, [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)çağrısını gerçekleştirmedi. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada başka niteleyiciler kalmadı. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) yöntemine bir çağrı kaydırır.

İşlev döndürülünceye `QualifierSet_Next` `WBEM_S_NO_MORE_DATA`kadar tüm niteleyicileri numaralandırmak için işlevi tekrar tekrar çağırın. Numaralandırmayı erken sonlandırmak için [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevini çağırın.

Numaralandırma sırasında döndürülen niteleyicilerin sırası tanımsız.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
