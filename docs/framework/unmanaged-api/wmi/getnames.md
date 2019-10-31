---
title: GetNames işlevi (yönetilmeyen API Başvurusu)
description: GetNames işlevi bir nesnenin özelliklerinin adlarını alır.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b03ed6a68fbe288e93dedb4f425f1511563dfeb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102519"
---
# <a name="getnames-function"></a>GetNames işlevi
Bir nesnenin özelliklerinin bir alt kümesini ya da tümünü alır. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszQualifierName`  
'ndaki Bir filtrenin parçası olarak çalışan bir niteleyici adı belirten geçerli bir `LPCWSTR` işaretçisi. Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın. Bu parametre `null`olabilir. 

`lFlags`  
'ndaki Bit alanlarının birleşimi. Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın.

`pQualifierValue`   
'ndaki Filtre değerine başlatılan geçerli `VARIANT` yapısına yönelik bir işaretçi. Bu parametre `null`olabilir. 

`pstrNames`  
dışı Özellik adlarını içeren `SAFEARRAY` yapısı. Girişte, bu parametrenin `null`için her zaman bir işaretçi olması gerekir. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil veya bayrakların ve parametrelerin yanlış birleşimi belirtildi. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) yöntemine bir çağrı kaydırır.

Döndürülen adlı ad, bayrakların ve parametrelerin birleşimiyle denetlenir. Örneğin, işlev tüm özelliklerin adlarını veya yalnızca anahtar özelliklerinin adlarını döndürebilir.  Birincil filtre `lFlags` parametresinde belirtilir ve diğer parametreler buna bağlı olarak değişir.

`lFlags` bayrak değerleri bit alanlardır

`lEnumFlags` bağımsız değişkeni olarak geçirilebilecek bayraklar, *Wbemcli. h* üstbilgi dosyasında tanımlanan bit alanlardır veya kodunuzda sabitler olarak tanımlayabilirsiniz.  Her bir grup için herhangi bir bayrak ile bir bayrak birleştirebilirsiniz. Ancak, aynı gruptaki Bayraklar birbirini dışlıyor. 

| Grup 1 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Tüm özellik adlarını döndürür. `strQualifierName` ve `pQualifierVal` kullanılmıyor. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1\. | Yalnızca `strQualifierName` parametresi tarafından belirtilen adın niteleyicisi olan özellikleri döndürür. Bu bayrak kullanılırsa, `strQualifierName`belirtmeniz gerekir. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Yalnızca `strQualifierName` parametresi tarafından belirtilen adın niteleyicisi olmayan özellikleri döndürür. Bu bayrak kullanılırsa, `strQualifierName`belirtmeniz gerekir. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Yalnızca `wszQualifierName` parametresi tarafından belirtilen ad niteleyicisi olan ve ayrıca `pQualifierVal` yapısıyla belirtilen değere sahip olan özellikleri döndürür. Bu bayrak kullanılırsa, hem `wszQualifierName` hem de `pQualifierValue`belirtmeniz gerekir. |

| Grup 2 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 4, | Yalnızca anahtarları tanımlayan özelliklerin adlarını döndürür. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Yalnızca nesne başvuruları olan özellik adlarını döndürür. |

| Grup 3 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca en türetilmiş sınıfa ait olan özellik adlarını döndürür. Üst sınıflardan özellikleri dışlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Yalnızca üst sınıflara ait olan özellik adlarını döndürür. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Yalnızca sistem özelliklerinin adlarını döndürür. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yalnızca sistem dışı özelliklerin adlarını döndürür. |

İşlev `WBEM_S_NO_ERROR`döndürürse her zaman yeni bir `SAFEARRAY` ayırır ve `pstrNames` her zaman işaret etmek üzere ayarlanır. Belirtilen filtrelerle eşleşen hiçbir özellik yoksa döndürülen dizide 0 öğesi olabilir. İşlev `WBM_S_NO_ERROR`dışında bir değer döndürürse, yeni bir `SAFEARRAY` yapısı döndürülmez.
 
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
