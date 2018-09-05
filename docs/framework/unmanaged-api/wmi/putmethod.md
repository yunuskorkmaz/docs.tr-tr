---
title: PutMethod işlevi (yönetilmeyen API Başvurusu)
description: PutMethod işlevi, bir metot oluşturur.
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
ms.openlocfilehash: 7cdf34ff6ae506ba209300685da3752820b250a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516756"
---
# <a name="putmethod-function"></a>PutMethod işlevi
Bir metot oluşturur.

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
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`wszName`  
[in] Oluşturmak için yöntemin adı. 

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pSignatureIn`  
[in] Bir kopyasını bir işaretçiye [__Parameters sistem sınıfı](/windows/desktop/WmiSdk/--parameters) içeren `in` yönteminin parametreleri. Bu parametre yoksayılır kümesine `null`.  

`pSignatureOut`  
[in]  Bir kopyasını bir işaretçiye [__Parameters sistem sınıfı](/windows/desktop/WmiSdk/--parameters) içeren `out` yönteminin parametreleri. Bu parametre yoksayılır kümesine `null`.
 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | `[in, out]` Hem de belirtilen yöntem parametresi *pInSignature* ve *pOutSignature* nesneleri farklı niteleyicileri sahiptir.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Bir yöntem parametresi belirtimi eksik **kimliği** niteleyicisi. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | Yöntem parametreleri için atanan kimliği serisi ardışık değil veya 0'da başlamaz. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | Bir yöntemin dönüş değerine sahip bir **kimliği** niteleyicisi. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Varolan bir yöntem adı bir üst sınıftan yeniden kullanmak için bir girişimde bulunuldu ve imzalar eşleşmez. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemi.

Bu yöntem çağrısı, yalnızca desteklenen `ptr` bir CIM sınıfı tanımıdır. Yöntem işleme kullanılabilir değil [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) CIM örneklerine işaret eden işaretçilerin.

Kullanıcılar, başlayamaz veya bir alt çizgiyle bitemez adlara sahip yöntemleri oluşturamaz. Bu, sistem sınıfları ve özellikleri için ayrılmıştır.

Bir yöntem için `in` ve `out` özellikleri olarak parametreler açıklanmıştır [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) nesneleri.

Bir `[in/out]` parametresinin işaret ettiği her iki nesnenin aynı özellik ekleyerek tanımlanabilir `pInSignature` ve `pOutSignature` parametreleri. Bu durumda, aynı özellikleri paylaşır **kimliği** niteleyici değeri.

Her bir özellik bir [__Parameters](/windows/desktop/WmiSdk/--parameters) dışındaki nesne sınıfının `ReturnValue` olmalıdır bir **kimliği** niteleyicisi, parametreleri görünme sırasını belirleyen sıfır tabanlı bir sayısal değer. İki parametre aynı olabilir **kimliği** değeri ve Hayır **kimliği** değeri atlanacak. Her iki durum ortaya çıkarsa, `PutMethod` işlevinin döndürdükleriyle `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Örnek

Bir örnek için bkz. [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
