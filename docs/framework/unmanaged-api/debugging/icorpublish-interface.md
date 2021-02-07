---
description: ': ICorPublish arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0cec1d3407246989c6b916ca0760e6f556566ce6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721833"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="2ee1d-103">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ee1d-103">ICorPublish Interface</span></span>

<span data-ttu-id="2ee1d-104">, Bu süreçlerdeki uygulama etki alanlarıyla ilgili süreçler ve bilgiler hakkında bilgi yayımlamak için genel arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="2ee1d-104">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ee1d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2ee1d-105">Methods</span></span>  
  
|<span data-ttu-id="2ee1d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2ee1d-106">Method</span></span>|<span data-ttu-id="2ee1d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ee1d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ee1d-108">EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ee1d-108">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="2ee1d-109">Bu bilgisayarda çalışan yönetilen işlemlerin bulunduğu bir [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="2ee1d-109">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="2ee1d-110">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ee1d-110">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="2ee1d-111">Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](icorpublishprocess-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="2ee1d-111">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ee1d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ee1d-112">Requirements</span></span>  

 <span data-ttu-id="2ee1d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ee1d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ee1d-114">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="2ee1d-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2ee1d-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2ee1d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ee1d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ee1d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee1d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ee1d-117">See also</span></span>

- [<span data-ttu-id="2ee1d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2ee1d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2ee1d-119">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="2ee1d-119">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
