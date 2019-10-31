---
title: ICorDebugModule2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129464"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus Yöntemi
Bu ICorDebugModule2 içindeki tüm sınıfların tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `pTokens` dizisinde, zıt değere göre ayarladıkları durumlar dışında, belirtilen değere ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIsJustMycode`  
 'ndaki Kodun ayıklanamayacağını `true` olarak ayarlayın; Aksi takdirde, `false`olarak ayarlayın.  
  
 `cTokens`  
 'ndaki `pTokens` dizisinin boyutu.  
  
 `pTokens`  
 'ndaki Her biri JMC durumunun olarak ayarlandığı bir yönteme başvuran `mdToken` değerleri dizisi!`bIsJustMycode`.  
  
## <a name="remarks"></a>Açıklamalar  
 `pTokens` dizisinde belirtilen her yöntemin JMC durumu `bIsJustMycode` değerinin tersi olarak ayarlanır. Bu modüldeki diğer tüm yöntemlerin durumu `bIsJustMycode` değerine ayarlanır.  
  
 `SetJMCStatus` yöntemi Bu modüldeki önceki tüm JMC ayarlarını siler.  
  
 Tüm işlevler başarıyla ayarlandıysa `SetJMCStatus` yöntemi bir S_OK HRESULT döndürür. `true` işaretlenen bazı işlevler hata ayıklanabilir değilse, bir CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
