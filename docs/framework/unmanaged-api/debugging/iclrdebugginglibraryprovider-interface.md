---
title: ICLRDebuggingLibraryProvider Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c62079a87c09bcbe09167a137fd39530652ae3e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106346"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="ca5c9-102">ICLRDebuggingLibraryProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca5c9-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="ca5c9-103">İçerir [ProvideLibrary yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) kitaplık sağlayıcı ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarına ve yüklenecek isteğe bağlı olmasını sağlayan bir geri arama arabirimini alan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca5c9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ca5c9-104">Methods</span></span>  
  
|<span data-ttu-id="ca5c9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ca5c9-105">Method</span></span>|<span data-ttu-id="ca5c9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca5c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca5c9-107">ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca5c9-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="ca5c9-108">Hata ayıklama kitaplığı yüklemek için kullanılabilecek bir modül için bir tanıtıcı sağlamak hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca5c9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca5c9-109">Requirements</span></span>  
 <span data-ttu-id="ca5c9-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca5c9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca5c9-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca5c9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca5c9-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca5c9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca5c9-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca5c9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca5c9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca5c9-114">See also</span></span>

- [<span data-ttu-id="ca5c9-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ca5c9-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ca5c9-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ca5c9-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
