---
title: ICorProfilerInfo::GetFunctionFromIP Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fba01c1dfdea83b2580f45b7dbcef91fb7b73fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452910"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="ca6d7-102">ICorProfilerInfo::GetFunctionFromIP Metodu</span><span class="sxs-lookup"><span data-stu-id="ca6d7-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="ca6d7-103">Yönetilen kod yönerge işaretçisi eşleyen bir `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="ca6d7-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca6d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca6d7-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca6d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca6d7-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="ca6d7-106">[in] Yönetilen kod yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ca6d7-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="ca6d7-107">[out] Döndürülen işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="ca6d7-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6d7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca6d7-108">Requirements</span></span>  
 <span data-ttu-id="ca6d7-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6d7-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ca6d7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca6d7-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca6d7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca6d7-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6d7-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca6d7-113">See Also</span></span>  
 [<span data-ttu-id="ca6d7-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca6d7-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
