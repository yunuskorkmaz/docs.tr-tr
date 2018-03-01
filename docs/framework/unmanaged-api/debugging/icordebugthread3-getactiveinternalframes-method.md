---
title: ICorDebugThread3::GetActiveInternalFrames Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ecfbaeff9416ee8e6541a23bac6ec76f99abd2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames Metodu
İç çerçeveleri bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneler) yığında.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cInternalFrames`  
 [in] Beklenen iç çerçeve sayısı `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Bir işaretçi bir `ULONG32` yığında iç çerçeve sayısını içerir.  
  
 `ppInternalFrames`  
 [içinde out] Yığında iç çerçeveler dizisi adresini gösteren bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|[Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesne başarıyla oluşturuldu.|  
|E_INVALIDARG|`cInternalFrames`sıfır değil ve `ppInternalFrames` olan `null`, veya `pcInternalFrames` olan `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`İç çerçeveler sayısından daha küçüktür.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 İç çerçeveler yığına geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarını ' dir.  
  
 İlk çağırdığınızda `GetActiveInternalFrames`, ayarlamanız gerekir `cInternalFrames` parametresi 0 (sıfır) ve `ppInternalFrames` parametresi null. Zaman `GetActiveInternalFrames` ilk döndürür, `pcInternalFrames` yığında iç çerçeve sayısını içerir.  
  
 `GetActiveInternalFrames`ardından ikinci bir kez çağrılmalıdır. Uygun sayısı geçirmelisiniz (`pcInternalFrames`) içinde `cInternalFrames` parametresi ve uygun şekilde boyutlu bir dizide bir işaretçi belirtin `ppInternalFrames`.  
  
 Kullanım [Icordebugstackwalk::getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) gerçek döndürülecek yöntemi yığın çerçeveleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
