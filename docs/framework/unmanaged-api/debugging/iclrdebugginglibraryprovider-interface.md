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
ms.openlocfilehash: 81b9ffe5979ad553a5bdfbc27111469b2ff4db6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111372"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="88d8e-102">ICLRDebuggingLibraryProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88d8e-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="88d8e-103">Ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi alan [ProvideLibrary Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="88d8e-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88d8e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="88d8e-104">Methods</span></span>  
  
|<span data-ttu-id="88d8e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="88d8e-105">Method</span></span>|<span data-ttu-id="88d8e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88d8e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88d8e-107">ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88d8e-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="88d8e-108">Hata ayıklayıcının bir modül için hata ayıklama kitaplığını yüklemek için kullanılabilecek bir tanıtıcı sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="88d8e-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88d8e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88d8e-109">Requirements</span></span>  
 <span data-ttu-id="88d8e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88d8e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88d8e-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88d8e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88d8e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="88d8e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88d8e-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88d8e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88d8e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88d8e-114">See also</span></span>

- [<span data-ttu-id="88d8e-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="88d8e-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="88d8e-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="88d8e-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
