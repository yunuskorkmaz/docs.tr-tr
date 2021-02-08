---
description: 'Daha fazla bilgi edinin: ICorDebugModule3 Interface'
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
ms.openlocfilehash: 5b47cffb267ab97de2cd225aca2998962ba66d99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790769"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="3c5c0-103">ICorDebugModule3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c5c0-103">ICorDebugModule3 Interface</span></span>

<span data-ttu-id="3c5c0-104">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c5c0-104">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5c0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c5c0-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3c5c0-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3c5c0-106">Methods</span></span>  
  
|<span data-ttu-id="3c5c0-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3c5c0-107">Method</span></span>|<span data-ttu-id="3c5c0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c5c0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c5c0-109">ICorDebugModule3::CreateReaderForInMemorySymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c5c0-109">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="3c5c0-110">Dinamik bir modül için bir sembol okuyucu (genellikle [ıstreamunmanagedreader arabirimi](../diagnostics/isymunmanagedreader-interface.md)) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c5c0-110">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c5c0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c5c0-111">Remarks</span></span>  

 <span data-ttu-id="3c5c0-112">Bu arabirim "ICorDebugModule" ve "ICorDebugModule2" arabirimlerini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="3c5c0-112">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c5c0-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="3c5c0-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c5c0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c5c0-114">Requirements</span></span>  

 <span data-ttu-id="3c5c0-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c5c0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c5c0-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3c5c0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c5c0-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3c5c0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c5c0-118">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="3c5c0-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3c5c0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c5c0-119">See also</span></span>

- [<span data-ttu-id="3c5c0-120">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c5c0-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="3c5c0-121">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c5c0-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="3c5c0-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c5c0-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
