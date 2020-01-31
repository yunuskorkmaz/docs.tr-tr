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
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790724"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="162d6-102">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="162d6-102">ICorPublish Interface</span></span>
<span data-ttu-id="162d6-103">, Bu süreçlerdeki uygulama etki alanlarıyla ilgili süreçler ve bilgiler hakkında bilgi yayımlamak için genel arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="162d6-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="162d6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="162d6-104">Methods</span></span>  
  
|<span data-ttu-id="162d6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="162d6-105">Method</span></span>|<span data-ttu-id="162d6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="162d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="162d6-107">EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="162d6-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="162d6-108">Bu bilgisayarda çalışan yönetilen işlemlerin bulunduğu bir [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="162d6-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="162d6-109">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="162d6-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="162d6-110">Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](icorpublishprocess-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="162d6-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="162d6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="162d6-111">Requirements</span></span>  
 <span data-ttu-id="162d6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="162d6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="162d6-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="162d6-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="162d6-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="162d6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="162d6-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="162d6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162d6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="162d6-116">See also</span></span>

- [<span data-ttu-id="162d6-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="162d6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="162d6-118">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="162d6-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
