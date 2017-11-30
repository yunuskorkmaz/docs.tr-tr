---
title: "GetObjectText işlevi (yönetilmeyen API Başvurusu)"
description: "GetObjectText işlevi bir nesnenin bir metinsel oluşturma MOF sözdiziminde döndürür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 27e25a7ab7131f5b1c995c9367de6fe5a6fae592
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getobjecttext-function"></a>GetObjectText işlevi
Nesnenin metinsel işleme Yönetilen Nesne Biçimi (MOF) sözdiziminde döndürür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`lFlags`  
[in] Normalde 0. Varsa `WBEM_FLAG_NO_FLAVORS` (veya 0x1) belirtilirse, niteleyicileri yayma veya özellik bilgileri olmadan dahil.

`pstrObjectText`   
[out] Bir işaretçi bir `null` girişi. Üzerinde dönün, yeni ayrılan `BSTR` nesnenin MOF sözdizimi işleme içerir.  

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) yöntemi.

Döndürülen MOF metni nesneyle ilgili tüm bilgileri, ancak yalnızca orijinal nesneyi yeniden yapabilmek MOF Derleyici yeterli bilgi içermiyor. Örneğin, hiçbir yayılan niteleyicileri veya üst sınıf özellikleri dahil edilir.

Aşağıdaki algoritması, bir yöntemin parametrelerini metnin yeniden oluşturmak için kullanılır:

1. Parametre tanımlayıcı değerlerini sırasına göre yeniden sıralanmış.
1. Olarak belirtilen parametreleri `[in]` ve `[out]` tek bir parametre birleştirilir.
 
`pstrObjectText`bir işaretçi olmalıdır bir `null` işlevi çağrıldığında; Bu işaretçinin değil serbest olduğundan yöntem çağrısı önce geçerli bir dize işaret etmelidir değil.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
