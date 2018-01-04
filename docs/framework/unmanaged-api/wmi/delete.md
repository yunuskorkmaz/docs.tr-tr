---
title: "Delete işlevi (yönetilmeyen API Başvurusu)"
description: "Silme işlevini belirtilen özellik ve tüm alt niteleyicileri bir CIM sınıfı tanımından siler."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30f5bf651990cafe06811019cf2b3d92f866f646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="delete-function"></a>İşlev Sil
Belirtilen özellik ve tüm alt niteleyicileri bir CIM sınıfı tanımından siler.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`wszName`  
[in] Silinecek özelliğinin adı. `wszName`Geçerli bir işaretçi olmalıdır `LPCWSTR`.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Belirlenemeyen bir hata oluştu. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Özellik silinemez. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszzName` geçersizdir. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik yok. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Özelliği bir taban sınıftan devralınır. |
| `WBEM_E_SYSTEM_PROPERTY` | | Özelliği bir sistem özelliğidir. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | İşlev geçerli sınıf için bir geçersiz kılma varsayılan değer silindi. Bu özellikte üst sınıfı için varsayılan değer reactiviated olmuştur. | 

## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
