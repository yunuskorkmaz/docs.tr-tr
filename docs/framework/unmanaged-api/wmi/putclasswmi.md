---
title: PutClassWmi işlevi (yönetilmeyen API Başvurusu)
description: PutClassWmi işlevi, yeni bir sınıf oluşturur veya mevcut olanı güncelleştirir.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de08662a825a84f19a40863cf73481d89364ebd0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45568325"
---
# <a name="putclasswmi-function"></a>PutClassWmi işlevi
Yeni bir sınıf oluşturur veya mevcut olanı güncelleştirir.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parametreler

`pObject`    
[in] Geçerli bir sınıf tanımı için bir işaretçi. Tüm gerekli özellik değerleri doğru şekilde yeniden başlatılmalıdır.

`lFlags`   
[in] Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Tüm niteleyicileri ile değiştirilmiş özellik kümesi, WMI depolamaz </br> Aksi durumda, küme bu nesne yerelleştirilmez ve tüm niteleyicileri storedwith başladığınız varsayılır Bu örneği. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Sınıfı, yok, veya zaten varsa üzerine oluşturun. |
| `WBEM_FLAG_UPDATE_ONLY` | 1. | Sınıf güncelleştirin. Sınıf araması başarılı olması mevcut olması gerekir. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Bir sınıf oluşturun. Sınıf zaten varsa başarısız olur. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumsuz bir çağrı neden olur. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Anında iletme sağlayıcıları, bu bayrak belirtmelisiniz, çağrılırken `PutClassWmi` Bu sınıf değiştirildiğini göstermek için. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Türetilmiş sınıfları ve bu sınıf örneği varsa güncelleştirilecek bir sınıf sağlar. Değişiklik yalnızca açıklama niteleyicisi gibi önemli niteleyicileri, ayrıca tüm durumlarda güncelleştirmeler sağlar. Sınıf örnekleri sahip veya bu değişiklikler için önemli niteleyicileri güncelleştirme başarısız olur. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Olsa bile alt sınıfları değişikliği alt sınıflarla çakışmaları neden olmaz sürece sınıflarının güncelleştirmelerine olanak sağlar. Örneğin, bu bayrak, herhangi bir alt sınıfı önceden olarak belirtilmeyen temel sınıfa eklenecek yeni bir özellik sağlar. Sınıf örneği varsa, güncelleştirmeyi başarısız olur. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | Çakışan alt sınıflar bulunduğunda sınıflarının güncelleştirmeleri zorlar. Örneğin, bu bayrak sınıf niteleyici bir alt sınıfında tanımlanır ve var olan bir thte ile çakışıyor aynı niteleyiciyi eklemek temel sınıf çalışırsa bir güncelleştirmenin yapılmasını sağlar. Zorlama modunda, çakışan alt sınıf niteleyicisi silerek TIS çakışma çözülür. |

`pCtx`  
[in] Genellikle, bu değer, `null`. Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen sınıfları sağlayan sağlayıcı tarafından kullanılan bir örnek. 

`ppCallResult`  
[out] Varsa `null`, bu parametre kullanılmaz. Varsa `lFlags` içeren `WBEM_FLAG_RETURN_IMMEDIATELY`, işlev ile hemen döndürür. `WBEM_S_NO_ERROR`. `ppCallResult` Parametre bir işaretçi yeni bir alan [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) nesne.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcı oluşturma veya sınıflar değiştirme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Belirtilen sınıf geçerli değil. Genellikle, gösterir `pObject` örneği nesnesini belirtir. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Belirtilen sınıf adı geçerli değil. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Bir alt kılacak bir değişiklik yapmak için girişimde bulunuldu. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Bayrağı belirtildi, ancak sınıf zaten mevcut. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` Belirtilen `lFlags`, ve sınıfı bulunamadı. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Tüm sınıflar için gerekli özellikleri ayarlanmadı. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durdu ve yeniden başlatılıyor. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) yöntemi.

Kullanıcı sınıfları ile başlayamaz veya bitemez ile bir alt çizgi chacater adları oluşturamaz

İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
