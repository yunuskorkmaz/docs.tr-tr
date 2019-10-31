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
ms.openlocfilehash: cbe2aa48a8b67b0b6e88f7b5267bc70848fe3cec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140319"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="8fb97-102">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fb97-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="8fb97-103">Bir işlemde mevcut olan [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) nesnelerinin bir koleksiyonunu gezme yöntemleri sağlayan [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) arabiriminin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8fb97-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8fb97-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8fb97-104">Methods</span></span>  
  
|<span data-ttu-id="8fb97-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8fb97-105">Method</span></span>|<span data-ttu-id="8fb97-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fb97-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8fb97-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fb97-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="8fb97-108">Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda `ICorPublishAppDomain` örneği alır.</span><span class="sxs-lookup"><span data-stu-id="8fb97-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fb97-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fb97-109">Remarks</span></span>  
 <span data-ttu-id="8fb97-110">`ICorPublishAppDomainEnum` arabirimi, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="8fb97-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fb97-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fb97-111">Requirements</span></span>  
 <span data-ttu-id="8fb97-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fb97-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fb97-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="8fb97-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8fb97-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8fb97-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fb97-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fb97-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb97-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb97-116">See also</span></span>

- [<span data-ttu-id="8fb97-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8fb97-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8fb97-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="8fb97-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
