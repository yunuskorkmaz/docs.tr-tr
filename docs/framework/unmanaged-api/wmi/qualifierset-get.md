---
title: QualifierSet_Get işlevi (Yönetilmeyen API Başvurusu)
description: QualifierSet_Get işlevi adlandırılmış bir niteleyici alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174894"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get fonksiyonu
Belirtilen adlandırılmış niteleyiciyi alır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`[içinde] Bu parametre kullanılmaz.

`ptr`[içinde] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneğine işaretçi.

`wszName`[içinde] Değeri istenen niteleyicinin adı.

`lFlags`[içinde] Saklı -dır. Bu parametre 0 olmalıdır.

`pVal`[çıkış] Başarılı olduğunda, niteleyici için doğru tür ve değer. İşlev başarısız olursa, işaret edilen `VARIANT` ler `pVal` değiştirilmez. Bu parametre `null`ise, parametre yoksayılır.

`plFlavor`[çıkış] İstenen niteleyici niteleyici için niteleyici lezzet bitlerini alan bir UZUN işaretçi. Lezzet bilgisi istenemiyorsa, `null`bu parametre .

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değildir. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen niteleyici yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev [IWbemQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) bir çağrı sarar::Get yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
