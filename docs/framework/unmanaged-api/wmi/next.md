---
title: Sonraki işlev (yönetilmeyen API Başvurusu)
description: Sonraki işlev retireves sonraki özelliğini bir sabit listesi.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c6e39c1bc4c2860e400e2708e588416eb5769bd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971890"
---
# <a name="next-function"></a>Next işlevi
Bir çağrı ile başlayan bir listedeki sonraki özelliği alır [BeginEnumeration](beginenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pstrName`  
[out] Yeni bir `BSTR` içeren özellik adı. Bu parametre ayarlayabileceğiniz `null` adı gerekli değilse.

`pVal`  
[out] A `VARIANT` özelliğinin değeri ile doldurulur. Bu parametre ayarlayabileceğiniz `null` değer gerekli değilse. İşlev bir hata kodu döndürmesi durumunda `VARIANT` geçirilen `pVal` sol değiştirilmemiş. 

`pvtType`  
[out] Bir işaretçi bir `CIMTYPE` değişkeni (bir `LONG` özelliğinin türü yerleştirildiği halinde). Bu özelliğin değeri olabilir bir `VT_NULL_VARIANT`, bu durumda özelliğinin gerçek türü belirlemek gerekli olur. Bu parametre aynı zamanda olabilir `null`. 

`plFlavor`  
[out] `null`, veya kaynak hakkında bilgi özelliğinin alan bir değer. Olası değerler için [açıklamalar] bölümüne bakın. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Hiçbir çağrı oluştu [ `BeginEnumeration` ](beginenumeration.md) işlevi. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Uzak yordam, Windows Yönetim başarısız oldu ve işlemin zamanlamalar çağırın. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Sabit listede daha fazla özellik vardır. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) yöntemi.

Bu yöntem Ayrıca Sistem özellikleri döndürür.

Özelliğin temel alınan türü bir nesne yolu, bir tarih veya saat veya başka bir özel türü ise, döndürülen tür yeterli bilgi içermiyor. Çağıranın incelemelisiniz `CIMTYPE` özelliği bir nesne başvurusu, bir tarih veya saat veya başka bir özel tür olup olmadığını belirlemek belirtilen özellik için.

Varsa `plFlavor` değil `null`, `LONG` değeri özellik kaynağı hakkındaki bilgileri aşağıdaki gibi alır:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Standart sistem özelliği özelliğidir. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Bir sınıf için: Özellik üst sınıftan devralındı. <br> Bir örneği için: Özellik üst sınıftan devralındı sırada örneği tarafından değiştirilmedi.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Bir sınıf için: Özelliği, türetilmiş bir sınıfa aittir. <br> Bir örneği için: Özellik örneği ile değiştirilir; diğer bir deyişle, bir değer sağlanmamış veya niteleyicisi eklenemez veya değiştirilemez. |

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
