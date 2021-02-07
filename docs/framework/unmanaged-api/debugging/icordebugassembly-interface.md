---
description: ': ICorDebugAssembly arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 746b5f4b2f26550788708d93bf0dd50f5f495041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711953"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="51424-103">ICorDebugAssembly Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51424-103">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="51424-104">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="51424-104">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51424-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="51424-105">Methods</span></span>  
  
|<span data-ttu-id="51424-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="51424-106">Method</span></span>|<span data-ttu-id="51424-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51424-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51424-108">EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51424-108">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="51424-109">Derlemede bulunan modüller için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="51424-109">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="51424-110">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51424-110">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="51424-111">Bu örneği içeren uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugAssembly` .</span><span class="sxs-lookup"><span data-stu-id="51424-111">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="51424-112">GetCodeBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51424-112">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="51424-113">.NET Framework geçerli sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="51424-113">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="51424-114">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51424-114">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="51424-115">Derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="51424-115">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="51424-116">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51424-116">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="51424-117">Derlemenin çalıştığı ICorDebugProcess örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="51424-117">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51424-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51424-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51424-119">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="51424-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51424-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51424-120">Requirements</span></span>  

 <span data-ttu-id="51424-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51424-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51424-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51424-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51424-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51424-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51424-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51424-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51424-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51424-125">See also</span></span>

- [<span data-ttu-id="51424-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51424-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
