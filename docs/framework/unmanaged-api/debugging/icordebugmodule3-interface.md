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
ms.openlocfilehash: 543a1a3c79b6cf3eb799da5844f35286dfa91940
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709563"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="6ebdb-102">ICorDebugModule3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ebdb-102">ICorDebugModule3 Interface</span></span>

<span data-ttu-id="6ebdb-103">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ebdb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ebdb-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="6ebdb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6ebdb-105">Methods</span></span>  
  
|<span data-ttu-id="6ebdb-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6ebdb-106">Method</span></span>|<span data-ttu-id="6ebdb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ebdb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ebdb-108">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ebdb-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="6ebdb-109">Dinamik bir modül için bir sembol okuyucu (genellikle [ıstreamunmanagedreader arabirimi](../diagnostics/isymunmanagedreader-interface.md)) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ebdb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ebdb-110">Remarks</span></span>  

 <span data-ttu-id="6ebdb-111">Bu arabirim "ICorDebugModule" ve "ICorDebugModule2" arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ebdb-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ebdb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ebdb-113">Requirements</span></span>  

 <span data-ttu-id="6ebdb-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ebdb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ebdb-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ebdb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ebdb-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6ebdb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ebdb-117">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="6ebdb-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6ebdb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-118">See also</span></span>

- [<span data-ttu-id="6ebdb-119">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ebdb-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="6ebdb-120">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ebdb-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="6ebdb-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6ebdb-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
