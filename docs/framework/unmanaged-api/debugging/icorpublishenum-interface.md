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
ms.openlocfilehash: 1eac0b9fe252e476f8ff781f2181a203886d3beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993544"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="4e759-102">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e759-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="4e759-103">Yayımlama işlemleri ve uygulama etki alanları hakkında bilgilerin kullanılan numaralandırıcılar için soyut temel arayüz görev yapar.</span><span class="sxs-lookup"><span data-stu-id="4e759-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e759-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4e759-104">Methods</span></span>  
  
|<span data-ttu-id="4e759-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4e759-105">Method</span></span>|<span data-ttu-id="4e759-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e759-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e759-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e759-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="4e759-108">Bu bir kopyasını oluşturur `ICorPublishEnum` nesne.</span><span class="sxs-lookup"><span data-stu-id="4e759-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="4e759-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e759-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="4e759-110">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4e759-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="4e759-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e759-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="4e759-112">İmleç numaralandırma başlangıcına taşır.</span><span class="sxs-lookup"><span data-stu-id="4e759-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="4e759-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e759-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="4e759-114">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="4e759-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e759-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e759-115">Remarks</span></span>  
 <span data-ttu-id="4e759-116">Aşağıdaki numaralandırıcılar türetilmesi `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="4e759-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="4e759-117">Icorpublishappdomainenum</span><span class="sxs-lookup"><span data-stu-id="4e759-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="4e759-118">Icorpublishprocessenum</span><span class="sxs-lookup"><span data-stu-id="4e759-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="4e759-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e759-119">Requirements</span></span>  
 <span data-ttu-id="4e759-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e759-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e759-121">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="4e759-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4e759-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e759-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e759-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e759-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e759-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e759-124">See also</span></span>

- [<span data-ttu-id="4e759-125">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="4e759-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="4e759-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e759-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
