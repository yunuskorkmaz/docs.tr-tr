---
description: 'Daha fazla bilgi edinin: ICorDebugModule2 Interface'
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
ms.openlocfilehash: 28de1f0d3411218ac92991d4fceda0612c8199bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659939"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="6ea27-103">ICorDebugModule2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ea27-103">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="6ea27-104">ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6ea27-104">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ea27-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6ea27-105">Methods</span></span>  
  
|<span data-ttu-id="6ea27-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6ea27-106">Method</span></span>|<span data-ttu-id="6ea27-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ea27-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ea27-108">ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ea27-108">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="6ea27-109">Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="6ea27-109">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="6ea27-110">GetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ea27-110">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="6ea27-111">Bunun için tam zamanında (JıT) derlemeyi denetleyen bayrakları alır `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="6ea27-111">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="6ea27-112">ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ea27-112">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="6ea27-113">Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="6ea27-113">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="6ea27-114">SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ea27-114">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="6ea27-115">Bu için JıT derlemesini denetleyen bayrakları ayarlar `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="6ea27-115">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="6ea27-116">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ea27-116">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="6ea27-117">Bu, dizideki tüm yöntemlerin tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `ICorDebugModule2` dizideki değerler hariç, bu değerin `pTokens` ters değere göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6ea27-117">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ea27-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ea27-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ea27-119">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6ea27-119">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ea27-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ea27-120">Requirements</span></span>  

 <span data-ttu-id="6ea27-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ea27-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ea27-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ea27-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ea27-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6ea27-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ea27-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ea27-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea27-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ea27-125">See also</span></span>

- [<span data-ttu-id="6ea27-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6ea27-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
