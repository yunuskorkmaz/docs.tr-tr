---
title: QualifierSet_Next işlevi (Yönetilmeyen API Başvurusu)
description: QualifierSet_Next işlevi bir sonraki elemeyi bir numaralandırmada alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174881"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next fonksiyonu
[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevine yapılan bir çağrıyla başlayan bir numaralandırmada bir sonraki elemeyi alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`[içinde] Bu parametre kullanılmaz.

`ptr`[içinde] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneğine işaretçi.

`lFlags`[içinde] Saklı -dır. Bu parametre 0 olmalıdır.

`pstrName`[çıkış] Elemenin adı. `null`Bu parametre yoksayılmazsa; aksi `pstrName` takdirde, geçerli `BSTR` bir veya bellek sızıntısı oluşur işaret etmemelidir. Null değilse, işlev her zaman `BSTR` döndürdüğünde `WBEM_S_NO_ERROR`yeni bir ayırır.

`pVal`[çıkış] Başarılı olduğunda, eleme değeri. İşlev başarısız olursa, işaret edilen `VARIANT` ler `pVal` değiştirilmez. Bu parametre `null`ise, parametre yoksayılır.

`plFlavor`[çıkış] Niteleyici lezzet alan bir UZUN için bir işaretçi. Lezzet bilgisi istenemiyorsa, `null`bu parametre .

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değildir. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Arayan [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)aramadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırmabaşlatmak için yeterli bellek kullanılabilir değil. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada artık eleme ler kalmamaktadır. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev [IWbemQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) bir çağrı sarar::Sonraki yöntem.

`QualifierSet_Next` İşlev dönene `WBEM_S_NO_MORE_DATA`kadar tüm niteleyicileri sayısallandırmak için işlevi tekrar tekrar çağırırsınız. Numaralandırmayı erken sonlandırmak için [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevini arayın.

Numaralandırma sırasında döndürülen niteleyicilerin sırası tanımsızdır.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
