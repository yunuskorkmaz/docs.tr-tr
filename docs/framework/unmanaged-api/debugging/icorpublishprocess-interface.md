---
title: ICorPublishProcess Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765be4e0ae7657d169ea561bc6a36bcf8cc11153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="d2e55-102">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2e55-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="d2e55-103">Görüntülenecek bir işlemle ilgili bilgileri erişim yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2e55-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2e55-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d2e55-104">Methods</span></span>  
  
|<span data-ttu-id="d2e55-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2e55-105">Method</span></span>|<span data-ttu-id="d2e55-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2e55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2e55-107">EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2e55-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="d2e55-108">Alır bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) bu tarafından başvurulan işlemindeki uygulama etki alanları içeren örneği `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="d2e55-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="d2e55-109">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2e55-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="d2e55-110">Bu tarafından başvurulan işlem yürütülebilir dosyasının tam yolunu alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="d2e55-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="d2e55-111">GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2e55-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="d2e55-112">Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="d2e55-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="d2e55-113">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2e55-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="d2e55-114">İşlemin bu tarafından başvurulan olup olmadığını belirten bir değer alır `ICorPublishProcess` yönetilen kod çalıştırması bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2e55-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2e55-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2e55-115">Requirements</span></span>  
 <span data-ttu-id="d2e55-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2e55-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2e55-117">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d2e55-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d2e55-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2e55-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2e55-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2e55-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e55-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2e55-120">See Also</span></span>  
 [<span data-ttu-id="d2e55-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d2e55-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d2e55-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="d2e55-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
