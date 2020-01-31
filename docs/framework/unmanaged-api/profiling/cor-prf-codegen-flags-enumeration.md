---
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
ms.openlocfilehash: 4dd4e39c9092d018f13e3bd2822e9492d71141ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867301"
---
# <a name="cor_prf_codegen_flags-enumeration"></a><span data-ttu-id="c97c5-102">COR_PRF_CODEGEN_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c97c5-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="c97c5-103">[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c97c5-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c97c5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c97c5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c97c5-105">Members</span></span>  
  
|<span data-ttu-id="c97c5-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c97c5-106">Member</span></span>|<span data-ttu-id="c97c5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c97c5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="c97c5-108">Bu işlevin gövdesinde hiçbir işlev satır içine alınmaz.</span><span class="sxs-lookup"><span data-stu-id="c97c5-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="c97c5-109">Ancak, işlevin kendisine çağıranları satır içine alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="c97c5-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="c97c5-110">Bu işlevin gövdesi için tüm iyileştirmeler devre dışı bırakılacak.</span><span class="sxs-lookup"><span data-stu-id="c97c5-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="c97c5-111">Ancak, işlevin kendisi hala çağıranlar içinde yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="c97c5-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c97c5-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c97c5-112">Remarks</span></span>  
 <span data-ttu-id="c97c5-113">`COR_PRF_CODEGEN_FLAGS` numaralandırması [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi tarafından, PROFIL oluşturucunun JIT-yeniden derleme işlevi için kod oluşturmayı denetlemesini etkinleştirmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c97c5-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c97c5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c97c5-114">Requirements</span></span>  
 <span data-ttu-id="c97c5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c97c5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97c5-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c97c5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c97c5-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c97c5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c97c5-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c97c5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97c5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c97c5-119">See also</span></span>

- [<span data-ttu-id="c97c5-120">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c97c5-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
