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
ms.openlocfilehash: 7b98302985d9d54599ea8ea2e01dc2503c468d58
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210234"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="3f104-102">ICorDebugModule2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f104-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="3f104-103">ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="3f104-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f104-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3f104-104">Methods</span></span>  
  
|<span data-ttu-id="3f104-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3f104-105">Method</span></span>|<span data-ttu-id="3f104-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f104-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f104-107">ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f104-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="3f104-108">Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="3f104-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="3f104-109">GetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f104-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="3f104-110">Bunun için tam zamanında (JıT) derlemeyi denetleyen bayrakları alır `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="3f104-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="3f104-111">ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f104-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="3f104-112">Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="3f104-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="3f104-113">SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f104-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="3f104-114">Bu için JıT derlemesini denetleyen bayrakları ayarlar `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="3f104-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="3f104-115">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f104-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="3f104-116">Bu, dizideki tüm yöntemlerin tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `ICorDebugModule2` dizideki değerler hariç, bu değerin `pTokens` ters değere göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3f104-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f104-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f104-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f104-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="3f104-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f104-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f104-119">Requirements</span></span>  
 <span data-ttu-id="3f104-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f104-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f104-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f104-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f104-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f104-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f104-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f104-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f104-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f104-124">See also</span></span>

- [<span data-ttu-id="3f104-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3f104-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
