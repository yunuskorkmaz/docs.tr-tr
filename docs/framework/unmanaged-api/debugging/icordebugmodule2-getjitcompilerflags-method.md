---
title: ICorDebugModule2::GetJITCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
ms.openlocfilehash: ab6551ba70ed4cd154b166eeb92138b6550d2cb2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792973"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="5f5f0-102">ICorDebugModule2::GetJITCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="5f5f0-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="5f5f0-103">Bu ICorDebugModule2 'ın tam zamanında (JıT) derlemesini denetleyen bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="5f5f0-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f5f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f5f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f5f0-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="5f5f0-106">dışı JıT derlemesini denetleyen [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5f5f0-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5f0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f5f0-107">Requirements</span></span>  
 <span data-ttu-id="5f5f0-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f5f0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f5f0-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5f5f0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f5f0-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5f5f0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f5f0-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f5f0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
