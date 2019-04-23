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
ms.openlocfilehash: 7581d68f5c2b575403ddc84d06147f012e7ab39e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076347"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="7d7fc-102">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-102">ICorPublish Interface</span></span>
<span data-ttu-id="7d7fc-103">Bu işlemde işlemleri hakkındaki bilgileri ve uygulama etki alanları hakkında bilgi yayımlamak için genel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d7fc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7d7fc-104">Methods</span></span>  
  
|<span data-ttu-id="7d7fc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7d7fc-105">Method</span></span>|<span data-ttu-id="7d7fc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d7fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d7fc-107">EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="7d7fc-108">Alır bir [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) bu bilgisayar üzerinde çalışan yönetilen işlemler içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="7d7fc-109">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="7d7fc-110">Alır bir [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) belirtilen tanımlayıcıya sahip bir işlemi temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d7fc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d7fc-111">Requirements</span></span>  
 <span data-ttu-id="7d7fc-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d7fc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d7fc-113">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7d7fc-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7d7fc-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d7fc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d7fc-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d7fc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7fc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-116">See also</span></span>

- [<span data-ttu-id="7d7fc-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d7fc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7d7fc-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="7d7fc-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
