---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396420"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="c10df-102">ICorDebugVirtualUnwinder:: Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="c10df-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="c10df-103">Çağıranın bağlamına ilerletir.</span><span class="sxs-lookup"><span data-stu-id="c10df-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c10df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c10df-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="c10df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c10df-105">Parameters</span></span>  
 <span data-ttu-id="c10df-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="c10df-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c10df-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c10df-107">Return Value</span></span>  
 <span data-ttu-id="c10df-108">`S_OK`geriye doğru izleme işlemi başarılı olduysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="c10df-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="c10df-109">Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri döndürülür `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="c10df-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c10df-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c10df-110">Remarks</span></span>  
 <span data-ttu-id="c10df-111">Yığın denetçisi ilerlemeye devam ettiğinden emin olunması gerekir, bu yüzden bir çağrısının `Next` başarısız BIR HRESULT veya geri dönmesi gerekir `CORDBG_S_AT_END_OF_STACK` .</span><span class="sxs-lookup"><span data-stu-id="c10df-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="c10df-112">Süresiz olarak döndürmek `S_OK` sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c10df-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c10df-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c10df-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c10df-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c10df-114">Requirements</span></span>  
 <span data-ttu-id="c10df-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c10df-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c10df-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c10df-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c10df-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c10df-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c10df-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c10df-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c10df-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c10df-119">See also</span></span>

- [<span data-ttu-id="c10df-120">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c10df-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="c10df-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c10df-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
