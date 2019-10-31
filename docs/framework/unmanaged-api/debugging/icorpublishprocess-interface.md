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
ms.openlocfilehash: 04f6a088c5bbe96e3909ba600aa8ffab937abe2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140407"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="57d16-102">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57d16-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="57d16-103">Bir işlem hakkında görüntülenecek bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="57d16-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57d16-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="57d16-104">Methods</span></span>  
  
|<span data-ttu-id="57d16-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="57d16-105">Method</span></span>|<span data-ttu-id="57d16-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57d16-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57d16-107">EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57d16-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="57d16-108">Bu `ICorPublishProcess`başvurduğu işlem içindeki uygulama etki alanlarını içeren bir [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) örneği alır.</span><span class="sxs-lookup"><span data-stu-id="57d16-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="57d16-109">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57d16-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="57d16-110">Bu `ICorPublishProcess`başvurduğu işlem için yürütülebilir dosyanın tam yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="57d16-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="57d16-111">GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57d16-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="57d16-112">Bu `ICorPublishProcess`başvurduğu işlemin işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="57d16-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="57d16-113">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57d16-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="57d16-114">Bu `ICorPublishProcess` başvurduğu işlemin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="57d16-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57d16-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57d16-115">Requirements</span></span>  
 <span data-ttu-id="57d16-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57d16-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57d16-117">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="57d16-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="57d16-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="57d16-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57d16-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57d16-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d16-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57d16-120">See also</span></span>

- [<span data-ttu-id="57d16-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="57d16-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="57d16-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="57d16-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
