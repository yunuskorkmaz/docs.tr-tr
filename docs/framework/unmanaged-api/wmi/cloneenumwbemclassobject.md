---
title: CloneEnumWbemClassObject fonksiyonu (Yönetilmeyen API Başvurusu)
description: CloneEnumWbemClassObject işlevi bir sayısalatörün mantıksal bir kopyasını yapar.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175024"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject işlevi
Numaralandırmada geçerli konumunu koruyarak numaralandırmanın mantıksal bir kopyasını yapar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a>Parametreler

`ppEnum`\
[çıkış] Yeni bir [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)için bir işaretçi alır.

`authLevel`\
[içinde] Yetkilendirme düzeyi.

`impLevel`\
[içinde] Kimliğe bürünme düzeyi.

`pCurrentEnumWbemClassObject`\
[çıkış] [Klonlanacak IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) örneğine işaretçi.

`strUser`\
[içinde] Kullanıcı adı. Daha fazla bilgi için [ConnectServerWmi](connectserverwmi.md) işlevine bakın.

`strPassword`\
[içinde] Şifre. Daha fazla bilgi için [ConnectServerWmi](connectserverwmi.md) işlevine bakın.

`strAuthority`\
[içinde] Kullanıcının etki alanı adı. Daha fazla bilgi için [ConnectServerWmi](connectserverwmi.md) işlevine bakın.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Genel bir başarısızlık oldu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçersizdir. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu [işlev, IEnumWbemClassObject::Klon](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemine bir çağrı yıkıyor.

Bu yöntem yalnızca bir "en iyi çaba" kopya yapar. Birçok CIM nesnesinin dinamik yapısı nedeniyle, yeni enumerator kaynak sonlandırıcı olarak nesnelerin aynı kümesini sıralamak değil mümkündür.

İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini arayarak ek hata bilgileri edinebilirsiniz.

## <a name="example"></a>Örnek

Örneğin, [IEnumWbemClassObject::Klon](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemine bakın.

## <a name="requirements"></a>Gereksinimler
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).

 **Üstbilgi:** WMINet_Utils.idl

 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)
