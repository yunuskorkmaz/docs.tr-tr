---
description: ': ICorDebugMemoryBuffer:: GetStartAddress yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugMemoryBuffer:: GetStartAddress yöntemi'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 46720d70b8a1019e712b577b24dec5d4c3d5a31d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722717"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="3a1ca-103">ICorDebugMemoryBuffer:: GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a1ca-103">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>

<span data-ttu-id="3a1ca-104">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-104">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a1ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a1ca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a1ca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a1ca-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="3a1ca-107">dışı Bellek arabelleğinin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-107">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a1ca-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a1ca-108">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="3a1ca-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a1ca-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a1ca-110">Requirements</span></span>  

 <span data-ttu-id="3a1ca-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a1ca-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a1ca-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a1ca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a1ca-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3a1ca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a1ca-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a1ca-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1ca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a1ca-115">See also</span></span>

- [<span data-ttu-id="3a1ca-116">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a1ca-116">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="3a1ca-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3a1ca-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
