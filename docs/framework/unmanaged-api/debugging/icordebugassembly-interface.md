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
ms.openlocfilehash: 3dd60defc1c003fa4b235ddcb0a78b9a819b1b0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645538"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="34db8-102">ICorDebugAssembly Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34db8-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="34db8-103">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="34db8-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34db8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="34db8-104">Methods</span></span>  
  
|<span data-ttu-id="34db8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="34db8-105">Method</span></span>|<span data-ttu-id="34db8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34db8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34db8-107">EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34db8-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="34db8-108">Derlemesinde bulunan modüller için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="34db8-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="34db8-109">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34db8-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="34db8-110">Bu içeren uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugAssembly` örneği.</span><span class="sxs-lookup"><span data-stu-id="34db8-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="34db8-111">GetCodeBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34db8-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="34db8-112">.NET Framework'ün geçerli sürümde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="34db8-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="34db8-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34db8-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="34db8-114">Derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="34db8-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="34db8-115">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34db8-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="34db8-116">Derleme çalıştığı Icordebugprocess örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="34db8-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34db8-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34db8-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34db8-118">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="34db8-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34db8-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34db8-119">Requirements</span></span>  
 <span data-ttu-id="34db8-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34db8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34db8-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34db8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34db8-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34db8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34db8-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34db8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34db8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34db8-124">See also</span></span>

- [<span data-ttu-id="34db8-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="34db8-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
