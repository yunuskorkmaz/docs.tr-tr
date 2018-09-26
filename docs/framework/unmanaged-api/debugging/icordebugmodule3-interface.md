---
title: ICorDebugModule3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58bad617eb91b7e529ff3d95edd06a5c73feee64
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196830"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="eadd3-102">ICorDebugModule3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eadd3-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="eadd3-103">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eadd3-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eadd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eadd3-104">Syntax</span></span>  
  
```  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eadd3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eadd3-105">Methods</span></span>  
  
|<span data-ttu-id="eadd3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eadd3-106">Method</span></span>|<span data-ttu-id="eadd3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eadd3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eadd3-108">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eadd3-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="eadd3-109">Simge okuyucu oluşturur (genellikle [Isymunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) dinamik modül için.</span><span class="sxs-lookup"><span data-stu-id="eadd3-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eadd3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eadd3-110">Remarks</span></span>  
 <span data-ttu-id="eadd3-111">Bu arabirim "ICorDebugModule" ve "ICorDebugModule2" arabirimleri mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="eadd3-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eadd3-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="eadd3-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eadd3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eadd3-113">Requirements</span></span>  
 <span data-ttu-id="eadd3-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eadd3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eadd3-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eadd3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eadd3-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eadd3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eadd3-117">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="eadd3-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eadd3-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eadd3-118">See Also</span></span>  
 [<span data-ttu-id="eadd3-119">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eadd3-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="eadd3-120">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eadd3-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="eadd3-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eadd3-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
