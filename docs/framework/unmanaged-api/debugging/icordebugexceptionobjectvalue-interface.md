---
title: ICorDebugExceptionObjectValue Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6ee743a5e3e28b5d8b864f325239725ca6c0042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="e85a0-102">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e85a0-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="e85a0-103">Yönetilen özel durum nesnesinden yığın izleme bilgileri sağlamak için "ICorDebugObjectValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="e85a0-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e85a0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e85a0-104">Methods</span></span>  
  
|<span data-ttu-id="e85a0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e85a0-105">Method</span></span>|<span data-ttu-id="e85a0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e85a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e85a0-107">EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e85a0-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="e85a0-108">Bir özel durum nesnesi katıştırılmış çağrı yığını için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e85a0-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e85a0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e85a0-109">Remarks</span></span>  
 <span data-ttu-id="e85a0-110">Çağrı `QueryInterface` öğesinden türetilen yönetilen nesneler için başarılı olur <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e85a0-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85a0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e85a0-111">Requirements</span></span>  
 <span data-ttu-id="e85a0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e85a0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85a0-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e85a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e85a0-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e85a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e85a0-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e85a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85a0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e85a0-116">See Also</span></span>  
 [<span data-ttu-id="e85a0-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e85a0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e85a0-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e85a0-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
