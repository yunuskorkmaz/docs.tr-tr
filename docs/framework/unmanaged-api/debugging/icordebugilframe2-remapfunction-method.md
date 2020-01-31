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
ms.openlocfilehash: f4f73b99b4cb48690a2a8611dbf5a5420adab5d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794346"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction Yöntemi
Yeni Microsoft ara dili (MSIL) sapmasını belirterek düzenlenmiş bir işlevi yeniden eşler  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `newILOffset`  
 'ndaki Yığın çerçevesinin, yönerge işaretçisinin yerleştirilmesi gereken yeni MSIL kayması. Bu değer bir dizi noktası olmalıdır.  
  
 Bu değerin geçerliliğini sağlamak için çağıranın sorumluluğundadır. Örneğin, MSIL boşluğu, işlev sınırlarının dışındaysa geçerli değildir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir çerçevenin işlevi düzenlendiğinde, hata ayıklayıcı çerçeve işlevinin en son sürümünde takas etmek için `RemapFunction` yöntemini çağırabilir, böylece yürütülür. Kod yürütme, verilen MSIL uzaklığında başlar.  
  
> [!NOTE]
> [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md)çağırma gibi `RemapFunction`çağırmak, iş parçacığı için yığın izlemesi oluşturma ile ilgili tüm hata ayıklama arabirimlerini hemen geçersiz kılar. Bu arabirimler [ıcordebugzincirini](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame ve ICorDebugNativeFrame ' i içerir.  
  
 `RemapFunction` yöntemi yalnızca geçerli çerçevenin bağlamında ve yalnızca aşağıdaki durumlardan birinde çağrılabilir:  
  
- [ICorDebugManagedCallback2:: FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) geri çağrısının alındıktan sonra henüz devam edilmemiş.  
  
- Bu çerçeve için [ICorDebugManagedCallback:: EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) olayı nedeniyle kod yürütme işlemi durduruldu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
