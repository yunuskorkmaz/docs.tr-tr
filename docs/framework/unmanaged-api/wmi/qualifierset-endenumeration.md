---
title: QualifierSet_EndEnumeration işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_EndEnumeration işlevi numaralandırma sonlandırır.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e24acdde486f377cc9187aac088ce7a611cd4eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460756"
---
# <a name="qualifiersetendenumeration-function"></a>QualifierSet_EndEnumeration işlevi
Çağrısıyla başlamış numaralandırması sonlandırır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen değerin aşağıdaki tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz, bir sabit değer olarak, kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) yöntemi.

Bu çağrı, önerilir ancak gerekli değildir. Hemen numaralandırması ile ilişkili kaynakları serbest bırakır.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
**Başlık:** WMINet_Utils.idl  
  
**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
