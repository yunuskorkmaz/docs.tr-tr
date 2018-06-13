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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bb275f08143362d62f241ea659ea39ff8eef5d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413088"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="5d83c-102">ICorDebugModule2::GetJITCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="5d83c-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="5d83c-103">Bu Icordebugmodule2 tam zamanında (JIT) derlenmesini denetim bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="5d83c-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d83c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d83c-104">Syntax</span></span>  
  
```  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d83c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d83c-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="5d83c-106">[out] Değerini gösteren bir işaretçi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) JIT derleme denetimleri numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="5d83c-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d83c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d83c-107">Requirements</span></span>  
 <span data-ttu-id="5d83c-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d83c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d83c-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d83c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d83c-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d83c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d83c-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d83c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
