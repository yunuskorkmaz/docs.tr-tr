---
title: QualifierSet_EndEnumeration işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_EndEnumeration işlevi bir numaralandırmayı sonlandırır.
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
ms.openlocfilehash: 82627fa416f71e123ed2c03bae4584e4433310eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127285"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration işlevi
[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevine yapılan bir çağrıyla başlatılan numaralandırmayı sonlandırır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`   
'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değer *Wbemcli. h* üstbilgi dosyasında tanımlanır veya kodunuzda bir sabit olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet:: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) yöntemine bir çağrı kaydırır.

Bu çağrı önerilir, ancak gerekli değildir. Numaralandırmada ilişkili kaynakları hemen yayınlar.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
**Üst bilgi:** WMINet_Utils. IDL  
  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
