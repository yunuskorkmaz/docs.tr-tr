---
title: Icordebugassembly Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88134fb7854091bb60e8084a6d776bdec922c7e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406376"
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="3d4d2-102">Icordebugassembly Interface1</span><span class="sxs-lookup"><span data-stu-id="3d4d2-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="3d4d2-103">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d4d2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3d4d2-104">Methods</span></span>  
  
|<span data-ttu-id="3d4d2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3d4d2-105">Method</span></span>|<span data-ttu-id="3d4d2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d4d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d4d2-107">EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d4d2-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="3d4d2-108">Derlemesinde bulunan modülleri için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="3d4d2-109">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d4d2-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="3d4d2-110">Bu içeren uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugAssembly` örneği.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="3d4d2-111">GetCodeBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d4d2-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="3d4d2-112">.NET Framework'ün geçerli sürümde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="3d4d2-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d4d2-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="3d4d2-114">Derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="3d4d2-115">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d4d2-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="3d4d2-116">Derleme çalıştığı Icordebugprocess örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d4d2-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d4d2-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d4d2-118">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d4d2-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d4d2-119">Requirements</span></span>  
 <span data-ttu-id="3d4d2-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d4d2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4d2-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d4d2-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d4d2-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d4d2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d4d2-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4d2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4d2-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-124">See Also</span></span>  
 [<span data-ttu-id="3d4d2-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3d4d2-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
