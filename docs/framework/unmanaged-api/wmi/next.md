---
title: Next işlevi (yönetilmeyen API Başvurusu)
description: Sonraki işlev retireves numaralandırma sonraki özelliği.
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
ms.openlocfilehash: e945930a9a668d0a1c1e4c26bf3add9cc574c261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461434"
---
# <a name="next-function"></a>Next işlevi
Sonraki çağrı ile başlayan bir numaralandırma özelliğinde alır [BeginEnumeration](beginenumeration.md).  

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
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pstrName`  
[out] Yeni bir `BSTR` özellik adını içerir. Bu parametre ayarlayabileceğiniz `null` adı gerekli değilse.

`pVal`  
[out] A `VARIANT` özelliğinin değeri ile doldurulur. Bu parametre ayarlayabileceğiniz `null` değeri gerekli değilse. İşlevi bir hata kodu döndürürse `VARIANT` geçirilen `pVal` sol değiştirilmemiş. 

`pvtType`  
[out] Bir işaretçi bir `CIMTYPE` değişken (bir `LONG` özelliğinin türü yerleştirildiği içine). Bu özelliğin değeri olabilir bir `VT_NULL_VARIANT`, gerçek tür özelliğinin belirlemek gerekli değildir; bu durumda. Bu parametre de olabilir `null`. 

`plFlavor`  
[out] `null`, veya özelliğin kaynak hakkında bilgi alan bir değer. Olası değerler [uyarılar] bölümüne bakın. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçersiz. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Hiçbir çağrısına vardı [ `BeginEnumeration` ](beginenumeration.md) işlevi. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Uzak yordam çağrısı zamanlamalar geçerli işlem ile Windows Yönetimi başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Sabit listede daha fazla özellik yok. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) yöntemi.

Bu yöntem aynı zamanda Sistem özellikleri döndürür.

Özelliğin temel türü bir nesne yolu, bir tarih veya saat veya başka bir özel tür ise, döndürülen tür yeterli bilgi içermiyor. Arayan incelemelisiniz `CIMTYPE` özelliği bir nesne başvurusu, bir tarih veya saat veya başka bir özel tür olup olmadığını belirlemek belirtilen özellik için.

Varsa `plFlavor` değil `null`, `LONG` değer özelliğinin kaynak hakkında bilgi aşağıdaki gibi alır:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Özelliği bir standart sistemi özelliğidir. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Bir sınıf için: özellik üst sınıftan devralındı. </br> Bir örneği için: özellik üst sınıftan devralındı ederken örneği tarafından değiştirildi.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Bir sınıf için: türetilmiş sınıf özellik ait. </br> Bir örneği için: özelliğini örneği tarafından; değiştirdi diğer bir deyişle, bir değer sağlandı veya bir niteleyicisi eklenemez veya değiştirilemez. |

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
