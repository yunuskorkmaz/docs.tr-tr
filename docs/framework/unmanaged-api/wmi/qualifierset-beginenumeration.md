---
title: "QualifierSet_BeginEnumeration işlevi (yönetilmeyen API Başvurusu)"
description: "QualifierSet_BeginEnumeration işlevi bir nesnenin niteleyicileri numaralandırması sıfırlar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 440dde03f4ed138a33eb6f817723d7c5c74f6d46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration işlevi
Bir nesnenin niteleyicileri numaralandırması sabit başlangıç durumuna sıfırlar.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
[in] Bu parametre kullanılmıyor.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.

`lFlags`   
[in] Bayrakları veya açıklanan değerlerinin Bitsel bir birleşimi [açıklamalar](#remarks) numaralandırmada içerecek şekilde niteleyicileri belirtir bölümü.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametresi geçerli değil. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | İkinci çağrı `QualifierSet_BeginEnumeration` olmadan müdahalede bulunan bir çağrı yapıldı [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) yöntemi.

Bir nesne üzerinde niteleyicileri tümünün numaralandırmak için bu yöntem ilk çağrıda önce çağrılmalıdır [QualifierSet_Next](qualifierset-next.md). Niteleyiciler numaralandırılan sipariş için belirli bir numaralandırma sabit olması sağlanır.

Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni tanımlanmış *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.   

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|  | 0 | Tüm niteleyicileri adlarını döndürür. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca niteleyicileri adlarını belirli geçerli özellik veya nesne döndürür. <br/> Bir özellik için: yalnızca niteleyicileri (geçersiz kılmaları dahil) özelliğine belirli dönün ve bu niteleyicileri sınıf tanımı yayılır. <br/> Bir örneği için: yalnızca örneğe özgü niteleyicisi adlarını döndürür. <br/> Bir sınıf için: yalnızca niteleyicileri türetilmiş sınıf beiong belirli döndürür.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Başka bir nesne yalnızca niteleyicileri adlarını yayılan dönüş. <br/> Bir özellik için: sınıf tanımı ve özelliğinden olanlar geri dönmek için bu özelliği olarak yalnızca niteleyicileri yayılır. <br/> Bir örneği için: sınıf tanımını dönüş yalnızca bu niteleyicileri yayılır. <br/> Bir sınıf için: Return niteleyicisi adları yalnızca üst sınıflardan devralınır. |

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
