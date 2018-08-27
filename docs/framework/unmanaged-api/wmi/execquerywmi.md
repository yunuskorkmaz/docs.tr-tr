---
title: ExecQueryWmi işlevi (yönetilmeyen API Başvurusu)
description: ExecQueryWmi işlevi nesneleri almak için bir sorgu yürütür.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc22edf51cbd726b69dff3da2f0540b2c3864f2e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929632"
---
# <a name="execquerywmi-function"></a>ExecQueryWmi işlevi
Nesneleri almak için bir sorgu yürütür.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExecQueryWmi (
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
[in] Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

| Sabit | Değer  | Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri işlev kümesini alır <br/> Aksi durumda, küme yalnızca anında ad alanında depolanan niteleyicileri işlevi alır. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumsuz bir çağrı neden olur. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlev yalnızca iletme bir numaralandırıcı döndürür. Genellikle, yalnızca iletme numaralandırıcılar daha hızlıdır ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrısına izin verme [kopya](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur. | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Döndürülen tüm nesneler sahip yeterli bilgi bunları böylece sağlar, Sistem özellikleri gibi **__PATH**, **__RELPATH**, ve **__SERVER**, olmayan `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Bu bayrak, prototip oluşturma için kullanılır. Bu sorgu çalıştırma ve bunun yerine bir normal sonuç nesnesi gibi görünen bir nesne döndürür. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Doğrudan sağlayıcı erişim kendi üst sınıfı veya alt sınıfların bakılmaksızın belirtilen sınıf için neden olur. |

Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.

`pCtx`  
[in] Genellikle, bu değer, `null`. Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen sınıfları sağlayan sağlayıcı tarafından kullanılan bir örnek. 

`ppEnum`  
[out] Eğer hiç Hata oluşmazsa, işaretçi örnekleri sorgunun sonuç kümesinde almak çağırıcı veren numaralandırıcıyı alır. Sorgu bir sonuç kümesi sıfır örnekleriyle olabilir. Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.

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
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Sorgu söz dizimi hatası vardı. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | İstenen sorgu dili desteklenmiyor. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Sorgu çok daha karmaşıktır. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durdu ve yeniden başlatılıyor. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Sorgu var olmayan bir sınıfı belirtiyor. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) yöntemi.

Bu işlev, belirtilen sorgu işlemleri `strQuery` parametresi üzerinden çağıran sorgu sonuçları erişebilir bir numaralandırıcı oluşturur. Numaralandırıcı işaretçisidir bir [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) arabirimi; sorgu sonuçları olan kullanılabilir hale sınıf nesnelerin örneklerini [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) arabirimi.

Bununla ilgili sınırlamalar sayısını `AND` ve `OR` WQL sorguları kullanılabilir anahtar sözcükler. Çok sayıda karmaşık bir sorguda kullanılan WQL anahtar sözcükleri döndürmek WMI neden olabilecek `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodunu bir `HRESULT` değeri. WQL anahtar sözcük sınırını nasıl karmaşık sorgu olduğuna bağlıdır.

İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
