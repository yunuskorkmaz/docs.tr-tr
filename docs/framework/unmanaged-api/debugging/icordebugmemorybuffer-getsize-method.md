---
description: ': ICorDebugMemoryBuffer:: GetSize yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugMemoryBuffer:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 7de23dd13a1e0ef841145e3845d7d0052ce3ef9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754046"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="9bc73-103">ICorDebugMemoryBuffer:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bc73-103">ICorDebugMemoryBuffer::GetSize Method</span></span>

<span data-ttu-id="9bc73-104">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="9bc73-104">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc73-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bc73-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bc73-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bc73-106">Parameters</span></span>  

 `pcbBufferLength`  
 <span data-ttu-id="9bc73-107">dışı Bellek arabelleğinin boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9bc73-107">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bc73-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bc73-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9bc73-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9bc73-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bc73-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bc73-110">Requirements</span></span>  

 <span data-ttu-id="9bc73-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bc73-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bc73-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9bc73-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bc73-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9bc73-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bc73-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bc73-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc73-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bc73-115">See also</span></span>

- [<span data-ttu-id="9bc73-116">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bc73-116">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="9bc73-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9bc73-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
