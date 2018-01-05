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
ms.workload: dotnet
ms.openlocfilehash: cd05f1ed64e32c4b451f3e60d856be0e99e302b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="ad085-102">ICorProfilerInfo::GetCodeInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="ad085-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="ad085-103">Belirtilen işlev kimlikle ilişkili yerel kod kapsamını alır</span><span class="sxs-lookup"><span data-stu-id="ad085-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="ad085-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ad085-104">This method is obsolete.</span></span> <span data-ttu-id="ad085-105">Kullanım [Icorprofilerınfo2::getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="ad085-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad085-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad085-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad085-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad085-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ad085-108">[in] Yerel kod ilişkilendirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="ad085-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="ad085-109">[out] Yerel kod işlevinin oluşturan bir bayt dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad085-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="ad085-110">[out] Yerel kod bayt cinsinden boyutu belirten bir tamsayı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad085-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad085-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad085-111">Remarks</span></span>  
 <span data-ttu-id="ad085-112">Performansı iyileştirmek için çalışma zamanında .NET Framework sürüm 2.0 işlevinin önceden derlenmiş, yerel kod birden fazla bölgeye böler.</span><span class="sxs-lookup"><span data-stu-id="ad085-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="ad085-113">Sonuç olarak, `GetCodeInfo` yöntemi nedeni .NET Framework 2. 0 ' eski bir işlevin yerel kod kapsamını işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="ad085-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="ad085-114">Profil oluşturucular geçiş daha genel kullanmaya `ICorProfilerInfo2::GetCodeInfo2` yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="ad085-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="ad085-115">Bu işlev, çağıran tarafından ayrılan arabellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad085-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad085-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad085-116">Requirements</span></span>  
 <span data-ttu-id="ad085-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad085-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad085-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad085-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad085-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad085-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad085-120">**.NET framework sürümleri:** 1.0</span><span class="sxs-lookup"><span data-stu-id="ad085-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad085-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad085-121">See Also</span></span>  
 [<span data-ttu-id="ad085-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad085-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ad085-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad085-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ad085-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad085-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
