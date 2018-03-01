---
title: "QualifierSet_GetNames işlevi (yönetilmeyen API Başvurusu)"
description: "QualifierSet_GetNames işlevi, bir nesneye veya özelliğe niteleyicileri adlarını alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6077b448c2644f68d12679cf208ee921c2af119a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames işlevi
Tüm niteleyicileri veya geçerli nesne ya da özellik kullanılabilir belirli niteleyicileri adlarını alır. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
[in] Bu parametre kullanılmıyor.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.

`lFlags`   
[in] Aşağıdaki bayraklar veya numaralandırmada dahil etmek için hangi adlarını belirtir değerleri biri.

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|  | 0 | Tüm niteleyicileri adlarını döndürür. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca niteleyicileri adlarını belirli geçerli özellik veya nesne döndürür. <br/> Bir özellik için: yalnızca niteleyicileri (geçersiz kılmaları dahil) özelliğine belirli dönün ve bu niteleyicileri sınıf tanımı yayılır. <br/> Bir örneği için: yalnızca örneğe özgü niteleyicisi adlarını döndürür. <br/> Bir sınıf için: yalnızca niteleyicileri türetilmiş sınıf beiong belirli döndürür.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Başka bir nesne yalnızca niteleyicileri adlarını yayılan dönüş. <br/> Bir özellik için: sınıf tanımı ve özelliğinden olanlar geri dönmek için bu özelliği olarak yalnızca niteleyicileri yayılır. <br/> Bir örneği için: sınıf tanımını dönüş yalnızca bu niteleyicileri yayılır. <br/> Bir sınıf için: Return niteleyicisi adları yalnızca üst sınıflardan devralınır. |

`pstrNames`[out] Yeni bir `SAFEARRAY` istenen adlarını içerir. Dizi 0 öğeler bulunabilir. Bir hata oluşursa, yeni bir `SAFEARRAY` döndürülmez.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) yöntemi.

Niteleyici adları elde sonra her niteleyicisi ada göre arayarak erişebilirsiniz [QualifierSet_Get](qualifierset-get.md) işlevi. 

Sıfır niteleyicileri olması belirli bir nesne için bir hata değildir dizelerde sayısı `pstrNames` işlevi döndürür olsa bile getirisi 0, olabilir `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
