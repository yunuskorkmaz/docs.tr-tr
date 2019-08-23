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
ms.openlocfilehash: e51ff64115ce3417087eee6845aa802ad64f2a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961001"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="aa19b-102">ICorDebugModule3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa19b-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="aa19b-103">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aa19b-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa19b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa19b-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="aa19b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aa19b-105">Methods</span></span>  
  
|<span data-ttu-id="aa19b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aa19b-106">Method</span></span>|<span data-ttu-id="aa19b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa19b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa19b-108">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa19b-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="aa19b-109">Dinamik bir modül için bir sembol okuyucu (genellikle [ıstreamunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aa19b-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa19b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa19b-110">Remarks</span></span>  
 <span data-ttu-id="aa19b-111">Bu arabirim "ICorDebugModule" ve "ICorDebugModule2" arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="aa19b-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa19b-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="aa19b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa19b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa19b-113">Requirements</span></span>  
 <span data-ttu-id="aa19b-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa19b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa19b-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa19b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa19b-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aa19b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa19b-117">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="aa19b-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aa19b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa19b-118">See also</span></span>

- [<span data-ttu-id="aa19b-119">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa19b-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="aa19b-120">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa19b-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="aa19b-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aa19b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
