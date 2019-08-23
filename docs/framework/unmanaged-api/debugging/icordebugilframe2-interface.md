---
title: ICorDebugILFrame2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d02dab01eca3bd4f8ce3ae7ace7f9d4be8233dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917012"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="8a411-102">ICorDebugILFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a411-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="8a411-103">ICorDebugILFrame arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="8a411-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a411-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a411-104">Methods</span></span>  
  
|<span data-ttu-id="8a411-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a411-105">Method</span></span>|<span data-ttu-id="8a411-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a411-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a411-107">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a411-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="8a411-108">Bu çerçevedeki <xref:System.Type> parametreleri içeren bir ICorDebugTypeEnum nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="8a411-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="8a411-109">RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a411-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="8a411-110">Yeni MSIL sapmasını belirterek düzenlenmiş bir işlevi yeniden eşler.</span><span class="sxs-lookup"><span data-stu-id="8a411-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a411-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a411-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a411-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="8a411-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a411-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a411-113">Requirements</span></span>  
 <span data-ttu-id="8a411-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a411-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a411-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a411-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a411-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8a411-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a411-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a411-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a411-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a411-118">See also</span></span>

- [<span data-ttu-id="8a411-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a411-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
