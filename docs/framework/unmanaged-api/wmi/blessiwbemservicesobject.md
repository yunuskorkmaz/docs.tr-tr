---
title: BlessIWbemServicesObject işlevi (Yönetilmeyen API Başvurusu)
description: BlessIWbemServicesObject işlevi, kullanıcı kimlik bilgilerinin bir IWbemServices nesnesine erişime izin verip vermediğini gösterir
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175037"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject işlevi
Kullanıcı kimlik bilgilerinin belirtilen bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine erişime izin verip vermediğini gösterir.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>Parametreler

`pIWbemServices`\
[içinde] WMI hizmet nesnesine işaretçi.

`strUser`\
[içinde] Kullanıcı adı.

`strPassword`\
[içinde] `strUser`' ile ilişkili parola

`strAuthority`\
[içinde] Kullanıcının etki alanı adı. Daha fazla bilgi için [ConnectServerWmi](connectserverwmi.md) işlevine bakın.

`impLevel`\
[içinde] Kimliğe bürünme düzeyi.

`authnLevel`\
[içinde] Yetkilendirme düzeyi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WinError.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | Bir veya daha fazla bağımsız değişken geçersizdir. |
| `E_POINTER` | 0x80004003 | `pIWbemServices``null`. |
| `E_FAIL` | 0x80000008 | Belirtilmeyen bir hata oluştu. |
| `E_OUTOFMEMORY` | 0x80000002 | İşlemi gerçekleştirmek için yetersiz bellek kullanılabilir. |
| `S_OK` | 0 | İşlev çağrısı başarılı oldu. |

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).

 **Üstbilgi:** WMINet_Utils.idl

 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
