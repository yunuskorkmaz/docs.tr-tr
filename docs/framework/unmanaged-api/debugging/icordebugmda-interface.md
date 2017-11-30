---
title: ICorDebugMDA Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA
helpviewer_keywords: ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00a003ee060de59fe0eb8ce8f740a620d77a7c85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="68736-102">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68736-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="68736-103">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68736-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68736-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="68736-104">Methods</span></span>  
  
|<span data-ttu-id="68736-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="68736-105">Method</span></span>|<span data-ttu-id="68736-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68736-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68736-107">GetDescription yöntemi</span><span class="sxs-lookup"><span data-stu-id="68736-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="68736-108">Bu MDA açıklamasını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="68736-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="68736-109">GetFlags yöntemi</span><span class="sxs-lookup"><span data-stu-id="68736-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="68736-110">Bu MDA ile ilişkili bayraklar alır.</span><span class="sxs-lookup"><span data-stu-id="68736-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="68736-111">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="68736-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="68736-112">Bu MDA adını içeren bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="68736-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="68736-113">Getosthreadıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="68736-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="68736-114">Bu MDA dosyanızın çalıştığı işletim sistemi iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="68736-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="68736-115">GetXML yöntemi</span><span class="sxs-lookup"><span data-stu-id="68736-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="68736-116">Bu MDA ile ilişkili tam XML akışı alır.</span><span class="sxs-lookup"><span data-stu-id="68736-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68736-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68736-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68736-118">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="68736-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68736-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68736-119">Requirements</span></span>  
 <span data-ttu-id="68736-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68736-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68736-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68736-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68736-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68736-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68736-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68736-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68736-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68736-124">See Also</span></span>  
 [<span data-ttu-id="68736-125">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="68736-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="68736-126">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="68736-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
