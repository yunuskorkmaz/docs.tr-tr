---
title: ICorDebugCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: 1e5b92d99d8ae52c88f1517f9c3d7db8e70598ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720808"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="8fb4e-102">ICorDebugCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fb4e-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="8fb4e-103">"ICorDebugCode" yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8fb4e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8fb4e-104">Methods</span></span>  
  
|<span data-ttu-id="8fb4e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8fb4e-105">Method</span></span>|<span data-ttu-id="8fb4e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fb4e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8fb4e-107">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fb4e-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="8fb4e-108">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="8fb4e-109">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fb4e-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="8fb4e-110">Bu kod nesnesinin, yerel görüntü Oluşturucu (Ngen.exe) kullanılarak derlenen ya da oluşturulan ya da oluşturulduğu koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fb4e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fb4e-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fb4e-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fb4e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fb4e-113">Requirements</span></span>  

 <span data-ttu-id="8fb4e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fb4e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fb4e-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8fb4e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fb4e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8fb4e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fb4e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fb4e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb4e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-118">See also</span></span>

- [<span data-ttu-id="8fb4e-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fb4e-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="8fb4e-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8fb4e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
