---
title: GetNames işlevi (Yönetilmeyen API Başvurusu)
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174959"
---
# <a name="getnames-function"></a>GetNames işlevi
Bir alt kümeyi veya nesnenin özelliklerinin tüm adlarını alır.

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
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`wszQualifierName`  
[içinde] Bir filtrenin `LPCWSTR` parçası olarak çalışan bir niteleyici adı belirten bir geçerli için işaretçi. Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın. Bu parametre `null`olabilir .

`lFlags`  
[içinde] Bit alanlarının birleşimi. Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.

`pQualifierValue`[içinde] Filtre değerine `VARIANT` başlattı geçerli bir yapıiçin işaretçi. Bu parametre `null`olabilir .

`pstrNames`  
[çıkış] Özellik `SAFEARRAY` adları içeren bir yapı. Girişte, bu parametre her zaman `null`bir işaretçi olmalıdır. Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir başarısızlık oldu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değildir veya bayraklar ve parametrelerin yanlış bir birleşimi belirtilmiş. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) yöntemine bir çağrı yıkıyor.

Döndürülen ad, bayraklar ve parametrelerin birleşimi tarafından denetlenir. Örneğin, işlev tüm özelliklerin adlarını veya yalnızca anahtar özelliklerinin adlarını döndürebilir.  Birincil filtre `lFlags` parametrede belirtilir ve diğer parametreler buna bağlı olarak değişir.

Bayrak değerleri `lFlags` bit alanlarıdır

`lEnumFlags` Bağımsız değişken olarak geçirilebilen *bayraklar, WbemCli.h* üstbilgi dosyasında tanımlanan bit alanlarıdır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.  Her gruptan bir bayrağı başka bir gruptan herhangi bir bayrakla birleştirebilirsiniz. Ancak, aynı grubun bayrakları birbirini dışlar.

| Grup 1 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Tüm özellik adlarını döndürün. `strQualifierName`ve `pQualifierVal` kullanılmaz. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Yalnızca parametre tarafından belirtilen adı niteleyen `strQualifierName` özellikleri döndürün. Bu bayrak kullanılırsa, `strQualifierName`belirtmelisiniz. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Yalnızca parametre tarafından belirtilen adınitelemeye sahip `strQualifierName` olmayan özellikleri döndürün. Bu bayrak kullanılırsa, `strQualifierName`belirtmelisiniz. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Yalnızca `wszQualifierName` parametre tarafından belirtilen adı niteleyen ve yapı tarafından belirtilen değere sahip `pQualifierVal` özellikleri döndürün. Bu bayrak kullanılırsa, hem `wszQualifierName` a `pQualifierValue`hem de bir . belirtmeniz gerekir |

| Grup 2 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Yalnızca anahtarları tanımlayan özelliklerin adlarını döndürün. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Yalnızca nesne başvuruları olan özellik adlarını döndürün. |

| Grup 3 bayrakları |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca en çok türetilmiş sınıfa ait özellik adlarını döndürün. Özellikleri üst sınıflardan hariç tinler. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Yalnızca üst sınıflara ait özellik adlarını döndürün. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Yalnızca sistem özelliklerinin adlarını döndürün. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Yalnızca sistem dışı özelliklerin adlarını döndürün. |

İşlev her zaman `SAFEARRAY` yeni `WBEM_S_NO_ERROR` `pstrNames` bir döner ve her zaman onu işaret etmek için ayarlanır ayırır. Döndürülen dizi, belirtilen filtrelerle hiçbir özellik eşleşmezse 0 elemana sahip olabilir. İşlev, yeni bir `WBM_S_NO_ERROR` `SAFEARRAY` yapının döndürülmesi dışında bir değer döndürür.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
