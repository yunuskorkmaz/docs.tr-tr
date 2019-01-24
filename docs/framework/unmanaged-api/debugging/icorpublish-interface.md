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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1dea8cc54c68db333c409e3bd7b3e4211bd52ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713973"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="c07ba-102">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c07ba-102">ICorPublish Interface</span></span>
<span data-ttu-id="c07ba-103">Bu işlemde işlemleri hakkındaki bilgileri ve uygulama etki alanları hakkında bilgi yayımlamak için genel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="c07ba-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c07ba-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c07ba-104">Methods</span></span>  
  
|<span data-ttu-id="c07ba-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c07ba-105">Method</span></span>|<span data-ttu-id="c07ba-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c07ba-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c07ba-107">EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c07ba-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="c07ba-108">Alır bir [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) bu bilgisayar üzerinde çalışan yönetilen işlemler içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="c07ba-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="c07ba-109">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c07ba-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="c07ba-110">Alır bir [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) belirtilen tanımlayıcıya sahip bir işlemi temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="c07ba-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c07ba-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c07ba-111">Requirements</span></span>  
 <span data-ttu-id="c07ba-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c07ba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c07ba-113">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c07ba-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c07ba-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c07ba-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c07ba-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c07ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07ba-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c07ba-116">See also</span></span>
- [<span data-ttu-id="c07ba-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c07ba-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c07ba-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="c07ba-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
