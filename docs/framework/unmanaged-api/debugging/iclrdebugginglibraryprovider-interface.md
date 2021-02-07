---
description: 'Daha fazla bilgi edinin: ICLRDebuggingLibraryProvider Interface'
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
ms.openlocfilehash: 8aaec87e97d45c8b7b6f87aee64154ea3f48b133
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723289"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="595b6-103">ICLRDebuggingLibraryProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="595b6-103">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="595b6-104">Ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi alan [ProvideLibrary Yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="595b6-104">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="595b6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="595b6-105">Methods</span></span>  
  
|<span data-ttu-id="595b6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="595b6-106">Method</span></span>|<span data-ttu-id="595b6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="595b6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="595b6-108">ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="595b6-108">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="595b6-109">Hata ayıklayıcının bir modül için hata ayıklama kitaplığını yüklemek için kullanılabilecek bir tanıtıcı sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="595b6-109">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="595b6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="595b6-110">Requirements</span></span>  

 <span data-ttu-id="595b6-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="595b6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="595b6-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="595b6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="595b6-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="595b6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="595b6-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="595b6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595b6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="595b6-115">See also</span></span>

- [<span data-ttu-id="595b6-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="595b6-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="595b6-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="595b6-117">Debugging</span></span>](index.md)
