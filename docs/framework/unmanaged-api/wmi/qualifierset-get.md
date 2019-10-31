---
title: QualifierSet_Get işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Get işlevi adlandırılmış bir niteleyiciyi alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: dc09cd30c43647fa00cccc1dc00da4f8de367e84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127272"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get işlevi
Belirtilen adlandırılmış niteleyiciyi alır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
'ndaki Bu parametre kullanılmıyor.

`ptr`   
'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

`wszName`   
'ndaki Değeri istenen niteleyicinin adı.

`lFlags`   
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pVal`   
dışı Başarılı olduğunda, niteleyicisi için doğru tür ve değer. İşlev başarısız olursa, `pVal` tarafından işaret edilen `VARIANT` değiştirilmez. Bu parametre `null`, parametre yok sayılır.

`plFlavor`   
dışı İstenen niteleyici için niteleyici Flavor bitlerini alan bir LONG işaretçisi. Flavor bilgileri istenmiyorsa, bu parametre `null`olabilir. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen niteleyici yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) yöntemine bir çağrı kaydırır.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
