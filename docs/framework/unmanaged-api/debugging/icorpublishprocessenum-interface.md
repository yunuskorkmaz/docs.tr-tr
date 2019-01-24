---
title: ICorPublishProcessEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b72f2581b9670dbc110f2ab33cb861128bd78dca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525852"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="aaa63-102">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaa63-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="aaa63-103">Öğesinin [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) koleksiyonunu geçirmek için yöntemler sağlar arabirimi [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="aaa63-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aaa63-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aaa63-104">Methods</span></span>  
  
|<span data-ttu-id="aaa63-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aaa63-105">Method</span></span>|<span data-ttu-id="aaa63-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaa63-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aaa63-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaa63-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="aaa63-108">Belirtilen sayıda alır `ICorPublishProcess` geçerli konumunda başlayan koleksiyondan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="aaa63-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa63-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aaa63-109">Remarks</span></span>  
 <span data-ttu-id="aaa63-110">`ICorPublishProcessEnum` Arabirimi soyut arabirimin yöntemlerini uygulayan [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="aaa63-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="aaa63-111">Bir `ICorPublishProcessEnum` örneği tarafından oluşturulan [Icorpublish::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaa63-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="aaa63-112">Koleksiyonu geçişi `ICorPublishProcess` nesneleri zaman verilen filtre ölçütünü temel `ICorPublishProcessEnum` örneği oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="aaa63-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa63-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aaa63-113">Requirements</span></span>  
 <span data-ttu-id="aaa63-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa63-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa63-115">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="aaa63-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="aaa63-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaa63-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaa63-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa63-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa63-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaa63-118">See also</span></span>
- [<span data-ttu-id="aaa63-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aaa63-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aaa63-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="aaa63-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
