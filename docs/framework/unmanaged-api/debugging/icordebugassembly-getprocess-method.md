---
title: ICorDebugAssembly::GetProcess Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: 49b234b065eb66dc2ec0bc7e991117c5b54a92f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196345"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="b0a93-102">ICorDebugAssembly::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="b0a93-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="b0a93-103">Bu ICorDebugAssembly örneğinin çalıştırıldığı işleme yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b0a93-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0a93-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0a93-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0a93-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="b0a93-106">dışı İşlemi temsil eden ICorDebugProcess arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0a93-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0a93-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0a93-107">Requirements</span></span>  
 <span data-ttu-id="b0a93-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0a93-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a93-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0a93-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0a93-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0a93-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0a93-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a93-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
