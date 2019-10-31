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
ms.openlocfilehash: 7d083655326333f18ee98f8e84fff2ed182dde6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103459"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="c50f9-102">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c50f9-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="c50f9-103">, Süreçler ve uygulama etki alanları hakkında bilgi yayımlarken kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="c50f9-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c50f9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c50f9-104">Methods</span></span>  
  
|<span data-ttu-id="c50f9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c50f9-105">Method</span></span>|<span data-ttu-id="c50f9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c50f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c50f9-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c50f9-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="c50f9-108">Bu `ICorPublishEnum` nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c50f9-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="c50f9-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c50f9-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="c50f9-110">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c50f9-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="c50f9-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c50f9-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="c50f9-112">İmlecini numaralandırmanın başlangıcına taşımalıdır.</span><span class="sxs-lookup"><span data-stu-id="c50f9-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="c50f9-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c50f9-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="c50f9-114">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="c50f9-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c50f9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c50f9-115">Remarks</span></span>  
 <span data-ttu-id="c50f9-116">Aşağıdaki Numaralandırıcılar `ICorPublishEnum`türetilir:</span><span class="sxs-lookup"><span data-stu-id="c50f9-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="c50f9-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="c50f9-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="c50f9-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="c50f9-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="c50f9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c50f9-119">Requirements</span></span>  
 <span data-ttu-id="c50f9-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c50f9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c50f9-121">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c50f9-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c50f9-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c50f9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c50f9-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c50f9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c50f9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c50f9-124">See also</span></span>

- [<span data-ttu-id="c50f9-125">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="c50f9-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="c50f9-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c50f9-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
