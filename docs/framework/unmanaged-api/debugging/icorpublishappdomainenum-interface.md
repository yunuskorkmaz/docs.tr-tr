---
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
ms.openlocfilehash: a48e20413f466e25a9145e9dbf1ba93d90155770
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397040"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="4bf7b-102">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bf7b-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="4bf7b-103">Bir işlemde mevcut olan [ICorPublishAppDomain](icorpublishappdomain-interface.md) nesnelerinin bir koleksiyonunu gezme yöntemleri sağlayan [ICorPublishEnum](icorpublishenum-interface.md) arabiriminin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4bf7b-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4bf7b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4bf7b-104">Methods</span></span>  
  
|<span data-ttu-id="4bf7b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4bf7b-105">Method</span></span>|<span data-ttu-id="4bf7b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bf7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4bf7b-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bf7b-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="4bf7b-108">`ICorPublishAppDomain`Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda örnek alır.</span><span class="sxs-lookup"><span data-stu-id="4bf7b-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bf7b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bf7b-109">Remarks</span></span>  
 <span data-ttu-id="4bf7b-110">`ICorPublishAppDomainEnum`Arabirim, [ICorPublishEnum](icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="4bf7b-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf7b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bf7b-111">Requirements</span></span>  
 <span data-ttu-id="4bf7b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bf7b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf7b-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="4bf7b-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4bf7b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4bf7b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bf7b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bf7b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf7b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bf7b-116">See also</span></span>

- [<span data-ttu-id="4bf7b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4bf7b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4bf7b-118">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="4bf7b-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
