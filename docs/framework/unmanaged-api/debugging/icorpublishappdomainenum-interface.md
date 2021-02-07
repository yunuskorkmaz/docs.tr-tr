---
description: ': ICorPublishAppDomainEnum Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4e84af576103a792308fd44f903f2ae4daa5d736
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721794"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="add74-103">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="add74-103">ICorPublishAppDomainEnum Interface</span></span>

<span data-ttu-id="add74-104">Bir işlemde mevcut olan [ICorPublishAppDomain](icorpublishappdomain-interface.md) nesnelerinin bir koleksiyonunu gezme yöntemleri sağlayan [ICorPublishEnum](icorpublishenum-interface.md) arabiriminin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="add74-104">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="add74-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="add74-105">Methods</span></span>  
  
|<span data-ttu-id="add74-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="add74-106">Method</span></span>|<span data-ttu-id="add74-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="add74-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="add74-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="add74-108">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="add74-109">`ICorPublishAppDomain`Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda örnek alır.</span><span class="sxs-lookup"><span data-stu-id="add74-109">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="add74-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="add74-110">Remarks</span></span>  

 <span data-ttu-id="add74-111">`ICorPublishAppDomainEnum`Arabirim, [ICorPublishEnum](icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="add74-111">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="add74-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="add74-112">Requirements</span></span>  

 <span data-ttu-id="add74-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="add74-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="add74-114">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="add74-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="add74-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="add74-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="add74-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add74-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add74-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="add74-117">See also</span></span>

- [<span data-ttu-id="add74-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="add74-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="add74-119">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="add74-119">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
