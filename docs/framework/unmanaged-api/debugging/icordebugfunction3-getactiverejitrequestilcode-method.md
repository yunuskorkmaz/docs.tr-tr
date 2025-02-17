---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugFunction3:: Getactiverejrequestilcode yöntemi'
title: ICorDebugFunction3::GetActiveReJitRequestILCode Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 9225c5cdf97395b7e1b11c61d653cab8d52031c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692127"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode Metodu

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Etkin bir ReJIT isteğinden Il 'yi içeren bir [ICorDebugILCode](icordebugilcode-interface.md) için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppReJitedILCode`  
 Etkin bir ReJIT isteğinden Il 'ye yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu nesne tarafından temsil edilen yöntemin `ICorDebugFunction3` etkin bir ReJIT isteği varsa, `ppReJitedILCode` Il 'ye bir işaretçi döndürür. Ortak bir durum olan etkin istek yoksa, `ppReJitedILCode` **null** olur.  
  
 Yeniden JIT isteği, yürütme, [ICorProfilerCallback4:: Getrejparameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) yöntem çağrısından çağrıldıktan hemen sonra etkin hale gelir. Henüz JıT derlenemez ve iş parçacıkları kodun orijinal sürümünde hala yürütülüyor olabilir. Profil Oluşturucu [ICorProfilerInfo4:: Requestdöndürülüyor](../profiling/icorprofilerinfo4-requestrevert-method.md) yöntemine yapılan çağrı sırasında yeniden JIT isteği devre dışı olur. Il geri alındıktan sonra bile, bir iş parçacığı yine de JıT-yeniden derleme (ReJIT) kodunda yürütülüyor olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugFunction3 Arabirimi](icordebugfunction3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ReJIT: A How-To Kılavuzu](/archive/blogs/davbr/rejit-a-how-to-guide)
