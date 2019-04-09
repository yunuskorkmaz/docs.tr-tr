---
title: ICorDebugExceptionObjectValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5328442ceaee05b3f81466b785f04a361d456a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098487"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="b8e15-102">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8e15-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="b8e15-103">Yönetilen özel durum nesnesinden yığın izleme bilgisi sağlamak üzere "ICorDebugObjectValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8e15-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8e15-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b8e15-104">Methods</span></span>  
  
|<span data-ttu-id="b8e15-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b8e15-105">Method</span></span>|<span data-ttu-id="b8e15-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8e15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8e15-107">EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8e15-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="b8e15-108">Bir özel durum nesnesine katıştırılmış çağrı yığını için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b8e15-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e15-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8e15-109">Remarks</span></span>  
 <span data-ttu-id="b8e15-110">Çağrı `QueryInterface` türetilen bir yönetilen nesneler için başarılı olur <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b8e15-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e15-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8e15-111">Requirements</span></span>  
 <span data-ttu-id="b8e15-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8e15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e15-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8e15-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8e15-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8e15-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b8e15-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b8e15-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8e15-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8e15-116">See also</span></span>

- [<span data-ttu-id="b8e15-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b8e15-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b8e15-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b8e15-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
