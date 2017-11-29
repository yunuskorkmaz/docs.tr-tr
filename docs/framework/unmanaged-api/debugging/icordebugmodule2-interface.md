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
ms.openlocfilehash: 97259783d34babe3f0f229f5d62b3e945c0ac624
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="06d71-102">Icordebugmodule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="06d71-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="06d71-103">Icordebugmodule arabirimi için mantıksal bir uzantısı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="06d71-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06d71-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="06d71-104">Methods</span></span>  
  
|<span data-ttu-id="06d71-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="06d71-105">Method</span></span>|<span data-ttu-id="06d71-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06d71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06d71-107">ApplyChanges yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d71-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="06d71-108">Meta veri değişiklikleri ve Microsoft Ara dili (MSIL) kod değişiklikleri çalışan işlemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="06d71-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="06d71-109">Getjıtcompilerflags yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d71-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="06d71-110">Tam zamanında (JIT) derleme için bu denetim bayrakları alır `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="06d71-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="06d71-111">ResolveAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d71-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="06d71-112">Belirtilen meta veri simgesi tarafından başvurulan derleme çözümler.</span><span class="sxs-lookup"><span data-stu-id="06d71-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="06d71-113">Setjıtcompilerflags yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d71-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="06d71-114">JIT derleme için bu denetim bayrakları ayarlar `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="06d71-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="06d71-115">SetJMCStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d71-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="06d71-116">Tüm sınıfların tüm yöntemleri yalnızca My kod (JMC) durumunu bu ayarlar `ICorDebugModule2` hariç belirtilen değerle `pTokens` ters değerine ayarlar dizi.</span><span class="sxs-lookup"><span data-stu-id="06d71-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06d71-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06d71-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06d71-118">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="06d71-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d71-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06d71-119">Requirements</span></span>  
 <span data-ttu-id="06d71-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06d71-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06d71-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06d71-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06d71-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06d71-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06d71-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06d71-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d71-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06d71-124">See Also</span></span>  
 [<span data-ttu-id="06d71-125">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="06d71-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
