---
title: EndMethodEnumeration fonksiyonu (Yönetilmeyen API Başvurusu)
description: EndMethodEnumeration işlevi bir yöntem numaralandırma dizisini sonlandırır.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175011"
---
# <a name="endmethodenumeration-function"></a>EndMethodEnumeration işlevi
[BeginMethodEnumeration işlevine](beginmethodenumeration.md)yapılan çağrıyla başlayan numaralandırma dizisini sonlandırır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101d | Bir iç hata oluştu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) yöntemine bir çağrı yıkıyor.

Arayan, [BeginMethodEnumeration işlevini](beginmethodenumeration.md)kullanarak numaralandırma sırasını başlatır ve yöntem dönene `WBEM_S_NO_MORE_DATA`kadar [NextMethod işlevini](nextmethod.md )çağırır. Arayan isteğe bağlı olarak arayarak `EndMethodEnumeration`sırayı tamamlar. Arayan, herhangi bir zamanda arayarak `EndMethodEnumeration` numaralandırmayı erken sonlandırabilir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
