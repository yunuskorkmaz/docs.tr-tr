---
description: 'Daha fazla bilgi edinin: ICorDebugCode2 Interface'
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
ms.openlocfilehash: 29fd657ec56993d47ee57aa41c81b45e75352697
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765054"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="2d24c-103">ICorDebugCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d24c-103">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="2d24c-104">"ICorDebugCode" yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d24c-104">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d24c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2d24c-105">Methods</span></span>  
  
|<span data-ttu-id="2d24c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2d24c-106">Method</span></span>|<span data-ttu-id="2d24c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d24c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d24c-108">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d24c-108">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="2d24c-109">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="2d24c-109">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="2d24c-110">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d24c-110">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="2d24c-111">Bu kod nesnesinin, yerel görüntü Oluşturucu (Ngen.exe) kullanılarak derlenen ya da oluşturulan ya da oluşturulduğu koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="2d24c-111">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d24c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d24c-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d24c-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="2d24c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d24c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d24c-114">Requirements</span></span>  

 <span data-ttu-id="2d24c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d24c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d24c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d24c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d24c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2d24c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d24c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d24c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d24c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d24c-119">See also</span></span>

- [<span data-ttu-id="2d24c-120">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d24c-120">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="2d24c-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2d24c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
