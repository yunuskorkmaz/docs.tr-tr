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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421091"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="c02de-102">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c02de-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="c02de-103">Bir işlem hakkında görüntülenecek bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c02de-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c02de-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c02de-104">Methods</span></span>  
  
|<span data-ttu-id="c02de-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c02de-105">Method</span></span>|<span data-ttu-id="c02de-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c02de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c02de-107">EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c02de-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="c02de-108">Bu tarafından başvurulan işlemdeki uygulama etki alanlarını içeren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneği alır `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="c02de-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="c02de-109">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c02de-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="c02de-110">Bu tarafından başvurulan işlem için yürütülebilir dosyanın tam yolunu alır `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="c02de-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="c02de-111">GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c02de-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="c02de-112">Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="c02de-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="c02de-113">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c02de-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="c02de-114">Bu tarafından başvurulan işlemin `ICorPublishProcess` yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c02de-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c02de-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c02de-115">Requirements</span></span>  
 <span data-ttu-id="c02de-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c02de-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c02de-117">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c02de-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c02de-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c02de-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c02de-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c02de-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c02de-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c02de-120">See also</span></span>

- [<span data-ttu-id="c02de-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c02de-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c02de-122">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="c02de-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
