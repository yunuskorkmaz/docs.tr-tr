---
description: ': ICorPublishProcessEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 87d80d066995dbeca67f461e01652dd3deb3bf1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790496"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="df23a-103">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df23a-103">ICorPublishProcessEnum Interface</span></span>

<span data-ttu-id="df23a-104">ICorPublishEnum [](icorpublishenum-interface.md) arabiriminin bir [ICorPublishProcess](icorpublishprocess-interface.md) nesneleri koleksiyonunu gezme yöntemleri sağlayan bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="df23a-104">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df23a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="df23a-105">Methods</span></span>  
  
|<span data-ttu-id="df23a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="df23a-106">Method</span></span>|<span data-ttu-id="df23a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df23a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df23a-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df23a-108">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="df23a-109">`ICorPublishProcess`Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda örnek alır.</span><span class="sxs-lookup"><span data-stu-id="df23a-109">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df23a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df23a-110">Remarks</span></span>  

 <span data-ttu-id="df23a-111">`ICorPublishProcessEnum`Arabirim, [ICorPublishEnum](icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="df23a-111">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="df23a-112">`ICorPublishProcessEnum` [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) yöntemi tarafından bir örnek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="df23a-112">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="df23a-113">Nesne koleksiyonunun çapraz geçişi, `ICorPublishProcess` örnek oluşturulduğu sırada verilen filtre ölçütlerini temel alır `ICorPublishProcessEnum` .</span><span class="sxs-lookup"><span data-stu-id="df23a-113">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df23a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df23a-114">Requirements</span></span>  

 <span data-ttu-id="df23a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df23a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df23a-116">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="df23a-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="df23a-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df23a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df23a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df23a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df23a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df23a-119">See also</span></span>

- [<span data-ttu-id="df23a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df23a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="df23a-121">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="df23a-121">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
