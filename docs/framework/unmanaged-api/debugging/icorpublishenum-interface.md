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
ms.openlocfilehash: acbc37d0f49af21c60ff6989932c5d341673512b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421182"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="07790-102">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07790-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="07790-103">, Süreçler ve uygulama etki alanları hakkında bilgi yayımlarken kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="07790-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07790-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="07790-104">Methods</span></span>  
  
|<span data-ttu-id="07790-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="07790-105">Method</span></span>|<span data-ttu-id="07790-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07790-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07790-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07790-107">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="07790-108">Bu nesnenin bir kopyasını oluşturur `ICorPublishEnum` .</span><span class="sxs-lookup"><span data-stu-id="07790-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="07790-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07790-109">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="07790-110">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="07790-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="07790-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07790-111">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="07790-112">İmlecini numaralandırmanın başlangıcına taşımalıdır.</span><span class="sxs-lookup"><span data-stu-id="07790-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="07790-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07790-113">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="07790-114">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="07790-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07790-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07790-115">Remarks</span></span>  
 <span data-ttu-id="07790-116">Aşağıdaki Numaralandırıcılar öğesinden türetilir `ICorPublishEnum` :</span><span class="sxs-lookup"><span data-stu-id="07790-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="07790-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="07790-117">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="07790-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="07790-118">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="07790-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07790-119">Requirements</span></span>  
 <span data-ttu-id="07790-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07790-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07790-121">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="07790-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="07790-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07790-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07790-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07790-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07790-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07790-124">See also</span></span>

- [<span data-ttu-id="07790-125">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="07790-125">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="07790-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="07790-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
