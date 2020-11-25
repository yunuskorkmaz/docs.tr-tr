---
title: 'ICorDebugMemoryBuffer:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 7f5458dd12ca83c1a5190bbf7fab0f8e5d06a0e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710771"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="d3997-102">ICorDebugMemoryBuffer:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3997-102">ICorDebugMemoryBuffer::GetSize Method</span></span>

<span data-ttu-id="d3997-103">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="d3997-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3997-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d3997-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3997-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3997-105">Parameters</span></span>  

 `pcbBufferLength`  
 <span data-ttu-id="d3997-106">dışı Bellek arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d3997-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3997-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3997-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3997-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3997-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3997-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3997-109">Requirements</span></span>  

 <span data-ttu-id="d3997-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3997-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3997-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3997-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3997-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3997-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3997-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3997-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3997-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3997-114">See also</span></span>

- [<span data-ttu-id="d3997-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3997-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="d3997-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3997-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
