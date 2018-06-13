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
ms.openlocfilehash: b3536184fa7798ac8eabe851221ec692c126460b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424020"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="e7d67-102">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7d67-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="e7d67-103">İşlemler ve uygulama etki alanları hakkında bilgi yayımlama kullanılan numaralandırmalar için Özet temel arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="e7d67-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7d67-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e7d67-104">Methods</span></span>  
  
|<span data-ttu-id="e7d67-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e7d67-105">Method</span></span>|<span data-ttu-id="e7d67-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7d67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7d67-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7d67-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="e7d67-108">Bu bir kopyasını oluşturur `ICorPublishEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e7d67-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="e7d67-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7d67-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="e7d67-110">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e7d67-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="e7d67-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7d67-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="e7d67-112">İmleç numaralandırması başlangıcına taşır.</span><span class="sxs-lookup"><span data-stu-id="e7d67-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="e7d67-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7d67-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="e7d67-114">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="e7d67-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7d67-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7d67-115">Remarks</span></span>  
 <span data-ttu-id="e7d67-116">Aşağıdaki numaralandırıcılar türetin `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="e7d67-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="e7d67-117">Icorpublishappdomainenum</span><span class="sxs-lookup"><span data-stu-id="e7d67-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="e7d67-118">Icorpublishprocessenum</span><span class="sxs-lookup"><span data-stu-id="e7d67-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="e7d67-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7d67-119">Requirements</span></span>  
 <span data-ttu-id="e7d67-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d67-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d67-121">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e7d67-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e7d67-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7d67-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7d67-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d67-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d67-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7d67-124">See Also</span></span>  
 [<span data-ttu-id="e7d67-125">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="e7d67-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="e7d67-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e7d67-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
