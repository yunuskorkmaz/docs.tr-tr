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
ms.openlocfilehash: f9cac9e00c8cb6a13e2acc62b5f314b7bc0cf9e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629137"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary Yöntemi
Kitaplık sağlayıcı, ortak dil çalışma zamanı (CLR) sürümüne özel hata ayıklama kitaplıklarına ve yüklenecek isteğe bağlı olmasını sağlayan bir geri arama arabirimini alır.  
  
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
 [in] İstenen modülün adı.  
  
 `dwTimestamp`  
 [in] Tarih zaman damgası PE dosyaları COFF dosya üst bilgisinde depolanır.  
  
 `pLibraryProvider`  
 [in] `SizeOfImage` Alan PE dosyaları COFF isteğe bağlı dosya üst bilgisinde depolanır.  
  
 `hModule`  
 [out] İstenen modül tanıtıcısını.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 `ProvideLibrary` belirli bir CLR dosyaları mscordbi.dll ve Mscordacwks.dll dosyasının gibi hata ayıklama için gerekli olan modülleri sağlamak hata ayıklayıcı sağlar. Modül tutamaçları çağrısı kadar geçerli kalır zorunda [Iclrdebugging::canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) boşaltılması, bu noktada, tutamaçları ücretsiz çağrı sahibinin sorumluluğundadır yöntemi gösterir.  
  
 Hata ayıklayıcı kullanılabilir herhangi bir araç bulun veya hata ayıklama modülü tedarik kullanabilir.  
  
> [!IMPORTANT]
>  Bu özellik, yürütülebilir ve büyük olasılıkla kötü amaçlı kod içeren modülleri sağlamak API çağıran sağlar. Bir güvenlik önlemi olarak çağıran kullanmamalısınız `ProvideLibrary` kendisini yürütmek için değil, herhangi bir kod dağıtmak için.  
>   
>  Önemli güvenlik sorunu mscordbi.dll veya Mscordacwks.dll dosyasının, gibi zaten yayımlanmış bir kitaplıktaki bulunursa dolgu dosyalarının hatalı sürümleri tanımak için düzeltme eki uygulanabilir. Dolgu sonra dosyalar, düzeltme eki uygulama sürümleri için istekleri ve tüm isteğine yanıt olarak sağlanırsa, hatalı sürümleri reddet. Yalnızca kullanıcı yeni bir dolgu sürümüne yama değilse bu durum oluşabilir. Yüklenmemiş sürümleri saldırılara açık kalır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
