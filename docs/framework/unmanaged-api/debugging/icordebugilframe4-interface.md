---
description: 'Daha fazla bilgi edinin: ICorDebugILFrame4 Interface'
title: ICorDebugILFrame4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: f2d29229f039509ed7799399f0d4d701e8cafba7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791211"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="73f60-103">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73f60-103">ICorDebugILFrame4 Interface</span></span>

<span data-ttu-id="73f60-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="73f60-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="73f60-105">Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="73f60-105">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="73f60-106">Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f60-106">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73f60-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="73f60-107">Methods</span></span>  
  
|<span data-ttu-id="73f60-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="73f60-108">Method</span></span>|<span data-ttu-id="73f60-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73f60-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73f60-110">EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73f60-110">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="73f60-111">Geçerli çerçevede kullanılabilir olan yerel değişkenlerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="73f60-111">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="73f60-112">GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73f60-112">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="73f60-113">Bu yığın çerçevesinin çalıştığı kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="73f60-113">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="73f60-114">GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73f60-114">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="73f60-115">Il çerçevesindeki yerel bir değişkenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="73f60-115">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73f60-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73f60-116">Remarks</span></span>  

 <span data-ttu-id="73f60-117">Bu yöntemler, [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)ve [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemleri tarafından sağlana ek olarak işlevsellik sunar.</span><span class="sxs-lookup"><span data-stu-id="73f60-117">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="73f60-118">Her yöntem `flags` , profil oluşturucunun yeniden JIT isteği tarafından tanımlanan ek yerel değişkenlerin veya kodun görünür olup olmadığını belirten bir parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="73f60-118">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73f60-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73f60-119">Requirements</span></span>  

 <span data-ttu-id="73f60-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73f60-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73f60-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73f60-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73f60-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="73f60-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73f60-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73f60-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f60-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73f60-124">See also</span></span>

- [<span data-ttu-id="73f60-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="73f60-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="73f60-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="73f60-126">Debugging</span></span>](index.md)
