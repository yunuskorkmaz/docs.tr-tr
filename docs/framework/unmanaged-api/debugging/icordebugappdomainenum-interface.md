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
ms.openlocfilehash: c48c222a34e2e78f29c33e49da331d97d409bae1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949755"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="f65ac-102">ICorDebugAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f65ac-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="f65ac-103">, Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen `ICorDebugAppDomainEnum` sayıda değer döndüren yönteminisağlar.`Next`</span><span class="sxs-lookup"><span data-stu-id="f65ac-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="f65ac-104">Bu arabirim "ıcordebuggenum" öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="f65ac-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f65ac-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f65ac-105">Methods</span></span>  
  
|<span data-ttu-id="f65ac-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f65ac-106">Method</span></span>|<span data-ttu-id="f65ac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f65ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f65ac-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f65ac-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="f65ac-109">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda uygulama etki alanı alır.</span><span class="sxs-lookup"><span data-stu-id="f65ac-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f65ac-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f65ac-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f65ac-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f65ac-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f65ac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f65ac-112">Requirements</span></span>  
 <span data-ttu-id="f65ac-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f65ac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f65ac-114">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f65ac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f65ac-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f65ac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f65ac-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f65ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f65ac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f65ac-117">See also</span></span>

- [<span data-ttu-id="f65ac-118">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f65ac-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="f65ac-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f65ac-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
