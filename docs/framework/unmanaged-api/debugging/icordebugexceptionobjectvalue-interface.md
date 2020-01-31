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
ms.openlocfilehash: fa154d0bb48f4ecd4fc6a50ce22fd13c592b7c40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782742"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="ce8ab-102">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce8ab-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="ce8ab-103">Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için "ICorDebugObjectValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce8ab-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ce8ab-104">Methods</span></span>  
  
|<span data-ttu-id="ce8ab-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ce8ab-105">Method</span></span>|<span data-ttu-id="ce8ab-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce8ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce8ab-107">EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce8ab-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="ce8ab-108">Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce8ab-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce8ab-109">Remarks</span></span>  
 <span data-ttu-id="ce8ab-110">`QueryInterface` çağrısı, <xref:System.Exception?displayProperty=nameWithType>türetilen yönetilen nesneler için başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce8ab-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce8ab-111">Requirements</span></span>  
 <span data-ttu-id="ce8ab-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce8ab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce8ab-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce8ab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce8ab-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ce8ab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce8ab-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce8ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8ab-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-116">See also</span></span>

- [<span data-ttu-id="ce8ab-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ce8ab-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ce8ab-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ce8ab-118">Debugging</span></span>](index.md)
