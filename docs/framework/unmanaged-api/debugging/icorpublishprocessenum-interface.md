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
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421078"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="42cc6-102">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42cc6-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="42cc6-103">ICorPublishEnum [ICorPublishEnum](icorpublishenum-interface.md) arabiriminin bir [ICorPublishProcess](icorpublishprocess-interface.md) nesneleri koleksiyonunu gezme yöntemleri sağlayan bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="42cc6-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42cc6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="42cc6-104">Methods</span></span>  
  
|<span data-ttu-id="42cc6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="42cc6-105">Method</span></span>|<span data-ttu-id="42cc6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42cc6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42cc6-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42cc6-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="42cc6-108">`ICorPublishProcess`Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda örnek alır.</span><span class="sxs-lookup"><span data-stu-id="42cc6-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42cc6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42cc6-109">Remarks</span></span>  
 <span data-ttu-id="42cc6-110">`ICorPublishProcessEnum`Arabirim, [ICorPublishEnum](icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="42cc6-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="42cc6-111">`ICorPublishProcessEnum` [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) yöntemi tarafından bir örnek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42cc6-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="42cc6-112">Nesne koleksiyonunun çapraz geçişi, `ICorPublishProcess` örnek oluşturulduğu sırada verilen filtre ölçütlerini temel alır `ICorPublishProcessEnum` .</span><span class="sxs-lookup"><span data-stu-id="42cc6-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42cc6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42cc6-113">Requirements</span></span>  
 <span data-ttu-id="42cc6-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42cc6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42cc6-115">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="42cc6-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="42cc6-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="42cc6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42cc6-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42cc6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42cc6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42cc6-118">See also</span></span>

- [<span data-ttu-id="42cc6-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="42cc6-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="42cc6-120">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="42cc6-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
