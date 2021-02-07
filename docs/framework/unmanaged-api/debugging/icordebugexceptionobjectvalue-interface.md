---
description: ': ICorDebugExceptionObjectValue Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 67672f9921bab31019a42b742480176e6d0bf3d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693206"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="98021-103">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98021-103">ICorDebugExceptionObjectValue Interface</span></span>

<span data-ttu-id="98021-104">Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için "ICorDebugObjectValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="98021-104">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98021-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="98021-105">Methods</span></span>  
  
|<span data-ttu-id="98021-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="98021-106">Method</span></span>|<span data-ttu-id="98021-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98021-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98021-108">EnumerateExceptionCallStack Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98021-108">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="98021-109">Özel durum nesnesine katıştırılmış çağrı yığınına bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="98021-109">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98021-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98021-110">Remarks</span></span>  

 <span data-ttu-id="98021-111">' A yapılan çağrı, `QueryInterface` öğesinden türetilen yönetilen nesneler için başarılı olacaktır <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="98021-111">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98021-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98021-112">Requirements</span></span>  

 <span data-ttu-id="98021-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98021-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98021-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98021-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98021-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98021-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98021-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98021-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98021-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98021-117">See also</span></span>

- [<span data-ttu-id="98021-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98021-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="98021-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="98021-119">Debugging</span></span>](index.md)
