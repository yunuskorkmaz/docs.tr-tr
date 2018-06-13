---
title: ICorDebugCode4 arabirimi
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
ms.openlocfilehash: 624db77f0db2fe374e16abae64b6bf6ad290baa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411440"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="1a45e-102">ICorDebugCode4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a45e-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="1a45e-103">Yerel değişkenleri ve bir işlev bağımsız değişkenleri numaralandırmak bir hata ayıklayıcısı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a45e-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a45e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1a45e-104">Methods</span></span>  
  
|<span data-ttu-id="1a45e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1a45e-105">Method</span></span>|<span data-ttu-id="1a45e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a45e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a45e-107">EnumerateVariableHomes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a45e-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="1a45e-108">Bir numaralandırıcı bir işlevde yerel değişkenleri ve bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="1a45e-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a45e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a45e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a45e-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1a45e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a45e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a45e-111">Requirements</span></span>  
 <span data-ttu-id="1a45e-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a45e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a45e-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a45e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a45e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a45e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a45e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a45e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a45e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a45e-116">See Also</span></span>  
    
    
 [<span data-ttu-id="1a45e-117">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a45e-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="1a45e-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1a45e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
