---
title: ICorPublish Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8eb3bd2da9529a681f7f3a09ef7eb78c776cc302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublish-interface"></a><span data-ttu-id="fe80b-102">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe80b-102">ICorPublish Interface</span></span>
<span data-ttu-id="fe80b-103">Bu işlemleri işlemler hakkındaki bilgileri ve uygulama etki alanları hakkında bilgi yayımlamak için genel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="fe80b-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe80b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fe80b-104">Methods</span></span>  
  
|<span data-ttu-id="fe80b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe80b-105">Method</span></span>|<span data-ttu-id="fe80b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe80b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe80b-107">EnumProcesses yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe80b-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="fe80b-108">Alır bir [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) bu bilgisayarda çalışan yönetilen işlemler içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="fe80b-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="fe80b-109">GetProcess yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe80b-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="fe80b-110">Alır bir [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) belirtilen tanımlayıcı ile işlem temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="fe80b-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe80b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe80b-111">Requirements</span></span>  
 <span data-ttu-id="fe80b-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe80b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe80b-113">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="fe80b-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fe80b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe80b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe80b-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe80b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe80b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe80b-116">See Also</span></span>  
 [<span data-ttu-id="fe80b-117">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe80b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fe80b-118">Corpubpublish ortak sınıfı</span><span class="sxs-lookup"><span data-stu-id="fe80b-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
