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
ms.openlocfilehash: 0f6d4af7c01f91dff77d6ba715ef845f523c7fb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090055"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="b18e3-102">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b18e3-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="b18e3-103">Öğesinin [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) koleksiyonunu geçirmek için yöntemler sağlar arabirimi [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) şu anda bir işlem içinde varolan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b18e3-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b18e3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b18e3-104">Methods</span></span>  
  
|<span data-ttu-id="b18e3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b18e3-105">Method</span></span>|<span data-ttu-id="b18e3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b18e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b18e3-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b18e3-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="b18e3-108">Belirtilen sayıda alır `ICorPublishAppDomain` geçerli konumunda başlayan koleksiyondan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b18e3-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b18e3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b18e3-109">Remarks</span></span>  
 <span data-ttu-id="b18e3-110">`ICorPublishAppDomainEnum` Arabirimi soyut arabirimin yöntemlerini uygulayan [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b18e3-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b18e3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b18e3-111">Requirements</span></span>  
 <span data-ttu-id="b18e3-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b18e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b18e3-113">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b18e3-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b18e3-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b18e3-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b18e3-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b18e3-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b18e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b18e3-116">See also</span></span>

- [<span data-ttu-id="b18e3-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b18e3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b18e3-118">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="b18e3-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
