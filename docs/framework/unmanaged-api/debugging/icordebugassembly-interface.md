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
ms.openlocfilehash: ecd4ad31b8dad55e9538642a4dc652341bc84b97
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784667"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="53bd6-102">ICorDebugAssembly Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53bd6-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="53bd6-103">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="53bd6-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53bd6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="53bd6-104">Methods</span></span>  
  
|<span data-ttu-id="53bd6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="53bd6-105">Method</span></span>|<span data-ttu-id="53bd6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53bd6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53bd6-107">EnumerateModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bd6-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="53bd6-108">Derlemede bulunan modüller için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="53bd6-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="53bd6-109">GetAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bd6-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="53bd6-110">Bu `ICorDebugAssembly` örneğini içeren uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="53bd6-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="53bd6-111">GetCodeBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bd6-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="53bd6-112">.NET Framework geçerli sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="53bd6-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="53bd6-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bd6-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="53bd6-114">Derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="53bd6-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="53bd6-115">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53bd6-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="53bd6-116">Derlemenin çalıştığı ICorDebugProcess örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="53bd6-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53bd6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53bd6-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53bd6-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="53bd6-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53bd6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53bd6-119">Requirements</span></span>  
 <span data-ttu-id="53bd6-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53bd6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53bd6-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="53bd6-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53bd6-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="53bd6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53bd6-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53bd6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53bd6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53bd6-124">See also</span></span>

- [<span data-ttu-id="53bd6-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53bd6-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
