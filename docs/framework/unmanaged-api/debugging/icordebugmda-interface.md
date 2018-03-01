---
title: ICorDebugMDA Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c53e03acddc5d732a684cf825bce49a65bb4c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="304cc-102">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="304cc-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="304cc-103">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="304cc-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="304cc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="304cc-104">Methods</span></span>  
  
|<span data-ttu-id="304cc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="304cc-105">Method</span></span>|<span data-ttu-id="304cc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="304cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="304cc-107">GetDescription Yöntemi</span><span class="sxs-lookup"><span data-stu-id="304cc-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="304cc-108">Bu MDA açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="304cc-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="304cc-109">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="304cc-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="304cc-110">Bu MDA ile ilişkili bayraklar alır.</span><span class="sxs-lookup"><span data-stu-id="304cc-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="304cc-111">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="304cc-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="304cc-112">Bu MDA adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="304cc-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="304cc-113">GetOSThreadId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="304cc-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="304cc-114">Bu MDA dosyanızın çalıştığı işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="304cc-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="304cc-115">GetXML Yöntemi</span><span class="sxs-lookup"><span data-stu-id="304cc-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="304cc-116">Bu MDA ile ilişkili tam XML akışı alır.</span><span class="sxs-lookup"><span data-stu-id="304cc-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="304cc-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="304cc-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="304cc-118">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="304cc-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="304cc-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="304cc-119">Requirements</span></span>  
 <span data-ttu-id="304cc-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="304cc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="304cc-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="304cc-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="304cc-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="304cc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="304cc-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="304cc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="304cc-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="304cc-124">See Also</span></span>  
 [<span data-ttu-id="304cc-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="304cc-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="304cc-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="304cc-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
