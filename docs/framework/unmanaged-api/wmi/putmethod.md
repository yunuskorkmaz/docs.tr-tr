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
ms.openlocfilehash: 7f74b0d30a1a8899d3c8d0a2bf0f108ea11165cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461863"
---
# <a name="putmethod-function"></a>PutMethod işlevi
Bir yöntem oluşturur.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
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
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`wszName`  
[in] Oluşturmak için yöntemin adı. 

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pSignatureIn`  
[in] Bir işaretçi bir kopyasını [__Parameters sistem sınıfı](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) içeren `in` yöntemi için parametreler. Bu parametre yoksayılır kümesine `null`.  

`pSignatureOut`  
[in]  Bir işaretçi bir kopyasını [__Parameters sistem sınıfı](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) içeren `out` yöntemi için parametreler. Bu parametre yoksayılır kümesine `null`.
 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]` Hem de belirtilen yöntem parametresi *pInSignature* ve *pOutSignature* nesneleri farklı niteleyicileri sahiptir.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Yöntem parametresi belirtimi eksik **kimliği** niteleyicisi. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Yöntem parametreleri atanan kimliği seri ardışık değil veya 0'da başlatılmaz. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Bir yöntemin dönüş değerine sahip bir **kimliği** niteleyicisi. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Varolan bir yöntem adı bir üst sınıftan yeniden çalışıldı ve imzalar eşleşmedi. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) yöntemi.

Bu yöntem çağrısı yalnızca, desteklenen `ptr` bir CIM sınıfı tanımıdır. Yöntem işleme kullanılabilir değil [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) CIM örneklerine noktası işaretçileri.

Kullanıcılar, başlayamaz veya alt çizgiyle bitemez adlarla yöntemleri oluşturamaz. Bu, sistem sınıfları ve özellikleri için ayrılmıştır.

Bir yöntem için `in` ve `out` parametreleri özellikleri olarak açıklanmıştır [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) nesneleri.

Bir `[in/out]` parametresi gösterdiği her iki nesnenin aynı özelliği ekleyerek tanımlanabilir `pInSignature` ve `pOutSignature` parametreleri. Bu durumda, aynı özellikleri paylaşır **kimliği** niteleyici değeri.

Her bir özellik bir [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) nesne dışında sınıfının `ReturnValue` olmalıdır bir **kimliği** Niteleyici, parametreleri görünme sırasını tanımlar sıfır tabanlı bir sayısal değer. İki parametresi'nın aynı olmayan **kimliği** değeri ve no **kimliği** değeri atlandı. Her iki durum ortaya çıkarsa, `PutMethod` işlev döndürür `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Örnek

Bir örnek için bkz: [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
