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
ms.openlocfilehash: b17c7630160af78fe3163e6962b8fe085af1edc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206622"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="c7955-102">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7955-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="c7955-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="c7955-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c7955-104">Yerel değişkenleri ve Ara dil (IL) kodu bir yığın çerçevesi kodu erişim olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7955-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="c7955-105">Bir parametre, hata ayıklayıcı değişkenleri ve ReJIT izleme profil oluşturucu, eklenen kod erişimi olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7955-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7955-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c7955-106">Methods</span></span>  
  
|<span data-ttu-id="c7955-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c7955-107">Method</span></span>|<span data-ttu-id="c7955-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7955-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7955-109">EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7955-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="c7955-110">Geçerli kare yerel değişkenler listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7955-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="c7955-111">GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7955-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="c7955-112">Bu yığın çerçevesi çalışan kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7955-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="c7955-113">GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7955-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="c7955-114">IL çerçevesinde yerel değişkenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7955-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7955-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7955-115">Remarks</span></span>  
 <span data-ttu-id="c7955-116">Bu yöntemlere ek olarak, tarafından sağlanan işlevsellik sunabilir [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), ve [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c7955-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="c7955-117">Her yöntem içeren bir `flags` parametresi ek yerel değişkenler veya bir profil oluşturucunun ReJIT istek tarafından tanımlanan kod görünür olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7955-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7955-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7955-118">Requirements</span></span>  
 <span data-ttu-id="c7955-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7955-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7955-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7955-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7955-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7955-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c7955-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c7955-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c7955-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7955-123">See also</span></span>

- [<span data-ttu-id="c7955-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c7955-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c7955-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c7955-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
