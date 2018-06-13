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
ms.openlocfilehash: b482f2ca2e2d5c06e69945adb71aa6c0f5d26465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462097"
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
[in] Windows Yönetimi tarafından desteklenen geçerli bir sorgu dili olan bir dize. WMI Sorgu Dili kısaltması "WQL" olmalıdır.

`strQuery`  
[in] Sorgu metni. Bu parametre olamaz `null`.

`lFlags`   
[in] Bu işlev davranışını etkileyen bayrak birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

| Sabit | Değer  | Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Geçerli bağlantının yerel yerelleştirilmiş ad alanında depolanan değiştirilen niteleyicileri kümesi, işlevi alır <br/> Aksi durumda kümesi işlevi yalnızca hemen ad alanında depolanan niteleyicileri alır. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumlu bir çağrı neden olur. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | İşlevi yalnızca ileri bir numaralandırıcı döndürür. Genellikle, yalnızca ileri numaralandırıcılar daha hızlı ve geleneksel numaralandırıcılar daha az bellek kullanır, ancak çağrıları izin verme [kopya](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Serbest bırakılana kadar WMI enumration nesnelerine işaretçiler korur. | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Döndürülen herhangi nesneler sahip yeterli bilgi bunları böylece sağlar, Sistem özellikleri gibi **__PATH**, **__RELPATH**, ve **__SERVER**, değil `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Bu bayrak için prototipi oluşturulurken kullanılır. Sorgu çalıştırma ve bunun yerine normal sonuç nesnesi gibi görünen bir nesne döndürür. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Nedenler sağlayıcısına erişim kendi üst sınıfı veya alt sınıfların bakılmaksızın belirtilen sınıfı için doğrudan. |

Önerilen bayraklar `WBEM_FLAG_RETURN_IMMEDIATELY` ve `WBEM_FLAG_FORWARD_ONLY` en iyi performans için.

`pCtx`  
[in] Bu değer genellikle `null`. Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek. 

`ppEnum`  
[out] Herhangi bir hata oluşursa, sorgunun sonuç kümesinde örnekleri almak arayan verir Numaralandırıcı işaretçisine alır. Sorgu bir sonuç sıfır örnekleriyle kümesi olabilir. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.

`authLevel`  
[in] Kimlik doğrulama düzeyi.

`impLevel` [in] Kimliğe bürünme düzeyi.

`pCurrentNamespace`   
[in] Bir işaretçi bir [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) geçerli ad alanını temsil eden nesne.

`strUser`   
[in] Kullanıcı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.

`strPassword`   
[in] Parola. Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.

`strAuthority`   
[in] Kullanıcının etki alanı adı. Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcı, bir veya daha fazla işlev döndürebilir sınıfları görüntüleme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirlenemeyen bir hata oluştu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Sorgu sözdizimi hatası oluştu. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | İstenen sorgu dili desteklenmiyor. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Sorgu çok karmaşıktır. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durduruldu ve yeniden başlatma. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Sorgu var olmayan bir sınıfı belirtiyor. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) yöntemi.

Bu işlev belirtilen sorgu işlemleri `strQuery` parametre ve üzerinden çağıran sorgu sonuçlarını erişebileceği bir numaralandırıcı oluşturur. Numaralayıcı gösteren bir işaretçidir bir [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) arabirimi; sorgu sonucu olan kullanılabilir hale sınıfı nesnelerinin örneklerini [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) arabirimi.

Sayısıyla sınırlar vardır `AND` ve `OR` WQL sorguları kullanılabilir anahtar sözcükler. Çok sayıda karmaşık bir sorguda kullanılan WQL anahtar sözcükleri döndürmek WMI neden `WBEM_E_QUOTA_VIOLATION` (veya 0x8004106c) hata kodu olarak bir `HRESULT` değeri. WQL anahtar sözcükleri sınırını sorgu nasıl karmaşık olduğuna bağlıdır.

İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
