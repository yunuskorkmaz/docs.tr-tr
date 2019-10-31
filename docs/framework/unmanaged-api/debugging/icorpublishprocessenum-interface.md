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
ms.openlocfilehash: 3a7267548a957d403cfe02aa3d800a410c14b82a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103425"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="a18b2-102">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a18b2-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="a18b2-103">ICorPublishEnum [](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) arabiriminin bir [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesneleri koleksiyonunu gezme yöntemleri sağlayan bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a18b2-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a18b2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a18b2-104">Methods</span></span>  
  
|<span data-ttu-id="a18b2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a18b2-105">Method</span></span>|<span data-ttu-id="a18b2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a18b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a18b2-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a18b2-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="a18b2-108">Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda `ICorPublishProcess` örneği alır.</span><span class="sxs-lookup"><span data-stu-id="a18b2-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a18b2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a18b2-109">Remarks</span></span>  
 <span data-ttu-id="a18b2-110">`ICorPublishProcessEnum` arabirimi, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="a18b2-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="a18b2-111">[ICorPublish:: EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) yöntemi tarafından bir `ICorPublishProcessEnum` örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a18b2-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="a18b2-112">`ICorPublishProcess` nesne koleksiyonunun çapraz geçişi, `ICorPublishProcessEnum` örneği oluşturulduğu sırada verilen filtre ölçütüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a18b2-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a18b2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a18b2-113">Requirements</span></span>  
 <span data-ttu-id="a18b2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a18b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a18b2-115">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a18b2-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a18b2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a18b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a18b2-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a18b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18b2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a18b2-118">See also</span></span>

- [<span data-ttu-id="a18b2-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a18b2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a18b2-120">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="a18b2-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
