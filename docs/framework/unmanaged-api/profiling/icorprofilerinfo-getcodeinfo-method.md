---
title: ICorProfilerInfo::GetCodeInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5004de587f715a2f3958c36999e432d7d6e9f2fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632666"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="ed59a-102">ICorProfilerInfo::GetCodeInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="ed59a-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="ed59a-103">Belirtilen işlev kimlikle ilişkili yerel kod kapsamını alır</span><span class="sxs-lookup"><span data-stu-id="ed59a-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="ed59a-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ed59a-104">This method is obsolete.</span></span> <span data-ttu-id="ed59a-105">Kullanım [Icorprofilerınfo2::getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="ed59a-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed59a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed59a-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed59a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed59a-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ed59a-108">[in] Yerel kod ilişkilendirildiği işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="ed59a-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="ed59a-109">[out] İşlevin yerel kodu oluşturan bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed59a-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="ed59a-110">[out] Yerel kod bayt cinsinden boyutunu belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ed59a-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed59a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed59a-111">Remarks</span></span>  
 <span data-ttu-id="ed59a-112">Performansı iyileştirmek için önceden derlenmiş yerel kod bir işlevin .NET Framework sürüm 2.0 çalışma zamanında birden fazla bölgeye böler.</span><span class="sxs-lookup"><span data-stu-id="ed59a-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="ed59a-113">Sonuç olarak, `GetCodeInfo` yöntemi artık kullanılmıyor .NET Framework 2.0 sürümünde çünkü bir işlevin yerel kodunu kapsamını işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="ed59a-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="ed59a-114">Profil oluşturucular geçiş daha genel kullanarak `ICorProfilerInfo2::GetCodeInfo2` yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="ed59a-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="ed59a-115">Bu işlev, arayana ayrılan arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed59a-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed59a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed59a-116">Requirements</span></span>  
 <span data-ttu-id="ed59a-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed59a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed59a-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed59a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed59a-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed59a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed59a-120">**.NET framework sürümleri:** 1.0</span><span class="sxs-lookup"><span data-stu-id="ed59a-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed59a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed59a-121">See also</span></span>
- [<span data-ttu-id="ed59a-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed59a-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="ed59a-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ed59a-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ed59a-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed59a-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
