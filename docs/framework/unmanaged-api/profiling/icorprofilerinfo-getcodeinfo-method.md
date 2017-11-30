---
title: ICorProfilerInfo::GetCodeInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCodeInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0b5c7b0d932200f04df0a1a84dd1f747b7945943
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="3d8ed-102">ICorProfilerInfo::GetCodeInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="3d8ed-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="3d8ed-103">Belirtilen işlev kimlikle ilişkili yerel kod kapsamını alır</span><span class="sxs-lookup"><span data-stu-id="3d8ed-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="3d8ed-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-104">This method is obsolete.</span></span> <span data-ttu-id="3d8ed-105">Kullanım [Icorprofilerınfo2::getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d8ed-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d8ed-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d8ed-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d8ed-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3d8ed-108">[in] Yerel kod ilişkilendirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="3d8ed-109">[out] Yerel kod işlevinin oluşturan bir bayt dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="3d8ed-110">[out] Yerel kod bayt cinsinden boyutu belirten bir tamsayı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d8ed-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d8ed-111">Remarks</span></span>  
 <span data-ttu-id="3d8ed-112">Performansı iyileştirmek için çalışma zamanında .NET Framework sürüm 2.0 işlevinin önceden derlenmiş, yerel kod birden fazla bölgeye böler.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="3d8ed-113">Sonuç olarak, `GetCodeInfo` yöntemi nedeni .NET Framework 2. 0 ' eski bir işlevin yerel kod kapsamını işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="3d8ed-114">Profil oluşturucular geçiş daha genel kullanmaya `ICorProfilerInfo2::GetCodeInfo2` yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="3d8ed-115">Bu işlev, çağıran tarafından ayrılan arabellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d8ed-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d8ed-116">Requirements</span></span>  
 <span data-ttu-id="3d8ed-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d8ed-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d8ed-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d8ed-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d8ed-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d8ed-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d8ed-120">**.NET framework sürümleri:** 1.0</span><span class="sxs-lookup"><span data-stu-id="3d8ed-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d8ed-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d8ed-121">See Also</span></span>  
 [<span data-ttu-id="3d8ed-122">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d8ed-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3d8ed-123">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3d8ed-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3d8ed-124">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d8ed-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
