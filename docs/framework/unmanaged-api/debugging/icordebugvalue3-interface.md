---
description: 'Daha fazla bilgi edinin: ICorDebugValue3 Interface'
title: ICorDebugValue3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: e5868b91d23426a2d8dd8fed87b13ec61fef95ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794656"
---
# <a name="icordebugvalue3-interface"></a>ICorDebugValue3 Arabirimi

2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSize64 Yöntemi](icordebugvalue3-getsize64-method.md)|Bu nesnenin boyutunu bayt cinsinden alır `ICorDebugValue3` .|  
  
## <a name="remarks"></a>Açıklamalar  

 [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) yöntemi, 0 ile 2.147.483.647 bayt arasında değişen bir nesne boyutu döndürür. .NET Framework 4,5 ' de, dizilerin boyutu 2 GB 'ı aşabilirler. `ICorDebugValue3`Arabirim, bu dizilerin boyutunu belirlemenizi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
