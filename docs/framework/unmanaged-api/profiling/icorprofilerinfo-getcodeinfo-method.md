---
title: ICorProfilerInfo::GetCodeInfo Yöntemi
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
ms.openlocfilehash: eb6efc738b270f8f76d7130a12af4927fb6220ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498368"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="be65d-102">ICorProfilerInfo::GetCodeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be65d-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="be65d-103">Belirtilen işlev KIMLIĞIYLE ilişkili yerel kod kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="be65d-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="be65d-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="be65d-104">This method is obsolete.</span></span> <span data-ttu-id="be65d-105">Bunun yerine [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="be65d-105">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be65d-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="be65d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be65d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be65d-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="be65d-108">'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="be65d-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="be65d-109">dışı İşlevin yerel kodunu oluşturan bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be65d-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="be65d-110">dışı Yerel kodun boyutunu bayt cinsinden belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="be65d-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be65d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be65d-111">Remarks</span></span>  
 <span data-ttu-id="be65d-112">Performansı iyileştirmek için .NET Framework sürüm 2,0 çalışma zamanı, bir işlevin önceden derlenmiş, yerel kodunu birden çok bölgeye ayırır.</span><span class="sxs-lookup"><span data-stu-id="be65d-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="be65d-113">Sonuç olarak, `GetCodeInfo` bir işlevin yerel kodunun kapsamını işleyemediği için yöntem .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="be65d-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="be65d-114">Profil oluşturucular bunun yerine daha genel yöntemi kullanmak için kullanılmalıdır `ICorProfilerInfo2::GetCodeInfo2` .</span><span class="sxs-lookup"><span data-stu-id="be65d-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="be65d-115">Bu işlev, arayana ayrılan arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="be65d-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be65d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be65d-116">Requirements</span></span>  
 <span data-ttu-id="be65d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be65d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be65d-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="be65d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be65d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="be65d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be65d-120">**.NET Framework sürümleri:** 1,0</span><span class="sxs-lookup"><span data-stu-id="be65d-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be65d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be65d-121">See also</span></span>

- [<span data-ttu-id="be65d-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be65d-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="be65d-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="be65d-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="be65d-124">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="be65d-124">Profiling</span></span>](index.md)
