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
ms.openlocfilehash: cd17cbc808b7f8381ac320bb55999c6b0466c3d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723549"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="39755-102">ICLRDebuggingLibraryProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39755-102">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="39755-103">Ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi alan [ProvideLibrary Yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="39755-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39755-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="39755-104">Methods</span></span>  
  
|<span data-ttu-id="39755-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="39755-105">Method</span></span>|<span data-ttu-id="39755-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39755-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39755-107">ProvideLibrary Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39755-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="39755-108">Hata ayıklayıcının bir modül için hata ayıklama kitaplığını yüklemek için kullanılabilecek bir tanıtıcı sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="39755-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39755-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39755-109">Requirements</span></span>  

 <span data-ttu-id="39755-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39755-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39755-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39755-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39755-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="39755-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39755-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39755-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39755-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39755-114">See also</span></span>

- [<span data-ttu-id="39755-115">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="39755-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="39755-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="39755-116">Debugging</span></span>](index.md)
