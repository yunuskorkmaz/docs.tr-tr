---
title: "GetNames işlevi (yönetilmeyen API Başvurusu)"
description: "GetNames işlevi bir nesnenin özellik adlarını alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetNames
helpviewer_keywords: GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80284900c318a3776168b781ce2e0e5e4a68f96d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`wszQualifierName`  
[in] Geçerli bir işaretçi `LPCWSTR` bir filtre bir parçası olarak çalışır bir niteleyici adını belirtir. Daha fazla bilgi için bkz: [açıklamalar](#remarks) bölümü. Bu parametre olabilir `null`. 

`lFlags`  
[in] Bit alanları birleşimi. Daha fazla bilgi için bkz: [açıklamalar](#remarks) bölümü.

`pQualifierValue`   
[in] Geçerli bir işaretçi `VARIANT` yapısı için bir filtre değeri başlatılmadı. Bu parametre olabilir `null`. 

`pstrNames`  
[out] A `SAFEARRAY` özellik adları içeren yapısı. Üzerinde bu parametre her zaman bir işaretçi girilmelidir `null`. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil veya yanlış bir birleşimi bayrakları ve parametreleri belirtildi. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) yöntemi.

Adlandırılmış döndürülen bayrakları ve parametre birleşimi tarafından denetlenir. Örneğin, işlev tüm özellik adlarını veya yalnızca anahtar özellikler adları döndürebilir.  Birincil filtre belirtilen `lFlags` parametresi ve diğer parametreler, bağlı olarak farklılık.

Bayrak değerleri `lFlags` bit alanları


Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni olan tanımlanan bit alanları *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.  Diğer bir gruptaki tüm bayrağıyla her grubundan bir bayrak birleştirebilirsiniz. Ancak, aynı gruptan bayrakları karşılıklı olarak birbirini dışlar. 

| Grup 1 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Tüm özellik adlarını döndürür. `strQualifierName`ve `pQualifierVal` kullanılmayan. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1. | Niteleyici tarafından belirtilen adının sahip yalnızca Özellikler `strQualifierName` parametresi. Bu bayrak kullanılıp kullanılmadığını belirtmeniz gerekir `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Tarafından belirtilen adının niteleyicisi yok yalnızca Özellikler `strQualifierName` parametresi. Bu bayrak kullanılıp kullanılmadığını belirtmeniz gerekir `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Niteleyici tarafından belirtilen adı olan özellikler `wszQualifierName` parametre ve ayrıca bir değer tarafından belirtilen aynı `pQualifierVal` yapısı. Bu bayrak kullanılırsa, her ikisini de belirtmelisiniz bir `wszQualifierName` ve `pQualifierValue`. |

| Grup 2 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Yalnızca anahtarları tanımlayan özellikleri adlarını döndürür. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Nesne başvuruları dönüş yalnızca özellik adları. |

| Grup 3 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | En çok türetilen sınıfına ait özellik adlarını döndürür. Özellikleri üst sınıflardan çıkarın. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Üst sınıflarına ait özellik adlarını döndürür. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Yalnızca Sistem özellikleri adlarını döndürür. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yalnızca sistem dışı özellik adlarını döndürür. |

İşlevi her zaman yeni bir ayırır `SAFEARRAY` döndürürse `WBEM_S_NO_ERROR`, ve `pstrNames` her zaman üzerine ayarlanır. Verilen dizi özellik belirtilen filtrelerle eşleşen 0 öğeleri olabilir. İşlevi dışındaki bir değer döndürürse `WBM_S_NO_ERROR`, yeni bir `SAFEARRAY` yapısı alınmadı.
 
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
