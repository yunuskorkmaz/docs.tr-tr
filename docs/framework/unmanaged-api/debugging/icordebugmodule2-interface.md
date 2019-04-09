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
ms.openlocfilehash: d3fb1bf3f61c78f4eb157b93363b1c06b25bee04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119905"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="d249c-102">ICorDebugModule2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d249c-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="d249c-103">Icordebugmodule arabirimi mantıksal uzantısı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="d249c-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d249c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d249c-104">Methods</span></span>  
  
|<span data-ttu-id="d249c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d249c-105">Method</span></span>|<span data-ttu-id="d249c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d249c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d249c-107">ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d249c-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="d249c-108">Meta veri değişiklikleri ve Microsoft Ara dil (MSIL) kodu değişiklikleri çalışan işlemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d249c-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="d249c-109">GetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d249c-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="d249c-110">Just-in-time (JIT) derlenmesi için bu denetim bayrakları alır `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="d249c-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="d249c-111">ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d249c-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="d249c-112">Belirtilen meta veri belirteci tarafından başvurulan derlemenin çözümler.</span><span class="sxs-lookup"><span data-stu-id="d249c-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="d249c-113">SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d249c-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="d249c-114">Bunun için JIT derlemesi denetleyen bayraklar ayarlar `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="d249c-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="d249c-115">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d249c-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="d249c-116">Bu tüm yöntemleri tüm sınıflara yalnızca benim kodum (JMC) durumunu ayarlar `ICorDebugModule2` hariç belirtilen değere `pTokens` dizisi karşı değer olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d249c-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d249c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d249c-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d249c-118">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d249c-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d249c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d249c-119">Requirements</span></span>  
 <span data-ttu-id="d249c-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d249c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d249c-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d249c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d249c-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d249c-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d249c-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d249c-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d249c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d249c-124">See also</span></span>

- [<span data-ttu-id="d249c-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d249c-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
