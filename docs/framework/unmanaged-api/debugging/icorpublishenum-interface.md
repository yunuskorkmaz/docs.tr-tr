---
title: ICorPublishEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum
helpviewer_keywords: ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7034945824e439b42134f8ea3c13bfaf73dbb649
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="7ef4b-102">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ef4b-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="7ef4b-103">İşlemler ve uygulama etki alanları hakkında bilgi yayımlama kullanılan numaralandırmalar için Özet temel arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="7ef4b-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ef4b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ef4b-104">Methods</span></span>  
  
|<span data-ttu-id="7ef4b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ef4b-105">Method</span></span>|<span data-ttu-id="7ef4b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ef4b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ef4b-107">Clone yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ef4b-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="7ef4b-108">Bu bir kopyasını oluşturur `ICorPublishEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7ef4b-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="7ef4b-109">GetCount yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ef4b-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="7ef4b-110">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7ef4b-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="7ef4b-111">Reset yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ef4b-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="7ef4b-112">İmleç numaralandırması başlangıcına taşır.</span><span class="sxs-lookup"><span data-stu-id="7ef4b-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="7ef4b-113">Skip yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ef4b-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="7ef4b-114">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="7ef4b-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ef4b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ef4b-115">Remarks</span></span>  
 <span data-ttu-id="7ef4b-116">Aşağıdaki numaralandırıcılar türetin `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="7ef4b-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="7ef4b-117">Icorpublishappdomainenum</span><span class="sxs-lookup"><span data-stu-id="7ef4b-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="7ef4b-118">Icorpublishprocessenum</span><span class="sxs-lookup"><span data-stu-id="7ef4b-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="7ef4b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ef4b-119">Requirements</span></span>  
 <span data-ttu-id="7ef4b-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ef4b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ef4b-121">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7ef4b-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7ef4b-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ef4b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ef4b-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ef4b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef4b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ef4b-124">See Also</span></span>  
 [<span data-ttu-id="7ef4b-125">Corpubpublish ortak sınıfı</span><span class="sxs-lookup"><span data-stu-id="7ef4b-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="7ef4b-126">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ef4b-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
