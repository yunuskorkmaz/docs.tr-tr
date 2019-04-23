---
title: ICorDebugCode4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23f588b46eb452b7670085249938f7d10cea1ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108185"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="e9391-102">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9391-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="e9391-103">Bir işlevdeki bağımsız değişkenler ve yerel değişkenler numaralandırmak bir hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9391-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9391-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e9391-104">Methods</span></span>  
  
|<span data-ttu-id="e9391-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e9391-105">Method</span></span>|<span data-ttu-id="e9391-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9391-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9391-107">EnumerateVariableHomes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9391-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="e9391-108">Bir numaralandırıcı bir işlevde yerel değişkenleri ve bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="e9391-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9391-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9391-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9391-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e9391-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9391-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9391-111">Requirements</span></span>  
 <span data-ttu-id="e9391-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9391-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9391-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9391-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9391-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9391-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9391-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9391-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9391-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9391-116">See also</span></span>

- [<span data-ttu-id="e9391-117">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9391-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="e9391-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e9391-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
