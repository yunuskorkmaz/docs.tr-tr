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
ms.openlocfilehash: 54d79a3dc081e9cdcb42153b6f7aa457557e3399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721133"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next işlevi

[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevine yapılan çağrıyla başlatılan bir Numaralandırmadaki bir sonraki niteleyiciyi alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Söz dizimi  
  
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

`vFunc` 'ndaki Bu parametre kullanılmıyor.

`ptr` 'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

`lFlags` 'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pstrName` dışı Niteleyicinin adı. `null`Bu parametre yok sayılır; Aksi takdirde, `pstrName` geçerli bir `BSTR` veya bir Bellek sızıntısının gerçekleşmemelidir. Null değilse, işlev her zaman döndürüldüğünde yeni bir değer ayırır `BSTR` `WBEM_S_NO_ERROR` .

`pVal` dışı Başarılı olduğunda, niteleyicinin değeri. İşlev başarısız olursa, `VARIANT` tarafından işaret edilen `pVal` değiştirilmez. Bu parametre ise `null` parametresi yok sayılır.

`plFlavor` dışı Niteleyiciyi alan bir LONG işaretçisi. Flavor bilgileri istenmiyorsa, bu parametre olabilir `null` .

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_UNEXPECTED` | 0x8004101D | Çağıran [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)çağırmadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada başka niteleyiciler kalmadı. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) yöntemine bir çağrı kaydırır.

İşlev `QualifierSet_Next` döndürülünceye kadar tüm niteleyicileri numaralandırmak için işlevi tekrar tekrar çağırın `WBEM_S_NO_MORE_DATA` . Numaralandırmayı erken sonlandırmak için [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevini çağırın.

Numaralandırma sırasında döndürülen niteleyicilerin sırası tanımsız.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
