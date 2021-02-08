---
description: 'Daha fazla bilgi edinin: ICorDebugThread3:: GetActiveInternalFrames yöntemi'
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
ms.openlocfilehash: f228dd84708478bb364ac09407a68df3e8d971b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800987"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames Metodu

Yığında iç çerçeveler ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.  
  
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
 'ndaki İçinde beklenen iç çerçeve sayısı `ppInternalFrames` .  
  
 `pcInternalFrames`  
 dışı `ULONG32` Yığın üzerindeki iç çerçevelerin sayısını içeren bir işaretçisi.  
  
 `ppInternalFrames`  
 [in, out] Yığındaki iç çerçeveler dizisinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesnesi başarıyla oluşturuldu.|  
|E_INVALIDARG|`cInternalFrames` sıfır değildir ve `ppInternalFrames` `null` , veya ' dir `pcInternalFrames` `null` .|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` , iç çerçeve sayısından daha küçüktür.|  
  
## <a name="exceptions"></a>Özel durumlar  
  
## <a name="remarks"></a>Açıklamalar  

 İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına gönderilen veri yapılarıdır.  
  
 İlk kez çağırdığınızda `GetActiveInternalFrames` `cInternalFrames` parametresini 0 (sıfır) ve parametresini null olarak ayarlamanız gerekir `ppInternalFrames` . `GetActiveInternalFrames`İlk döndüğünde, `pcInternalFrames` yığındaki iç çerçevelerin sayısını içerir.  
  
 `GetActiveInternalFrames` ikinci kez çağrılmalıdır. Parametreye doğru Count ( `pcInternalFrames` ) geçirin `cInternalFrames` ve içinde uygun boyutta bir diziye yönelik bir işaretçi belirtmeniz gerekir `ppInternalFrames` .  
  
 Gerçek yığın çerçevelerini döndürmek için [ıcordebugstackyürüme:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
