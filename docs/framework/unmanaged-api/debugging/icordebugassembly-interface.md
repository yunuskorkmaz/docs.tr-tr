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
ms.openlocfilehash: d9e2236b944137de82bb056820f81014febfcc5f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894904"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="b7434-102">ICorDebugAssembly Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7434-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="b7434-103">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b7434-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7434-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b7434-104">Methods</span></span>  
  
|<span data-ttu-id="b7434-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b7434-105">Method</span></span>|<span data-ttu-id="b7434-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7434-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7434-107">EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7434-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="b7434-108">Derlemede bulunan modüller için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b7434-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="b7434-109">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7434-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="b7434-110">Bu `ICorDebugAssembly` örneği içeren uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b7434-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="b7434-111">GetCodeBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7434-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="b7434-112">.NET Framework geçerli sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="b7434-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="b7434-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7434-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="b7434-114">Derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="b7434-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="b7434-115">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7434-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="b7434-116">Derlemenin çalıştığı ICorDebugProcess örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="b7434-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7434-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7434-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7434-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b7434-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7434-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7434-119">Requirements</span></span>  
 <span data-ttu-id="b7434-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7434-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7434-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b7434-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7434-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b7434-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7434-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7434-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7434-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7434-124">See also</span></span>

- [<span data-ttu-id="b7434-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b7434-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
