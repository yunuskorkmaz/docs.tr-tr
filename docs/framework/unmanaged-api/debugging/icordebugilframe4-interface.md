---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b57289e1d96a56bc4ab5cb8c07cbcac4b1d98b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416585"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="756c2-102">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="756c2-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="756c2-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="756c2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="756c2-104">Yerel değişkenleri ve Ara dile (IL) kodunun yığın çerçevesi kodda erişmenize olanak sağlayan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="756c2-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="756c2-105">Bir parametre hata ayıklayıcı değişkenleri ve profiler ReJIT araçları eklenen kod erişim sahip olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="756c2-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="756c2-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="756c2-106">Methods</span></span>  
  
|<span data-ttu-id="756c2-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="756c2-107">Method</span></span>|<span data-ttu-id="756c2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="756c2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="756c2-109">EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="756c2-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="756c2-110">Geçerli çerçevede kullanılabilir yerel değişkenler listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="756c2-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="756c2-111">GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="756c2-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="756c2-112">Bu yığın çerçevesi çalıştıran kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="756c2-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="756c2-113">GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="756c2-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="756c2-114">Yerel bir değişken değerini IL çerçevede döndürür.</span><span class="sxs-lookup"><span data-stu-id="756c2-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="756c2-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="756c2-115">Remarks</span></span>  
 <span data-ttu-id="756c2-116">Bu yöntemler tarafından sağlanana ek olarak işlevleri sunar [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), ve [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="756c2-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="756c2-117">Her yöntem içerir bir `flags` ek yerel değişkenler veya Profil Oluşturucu'nın ReJIT isteği tarafından tanımlanan kod olup görünür belirten parametre.</span><span class="sxs-lookup"><span data-stu-id="756c2-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="756c2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="756c2-118">Requirements</span></span>  
 <span data-ttu-id="756c2-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="756c2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="756c2-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="756c2-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="756c2-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="756c2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="756c2-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="756c2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756c2-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="756c2-123">See Also</span></span>  
 [<span data-ttu-id="756c2-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="756c2-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="756c2-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="756c2-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
