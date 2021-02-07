---
description: ': ICorDebugAssembly:: GetProcess metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b121d7f892f6e2e2aa76290d4aee51767c72e9fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754157"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="a7db3-103">ICorDebugAssembly::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="a7db3-103">ICorDebugAssembly::GetProcess Method</span></span>

<span data-ttu-id="a7db3-104">Bu ICorDebugAssembly örneğinin çalıştırıldığı işleme yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a7db3-104">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7db3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7db3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7db3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7db3-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="a7db3-107">dışı İşlemi temsil eden ICorDebugProcess arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7db3-107">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7db3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7db3-108">Requirements</span></span>  

 <span data-ttu-id="a7db3-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7db3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7db3-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7db3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7db3-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7db3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7db3-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7db3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
