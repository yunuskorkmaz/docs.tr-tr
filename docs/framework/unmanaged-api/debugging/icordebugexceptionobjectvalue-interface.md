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
ms.openlocfilehash: 6a0c33799b2b2aaa48e3b18b7b4bb37643508bd4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678889"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="dc2a1-102">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc2a1-102">ICorDebugExceptionObjectValue Interface</span></span>

<span data-ttu-id="dc2a1-103">Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için "ICorDebugObjectValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="dc2a1-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc2a1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dc2a1-104">Methods</span></span>  
  
|<span data-ttu-id="dc2a1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dc2a1-105">Method</span></span>|<span data-ttu-id="dc2a1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc2a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc2a1-107">EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc2a1-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="dc2a1-108">Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="dc2a1-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc2a1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc2a1-109">Remarks</span></span>  

 <span data-ttu-id="dc2a1-110">' A yapılan çağrı, `QueryInterface` öğesinden türetilen yönetilen nesneler için başarılı olacaktır <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dc2a1-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc2a1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc2a1-111">Requirements</span></span>  

 <span data-ttu-id="dc2a1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc2a1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc2a1-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dc2a1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc2a1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dc2a1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc2a1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc2a1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc2a1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc2a1-116">See also</span></span>

- [<span data-ttu-id="dc2a1-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc2a1-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dc2a1-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dc2a1-118">Debugging</span></span>](index.md)
