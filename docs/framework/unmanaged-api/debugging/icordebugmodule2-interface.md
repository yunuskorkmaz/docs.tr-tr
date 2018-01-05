---
title: Icordebugmodule2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2
helpviewer_keywords: ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3d62619fd83264bdc774cc1f09f4d98492d0a57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="6042d-102">Icordebugmodule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="6042d-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="6042d-103">Icordebugmodule arabirimi için mantıksal bir uzantısı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="6042d-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6042d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6042d-104">Methods</span></span>  
  
|<span data-ttu-id="6042d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6042d-105">Method</span></span>|<span data-ttu-id="6042d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6042d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6042d-107">ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6042d-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="6042d-108">Meta veri değişiklikleri ve Microsoft Ara dili (MSIL) kod değişiklikleri çalışan işlemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6042d-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="6042d-109">GetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6042d-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="6042d-110">Tam zamanında (JIT) derleme için bu denetim bayrakları alır `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="6042d-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="6042d-111">ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6042d-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="6042d-112">Belirtilen meta veri simgesi tarafından başvurulan derleme çözümler.</span><span class="sxs-lookup"><span data-stu-id="6042d-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="6042d-113">SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6042d-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="6042d-114">JIT derleme için bu denetim bayrakları ayarlar `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="6042d-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="6042d-115">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6042d-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="6042d-116">Tüm sınıfların tüm yöntemleri yalnızca My kod (JMC) durumunu bu ayarlar `ICorDebugModule2` hariç belirtilen değerle `pTokens` ters değerine ayarlar dizi.</span><span class="sxs-lookup"><span data-stu-id="6042d-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6042d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6042d-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6042d-118">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6042d-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6042d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6042d-119">Requirements</span></span>  
 <span data-ttu-id="6042d-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6042d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6042d-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6042d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6042d-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6042d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6042d-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6042d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6042d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6042d-124">See Also</span></span>  
 [<span data-ttu-id="6042d-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6042d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
