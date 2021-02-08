---
description: ': ICorPublishProcess arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8dbc619d33c2c9b625dde852948dff00b5be926e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800883"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="33cbe-103">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33cbe-103">ICorPublishProcess Interface</span></span>

<span data-ttu-id="33cbe-104">Bir işlem hakkında görüntülenecek bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="33cbe-104">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33cbe-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="33cbe-105">Methods</span></span>  
  
|<span data-ttu-id="33cbe-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="33cbe-106">Method</span></span>|<span data-ttu-id="33cbe-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33cbe-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33cbe-108">EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33cbe-108">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="33cbe-109">Bu tarafından başvurulan işlemdeki uygulama etki alanlarını içeren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneği alır `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="33cbe-109">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="33cbe-110">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33cbe-110">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="33cbe-111">Bu tarafından başvurulan işlem için yürütülebilir dosyanın tam yolunu alır `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="33cbe-111">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="33cbe-112">GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33cbe-112">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="33cbe-113">Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="33cbe-113">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="33cbe-114">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33cbe-114">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="33cbe-115">Bu tarafından başvurulan işlemin `ICorPublishProcess` yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="33cbe-115">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33cbe-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33cbe-116">Requirements</span></span>  

 <span data-ttu-id="33cbe-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33cbe-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33cbe-118">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="33cbe-118">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="33cbe-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="33cbe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33cbe-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33cbe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33cbe-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33cbe-121">See also</span></span>

- [<span data-ttu-id="33cbe-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="33cbe-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="33cbe-123">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="33cbe-123">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
