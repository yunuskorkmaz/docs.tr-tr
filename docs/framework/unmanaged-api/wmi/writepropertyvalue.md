---
title: WritePropertyValue işlevi (yönetilmeyen API Başvurusu)
description: WritePropertyValue işlevi, bir özelliğe bayt yazar.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729414"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue işlevi

Bir özellik tanıtıcısı tarafından tanımlanan bir özelliğe belirtilen sayıda bayt yazar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki Bir [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneği işaretçisi.

`lHandle`  
'ndaki Bu özelliği tanımlayan tanıtıcıyı içeren bir tamsayı. Tanıtıcı, [Getpropertyhandle](getpropertyhandle.md) işlevi çağırarak alınabilir.

`lNumBytes`  
'ndaki Özelliğe yazılan bayt sayısı. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

`pHandle` dışı Verileri içeren bayt dizisine yönelik bir işaretçi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Tür uyumsuzluğu oluştu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) yöntemine bir çağrı kaydırır.

Bu işlevi, dizeyi ve diğer tüm veri olmayan verileri ayarlamak için kullanın `DWORD` `QWORD` .

Dize olmayan özellik değerleri için `lNumBytes` belirtilen özellik türünün doğru veri boyutu olmalıdır. Dize özellik değerleri için, `lNumBytes` belirtilen dizenin bayt cinsinden uzunluğu olmalıdır ve dizenin kendisi, bayt cinsinden bir çift uzunluğunda olmalı ve ardından null sonlandırma karakteriyle birlikte gelmelidir.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
