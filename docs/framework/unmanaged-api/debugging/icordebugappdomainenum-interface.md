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
ms.openlocfilehash: 38603fb53b9cd6548595437b05c1e99ef208d940
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895090"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="730e0-102">ICorDebugAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="730e0-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="730e0-103">, Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen sayıda `Next` `ICorDebugAppDomainEnum` değer döndüren yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="730e0-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="730e0-104">Bu arabirim "ıcordebuggenum" öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="730e0-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="730e0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="730e0-105">Methods</span></span>  
  
|<span data-ttu-id="730e0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="730e0-106">Method</span></span>|<span data-ttu-id="730e0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730e0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="730e0-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="730e0-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="730e0-109">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda uygulama etki alanı alır.</span><span class="sxs-lookup"><span data-stu-id="730e0-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="730e0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="730e0-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="730e0-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="730e0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730e0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="730e0-112">Requirements</span></span>  
 <span data-ttu-id="730e0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="730e0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="730e0-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="730e0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="730e0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="730e0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="730e0-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="730e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730e0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="730e0-117">See also</span></span>

- [<span data-ttu-id="730e0-118">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="730e0-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="730e0-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="730e0-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
