---
title: ICorDebugDataTarget::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: faacea6a2f04ef20025fd33adb4ce76eaf54f32c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679747"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext Metodu

Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwThreadID`  
 'ndaki Bağlamını alınacak olan iş parçacığının tanımlayıcısı. Tanımlayıcı, işletim sistemi tarafından tanımlanır.  
  
 `contextFlags`  
 'ndaki İçeriğin hangi bölümlerinin okunabileceği belirten, platforma bağımlı bayrakların bit düzeyinde birleşimi.  
  
 `contextSize`  
 'ndaki Boyutu `pContext` .  
  
 `pContext`  
 dışı İş parçacığı bağlamının depolanacağı arabellek.  
  
## <a name="remarks"></a>Açıklamalar  

 Windows platformlarında, `pContext` `CONTEXT` [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından belirtilen makine türüne uygun bir yapı (Winnt. h içinde tanımlanır) olmalıdır. `contextFlags` yapının alanıyla aynı değerlere sahip olmalıdır `ContextFlags` `CONTEXT` . `CONTEXT`Yapı, işlemciye özeldir; Ayrıntılar Için Winnt. h dosyasına bakın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget Arabirimi](icordebugdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
