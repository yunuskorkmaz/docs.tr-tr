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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106346"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="77674-102">ICLRDebuggingLibraryProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77674-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="77674-103">İçerir [ProvideLibrary yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) kitaplık sağlayıcı ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarına ve yüklenecek isteğe bağlı olmasını sağlayan bir geri arama arabirimini alan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77674-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77674-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="77674-104">Methods</span></span>  
  
|<span data-ttu-id="77674-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="77674-105">Method</span></span>|<span data-ttu-id="77674-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77674-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77674-107">ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77674-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="77674-108">Hata ayıklama kitaplığı yüklemek için kullanılabilecek bir modül için bir tanıtıcı sağlamak hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="77674-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77674-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77674-109">Requirements</span></span>  
 <span data-ttu-id="77674-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77674-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77674-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77674-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77674-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77674-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="77674-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="77674-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77674-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77674-114">See also</span></span>

- [<span data-ttu-id="77674-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="77674-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="77674-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="77674-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
