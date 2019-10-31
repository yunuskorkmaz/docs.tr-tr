---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: ed80b7a630f78002ded14a1bec206cc8712bd504
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121856"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="54c4b-102">ICorDebugVirtualUnwinder:: Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="54c4b-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="54c4b-103">Çağıranın bağlamına ilerletir.</span><span class="sxs-lookup"><span data-stu-id="54c4b-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54c4b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="54c4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54c4b-105">Parameters</span></span>  
 <span data-ttu-id="54c4b-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="54c4b-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54c4b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="54c4b-107">Return Value</span></span>  
 <span data-ttu-id="54c4b-108">geriye doğru bir şekilde oluştuysa veya daha fazla çerçeve olmadığından geriye doğru izleme `S_OK` `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="54c4b-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="54c4b-109">Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri `CORDBG_E_DATA_TARGET_ERROR`döndürür.</span><span class="sxs-lookup"><span data-stu-id="54c4b-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54c4b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54c4b-110">Remarks</span></span>  
 <span data-ttu-id="54c4b-111">Yığın denetçisi ilerlemesinin devam ettiğinden emin olunması gerekir, böylece sonuç olarak bir `Next` çağrısı, başarısız bir HRESULT veya `CORDBG_S_AT_END_OF_STACK`döndürmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="54c4b-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="54c4b-112">Sonsuza kadar `S_OK` döndürme sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="54c4b-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54c4b-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54c4b-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c4b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54c4b-114">Requirements</span></span>  
 <span data-ttu-id="54c4b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c4b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c4b-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54c4b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54c4b-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="54c4b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54c4b-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c4b-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c4b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54c4b-119">See also</span></span>

- [<span data-ttu-id="54c4b-120">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54c4b-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="54c4b-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="54c4b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
