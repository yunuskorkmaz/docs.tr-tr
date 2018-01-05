---
title: "PutClassWmi işlevi (yönetilmeyen API Başvurusu)"
description: "PutClassWmi işlevi yeni bir sınıf oluşturur veya mevcut bir güncelleştirir."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 219cec2096cd3d1dfe1e0d3c0903b62692e444e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="putclasswmi-function"></a>PutClassWmi işlevi
Yeni bir sınıf oluşturur veya mevcut bir güncelleştirir.  

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
[in] Geçerli bir sınıf tanımı için bir işaretçi. Gereken tüm özellik değerlerini ile doğru şekilde yeniden başlatılmalıdır.

`lFlags`   
[in] Bu işlev davranışını etkileyen bayrak birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Ayarlama, WMI herhangi niteleyicileri değiştirilmiş özellik ile depolamaz </br> Değilse kümesi varsayılır Bu nesne yerelleştirilmemiş ve tüm niteleyiciler storedwith olduğundan bu örnek. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Bunu yok, veya zaten varsa üzerine sınıfı oluşturun. |
| `WBEM_FLAG_UPDATE_ONLY` | 1. | Sınıf güncelleştirin. Sınıfı, çağrı başarılı olması mevcut olması gerekir. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Sınıf oluşturun. Sınıf zaten varsa çağrı başarısız olur. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumlu bir çağrı neden olur. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | İtme sağlayıcıları, bu bayrak belirtmelisiniz, çağrılırken `PutClassWmi` Bu sınıf değiştiğini belirtmek için. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Türetilmiş sınıfları ve bu sınıfın hiçbir örneği varsa güncelleştirilmesi için bir sınıf sağlar. Değişiklik yalnızca açıklama niteleyici gibi önemli niteleyicileri istiyorsanız tüm durumlarda da güncelleştirmeler sağlar. Sınıf örnekleri olan veya önemli niteleyicileri değişikliklerdir güncelleştirme başarısız olur. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Olsa bile alt sınıflar değişiklik alt sınıflarla çakışmaları neden olmaz sürece sınıfların güncelleştirmeler sağlar. Örneğin, bu bayrak herhangi bir alt sınıfı önceden olarak belirtilmeyen temel sınıf eklemek yeni bir özellik sağlar. Sınıf örneği varsa, güncelleştirme başarısız. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | Çakışan alt sınıflar bulunduğunda sınıfların güncelleştirmeleri zorlar. Örneğin, bu bayrak, sınıf niteleyici bir alt sınıfında tanımlanır ve olduğu bir varolan thte ile çakışıyor aynı niteleyici eklemek temel sınıf çalışırsa bir güncelleştirme zorlar. Zorlama modunda TIS çakışma alt sınıf çakışan niteleyicisinde silerek çözümlenir. |

`pCtx`  
[in] Bu değer genellikle `null`. Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek. 

`ppCallResult`  
[out] Varsa `null`, bu parametre kullanılmıyor. Varsa `lFlags` içeren `WBEM_FLAG_RETURN_IMMEDIATELY`, işlevi ile hemen döndürür `WBEM_S_NO_ERROR`. `ppCallResult` Parametre alan yeni bir işaretçi [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) nesnesi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcı oluşturma veya sınıfları değiştirme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirlenemeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Belirtilen sınıf geçerli değil. Genellikle, bu belirten `pObject` örneği nesneyi belirtir. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Belirtilen sınıf adı geçerli değil. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Bir alt sınıfı kılacak bir değişiklik yapılmaya çalışıldı. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Bayrağı belirtildi, ancak sınıf zaten mevcut. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`Belirtilen `lFlags`, ve sınıfı bulunamadı. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Tüm sınıflar için gerekli özellikleri ayarlanmadı. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durduruldu ve yeniden başlatma. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) yöntemi.

Kullanıcı sınıfları başlayamaz ya da bir alt çizgi chacater ile bitemez adlarla oluşturamaz

İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
