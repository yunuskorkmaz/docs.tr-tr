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
ms.openlocfilehash: 2739003fc9c1f93d379e4a59338cbef7a1a0f135
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726749"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration işlevi

[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi çağrısıyla başlatılan numaralandırmayı sonlandırır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr` 'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

## <a name="return-value"></a>Döndürülen değer

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
  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
