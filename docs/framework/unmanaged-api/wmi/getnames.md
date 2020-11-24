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
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687664"
---
# <a name="getnames-function"></a>GetNames işlevi

Bir nesnenin özelliklerinin bir alt kümesini ya da tümünü alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Söz dizimi  
  
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
'ndaki Bir `LPCWSTR` filtrenin parçası olarak çalışan bir niteleyici adı belirten geçerli bir işaretçisi. Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın. Bu parametre olabilir `null` .

`lFlags`  
'ndaki Bit alanlarının birleşimi. Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın.

`pQualifierValue` 'ndaki `VARIANT` Filtre değerine başlatılan geçerli bir yapıya yönelik işaretçi. Bu parametre olabilir `null` .

`pstrNames`  
dışı `SAFEARRAY` Özellik adlarını içeren bir yapı. Girişte, bu parametrenin her zaman bir işaretçi olması gerekir `null` . Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil veya bayrakların ve parametrelerin yanlış birleşimi belirtildi. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) yöntemine bir çağrı kaydırır.

Döndürülen adlı ad, bayrakların ve parametrelerin birleşimiyle denetlenir. Örneğin, işlev tüm özelliklerin adlarını veya yalnızca anahtar özelliklerinin adlarını döndürebilir.  Birincil filtre `lFlags` parametresinde belirtilir ve diğer parametreler buna bağlı olarak farklılık gösterir.

İçindeki bayrak değerleri `lFlags` bit alanlardır

Bağımsız değişken olarak geçirilebilecek bayraklar, `lEnumFlags` *Wbemcli. h* üstbilgi dosyasında tanımlanan bit alanlardır veya kodunuzda sabitler olarak tanımlayabilirsiniz.  Her bir grup için herhangi bir bayrak ile bir bayrak birleştirebilirsiniz. Ancak, aynı gruptaki Bayraklar birbirini dışlıyor.

| Grup 1 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Tüm özellik adlarını döndürür. `strQualifierName` ve `pQualifierVal` kullanılmıyor. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Yalnızca parametresi tarafından belirtilen ad niteleyicisi olan özellikleri döndürür `strQualifierName` . Bu bayrak kullanılırsa, belirtmeniz gerekir `strQualifierName` . |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Yalnızca parametresi tarafından belirtilen adın niteleyicisi olmayan özellikleri döndürür `strQualifierName` . Bu bayrak kullanılırsa, belirtmeniz gerekir `strQualifierName` . |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Yalnızca parametresi tarafından belirtilen ad niteleyicisi olan `wszQualifierName` ve aynı zamanda yapı tarafından belirtilen bir değere sahip olan özellikleri döndürür `pQualifierVal` . Bu bayrak kullanılırsa, hem a hem de belirtmeniz gerekir `wszQualifierName` `pQualifierValue` . |

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

İşlevi, döndürürse her zaman yeni bir ayırır `SAFEARRAY` `WBEM_S_NO_ERROR` ve `pstrNames` her zaman onu işaret etmek üzere ayarlanır. Belirtilen filtrelerle eşleşen hiçbir özellik yoksa döndürülen dizide 0 öğesi olabilir. İşlev dışında bir değer döndürürse `WBM_S_NO_ERROR` , yeni bir `SAFEARRAY` Yapı döndürülmez.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
