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
ms.openlocfilehash: 7f1c5d7a6fdae3e4c5a66c9aa4a82911105f4597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788501"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="f89fd-102">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f89fd-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="f89fd-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="f89fd-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f89fd-104">Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f89fd-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="f89fd-105">Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f89fd-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f89fd-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f89fd-106">Methods</span></span>  
  
|<span data-ttu-id="f89fd-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f89fd-107">Method</span></span>|<span data-ttu-id="f89fd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f89fd-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f89fd-109">EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f89fd-109">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="f89fd-110">Geçerli çerçevede kullanılabilir olan yerel değişkenlerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f89fd-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="f89fd-111">GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f89fd-111">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="f89fd-112">Bu yığın çerçevesinin çalıştığı kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f89fd-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="f89fd-113">GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f89fd-113">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="f89fd-114">Il çerçevesindeki yerel bir değişkenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f89fd-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f89fd-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f89fd-115">Remarks</span></span>  
 <span data-ttu-id="f89fd-116">Bu yöntemler, [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)ve [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemleri tarafından sağlana ek olarak işlevsellik sunar.</span><span class="sxs-lookup"><span data-stu-id="f89fd-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="f89fd-117">Her yöntem, profil oluşturucunun ReJIT isteği tarafından tanımlanan ek yerel değişkenlerin veya kodun görünür olup olmadığını belirten bir `flags` parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="f89fd-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f89fd-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f89fd-118">Requirements</span></span>  
 <span data-ttu-id="f89fd-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f89fd-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f89fd-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f89fd-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f89fd-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f89fd-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f89fd-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f89fd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89fd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f89fd-123">See also</span></span>

- [<span data-ttu-id="f89fd-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f89fd-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f89fd-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f89fd-125">Debugging</span></span>](index.md)
