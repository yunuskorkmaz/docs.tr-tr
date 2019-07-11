---
title: ICorDebugVirtualUnwinder::Next yöntemi
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd12861b34d577a002fbf0cc8a7962b7bfc35fe1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775334"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="37eeb-102">ICorDebugVirtualUnwinder::Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="37eeb-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="37eeb-103">Arayanın bağlam ilerler.</span><span class="sxs-lookup"><span data-stu-id="37eeb-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37eeb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37eeb-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="37eeb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37eeb-105">Parameters</span></span>  
 <span data-ttu-id="37eeb-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="37eeb-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37eeb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37eeb-107">Return Value</span></span>  
 <span data-ttu-id="37eeb-108">`S_OK` geriye doğru izleme başarıyla oluştuysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru izleme tamamlanamıyorsa.</span><span class="sxs-lookup"><span data-stu-id="37eeb-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="37eeb-109">Döndürülen HRESULT başarısız olan bir Icordebug API'leri döndürür `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="37eeb-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37eeb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37eeb-110">Remarks</span></span>  
 <span data-ttu-id="37eeb-111">Yığın değişkeni, ilerleme, bu sonuç kılar emin olmalısınız çağrısı `Next` başarısız döndüreceği HRESULT veya `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="37eeb-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="37eeb-112">Döndüren `S_OK` süresiz olarak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="37eeb-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37eeb-113">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37eeb-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37eeb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37eeb-114">Requirements</span></span>  
 <span data-ttu-id="37eeb-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37eeb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37eeb-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37eeb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37eeb-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37eeb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37eeb-118">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37eeb-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37eeb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37eeb-119">See also</span></span>

- [<span data-ttu-id="37eeb-120">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37eeb-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="37eeb-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37eeb-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
