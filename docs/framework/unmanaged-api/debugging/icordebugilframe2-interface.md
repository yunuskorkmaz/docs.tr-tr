---
description: 'Daha fazla bilgi edinin: ICorDebugILFrame2 Interface'
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
ms.openlocfilehash: 8379fda39a210e1df902dab3ac85132f04aee5fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791315"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="6a018-103">ICorDebugILFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a018-103">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="6a018-104">ICorDebugILFrame arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="6a018-104">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a018-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6a018-105">Methods</span></span>  
  
|<span data-ttu-id="6a018-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6a018-106">Method</span></span>|<span data-ttu-id="6a018-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a018-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a018-108">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a018-108">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="6a018-109">Bu çerçevedeki parametreleri içeren bir ICorDebugTypeEnum nesnesi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="6a018-109">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="6a018-110">RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a018-110">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="6a018-111">Yeni MSIL sapmasını belirterek düzenlenmiş bir işlevi yeniden eşler.</span><span class="sxs-lookup"><span data-stu-id="6a018-111">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a018-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a018-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a018-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6a018-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a018-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a018-114">Requirements</span></span>  

 <span data-ttu-id="6a018-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a018-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a018-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a018-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a018-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a018-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a018-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a018-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a018-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a018-119">See also</span></span>

- [<span data-ttu-id="6a018-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6a018-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
