---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_CODEGEN_FLAGS numaralandırması'
title: COR_PRF_CODEGEN_FLAGS Sabit Listesi
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 40ddaa77047e0b1daa743b512f21ba7643127230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649182"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="8b385-103">COR_PRF_CODEGEN_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8b385-103">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>

<span data-ttu-id="8b385-104">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b385-104">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b385-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b385-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8b385-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8b385-106">Members</span></span>  
  
|<span data-ttu-id="8b385-107">Üye</span><span class="sxs-lookup"><span data-stu-id="8b385-107">Member</span></span>|<span data-ttu-id="8b385-108">Description</span><span class="sxs-lookup"><span data-stu-id="8b385-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="8b385-109">Bu işlevin gövdesinde hiçbir işlev satır içine alınmaz.</span><span class="sxs-lookup"><span data-stu-id="8b385-109">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="8b385-110">Ancak, işlevin kendisine çağıranları satır içine alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b385-110">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="8b385-111">Bu işlevin gövdesi için tüm iyileştirmeler devre dışı bırakılacak.</span><span class="sxs-lookup"><span data-stu-id="8b385-111">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="8b385-112">Ancak, işlevin kendisi hala çağıranlar içinde yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="8b385-112">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b385-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b385-113">Remarks</span></span>  

 <span data-ttu-id="8b385-114">`COR_PRF_CODEGEN_FLAGS`Numaralandırma, [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi tarafından, profil oluşturucunun JIT işlevi için kod oluşturmayı denetlemesini etkinleştirmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b385-114">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b385-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b385-115">Requirements</span></span>  

 <span data-ttu-id="8b385-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b385-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b385-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8b385-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b385-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8b385-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b385-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b385-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b385-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b385-120">See also</span></span>

- [<span data-ttu-id="8b385-121">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8b385-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
