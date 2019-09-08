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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 748767596a8f4680a2d7b63cb0579acaed5f53f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798518"
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
'ndaki Bir filtrenin parçası olarak çalışan `LPCWSTR` bir niteleyici adı belirten geçerli bir işaretçisi. Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın. Bu parametre `null`olabilir. 

`lFlags`  
'ndaki Bit alanlarının birleşimi. Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın.

`pQualifierValue`   
'ndaki Filtre değerine başlatılan geçerli `VARIANT` bir yapıya yönelik işaretçi. Bu parametre `null`olabilir. 

`pstrNames`  
dışı Özellik `SAFEARRAY` adlarını içeren bir yapı. Girişte, bu parametrenin her zaman bir işaretçi `null`olması gerekir. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın. 

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

Döndürülen adlı ad, bayrakların ve parametrelerin birleşimiyle denetlenir. Örneğin, işlev tüm özelliklerin adlarını veya yalnızca anahtar özelliklerinin adlarını döndürebilir.  Birincil filtre `lFlags` parametresinde belirtilir ve diğer parametreler buna bağlı olarak farklılık gösterir.

İçindeki `lFlags` bayrak değerleri bit alanlardır

`lEnumFlags` Bağımsız değişken olarak geçirilebilecek bayraklar, *wbemcli. h* üstbilgi dosyasında tanımlanan bit alanlardır veya kodunuzda sabitler olarak tanımlayabilirsiniz.  Her bir grup için herhangi bir bayrak ile bir bayrak birleştirebilirsiniz. Ancak, aynı gruptaki Bayraklar birbirini dışlıyor. 

| Grup 1 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Tüm özellik adlarını döndürür. `strQualifierName`ve `pQualifierVal` kullanılmıyor. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1\. | Yalnızca `strQualifierName` parametresi tarafından belirtilen ad niteleyicisi olan özellikleri döndürür. Bu bayrak kullanılırsa, belirtmeniz `strQualifierName`gerekir. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Yalnızca `strQualifierName` parametresi tarafından belirtilen adın niteleyicisi olmayan özellikleri döndürür. Bu bayrak kullanılırsa, belirtmeniz `strQualifierName`gerekir. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Yalnızca `wszQualifierName` parametresi tarafından belirtilen ad niteleyicisi olan ve aynı zamanda `pQualifierVal` yapı tarafından belirtilen bir değere sahip olan özellikleri döndürür. Bu bayrak kullanılırsa, hem a `wszQualifierName` `pQualifierValue`hem de belirtmeniz gerekir. |

| Grup 2 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Yalnızca anahtarları tanımlayan özelliklerin adlarını döndürür. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Yalnızca nesne başvuruları olan özellik adlarını döndürür. |

| Grup 3 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca en türetilmiş sınıfa ait olan özellik adlarını döndürür. Üst sınıflardan özellikleri dışlayın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Yalnızca üst sınıflara ait olan özellik adlarını döndürür. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Yalnızca sistem özelliklerinin adlarını döndürür. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yalnızca sistem dışı özelliklerin adlarını döndürür. |

İşlevi, döndürürse `WBEM_S_NO_ERROR`her zaman yeni `SAFEARRAY` bir ayırır ve `pstrNames` her zaman onu işaret etmek üzere ayarlanır. Belirtilen filtrelerle eşleşen hiçbir özellik yoksa döndürülen dizide 0 öğesi olabilir. İşlev dışında `WBM_S_NO_ERROR`bir değer döndürürse, yeni `SAFEARRAY` bir yapı döndürülmez.
 
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
