---
description: 'Daha fazla bilgi edinin: ICorDebugModule2:: GetJITCompilerFlags yöntemi'
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
ms.openlocfilehash: f1aa01bf2bc92a6fc20687b726ef1c0a6f860a97
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659978"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="97dca-103">ICorDebugModule2::GetJITCompilerFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="97dca-103">ICorDebugModule2::GetJITCompilerFlags Method</span></span>

<span data-ttu-id="97dca-104">Bu ICorDebugModule2 'ın tam zamanında (JıT) derlemesini denetleyen bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="97dca-104">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97dca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97dca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97dca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97dca-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="97dca-107">dışı JıT derlemesini denetleyen [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırması değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97dca-107">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97dca-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97dca-108">Requirements</span></span>  

 <span data-ttu-id="97dca-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97dca-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97dca-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97dca-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97dca-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97dca-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97dca-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97dca-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
