---
title: ICorPublishProcess Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182968"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="5f0aa-102">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f0aa-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="5f0aa-103">Görüntülenecek işlemle ilgili bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f0aa-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f0aa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5f0aa-104">Methods</span></span>  
  
|<span data-ttu-id="5f0aa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5f0aa-105">Method</span></span>|<span data-ttu-id="5f0aa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f0aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f0aa-107">EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f0aa-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="5f0aa-108">Alır bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) bu tarafından başvurulan işlemde uygulama etki alanları içeren örneğini `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5f0aa-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5f0aa-109">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f0aa-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="5f0aa-110">Bu tarafından başvurulan işlemi için yürütülebilir dosyanın tam yolunu alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5f0aa-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5f0aa-111">GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f0aa-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="5f0aa-112">Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5f0aa-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5f0aa-113">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f0aa-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="5f0aa-114">İşlem bu tarafından başvurulan olup olmadığını gösteren bir değer alır `ICorPublishProcess` yönetilen kod çalıştırması bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="5f0aa-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f0aa-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f0aa-115">Requirements</span></span>  
 <span data-ttu-id="5f0aa-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f0aa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f0aa-117">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5f0aa-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5f0aa-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f0aa-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5f0aa-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5f0aa-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5f0aa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f0aa-120">See also</span></span>

- [<span data-ttu-id="5f0aa-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5f0aa-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5f0aa-122">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="5f0aa-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
