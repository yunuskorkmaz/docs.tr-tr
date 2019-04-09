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
ms.openlocfilehash: 5186df61eb82b29fcfa9776408498b748068e122
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173660"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="15477-102">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15477-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="15477-103">Öğesinin [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) koleksiyonunu geçirmek için yöntemler sağlar arabirimi [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="15477-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15477-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15477-104">Methods</span></span>  
  
|<span data-ttu-id="15477-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="15477-105">Method</span></span>|<span data-ttu-id="15477-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15477-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15477-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15477-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="15477-108">Belirtilen sayıda alır `ICorPublishProcess` geçerli konumunda başlayan koleksiyondan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="15477-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15477-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15477-109">Remarks</span></span>  
 <span data-ttu-id="15477-110">`ICorPublishProcessEnum` Arabirimi soyut arabirimin yöntemlerini uygulayan [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="15477-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="15477-111">Bir `ICorPublishProcessEnum` örneği tarafından oluşturulan [Icorpublish::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15477-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="15477-112">Koleksiyonu geçişi `ICorPublishProcess` nesneleri zaman verilen filtre ölçütünü temel `ICorPublishProcessEnum` örneği oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="15477-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15477-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15477-113">Requirements</span></span>  
 <span data-ttu-id="15477-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15477-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15477-115">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="15477-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="15477-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15477-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="15477-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="15477-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="15477-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15477-118">See also</span></span>

- [<span data-ttu-id="15477-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15477-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="15477-120">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="15477-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
