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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178460"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames Metodu
Yığında bir dizi iç çerçeve[(ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
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
 [içinde] 'de `ppInternalFrames`beklenen iç çerçeve sayısı.  
  
 `pcInternalFrames`  
 [çıkış] Yığındaki iç `ULONG32` çerçeve sayısını içeren bir işaretçi.  
  
 `ppInternalFrames`  
 [içinde, dışarı] Yığındaki bir iç çerçeve dizisinin adresine işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, yöntem hatasını gösteren HRESULT hatalarının yanı sıra aşağıdaki özel HRESULT'ları da döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesnesi başarıyla oluşturuldu.|  
|E_ınvalıdarg|`cInternalFrames`sıfır değildir `ppInternalFrames` ve `null`, `pcInternalFrames` `null`ya da .|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`iç çerçeve sayısından daha küçüktür.|  
  
## <a name="exceptions"></a>Özel durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına itilen veri yapılarıdır.  
  
 İlk aradığınızda, `GetActiveInternalFrames`parametreyi `cInternalFrames` 0 (sıfır) ve `ppInternalFrames` parametreyi null olarak ayarlamanız gerekir. İlk `GetActiveInternalFrames` döndürdüğünde, `pcInternalFrames` yığındaki iç çerçevesayısını içerir.  
  
 `GetActiveInternalFrames`sonra ikinci kez çağrılmalıdır. Parametredeki uygun sayıyı (`pcInternalFrames`) geçirmeli ve 'de `ppInternalFrames`uygun büyüklükteki bir diziye işaretçi belirtmelisiniz. `cInternalFrames`  
  
 Gerçek yığın çerçevelerini döndürmek için [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) yöntemini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata ayıklama](index.md)
