---
title: GetPropertyQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetPropertyQualifierSet işlevi için bir özellik Ayarla niteleyicisi alır.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2951733211737f06cd737b20bd1537277be1be1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461483"
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet işlevi
Belirli bir özelliği için belirlenen niteleyicisi alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`wszMethod`  
[in] Özellik adı. `wszProperty` Geçerli bir işaret etmelidir `LPCWSTR`. 

`ppQualSet`  
[out] Özelliğin niteleyicileri erişmesini sağlayan arabirim işaretçisi alır. `ppQualSet` olamaz `null`. Bir hata oluştuğunda yeni bir nesne değil döndürülür ve işaretçi işaret edecek şekilde ayarlanır `null`. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen yöntem yok. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | İşlev sistem özelliğinin niteleyicileri almaya çalışır. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) yöntemi. 

Yalnızca geçerli nesne bir CIM sınıfı tanımı ise bu işlev için bir çağrı desteklenir. Yöntem işleme için kullanılabilir olmadığından [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM örneklerine noktası ponters.

Her yöntemin kendi niteleyicileri olabileceğinden [IWbemQualifierSet işaretçi](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) eklemek, düzenlemek veya silmek bu niteleyicileri çağıran olanak sağlar.

Sistem özellikleri hiçbir niteleyicileri bulunduğundan, işlevi döndürür `WBEM_E_SYSTEM_PROPERTY` elde çalışırsanız, bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) sistem özelliği için bir işaretçi.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
