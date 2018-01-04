---
title: "PutInstanceWmi işlevi (yönetilmeyen API Başvurusu)"
description: "PutInstanceWmi işlevi oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1996103eea87562226537f9aa90dc337c56313c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi işlevi
Oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir. Örnek için WMI deposunun yazılır. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parametreler

`pInst`    
[in] Writen olmasını örneği için bir işaretçi.

`lFlags`   
[in] Bu işlev davranışını etkileyen bayrak birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Ayarlama, WMI ile tüm niteleyicileri depolamaz, **Amended** çeşidi. </br> Değilse kümesi varsayılır Bu nesne yerelleştirilmemiş ve tüm niteleyiciler storedwith olduğundan bu örnek. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Bunu yok, veya zaten varsa üzerine örneği oluşturun. |
| `WBEM_FLAG_UPDATE_ONLY` | 1. | Örnek güncelleştirin. Örnek çağrı başarılı olması mevcut olması gerekir. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Örneği oluşturun. Örneği zaten varsa çağrı başarısız olur. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumlu bir çağrı neden olur. |

`pCtx`  
[in] Bu değer genellikle `null`. Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek. 

`ppCallResult`  
[out] Varsa `null`, bu parametre kullanılmıyor. Varsa `lFlags` içeren `WBEM_FLAG_RETURN_IMMEDIATELY`, işlevi ile hemen döndürür `WBEM_S_NO_ERROR`. `ppCallResult` Parametre alan yeni bir işaretçi [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) nesnesi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcının belirtilen sınıfının bir örneği güncelleştirme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirlenemeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Bu örneğinin destekleyen sınıfı geçerli değil. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | bir `null` olamayacak bir özellik için belirtilen `null`, tarafından işaretlenen gibi bir **sıralı** veya **Not_Null** niteleyicisi. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Belirtilen örnek geçerli değil. (Örneğin, arama `PutInstanceWmi` sınıf ile bu değeri döndürür.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Bayrağı belirtildi, ancak örnek zaten var. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`Belirtilen `lFlags`, ancak örnek yok. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durduruldu ve yeniden başlatma. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) yöntemi.

`PutInstanceWmi` İşlev örnekleri oluşturma ve mevcut sınıfların örnekleri güncelleştirme destekler.  Bağlı olarak nasıl `pCtx` parametre olarak ayarlanmışsa, bazı veya tüm özellikleri örneğinin güncelleştirilir. 

Ne zaman örneği işaret için tarafından `pInst` bir alt sınıfı Windows Management çağrıları için bir alt türetilen sınıflar sorumlu tüm sağlayıcıları ait. Tüm bu sağlayıcıları için özgün başarılı `PutInstanceWmi` başarılı olması için istek. Hiyerarşide en üstteki sınıfı destekleyen sağlayıcı önce çağrılır. Arama sırası en üstteki sınıfın alt ile devam eder ve sağlayıcı gösterdiği örneği sorumlu sınıfı için Windows Yönetim ulaşana kadar üstten alta devam eder `pInst`.
Windows Yönetim sağlayıcıları herhangi bir örneğinin alt sınıfların çağırmaz. 

Bir sınıf hiyerarşiye ait bir örnek uygulamanın güncelleştirmeniz gerektiğinde `pInst` parametresi değiştirilecek özelliklerini içeren örneğine işaret etmelidir. Diğer bir deyişle, ait olduğu bir hedef örneği göz önünde bulundurun **ClassB**. **ClassB** örneği türer **ClassA**, ve **ClassA** özelliği tanımlar **PropA**. Bir uygulama değerine değişiklik yapmak isteyip istemediğini **PropA** içinde **ClassB** örneği, onu ayarlamanız gerekir `pInst` örneği yerine bu örnekte **ClassA** .

Çağırma `PutInstanceWmi` soyut bir sınıf örneği izin verilmiyor.

İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
