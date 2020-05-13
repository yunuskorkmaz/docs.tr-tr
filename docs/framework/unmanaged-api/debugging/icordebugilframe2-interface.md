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
ms.openlocfilehash: 2e0f284625e99215900c6aaab94e4eae611787ed
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212106"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="ee7f4-102">ICorDebugILFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee7f4-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="ee7f4-103">ICorDebugILFrame arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="ee7f4-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee7f4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ee7f4-104">Methods</span></span>  
  
|<span data-ttu-id="ee7f4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ee7f4-105">Method</span></span>|<span data-ttu-id="ee7f4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee7f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee7f4-107">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee7f4-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="ee7f4-108">Bu çerçevedeki parametreleri içeren bir ICorDebugTypeEnum nesnesi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="ee7f4-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="ee7f4-109">RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee7f4-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="ee7f4-110">Yeni MSIL sapmasını belirterek düzenlenmiş bir işlevi yeniden eşler.</span><span class="sxs-lookup"><span data-stu-id="ee7f4-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee7f4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee7f4-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee7f4-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ee7f4-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee7f4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee7f4-113">Requirements</span></span>  
 <span data-ttu-id="ee7f4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee7f4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee7f4-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee7f4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee7f4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ee7f4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee7f4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee7f4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee7f4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee7f4-118">See also</span></span>

- [<span data-ttu-id="ee7f4-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ee7f4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
