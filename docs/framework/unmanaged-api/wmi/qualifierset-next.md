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
ms.openlocfilehash: c9c824b0158618848c13183d92f88604460d5099
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141716"
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
dışı Niteleyicinin adı. `null`, bu parametre yok sayılır; Aksi takdirde, `pstrName` geçerli bir `BSTR` işaret etmelidir veya bir bellek sızıntısı oluşur. Null değilse, işlev `WBEM_S_NO_ERROR`döndürdüğünde her zaman yeni bir `BSTR` ayırır.

`pVal`   
dışı Başarılı olduğunda, niteleyicinin değeri. İşlev başarısız olursa, `pVal` tarafından işaret edilen `VARIANT` değiştirilmez. Bu parametre `null`, parametre yok sayılır.

`plFlavor`   
dışı Niteleyiciyi alan bir LONG işaretçisi. Flavor bilgileri istenmiyorsa, bu parametre `null`olabilir. 

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

İşlev `WBEM_S_NO_MORE_DATA`dönene kadar tüm niteleyicileri numaralandırmak için `QualifierSet_Next` işlevini tekrar tekrar çağırın. Numaralandırmayı erken sonlandırmak için [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevini çağırın.

Numaralandırma sırasında döndürülen niteleyicilerin sırası tanımsız.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
