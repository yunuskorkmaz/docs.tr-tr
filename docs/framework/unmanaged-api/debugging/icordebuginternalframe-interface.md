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
ms.openlocfilehash: 6bc24450cdda2e3ed324256b53b2d137d1eb90e4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788493"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="d894c-102">ICorDebugInternalFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d894c-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="d894c-103">Yığında bir çalışma zamanı iç çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d894c-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="d894c-104">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="d894c-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d894c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d894c-105">Methods</span></span>  
  
|<span data-ttu-id="d894c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d894c-106">Method</span></span>|<span data-ttu-id="d894c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d894c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d894c-108">GetFrameType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d894c-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="d894c-109">Bu iç çerçevenin türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d894c-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d894c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d894c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d894c-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="d894c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d894c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d894c-112">Requirements</span></span>  
 <span data-ttu-id="d894c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d894c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d894c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d894c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d894c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d894c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d894c-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d894c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d894c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d894c-117">See also</span></span>

- [<span data-ttu-id="d894c-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d894c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
