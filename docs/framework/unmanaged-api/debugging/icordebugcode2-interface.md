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
ms.openlocfilehash: a9ce778cfa1aed4dcf6117c4fe2eca23ccda37a3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777958"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="8c4c0-102">ICorDebugCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c4c0-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="8c4c0-103">"ICorDebugCode" yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c4c0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8c4c0-104">Methods</span></span>  
  
|<span data-ttu-id="8c4c0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8c4c0-105">Method</span></span>|<span data-ttu-id="8c4c0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c4c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c4c0-107">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c4c0-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="8c4c0-108">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="8c4c0-109">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c4c0-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="8c4c0-110">Bu kod nesnesinin yerel görüntü Oluşturucu (Ngen. exe) kullanılarak derlenen veya oluşturulan koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c4c0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c4c0-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c4c0-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c4c0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c4c0-113">Requirements</span></span>  
 <span data-ttu-id="8c4c0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c4c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c4c0-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c4c0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c4c0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8c4c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c4c0-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c4c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4c0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c4c0-118">See also</span></span>

- [<span data-ttu-id="8c4c0-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c4c0-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="8c4c0-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c4c0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
