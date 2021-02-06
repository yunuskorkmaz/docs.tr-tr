---
description: ': ICorProfilerInfo:: GetCodeInfo yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e965e9c21b7add0367b08f152bf509ad6b6ed4cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647667"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="f963d-103">ICorProfilerInfo::GetCodeInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f963d-103">ICorProfilerInfo::GetCodeInfo Method</span></span>

<span data-ttu-id="f963d-104">Belirtilen işlev KIMLIĞIYLE ilişkili yerel kod kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="f963d-104">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="f963d-105">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f963d-105">This method is obsolete.</span></span> <span data-ttu-id="f963d-106">Bunun yerine [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f963d-106">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f963d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f963d-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f963d-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f963d-108">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="f963d-109">'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f963d-109">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="f963d-110">dışı İşlevin yerel kodunu oluşturan bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f963d-110">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="f963d-111">dışı Yerel kodun boyutunu bayt cinsinden belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f963d-111">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f963d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f963d-112">Remarks</span></span>  

 <span data-ttu-id="f963d-113">Performansı iyileştirmek için .NET Framework sürüm 2,0 çalışma zamanı, bir işlevin önceden derlenmiş, yerel kodunu birden çok bölgeye ayırır.</span><span class="sxs-lookup"><span data-stu-id="f963d-113">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="f963d-114">Sonuç olarak, `GetCodeInfo` bir işlevin yerel kodunun kapsamını işleyemediği için yöntem .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f963d-114">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="f963d-115">Profil oluşturucular bunun yerine daha genel yöntemi kullanmak için kullanılmalıdır `ICorProfilerInfo2::GetCodeInfo2` .</span><span class="sxs-lookup"><span data-stu-id="f963d-115">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="f963d-116">Bu işlev, arayana ayrılan arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f963d-116">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f963d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f963d-117">Requirements</span></span>  

 <span data-ttu-id="f963d-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f963d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f963d-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f963d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f963d-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f963d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f963d-121">**.NET Framework sürümleri:** 1,0</span><span class="sxs-lookup"><span data-stu-id="f963d-121">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f963d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f963d-122">See also</span></span>

- [<span data-ttu-id="f963d-123">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f963d-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f963d-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f963d-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f963d-125">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f963d-125">Profiling</span></span>](index.md)
