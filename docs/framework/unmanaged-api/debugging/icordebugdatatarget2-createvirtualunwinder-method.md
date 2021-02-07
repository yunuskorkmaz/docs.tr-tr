---
description: 'Daha fazla bilgi edinin: ICorDebugDataTarget2:: CreateVirtualUnwinder yöntemi'
title: ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 0646c85000f42b303769d6587354b3105e2deabd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764417"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi

Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a>Parametreler  

 NativeThreadId  
 'ndaki Yığını ölçeklendirme yapılacak iş parçacığının yerel iş parçacığı KIMLIĞI.  
  
 contextFlags  
 'ndaki İçeriğin hangi bölümlerinin tanımlandığını belirten bayraklar `initialContext` .  
  
 cbContext  
 'ndaki Boyutu `initialContext` .  
  
 InitialContext  
 'ndaki Bağlamdaki veriler.  
  
 ppUnwinder  
 dışı Bir ICorDebugVirtualUnwinder Interface nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` başarılı olursa. Diğer bir `HRESULT` hata olduğunu gösterir. `HRESULT`Mscordbi tarafından alınan herhangi bir hata önemli kabul edilir ve [ICorDebug](icordebug-interface.md) yöntemlerinin döndürülmesine neden olur `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget2 Arabirimi](icordebugdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
