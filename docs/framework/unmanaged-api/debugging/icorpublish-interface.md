---
title: ICorPublish Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121762"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="5e4d9-102">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e4d9-102">ICorPublish Interface</span></span>
<span data-ttu-id="5e4d9-103">, Bu süreçlerdeki uygulama etki alanlarıyla ilgili süreçler ve bilgiler hakkında bilgi yayımlamak için genel arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="5e4d9-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e4d9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5e4d9-104">Methods</span></span>  
  
|<span data-ttu-id="5e4d9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5e4d9-105">Method</span></span>|<span data-ttu-id="5e4d9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e4d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e4d9-107">EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e4d9-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="5e4d9-108">Bu bilgisayarda çalışan yönetilen işlemlerin bulunduğu bir [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="5e4d9-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="5e4d9-109">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e4d9-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="5e4d9-110">Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="5e4d9-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e4d9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e4d9-111">Requirements</span></span>  
 <span data-ttu-id="5e4d9-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e4d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e4d9-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="5e4d9-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5e4d9-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e4d9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e4d9-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e4d9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4d9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e4d9-116">See also</span></span>

- [<span data-ttu-id="5e4d9-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5e4d9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5e4d9-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="5e4d9-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
