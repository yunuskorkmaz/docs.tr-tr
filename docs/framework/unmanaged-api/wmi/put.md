---
title: "PUT işlevi (yönetilmeyen API Başvurusu)"
description: "Put işlevi adlı bir özellik için yeni bir değer atar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Put
helpviewer_keywords: Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c4ad979a3a662618ab62b52d63bda3dbb1e71b9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="put-function"></a>PUT işlevi
Adlandırılmış bir özelliği için yeni bir değer ayarlar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`wszName`  
[in] Özelliğin adı. Bu parametre olamaz `null`.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pVal`   
[in] Geçerli bir işaretçi `VARIANT` yeni özellik değeri olur. Varsa `pVal` olan `null` veya işaret eden bir `VARIANT` türü `VT_NULL`, özellik kümesine `null`. 

`vtType`  
[in] Türü `VARIANT` gösterdiği `pVal`. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.
 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Özellik türü tanınmıyor. Bu değer, sınıf zaten varsa sınıf örnekleri oluşturulurken döndürülür. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | İçin örnekleri: belirten `pVal` işaret eden bir `VARIANT` özelliği için yanlış bir türde. <br/> Sınıf tanımları için: üst sınıfta bir özellik zaten var ve yeni COM türü eski COM türünden farklıdır. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) yöntemi.

Bu işlev her zaman geçerli özellik değeri ile yeni bir tane üzerine yazar. Varsa [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) işaret eden bir sınıf tanımına `Put` oluşturur veya özellik değeri güncelleştirir. Zaman [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) işaret eden bir CIM örneğine `Put` özellik değeri yalnızca; güncelleştirir `Put` bir özellik değeri oluşturulamıyor.

`__CLASS` Sistem özelliği olduğunda yalnızca yazılabilir sınıfı oluşturma sırasında bunu boş bırakılamaz. Diğer tüm sistem özellikleri salt okunurdur.

Kullanıcı özellikleri başlayamaz veya bitemez bir alt çizgi ("_") adlarla oluşturulamıyor. Bu, sistem sınıfları ve özellikleri için ayrılmıştır.

Özelliği ayarlarsanız `Put` üst sınıfında exists işlevi, özellik türü üst sınıf türü eşleşmiyor sürece özelliğinin varsayılan değeri değiştirilir. Özelliği yok ve tür uyuşmazlığı değilse ceated özelliğidir.

Kullanım `vtType` yalnızca yeni özellikleri bir CIM sınıfı tanımında oluşturulurken parametre ve `pVal` olan `null` veya işaret eden bir `VARIANT` türü `VT_NULL`. Bu durumda, `vType` parametresi özelliği CIM türünü belirtir. Diğer her durumda `vtType` 0 olmalıdır. `vtType`temel alınan nesnede bir örneğiyse 0 olmalıdır (olsa bile `Val` olan `null`) çünkü özelliğinin türü sabittir ve değiştirilemez.   

## <a name="example"></a>Örnek

Bir örnek için bkz: [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
