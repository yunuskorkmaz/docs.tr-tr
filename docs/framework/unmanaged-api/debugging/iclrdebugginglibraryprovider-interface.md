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
ms.openlocfilehash: 7537d3d6f741f36ab81d73751963a8539de0a36c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404475"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="07375-102">ICLRDebuggingLibraryProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07375-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="07375-103">İçeren [ProvideLibrary yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) ortak dil çalışma zamanı sürüme özgü hata ayıklama kitaplıkları bulunduğu ve yüklenen üzerinde isteğe bağlı olarak geri çağırma arabirimi kitaplığı sağlayıcısını alır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07375-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07375-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="07375-104">Methods</span></span>  
  
|<span data-ttu-id="07375-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="07375-105">Method</span></span>|<span data-ttu-id="07375-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07375-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07375-107">ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07375-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="07375-108">Hata ayıklama kitaplığı yüklemek için kullanılan bir modül için bir tanıtıcı sağlamak hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07375-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07375-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07375-109">Requirements</span></span>  
 <span data-ttu-id="07375-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07375-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07375-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07375-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07375-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07375-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07375-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07375-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07375-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07375-114">See Also</span></span>  
 [<span data-ttu-id="07375-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="07375-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="07375-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="07375-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
