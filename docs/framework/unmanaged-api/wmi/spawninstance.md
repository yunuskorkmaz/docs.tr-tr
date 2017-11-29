---
title: "SpawnInstance işlevi (yönetilmeyen API Başvurusu)"
description: "SpawnInstance işlevi bir sınıfının yeni bir örneğini oluşturur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnInstance
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnInstance
helpviewer_keywords: SpawnInstance function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 65050772e2f933583506b6612c32c6060f1d20df
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="spawninstance-function"></a>SpawnInstance işlevi
Bir sınıfın yeni bir örneğini oluşturur.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`ppNewInstance`  
[out] İşaretçi sınıfının yeni örneğini alır. Bir hata oluşursa, yeni bir nesne değil döndürülen ve `ppNewInstance` sol değiştirilmemiş.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`Geçerli bir sınıf tanımı değil ve yeni örnekleri oluşturma olamaz. Eksik ya da, Windows yönetimiyle çağırarak kaydedilmedi [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass`olan `null`. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemclassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) yöntemi.

`ptr`bir sınıf tanımı Windows Yönetimi'nden alınması gerekir. (Örneğini örneğinden oluşturma desteklenir, ancak döndürülen örneği boştur unutmayın.) Ardından yeni örnekleri oluşturmak için bu sınıf tanımını kullanın. Çağrı [PutInstanceWmi](putinstancewmi.md) işlevi, Windows Yönetimi için örnek yazmak istiyorsanız gereklidir.




Döndürülen yeni nesne `ppNewClass` otomatik olarak geçerli nesnenin bir alt sınıfı haline gelir. Bu davranışı geçersiz kılınamaz. Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için diğer bir yöntem yoktur.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
