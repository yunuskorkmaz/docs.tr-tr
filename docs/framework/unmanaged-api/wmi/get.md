---
title: Get işlevi (yönetilmeyen API Başvurusu)
description: Get işlevi, belirtilen özellik değerini alır.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f837a526879f80177bc9979e1d7671edfcd8d4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460154"
---
# <a name="get-function"></a>Get işlevi
Varsa belirtilen özellik değerini alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
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

`wszName`  
[in] Özelliğin adı.

`lFlags` [in] Ayrılmış. Bu parametre 0 olmalıdır.

`pVal` [out] İşlev başarıyla döndürürse, değerini içeren `wszName` özelliği. `pval` Bağımsız değişkeni doğru türü ve değerine Niteleyici için atanır.

`pvtType` [out] İşlev başarıyla döndürürse, içeren bir [CIM türü sabiti](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) özellik türü gösterir. Değerini de olabilir `null`. 

`plFlavor` [out] İşlev başarıyla döndürürse, özelliğin kaynak hakkında bilgi alır. Değerini olabilir `null`, veya tanımlanan WBEM_FLAVOR_TYPE sabitlerden biri *WbemCli.h* üstbilgi dosyası: 

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Özelliği bir standart sistemi özelliğidir. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Bir sınıf için: özellik üst sınıftan devralındı. </br> Bir örneği için: özellik üst sınıftan devralındı ederken örneği tarafından değiştirildi.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Bir sınıf için: türetilmiş sınıf özellik ait. </br> Bir örneği için: özelliğini örneği tarafından; değiştirdi diğer bir deyişle, bir değer sağlandı veya bir niteleyicisi eklenemez veya değiştirilemez. |

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik bulunamadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) yöntemi.

`Get` İşlevi ayrıca sistem özellikleri döndürür.

`pVal` Bağımsız değişkeni doğru türü ve değerine niteleyici ve COM için atanan [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) işlevi

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
