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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426269d14992ae0f1f8c02619b259cfdd4bcbf8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959434"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="0c8a6-102">ICorDebugAssembly Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c8a6-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="0c8a6-103">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c8a6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0c8a6-104">Methods</span></span>  
  
|<span data-ttu-id="0c8a6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0c8a6-105">Method</span></span>|<span data-ttu-id="0c8a6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c8a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c8a6-107">EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c8a6-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="0c8a6-108">Derlemede bulunan modüller için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="0c8a6-109">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c8a6-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="0c8a6-110">Bu `ICorDebugAssembly` örneği içeren uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="0c8a6-111">GetCodeBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c8a6-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="0c8a6-112">.NET Framework geçerli sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="0c8a6-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c8a6-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="0c8a6-114">Derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="0c8a6-115">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c8a6-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="0c8a6-116">Derlemenin çalıştığı ICorDebugProcess örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c8a6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c8a6-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c8a6-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8a6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c8a6-119">Requirements</span></span>  
 <span data-ttu-id="0c8a6-120">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8a6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8a6-121">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c8a6-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c8a6-122">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0c8a6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c8a6-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8a6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8a6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c8a6-124">See also</span></span>

- [<span data-ttu-id="0c8a6-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c8a6-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
