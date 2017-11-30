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
ms.openlocfilehash: cb62da277ff13bea33969bb9c728cac5d5a15554
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="e5aee-102">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5aee-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="e5aee-103">Görüntülenecek bir işlemle ilgili bilgileri erişim yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5aee-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5aee-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5aee-104">Methods</span></span>  
  
|<span data-ttu-id="e5aee-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e5aee-105">Method</span></span>|<span data-ttu-id="e5aee-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5aee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5aee-107">EnumAppDomains yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5aee-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="e5aee-108">Alır bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) bu tarafından başvurulan işlemindeki uygulama etki alanları içeren örneği `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="e5aee-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="e5aee-109">GetDisplayName yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5aee-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="e5aee-110">Bu tarafından başvurulan işlem yürütülebilir dosyasının tam yolunu alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="e5aee-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="e5aee-111">Getprocessıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5aee-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="e5aee-112">Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="e5aee-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="e5aee-113">Ismanaged yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5aee-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="e5aee-114">İşlemin bu tarafından başvurulan olup olmadığını belirten bir değer alır `ICorPublishProcess` yönetilen kod çalıştırması bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5aee-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5aee-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5aee-115">Requirements</span></span>  
 <span data-ttu-id="e5aee-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5aee-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5aee-117">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e5aee-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e5aee-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5aee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5aee-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5aee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5aee-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5aee-120">See Also</span></span>  
 [<span data-ttu-id="e5aee-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e5aee-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e5aee-122">Corpubpublish ortak sınıfı</span><span class="sxs-lookup"><span data-stu-id="e5aee-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
