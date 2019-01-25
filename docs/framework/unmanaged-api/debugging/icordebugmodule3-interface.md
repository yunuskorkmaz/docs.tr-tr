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
ms.openlocfilehash: 1d504e694810bfa1b9f3258f75e307bfb60d4ad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496812"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="1b706-102">ICorDebugModule3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b706-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="1b706-103">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b706-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b706-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b706-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1b706-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1b706-105">Methods</span></span>  
  
|<span data-ttu-id="1b706-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1b706-106">Method</span></span>|<span data-ttu-id="1b706-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b706-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b706-108">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b706-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="1b706-109">Simge okuyucu oluşturur (genellikle [Isymunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) dinamik modül için.</span><span class="sxs-lookup"><span data-stu-id="1b706-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b706-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b706-110">Remarks</span></span>  
 <span data-ttu-id="1b706-111">Bu arabirim "ICorDebugModule" ve "ICorDebugModule2" arabirimleri mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="1b706-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b706-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1b706-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b706-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b706-113">Requirements</span></span>  
 <span data-ttu-id="1b706-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b706-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b706-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b706-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b706-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b706-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b706-117">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1b706-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1b706-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b706-118">See also</span></span>
- [<span data-ttu-id="1b706-119">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b706-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="1b706-120">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b706-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="1b706-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b706-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
