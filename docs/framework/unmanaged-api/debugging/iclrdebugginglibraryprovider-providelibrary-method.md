---
title: ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0644258eb1622f388f55d0657c8922079fe4dc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407254"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi
Ortak dil çalışma zamanı (CLR) sürüme özgü hata ayıklama kitaplıkları bulunduğu ve yüklenen üzerinde isteğe bağlı olarak geri çağırma arabirimi kitaplığı sağlayıcısı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pwszFilename`  
 [in] İstenen modülü adı.  
  
 `dwTimestamp`  
 [in] PE dosyaları COFF dosya üstbilgisinde saklanan tarih ve saat damgası.  
  
 `pLibraryProvider`  
 [in] `SizeOfImage` PE dosyaları COFF isteğe bağlı bir dosya üstbilgisinde saklanan alan.  
  
 `hModule`  
 [out] İstenen modülü için tanıtıcı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 `ProvideLibrary` hata ayıklama mscordbi.dll ve Mscordacwks.dll dosyasının gibi belirli CLR dosyaları için gerekli olan modülleri sağlamak hata ayıklayıcı sağlar. Modül tanıtıcıları yapılan bir çağrı kadar geçerli kalır zorunda [Iclrdebugging::canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) yöntemi gösterir boşaltılması, bu noktada, tanıtıcıları serbest yapanın sorumluluğundadır.  
  
 Hata ayıklayıcı bulun veya hata ayıklama modülü tedarik etmek için herhangi bir kullanılabilir yöntem kullanabilir.  
  
> [!IMPORTANT]
>  Bu özellik yürütülebilir ve büyük olasılıkla kötü amaçlı kod içeren modüller sağlamak API çağıran sağlar. Bir güvenlik önlemi olarak çağıran değil kullanması gereken `ProvideLibrary` kendisini yürütmek hazır değil, herhangi bir kod dağıtmak için.  
>   
>  Örneğin mscordbi.dll veya Mscordacwks.dll dosyasının, önceden yayımlanmış bir Kitaplığı'nda ciddi güvenlik sorunu bulunup dolgu dosyalarının hatalı sürümleri tanımak için düzeltme eki. Dolgu sonra düzeltme eki dosyalarının sürümleri için istekleri ve herhangi isteğine yanıt olarak sağlandıysa hatalı sürümleri reddedin. Yalnızca kullanıcı dolgu yeni bir sürüme düzeltme eki uygulandı bu durum ortaya çıkabilir. Düzeltme eki yüklenmemiş sürümleri açık halde kalır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
