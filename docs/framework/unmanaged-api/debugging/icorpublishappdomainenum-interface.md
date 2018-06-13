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
ms.openlocfilehash: 610f62274aea88c1d5f9bbe1456685aa1d3bca68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423747"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="c468e-102">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c468e-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="c468e-103">Öğesinin bir alt [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) koleksiyonu geçiş için yöntemler sağlar arabirimi [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) şu anda bir işlem içinde mevcut nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c468e-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c468e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c468e-104">Methods</span></span>  
  
|<span data-ttu-id="c468e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c468e-105">Method</span></span>|<span data-ttu-id="c468e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c468e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c468e-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c468e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="c468e-108">Belirtilen sayıda alır `ICorPublishAppDomain` geçerli konumdan başlayarak koleksiyondan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c468e-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c468e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c468e-109">Remarks</span></span>  
 <span data-ttu-id="c468e-110">`ICorPublishAppDomainEnum` Arabirimini uygulayan soyut arabiriminin yöntemlerini [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c468e-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c468e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c468e-111">Requirements</span></span>  
 <span data-ttu-id="c468e-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c468e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c468e-113">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c468e-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c468e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c468e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c468e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c468e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c468e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c468e-116">See Also</span></span>  
 [<span data-ttu-id="c468e-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c468e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c468e-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="c468e-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
