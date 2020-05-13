---
title: ICorDebugInternalFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
ms.openlocfilehash: 332bc99795c0a4c896b60c61941a5a24b3f4accc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209963"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="697c6-102">ICorDebugInternalFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="697c6-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="697c6-103">Yığında bir çalışma zamanı iç çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="697c6-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="697c6-104">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="697c6-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="697c6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="697c6-105">Methods</span></span>  
  
|<span data-ttu-id="697c6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="697c6-106">Method</span></span>|<span data-ttu-id="697c6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="697c6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="697c6-108">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="697c6-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="697c6-109">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="697c6-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="697c6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="697c6-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="697c6-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="697c6-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="697c6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="697c6-112">Requirements</span></span>  
 <span data-ttu-id="697c6-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="697c6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="697c6-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="697c6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="697c6-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="697c6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="697c6-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="697c6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="697c6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="697c6-117">See also</span></span>

- [<span data-ttu-id="697c6-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="697c6-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
