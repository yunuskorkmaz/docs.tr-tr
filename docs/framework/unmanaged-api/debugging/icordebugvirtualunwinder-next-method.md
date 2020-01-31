---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790813"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="a2023-102">ICorDebugVirtualUnwinder:: Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2023-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="a2023-103">Çağıranın bağlamına ilerletir.</span><span class="sxs-lookup"><span data-stu-id="a2023-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2023-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2023-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2023-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2023-105">Parameters</span></span>  
 <span data-ttu-id="a2023-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2023-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2023-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2023-107">Return Value</span></span>  
 <span data-ttu-id="a2023-108">geriye doğru bir şekilde oluştuysa veya daha fazla çerçeve olmadığından geriye doğru izleme `S_OK` `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="a2023-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="a2023-109">Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri `CORDBG_E_DATA_TARGET_ERROR`döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2023-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2023-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2023-110">Remarks</span></span>  
 <span data-ttu-id="a2023-111">Yığın denetçisi ilerlemesinin devam ettiğinden emin olunması gerekir, böylece sonuç olarak bir `Next` çağrısı, başarısız bir HRESULT veya `CORDBG_S_AT_END_OF_STACK`döndürmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="a2023-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="a2023-112">Sonsuza kadar `S_OK` döndürme sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2023-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2023-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2023-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2023-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2023-114">Requirements</span></span>  
 <span data-ttu-id="a2023-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2023-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2023-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2023-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2023-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a2023-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2023-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2023-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2023-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2023-119">See also</span></span>

- [<span data-ttu-id="a2023-120">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2023-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="a2023-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a2023-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
