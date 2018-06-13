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
ms.openlocfilehash: 9f03d8c993be1ac83ca84275bcb94f1bb3cdf884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414989"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction Yöntemi
Yeni Microsoft Ara dili (MSIL) uzaklık belirterek düzenlenen işlevi remaps  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `newILOffset`  
 [in] Yönerge işaretçisi yerleştirilmelidir yığın çerçeve yeni MSIL uzaklığı. Bu değer bir dizi noktası olması gerekir.  
  
 Bu değer geçerliliği sağlamak yapanın sorumluluğundadır. Örneğin, MSIL uzaklık işlevi sınırların dışında kalan ise geçerli değil.  
  
## <a name="remarks"></a>Açıklamalar  
 Çerçevenin işlevi düzenlendiğinde hata ayıklayıcı çağırabilirsiniz `RemapFunction` yürütülmesi için en son sürümünü çerçeve işlevi değiştirilecek yöntemi. Kod yürütmeyi verilen MSIL uzaklığında başlar.  
  
> [!NOTE]
>  Çağırma `RemapFunction`gibi çağırma [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), iş parçacığı için yığın izlemesi oluşturma ile ilgili tüm hata ayıklama arabirimleri hemen geçersiz kılar. Bu arabirimleri dahil [Icordebugchain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), Icordebugılframe, Icordebugınternalframe ve Icordebugnativeframe.  
  
 `RemapFunction` Geçerli çerçevesi bağlamında yalnızca ve yalnızca aşağıdaki durumlarda birinde yöntemi çağrılabilir:  
  
-   Alınmasından sonra bir [Icordebugmanagedcallback2::functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) değil henüz devam ettirildi geri çağırma.  
  
-   Kod yürütmeyi nedeniyle durdurulurken bir [Icordebugmanagedcallback::editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) bu çerçevesi için olay.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
