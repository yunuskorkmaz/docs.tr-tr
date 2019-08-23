---
title: ICorDebugModule2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8fe1a25c4bc1f5e19f49f0d660d0aad5a180ea2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911896"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="fc9e5-102">ICorDebugModule2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc9e5-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="fc9e5-103">ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc9e5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fc9e5-104">Methods</span></span>  
  
|<span data-ttu-id="fc9e5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fc9e5-105">Method</span></span>|<span data-ttu-id="fc9e5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc9e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc9e5-107">ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc9e5-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="fc9e5-108">Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="fc9e5-109">GetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc9e5-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="fc9e5-110">Bunun `ICorDebugModule2`için tam zamanında (JIT) derlemeyi denetleyen bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="fc9e5-111">ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc9e5-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="fc9e5-112">Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="fc9e5-113">SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc9e5-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="fc9e5-114">Bu `ICorDebugModule2`için JIT derlemesini denetleyen bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="fc9e5-115">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc9e5-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="fc9e5-116">Bu, `pTokens` dizideki tüm yöntemlerin tüm yöntemlerinin yalnızca kendi kodum (JMC) durumunu, dizideki değerler hariç `ICorDebugModule2` , bu değerin ters değere göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc9e5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc9e5-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc9e5-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc9e5-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc9e5-119">Requirements</span></span>  
 <span data-ttu-id="fc9e5-120">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc9e5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc9e5-121">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc9e5-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc9e5-122">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fc9e5-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc9e5-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc9e5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9e5-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc9e5-124">See also</span></span>

- [<span data-ttu-id="fc9e5-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fc9e5-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
