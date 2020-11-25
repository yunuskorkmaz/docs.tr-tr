---
title: 'ICorDebugMemoryBuffer:: GetStartAddress yöntemi'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f76bf1479db987e4956d8b876f67d629d927f956
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710772"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="00243-102">ICorDebugMemoryBuffer:: GetStartAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="00243-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>

<span data-ttu-id="00243-103">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="00243-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00243-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="00243-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00243-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00243-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="00243-106">dışı Bellek arabelleğinin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="00243-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00243-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00243-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="00243-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00243-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00243-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00243-109">Requirements</span></span>  

 <span data-ttu-id="00243-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00243-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00243-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00243-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00243-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="00243-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00243-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00243-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00243-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00243-114">See also</span></span>

- [<span data-ttu-id="00243-115">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00243-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="00243-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00243-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
