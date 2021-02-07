---
description: ': ICorDebugRegisterSet:: Setyazmaçları yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugRegisterSet::SetRegisters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: 7a83d9d01a392d7ed435292f45ee0c75765ced36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690684"
---
# <a name="icordebugregistersetsetregisters-method"></a>ICorDebugRegisterSet::SetRegisters Yöntemi

`SetRegisters` .NET Framework sürüm 2,0 ' de uygulanmıyor. Bu yöntemi çağırmayın.  
  
> [!NOTE]
> [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md)gibi daha üst düzey işlemleri kullanın.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
