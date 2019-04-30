---
title: GetNames işlevi (yönetilmeyen API Başvurusu)
description: GetNames işlevi, bir nesnenin özellik adlarını alır.
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
ms.openlocfilehash: f664edf29e5d2f9ec4e523aa7f7b204cf999e01b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61724089"
---
# <a name="getnames-function"></a>GetNames işlevi
Bir alt veya tümünü bir nesnenin özellik adlarını alır. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
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
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`wszQualifierName`  
[in] Geçerli bir işaretçi `LPCWSTR` filtre kapsamında işleyen bir niteleyici adını belirtir. Daha fazla bilgi için [açıklamalar](#remarks) bölümü. Bu parametre olabilir `null`. 

`lFlags`  
[in] Bit alanları bileşimi. Daha fazla bilgi için [açıklamalar](#remarks) bölümü.

`pQualifierValue`   
[in] Geçerli bir işaretçi `VARIANT` yapısı için bir filtre değeri başlatıldı. Bu parametre olabilir `null`. 

`pstrNames`  
[out] A `SAFEARRAY` özellik adları içeren yapısı. Girişte, bu parametre her zaman bir işaretçi olmalıdır `null`. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil veya yanlış bir birleşimi bayrakları ve parametreleri belirtildi. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) yöntemi.

Adlandırılmış döndürülen bayrakları ve parametre birleşimi tarafından denetlenir. Örneğin, işlevi, tüm özelliklerin adları veya yalnızca anahtar özellikler adları döndürebilir.  Birincil filtre belirtilen `lFlags` parametre ve diğer parametreler, bağlı olarak değişir.

Bayrak değeri `lFlags` bit alanları

Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni olan tanımlanan bit alanları *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda.  Herhangi diğer bir grup bayrağı ile her bir gruptan bir bayrak birleştirebilirsiniz. Ancak, aynı grup bayrakları birbirini dışlar. 

| Grup 1 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Tüm özellik adlarını döndürür. `strQualifierName` ve `pQualifierVal` kullanılmadı. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1. | Tarafından belirtilen adının niteleyicisi olan özellikler yalnızca dönüş `strQualifierName` parametresi. Bu bayrak kullanılırsa belirtmeniz gerekir `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Tarafından belirtilen adının niteleyicisi olmayan özellikler yalnızca dönüş `strQualifierName` parametresi. Bu bayrak kullanılırsa belirtmeniz gerekir `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Yalnızca bir niteleyici tarafından belirtilen adı taşıyan özellikler dönüş `wszQualifierName` parametre ve bir değer tarafından belirtilen aynı de `pQualifierVal` yapısı. Bu bayrak kullanılırsa, her ikisini de belirtmelisiniz bir `wszQualifierName` ve `pQualifierValue`. |

| Grup 2 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Yalnızca anahtarları tanımlayan özellik adlarını döndürür. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Nesne başvuruları olan dönüş yalnızca özellik adları. |

| Grup 3 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | En çok türetilen sınıfa ait özellik adlarını döndürür. Özellikleri, üst sınıflardan hariç tutun. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ana sınıfa ait özellik adlarını döndürür. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Yalnızca Sistem özellikleri adlarını döndürür. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yalnızca sistem dışı özellik adlarını döndürür. |

İşlev her zaman yeni bir ayırır `SAFEARRAY` döndürürse `WBEM_S_NO_ERROR`, ve `pstrNames` her zaman için işaret edecek şekilde ayarlayın. Döndürülen dizi hiçbir özellik belirtilen filtrelerle eşleşen 0 öğeleri olabilir. İşlev dışında bir değer döndürürse `WBM_S_NO_ERROR`, yeni bir `SAFEARRAY` yapısı alınmadı.
 
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
