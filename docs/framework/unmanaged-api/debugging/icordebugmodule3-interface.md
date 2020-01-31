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
ms.openlocfilehash: 33acc4d9a0819c43d17c362fcbea2e7636521fd3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792928"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="8098f-102">ICorDebugModule3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8098f-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="8098f-103">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8098f-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8098f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8098f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8098f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8098f-105">Methods</span></span>  
  
|<span data-ttu-id="8098f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8098f-106">Method</span></span>|<span data-ttu-id="8098f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8098f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8098f-108">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8098f-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="8098f-109">Dinamik bir modül için bir sembol okuyucu (genellikle [ıstreamunmanagedreader arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8098f-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8098f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8098f-110">Remarks</span></span>  
 <span data-ttu-id="8098f-111">Bu arabirim "ICorDebugModule" ve "ICorDebugModule2" arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="8098f-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8098f-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="8098f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8098f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8098f-113">Requirements</span></span>  
 <span data-ttu-id="8098f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8098f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8098f-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8098f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8098f-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8098f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8098f-117">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="8098f-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8098f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8098f-118">See also</span></span>

- [<span data-ttu-id="8098f-119">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8098f-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="8098f-120">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8098f-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="8098f-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8098f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
