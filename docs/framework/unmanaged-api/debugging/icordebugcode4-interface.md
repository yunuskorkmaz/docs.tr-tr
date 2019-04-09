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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108185"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="a9512-102">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9512-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="a9512-103">Bir işlevdeki bağımsız değişkenler ve yerel değişkenler numaralandırmak bir hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9512-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9512-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a9512-104">Methods</span></span>  
  
|<span data-ttu-id="a9512-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a9512-105">Method</span></span>|<span data-ttu-id="a9512-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9512-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9512-107">EnumerateVariableHomes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9512-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="a9512-108">Bir numaralandırıcı bir işlevde yerel değişkenleri ve bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="a9512-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9512-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9512-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9512-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a9512-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9512-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9512-111">Requirements</span></span>  
 <span data-ttu-id="a9512-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9512-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9512-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9512-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9512-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9512-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a9512-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a9512-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a9512-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9512-116">See also</span></span>

- [<span data-ttu-id="a9512-117">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9512-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="a9512-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9512-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
