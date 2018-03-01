---
title: "ICorDebugILFrame2::RemapFunction Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9fed4759576d1b6d2fec1a5e9c1e36019e5944c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
