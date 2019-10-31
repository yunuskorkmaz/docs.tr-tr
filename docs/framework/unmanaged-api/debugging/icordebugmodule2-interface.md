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
ms.openlocfilehash: a3a1b658f4ab05c7029de907882fe5ab2513ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127880"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="72d9f-102">ICorDebugModule2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72d9f-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="72d9f-103">ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="72d9f-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72d9f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="72d9f-104">Methods</span></span>  
  
|<span data-ttu-id="72d9f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="72d9f-105">Method</span></span>|<span data-ttu-id="72d9f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72d9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72d9f-107">ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72d9f-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="72d9f-108">Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="72d9f-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="72d9f-109">GetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72d9f-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="72d9f-110">Bu `ICorDebugModule2`için tam zamanında (JıT) derlemeyi denetleyen bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="72d9f-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="72d9f-111">ResolveAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72d9f-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="72d9f-112">Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.</span><span class="sxs-lookup"><span data-stu-id="72d9f-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="72d9f-113">SetJITCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72d9f-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="72d9f-114">Bu `ICorDebugModule2`JıT derlemesini denetleyen bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="72d9f-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="72d9f-115">SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72d9f-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="72d9f-116">Bu `ICorDebugModule2` tüm sınıfların tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `pTokens` dizisinde, zıt değere göre ayarlaanlar dışında, belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="72d9f-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72d9f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72d9f-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72d9f-118">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="72d9f-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72d9f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72d9f-119">Requirements</span></span>  
 <span data-ttu-id="72d9f-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72d9f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72d9f-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72d9f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72d9f-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="72d9f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72d9f-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72d9f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d9f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72d9f-124">See also</span></span>

- [<span data-ttu-id="72d9f-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="72d9f-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
