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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790536"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="19190-102">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19190-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="19190-103">Bir işlem hakkında görüntülenecek bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="19190-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19190-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="19190-104">Methods</span></span>  
  
|<span data-ttu-id="19190-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="19190-105">Method</span></span>|<span data-ttu-id="19190-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19190-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19190-107">EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19190-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="19190-108">Bu `ICorPublishProcess`başvurduğu işlem içindeki uygulama etki alanlarını içeren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneği alır.</span><span class="sxs-lookup"><span data-stu-id="19190-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="19190-109">GetDisplayName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19190-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="19190-110">Bu `ICorPublishProcess`başvurduğu işlem için yürütülebilir dosyanın tam yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="19190-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="19190-111">GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19190-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="19190-112">Bu `ICorPublishProcess`başvurduğu işlemin işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="19190-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="19190-113">IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19190-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="19190-114">Bu `ICorPublishProcess` başvurduğu işlemin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="19190-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19190-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19190-115">Requirements</span></span>  
 <span data-ttu-id="19190-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19190-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19190-117">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="19190-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="19190-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="19190-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19190-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19190-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19190-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19190-120">See also</span></span>

- [<span data-ttu-id="19190-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="19190-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="19190-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="19190-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
