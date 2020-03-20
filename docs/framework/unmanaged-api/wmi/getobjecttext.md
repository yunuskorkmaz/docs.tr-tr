---
title: GetObjectText işlevi (Yönetilmeyen API Başvurusu)
description: GetObjectText işlevi, MOF sözdiziminde bir nesnenin metinsel bir işlemesini döndürür.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176792"
---
# <a name="getobjecttext-function"></a>GetObjectText işlevi
Yönetilen Nesne Biçimi (MOF) sözdiziminde nesnenin metin oluşturma biçimini döndürür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`lFlags`  
[içinde] Normalde 0. `WBEM_FLAG_NO_FLAVORS` (veya 0x1) belirtilirse, elemeler yayılma veya lezzet bilgisi olmadan dahil edilir.

`pstrObjectText`[çıkış] Giriş için `null` bir işaretçi. Döndükten sonra, `BSTR` nesnenin MOF sözdizimi oluşturmasını içeren yeni ayrılmış bir.  

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir başarısızlık oldu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değildir. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) yöntemine bir çağrı yıkLar.

Döndürülen MOF metni nesne yle ilgili tüm bilgileri içermez, ancak mof derleyicisinin özgün nesneyi yeniden oluşturabilmesi için yeterli bilgi içerir. Örneğin, hiçbir yayılan niteleyiciler veya üst sınıf özellikleri dahil edilir.

Bir yöntemin parametrelerinin metnini yeniden oluşturmak için aşağıdaki algoritma kullanılır:

1. Parametreler tanımlayıcı değerleri sırasına göre yeniden sıralanır.
1. Olarak `[in]` belirtilen ve `[out]` tek bir parametrede birleştirilen parametreler.

`pstrObjectText`işlev çağrıldığında `null` bir işaretçi olmalıdır; işaretçi ayrılmayacağı için yöntem çağrısından önce geçerli olan bir dizeyi işaret etmemelidir.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
