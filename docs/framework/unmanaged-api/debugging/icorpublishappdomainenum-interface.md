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
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790670"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="401d9-102">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="401d9-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="401d9-103">Bir işlemde mevcut olan [ICorPublishAppDomain](icorpublishappdomain-interface.md) nesnelerinin bir koleksiyonunu gezme yöntemleri sağlayan [ICorPublishEnum](icorpublishenum-interface.md) arabiriminin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="401d9-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="401d9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="401d9-104">Methods</span></span>  
  
|<span data-ttu-id="401d9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="401d9-105">Method</span></span>|<span data-ttu-id="401d9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="401d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="401d9-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="401d9-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="401d9-108">Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda `ICorPublishAppDomain` örneği alır.</span><span class="sxs-lookup"><span data-stu-id="401d9-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="401d9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="401d9-109">Remarks</span></span>  
 <span data-ttu-id="401d9-110">`ICorPublishAppDomainEnum` arabirimi, [ICorPublishEnum](icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="401d9-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="401d9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="401d9-111">Requirements</span></span>  
 <span data-ttu-id="401d9-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="401d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401d9-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="401d9-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="401d9-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="401d9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="401d9-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="401d9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401d9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="401d9-116">See also</span></span>

- [<span data-ttu-id="401d9-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="401d9-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="401d9-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="401d9-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
