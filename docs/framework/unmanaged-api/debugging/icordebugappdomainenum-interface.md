---
title: ICorDebugAppDomainEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c340eb76f3c1c570aa0c9ffa1d461f33d330175
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981510"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="cd0d5-102">ICorDebugAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd0d5-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="cd0d5-103">Sağlar `Next` belirtilen sayıda döndüren yöntemi `ICorDebugAppDomainEnum` sonraki konumdan başlayarak değerleri.</span><span class="sxs-lookup"><span data-stu-id="cd0d5-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="cd0d5-104">Bu arabirim "ICorDebugEnum" sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="cd0d5-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd0d5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd0d5-105">Methods</span></span>  
  
|<span data-ttu-id="cd0d5-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cd0d5-106">Method</span></span>|<span data-ttu-id="cd0d5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd0d5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd0d5-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd0d5-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="cd0d5-109">Koleksiyondan geçerli imleç konumdan başlayarak belirtilen sayıda uygulama etki alanları alır.</span><span class="sxs-lookup"><span data-stu-id="cd0d5-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd0d5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd0d5-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd0d5-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cd0d5-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd0d5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd0d5-112">Requirements</span></span>  
 <span data-ttu-id="cd0d5-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd0d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd0d5-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd0d5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd0d5-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd0d5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd0d5-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd0d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd0d5-117">See also</span></span>
- [<span data-ttu-id="cd0d5-118">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd0d5-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="cd0d5-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cd0d5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
