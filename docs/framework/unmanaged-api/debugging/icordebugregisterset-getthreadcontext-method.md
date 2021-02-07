---
description: ': ICorDebugRegisterSet:: GetThreadContext metodu hakkında daha fazla bilgi edinin'
title: ICorDebugRegisterSet::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: be6384562858d04b6e139eda83c172c09f2dfc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690814"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a>ICorDebugRegisterSet::GetThreadContext Metodu

Geçerli iş parçacığının bağlamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `contextSize`  
 'ndaki Dizinin bayt cinsinden boyutu `context` .  
  
 `context`  
 [in, out] Geçerli platform için Win32 yapısını oluşturan bir bayt dizisi `CONTEXT` .  
  
## <a name="remarks"></a>Açıklamalar  

 `GetThreadContext`İş parçacığı, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 işlevi yerine bu işlevi çağırmalıdır. Döndürülen veriler, `CONTEXT` geçerli platform için bir Win32 yapısıdır.  
  
 Yaprak olmayan kareler için, istemciler [ICorDebugRegisterSet:: GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md)kullanarak hangi yazmaçların geçerli olduğunu denetlemelidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
