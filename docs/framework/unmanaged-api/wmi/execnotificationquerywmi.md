---
title: ExecNotificationQueryWmi işlevi (yönetilmeyen API Başvurusu)
description: ExecNotificationQueryWmi işlevi olaylarını almak için bir sorgu yürütür.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d314d85e7c1297636e8dd5cecaf050a527151518
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752296"
---
# <a name="execnotificationquerywmi-function"></a>ExecNotificationQueryWmi işlevi
Olayları almak için bir sorgu yürütür. Çağrı hemen döndürür ve geldikçe çağırana döndürülen Numaralandırıcı olaylar için yoklama. Döndürülen Numaralandırıcı serbest sorguyu iptal eder.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

`strQueryLanguage`    
[in] Windows Management tarafından desteklenen geçerli bir sorgu dili olan bir dize. WMI Sorgu Dili kısaltması "WQL" olmalıdır.

`strQuery`  
[in] Sorgu metni. Bu parametre olamaz `null`.

`lFlags`   
[in] Bu işlevin davranışını etkileyen aşağıdaki iki bayrakların birleşimi. Bu değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda. 

| Sabit | Değer  | Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumsuz bir çağrı neden olur. Bu bayrak ayarlanmazsa, çağrı başarısız olur. Olayları sürekli olarak alınan kullanıcı döndürülen Numaralandırıcı yoklaması gerekir yani olmasıdır. Bu çağrı süresiz olarak engelleme, mümkün kılar. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlev yalnızca iletme bir numaralandırıcı döndürür. Genellikle, yalnızca iletme numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrısına izin verme [kopya](clone.md). |

`pCtx`  
[in] Genellikle, bu değer, `null`. Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen olaylar sağlayarak sağlayıcı tarafından kullanılan bir örnek. 

`ppEnum`  
[out] Eğer hiç Hata oluşmazsa, işaretçi örnekleri sorgunun sonuç kümesinde almak çağırıcı veren numaralandırıcıyı alır. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.

`authLevel`  
[in] Yetkilendirme düzeyi.

`impLevel` [in] Kimliğe bürünme düzeyi.

`pCurrentNamespace`   
[in] Bir işaretçi bir [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) geçerli ad alanını temsil eden nesne.

`strUser`   
[in] Kullanıcı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

`strPassword`   
[in] Parola. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

`strAuthority`   
[in] Kullanıcı etki alanı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Sorgu var olmayan bir sınıfı belirtiyor. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Çok fazla olay teslimini kesinlik istendi. Daha büyük bir yoklama toleransı belirtilmesi gerekir. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | Sorgu requess Windows yönetimi daha fazla bilgi sağlayabilir. Bu `HRESULT` isteğinde bir ad alanındaki tüm nesneler yoklamak üzere Olay sorgusu sonuçları döndürülür. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Sorgu söz dizimi hatası vardı. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | İstenen sorgu dili desteklenmiyor. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Sorgu çok daha karmaşıktır. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durdu ve yeniden başlatılıyor. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | Sorgu nelze analyzovat. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) yöntemi.

Çağıran düzenli aralıklarla işlev döndürdükten sonra döndürülen geçirir. `ppEnum` nesnesini [sonraki](next.md) meydana gelen olayları kullanılabilir olup olmadığını görmek için işlev.

Bununla ilgili sınırlamalar sayısını `AND` ve `OR` WQL sorguları kullanılabilir anahtar sözcükler. Çok sayıda karmaşık bir sorguda kullanılan WQL anahtar sözcükleri döndürmek WMI neden olabilecek `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodunu bir `HRESULT` değeri. WQL anahtar sözcük sınırını nasıl karmaşık sorgu olduğuna bağlıdır.

İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
