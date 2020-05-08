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
ms.openlocfilehash: 8e4f745440936a39e22faf60d10a05a0bb110606
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975959"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="52dec-102">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52dec-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="52dec-103">Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için "ICorDebugObjectValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="52dec-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52dec-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="52dec-104">Methods</span></span>  
  
|<span data-ttu-id="52dec-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="52dec-105">Method</span></span>|<span data-ttu-id="52dec-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52dec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52dec-107">EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52dec-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="52dec-108">Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="52dec-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52dec-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52dec-109">Remarks</span></span>  
 <span data-ttu-id="52dec-110">' A yapılan `QueryInterface` çağrı, öğesinden <xref:System.Exception?displayProperty=nameWithType>türetilen yönetilen nesneler için başarılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="52dec-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52dec-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52dec-111">Requirements</span></span>  
 <span data-ttu-id="52dec-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52dec-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52dec-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="52dec-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52dec-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="52dec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52dec-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52dec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dec-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52dec-116">See also</span></span>

- [<span data-ttu-id="52dec-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="52dec-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="52dec-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="52dec-118">Debugging</span></span>](index.md)
