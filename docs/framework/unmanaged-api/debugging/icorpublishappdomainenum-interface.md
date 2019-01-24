---
title: ICorPublishAppDomainEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2be3406cd4330fb477e8a1c89945be1e9f777bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706616"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="f2f79-102">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2f79-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="f2f79-103">Öğesinin [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) koleksiyonunu geçirmek için yöntemler sağlar arabirimi [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) şu anda bir işlem içinde varolan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f2f79-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2f79-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f2f79-104">Methods</span></span>  
  
|<span data-ttu-id="f2f79-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f2f79-105">Method</span></span>|<span data-ttu-id="f2f79-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2f79-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2f79-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="f2f79-108">Belirtilen sayıda alır `ICorPublishAppDomain` geçerli konumunda başlayan koleksiyondan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f2f79-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2f79-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2f79-109">Remarks</span></span>  
 <span data-ttu-id="f2f79-110">`ICorPublishAppDomainEnum` Arabirimi soyut arabirimin yöntemlerini uygulayan [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f2f79-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f79-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2f79-111">Requirements</span></span>  
 <span data-ttu-id="f2f79-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2f79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f79-113">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f2f79-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f2f79-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2f79-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f79-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f79-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f79-116">See also</span></span>
- [<span data-ttu-id="f2f79-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f2f79-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f2f79-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="f2f79-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
