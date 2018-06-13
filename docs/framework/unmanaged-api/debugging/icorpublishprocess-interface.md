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
ms.openlocfilehash: 19f76a163fae4a1390a2e0fcb85299f8ce78180c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435896"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="6f510-102">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f510-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="6f510-103">Görüntülenecek bir işlemle ilgili bilgileri erişim yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f510-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f510-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6f510-104">Methods</span></span>  
  
|<span data-ttu-id="6f510-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6f510-105">Method</span></span>|<span data-ttu-id="6f510-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f510-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f510-107">EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f510-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="6f510-108">Alır bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) bu tarafından başvurulan işlemindeki uygulama etki alanları içeren örneği `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="6f510-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="6f510-109">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f510-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="6f510-110">Bu tarafından başvurulan işlem yürütülebilir dosyasının tam yolunu alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="6f510-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="6f510-111">GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f510-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="6f510-112">Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="6f510-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="6f510-113">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f510-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="6f510-114">İşlemin bu tarafından başvurulan olup olmadığını belirten bir değer alır `ICorPublishProcess` yönetilen kod çalıştırması bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f510-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f510-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f510-115">Requirements</span></span>  
 <span data-ttu-id="6f510-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f510-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f510-117">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6f510-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6f510-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f510-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f510-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f510-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f510-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f510-120">See Also</span></span>  
 [<span data-ttu-id="6f510-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6f510-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6f510-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="6f510-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
