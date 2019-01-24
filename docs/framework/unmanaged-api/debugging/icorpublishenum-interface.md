---
title: ICorPublishEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5206b7cd07acd76237ab72268b492782ac6e49ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616725"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="b7ee1-102">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7ee1-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="b7ee1-103">Yayımlama işlemleri ve uygulama etki alanları hakkında bilgilerin kullanılan numaralandırıcılar için soyut temel arayüz görev yapar.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7ee1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b7ee1-104">Methods</span></span>  
  
|<span data-ttu-id="b7ee1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b7ee1-105">Method</span></span>|<span data-ttu-id="b7ee1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7ee1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7ee1-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7ee1-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="b7ee1-108">Bu bir kopyasını oluşturur `ICorPublishEnum` nesne.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="b7ee1-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7ee1-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="b7ee1-110">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="b7ee1-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7ee1-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="b7ee1-112">İmleç numaralandırma başlangıcına taşır.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="b7ee1-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7ee1-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="b7ee1-114">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7ee1-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7ee1-115">Remarks</span></span>  
 <span data-ttu-id="b7ee1-116">Aşağıdaki numaralandırıcılar türetilmesi `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="b7ee1-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="b7ee1-117">Icorpublishappdomainenum</span><span class="sxs-lookup"><span data-stu-id="b7ee1-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="b7ee1-118">Icorpublishprocessenum</span><span class="sxs-lookup"><span data-stu-id="b7ee1-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="b7ee1-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7ee1-119">Requirements</span></span>  
 <span data-ttu-id="b7ee1-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7ee1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ee1-121">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b7ee1-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b7ee1-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7ee1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7ee1-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ee1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ee1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7ee1-124">See also</span></span>
- [<span data-ttu-id="b7ee1-125">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="b7ee1-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="b7ee1-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b7ee1-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
