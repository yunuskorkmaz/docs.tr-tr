---
title: GetMethodOrigin işlevi (Yönetilmeyen API Başvurusu)
description: GetMethodOrigin işlevi, yöntemin bildirildiği sınıfı belirler.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176805"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin işlevi
Yöntemin bildirildiği sınıfı belirler.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`wszMethodName`  
[içinde] Sahibi sınıfı istenen nesne için yöntemin adı.

`pstrClassName`  
[çıkış] Yöntemin sahibi sınıfın adını alır.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen yöntem bulunamadı. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değildir. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı yıkıyor.

Bir sınıf yöntemleri bir veya daha fazla temel sınıftan devralabileceğinden, geliştiriciler genellikle belirli bir yöntemin tanımlandığı sınıfı belirlemek ister.

Bu `pstrClassName` bir parametre olduğundan, `BSTR` işlev çağrılmadan önce `out` parametre geçerliyi işaret etmemelidir; bu işaretçi işlev döndükten sonra ayrılmaz.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
