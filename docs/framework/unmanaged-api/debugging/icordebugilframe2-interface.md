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
ms.openlocfilehash: c5fa0a67309e23c02393b70d849af3884dfd0adf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788536"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="ae3af-102">ICorDebugILFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae3af-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="ae3af-103">ICorDebugILFrame arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="ae3af-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae3af-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ae3af-104">Methods</span></span>  
  
|<span data-ttu-id="ae3af-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ae3af-105">Method</span></span>|<span data-ttu-id="ae3af-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae3af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae3af-107">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae3af-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="ae3af-108">Bu çerçevede <xref:System.Type> parametrelerini içeren bir ICorDebugTypeEnum nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="ae3af-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="ae3af-109">RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae3af-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="ae3af-110">Yeni MSIL sapmasını belirterek düzenlenmiş bir işlevi yeniden eşler.</span><span class="sxs-lookup"><span data-stu-id="ae3af-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae3af-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae3af-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae3af-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ae3af-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae3af-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae3af-113">Requirements</span></span>  
 <span data-ttu-id="ae3af-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae3af-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae3af-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae3af-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae3af-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae3af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae3af-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae3af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae3af-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae3af-118">See also</span></span>

- [<span data-ttu-id="ae3af-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae3af-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
