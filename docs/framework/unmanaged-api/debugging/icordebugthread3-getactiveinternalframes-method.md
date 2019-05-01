---
title: ICorDebugThread3::GetActiveInternalFrames Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e264f2361c739536d15fbf31d366db74e107bac2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993895"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames Metodu
İç çerçeveler bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) yığında.  
  
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
  
## <a name="parameters"></a>Parametreler  
 `cInternalFrames`  
 [in] Beklenen iç çerçeve sayısı `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Bir işaretçi bir `ULONG32` içeren yığında iç çerçeve sayısı.  
  
 `ppInternalFrames`  
 [out içinde] İç çerçeveler yığın üzerinde bir dizi adresi için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|[Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesne başarıyla oluşturuldu.|  
|E_INVALIDARG|`cInternalFrames` sıfır değilse ve `ppInternalFrames` olduğu `null`, veya `pcInternalFrames` olduğu `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` İç çerçeveler sayısından küçük.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 İç çerçeveler, yığın üstüne, geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarıdır.  
  
 İlk çağırdığınızda `GetActiveInternalFrames`, ayarlamalısınız `cInternalFrames` parametresi 0 (sıfır) ve `ppInternalFrames` parametresi null. Zaman `GetActiveInternalFrames` ilk döndürür, `pcInternalFrames` yığında iç çerçeve sayısını içerir.  
  
 `GetActiveInternalFrames` ardından ikinci bir kez çağrılmalıdır. Uygun sayısı geçmelidir (`pcInternalFrames`) içinde `cInternalFrames` parametresi ve uygun boyutlandırılmış bir dizide bir işaretçi belirtin `ppInternalFrames`.  
  
 Kullanım [Icordebugstackwalk::getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) gerçek döndürmek için yöntemin yığın çerçevesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
