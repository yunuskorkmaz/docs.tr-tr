---
title: Icordebugcode2 Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13803a8cc292da602b1b920a3879120c3e754ca4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414564"
---
# <a name="icordebugcode2-interface1"></a><span data-ttu-id="63095-102">Icordebugcode2 Interface1</span><span class="sxs-lookup"><span data-stu-id="63095-102">ICorDebugCode2 Interface1</span></span>
<span data-ttu-id="63095-103">"ICorDebugCode" özelliklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="63095-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63095-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="63095-104">Methods</span></span>  
  
|<span data-ttu-id="63095-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="63095-105">Method</span></span>|<span data-ttu-id="63095-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63095-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63095-107">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63095-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="63095-108">Bu kod nesnesi oluşan kod parçalarını alır.</span><span class="sxs-lookup"><span data-stu-id="63095-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="63095-109">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63095-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="63095-110">Bu kod nesnesi ya da sadece derlenmiş veya yerel Görüntü Oluşturucu (Ngen.exe) kullanılarak oluşturulan zamanında (JIT) altında olduğu koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="63095-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63095-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63095-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63095-112">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="63095-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63095-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63095-113">Requirements</span></span>  
 <span data-ttu-id="63095-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63095-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63095-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63095-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63095-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63095-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63095-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63095-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63095-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63095-118">See Also</span></span>  
    
 [<span data-ttu-id="63095-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63095-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="63095-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="63095-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
