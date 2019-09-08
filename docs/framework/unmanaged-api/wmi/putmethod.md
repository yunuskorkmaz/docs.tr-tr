---
title: PutMethod işlevi (yönetilmeyen API Başvurusu)
description: PutMethod işlevi bir yöntem oluşturur.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b41cbbade9da5c2095309b9039b8ce2758f6f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798354"
---
# <a name="putmethod-function"></a>PutMethod işlevi
Bir yöntem oluşturur.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszName`  
'ndaki Oluşturulacak yöntemin adı. 

`lFlags`  
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pSignatureIn`  
'ndaki Yönteminin `in` parametrelerini içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) kopyasına yönelik bir işaretçi. Olarak `null`ayarlanırsa, bu parametre yoksayılır.  

`pSignatureOut`  
'ndaki  Yönteminin `out` parametrelerini içeren [__Parameters sistem sınıfının](/windows/desktop/WmiSdk/--parameters) kopyasına yönelik bir işaretçi. Olarak `null`ayarlanırsa, bu parametre yoksayılır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Hem pinsignature hem de *poutsignature* nesnelerinde belirtilen methodparametresifarklıniteleyicileresahip.`[in, out]`
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Yöntem parametresinde **kimlik** niteleyicisi belirtimi eksik. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Yöntem parametrelerine atanan KIMLIK serisi ardışık değildir veya 0 ' dan başlamaz. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Bir yöntemin dönüş değeri bir **kimlik** niteleyicisi içeriyor. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Bir üst sınıftan var olan bir yöntem adının yeniden kullanılması denendi ve imzalar eşleşmedi. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject::P utMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemine bir çağrı kaydırır.

Bu yöntem çağrısı yalnızca bir CIM sınıf `ptr` tanımınise desteklenir. Yöntem işleme, CıM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçilerinden kullanılamıyor.

Kullanıcılar alt çizgiyle başlayan veya biten adlara sahip Yöntemler oluşturamaz. Bu sistem sınıfları ve özellikleri için ayrılmıştır.

Bir yöntem `in` için, ve `out` parametreleri [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) nesnelerinde özellikler olarak açıklanır.

Bir `[in/out]` parametre, `pInSignature` ve `pOutSignature` parametreleri tarafından işaret edilen her iki nesneye aynı özelliği eklenerek tanımlanabilir. Bu durumda, özellikler aynı **kimlik** niteleyicisi değerini paylaşır.

Bir [__Parameters](/windows/desktop/WmiSdk/--parameters) sınıf nesnesindeki `ReturnValue` her bir özelliğin, parametrelerin görünme sırasını tanımlayan sıfır tabanlı sayısal bir değer olan bir **ID** niteleyicisi olmalıdır. İki parametre aynı **kimlik** değerine sahip olamaz ve hiçbir **kimlik** değeri atlanmaz. Herhangi bir koşul oluşursa, `PutMethod` işlev döndürür. `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`

## <a name="example"></a>Örnek

Bir örnek için, bkz. [IWbemClassObject::P utMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
