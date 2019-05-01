---
title: ICorDebugILFrame2::RemapFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92885d2a6514839a864d6a345dd8af8b07b90c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946529"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction Yöntemi
Yeni Microsoft Ara dili (MSIL) uzaklık belirterek düzenlenmiş bir işlevi yeniden eşlemesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `newILOffset`  
 [in] Yönerge işaretçisi yerleştirilmesi gereken yığın çerçeve yeni MSIL uzaklığı. Bu değer bir dizi noktası olması gerekir.  
  
 Bu değerin geçerliliği sağlamak çağrı sahibinin sorumluluğundadır. Örneğin, MSIL uzaklığı işlevi sınırları dışında olması durumunda geçerli değil.  
  
## <a name="remarks"></a>Açıklamalar  
 Çerçevenin işlevi düzenlendiğini, hata ayıklayıcı çağırabilirsiniz `RemapFunction` yürütülmesi için en son sürümünü çerçeve işlevi takas etmek için yöntemi. Kod yürütme belirli MSIL uzaklığında başlar.  
  
> [!NOTE]
>  Çağırma `RemapFunction`gibi çağırma [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), bir iş parçacığı için yığın izlemesi oluşturma ile ilgili tüm hata ayıklama arabirimleri hemen geçersiz kılar. Bu arabirimler dahil [Icordebugchain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), Icordebugılframe Icordebugınternalframe ve Icordebugnativeframe.  
  
 `RemapFunction` Bağlamında geçerli çerçeve yalnızca ve yalnızca aşağıdaki durumlarda birinde yöntemi çağrılabilir:  
  
- Giriş sonra bir [Icordebugmanagedcallback2::functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) değil henüz devam ettirildi geri çağırma.  
  
- Kod yürütme nedeniyle durdurulurken bir [Icordebugmanagedcallback::editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) bu çerçevesi için olay.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
