---
description: ': ICorDebugAppDomainEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: dfea6254e6cf4f162e44d057fb4126a67a087b61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754166"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="002bc-103">ICorDebugAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="002bc-103">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="002bc-104">, `Next` `ICorDebugAppDomainEnum` Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen sayıda değer döndüren yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="002bc-104">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="002bc-105">Bu arabirim "ıcordebuggenum" öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="002bc-105">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="002bc-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="002bc-106">Methods</span></span>  
  
|<span data-ttu-id="002bc-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="002bc-107">Method</span></span>|<span data-ttu-id="002bc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="002bc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="002bc-109">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="002bc-109">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="002bc-110">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda uygulama etki alanı alır.</span><span class="sxs-lookup"><span data-stu-id="002bc-110">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="002bc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="002bc-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="002bc-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="002bc-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002bc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="002bc-113">Requirements</span></span>  

 <span data-ttu-id="002bc-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002bc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002bc-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="002bc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="002bc-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="002bc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="002bc-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="002bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002bc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="002bc-118">See also</span></span>

- [<span data-ttu-id="002bc-119">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="002bc-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="002bc-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="002bc-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
