---
title: CreateInstanceEnumWmi işlevi (yönetilmeyen API Başvurusu)
description: CreateInstanceEnumWmi işlev seçim ölçütleri karşılayan belirli bir sınıf örneklerini içeren bir numaralandırıcı döndürür.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a1d082cae19bd83c90e063d841a0c9e4602bc40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040709"
---
# <a name="createinstanceenumwmi-function"></a>CreateInstanceEnumWmi işlevi

Belirtilen seçim ölçütlerine belirli bir sınıf örneğini döndüren bir numaralandırıcı döndürür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>Parametreler

`strFilter`\
[in] Kendisi için örnekleri istenen sınıfı adı. Bu parametre olamaz `null`.

`lFlags`\
[in] Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri işlev kümesini alır <br/> Aksi durumda, küme yalnızca anında ad alanında depolanan niteleyicileri işlevi alır. |
| `WBEM_FLAG_DEEP` | 0 | Numaralandırma hiyerarşi içinde bu ve tüm alt sınıflar içerir. |
| `WBEM_FLAG_SHALLOW` | 1. | Bu sınıfın yalnızca saf örneklerini içerir ve bu sınıfında bulunmayan özellikleri tedarik alt sınıfların tüm örneklerini dahil değildir. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumsuz bir çağrı neden olur. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlev yalnızca iletme bir numaralandırıcı döndürür. Genellikle, yalnızca iletme numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrısına izin verme [kopya](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Serbest bırakılana kadar WMI numaralandırmada nesnelerine işaretçiler korur. |

Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.

`pCtx`\
[in] Genellikle, bu değer, `null`. Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen örnekleri sağlayan sağlayıcı tarafından kullanılan bir örnek.

`ppEnum`\
[out] İşaretçi numaralandırıcıyı alır.

`authLevel`\
[in] Yetkilendirme düzeyi.

`impLevel`\
[in] Kimliğe bürünme düzeyi.

`pCurrentNamespace`\
[in] Bir işaretçi bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) geçerli ad alanını temsil eden nesne.

`strUser`\
[in] Kullanıcı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

`strPassword`\
[in] Parola. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

`strAuthority`\
[in] Kullanıcı etki alanı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcının belirtilen sınıf örneklerini görüntüleme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strFilter` mevcut değil. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durdu ve yeniden başlatılıyor. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) yöntemi.

Döndürülen Numaralandırıcı sıfır öğeleri sahip olabileceğini unutmayın.

İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils.idl

**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)