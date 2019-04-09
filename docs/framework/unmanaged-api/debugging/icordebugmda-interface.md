---
title: ICorDebugMDA Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098675"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="2f652-102">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f652-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="2f652-103">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2f652-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f652-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2f652-104">Methods</span></span>  
  
|<span data-ttu-id="2f652-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2f652-105">Method</span></span>|<span data-ttu-id="2f652-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f652-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f652-107">GetDescription Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f652-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="2f652-108">Bu mda'nın bir açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="2f652-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="2f652-109">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f652-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="2f652-110">İle bu mda'nın ilişkili bayraklar alır.</span><span class="sxs-lookup"><span data-stu-id="2f652-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="2f652-111">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f652-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="2f652-112">Bu mda'nın adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="2f652-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="2f652-113">GetOSThreadId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f652-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="2f652-114">Bu MDA, üzerinde yürütülmekte olan işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="2f652-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="2f652-115">GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f652-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="2f652-116">İle bu mda'nın ilişkili tam XML akışı alır.</span><span class="sxs-lookup"><span data-stu-id="2f652-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f652-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f652-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f652-118">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2f652-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f652-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f652-119">Requirements</span></span>  
 <span data-ttu-id="2f652-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f652-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f652-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f652-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f652-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f652-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2f652-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2f652-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2f652-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f652-124">See also</span></span>

- [<span data-ttu-id="2f652-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2f652-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2f652-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="2f652-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
