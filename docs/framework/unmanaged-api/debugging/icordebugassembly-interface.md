---
title: ICorDebugAssembly Arabirimi
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
ms.openlocfilehash: dea3231e3bbb361b56254756c6d99b115f73e792
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133964"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="e0d17-102">ICorDebugAssembly Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0d17-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="e0d17-103">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0d17-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0d17-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e0d17-104">Methods</span></span>  
  
|<span data-ttu-id="e0d17-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e0d17-105">Method</span></span>|<span data-ttu-id="e0d17-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0d17-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0d17-107">EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0d17-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="e0d17-108">Derlemede bulunan modüller için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e0d17-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="e0d17-109">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0d17-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="e0d17-110">Bu `ICorDebugAssembly` örneğini içeren uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e0d17-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="e0d17-111">GetCodeBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0d17-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="e0d17-112">.NET Framework geçerli sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e0d17-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="e0d17-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0d17-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="e0d17-114">Derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="e0d17-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="e0d17-115">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0d17-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="e0d17-116">Derlemenin çalıştığı ICorDebugProcess örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="e0d17-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0d17-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0d17-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0d17-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e0d17-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0d17-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0d17-119">Requirements</span></span>  
 <span data-ttu-id="e0d17-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0d17-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0d17-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0d17-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0d17-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e0d17-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0d17-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0d17-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d17-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0d17-124">See also</span></span>

- [<span data-ttu-id="e0d17-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0d17-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
