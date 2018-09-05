---
title: PutInstanceWmi işlevi (yönetilmeyen API Başvurusu)
description: PutInstanceWmi işlevi oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67abf017040b9e6bbe9b10e560c8d57c124ae84e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658970"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi işlevi
Oluşturur veya mevcut bir sınıfın bir örneğini güncelleştirir. Örneği, WMI deposuna yazılır. 

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
[in] Writen olmasını örneğine bir işaretçi.

`lFlags`   
[in] Bu işlevin davranışını etkileyen bayrakların birleşimi. Aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda: 

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Ayarlanırsa, WMI ile ilgili tüm niteleyicileri depolamaz, **Amended** çeşidi. </br> Aksi durumda, küme bu nesne yerelleştirilmez ve tüm niteleyicileri storedwith başladığınız varsayılır Bu örneği. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Olmayan mevcut veya zaten varsa üzerine örneği oluşturun. |
| `WBEM_FLAG_UPDATE_ONLY` | 1. | Örnek güncelleştirin. Örnek çağrı başarılı olması mevcut olması gerekir. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Örneği oluşturun. Örneği zaten varsa başarısız olur. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Bayrağı yarı zaman uyumsuz bir çağrı neden olur. |

`pCtx`  
[in] Genellikle, bu değer, `null`. Aksi takdirde, bir işaretçi olduğu bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) istenen sınıfları sağlayan sağlayıcı tarafından kullanılan bir örnek. 

`ppCallResult`  
[out] Varsa `null`, bu parametre kullanılmaz. Varsa `lFlags` içeren `WBEM_FLAG_RETURN_IMMEDIATELY`, işlev ile hemen döndürür. `WBEM_S_NO_ERROR`. `ppCallResult` Parametre bir işaretçi yeni bir alan [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) nesne.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Kullanıcının belirtilen sınıfın bir örneği güncelleştirme izni yok. |
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Bu örneğinin destekleyen sınıf geçerli değil. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | bir `null` edilemeyecek bir özelliği için belirtilen `null`, tarafından işaretlenen bir gibi bir **sıralı** veya **Not_Null** niteleyicisi. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Belirtilen örnek geçerli değil. (Örneğin, çağırma `PutInstanceWmi` bir sınıf ile bu değeri döndürür.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Bayrağı belirtildi, ancak örnek zaten mevcut. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` Belirtilen `lFlags`, ancak örneği yok. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI, büyük olasılıkla durdu ve yeniden başlatılıyor. Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) yöntemi.

`PutInstanceWmi` İşlev örnekleri oluşturma ve güncelleştirme yalnızca mevcut sınıfların örneklerini destekler.  Bağlı olarak nasıl `pCtx` parametresi olarak ayarlanmışsa, bazı veya tüm özelliklerini örneğinin güncelleştirilir. 

Ne zaman örneği tarafından işaret edilen `pInst` bir alt sınıfı için Windows Yönetim alt sınıfın türetildiği sınıfların için sorumlu tüm sağlayıcıları çağrıları ait. Tüm bu sağlayıcıları için özgün başarılı olması gerektiği `PutInstanceWmi` başarılı olması için istek. Hiyerarşideki en üst sınıf destekleyen sağlayıcı önce çağrılır. Arama sırası üstteki sınıfının alt ile devam eder ve sağlayıcı işaret ettiği örneğine sahip olan sınıf için Windows Yönetim ulaşana kadar üstten alta geçer `pInst`.
Windows yönetimi sağlayıcıları herhangi bir alt sınıfı örneğinin çağırmaz. 

Bir sınıf hiyerarşisine ait bir örnek uygulamanın güncelleştirmeniz gerektiğinde `pInst` parametresi değiştirilecek özellikleri içeren örneğine işaret etmelidir. Diğer bir deyişle, ait bir hedef örneği göz önünde bulundurun **Sınıfb**. **Sınıfb** örneği türetilir **Türetilme**, ve **Türetilme** özelliği tanımlar **PropA**. Bir uygulama değerinde bir değişiklik isteyip istemediği **PropA** içinde **Sınıfb** örneği, onu ayarlamanız gerekir `pInst` örneği yerine bu örneği **Türetilme** .

Çağırma `PutInstanceWmi` soyut bir sınıf örneği üzerinde izin verilmiyor.

İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
