---
description: 'Daha fazla bilgi edinin: ICorDebugVirtualUnwinder:: Next yöntemi'
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: b509e8e4fb24c66764999e67ba7e36299ce7f570
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790522"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="efd0f-103">ICorDebugVirtualUnwinder:: Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="efd0f-103">ICorDebugVirtualUnwinder::Next Method</span></span>

<span data-ttu-id="efd0f-104">Çağıranın bağlamına ilerletir.</span><span class="sxs-lookup"><span data-stu-id="efd0f-104">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd0f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efd0f-105">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="efd0f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="efd0f-106">Parameters</span></span>  

 <span data-ttu-id="efd0f-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="efd0f-107">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efd0f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="efd0f-108">Return Value</span></span>  

 <span data-ttu-id="efd0f-109">`S_OK` geriye doğru izleme işlemi başarılı olduysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="efd0f-109">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="efd0f-110">Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri döndürülür `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="efd0f-110">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efd0f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efd0f-111">Remarks</span></span>  

 <span data-ttu-id="efd0f-112">Yığın denetçisi ilerlemeye devam ettiğinden emin olunması gerekir, bu yüzden bir çağrısının `Next` başarısız BIR HRESULT veya geri dönmesi gerekir `CORDBG_S_AT_END_OF_STACK` .</span><span class="sxs-lookup"><span data-stu-id="efd0f-112">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="efd0f-113">Süresiz olarak döndürmek `S_OK` sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="efd0f-113">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efd0f-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="efd0f-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efd0f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="efd0f-115">Requirements</span></span>  

 <span data-ttu-id="efd0f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efd0f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efd0f-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="efd0f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efd0f-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="efd0f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efd0f-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efd0f-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd0f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efd0f-120">See also</span></span>

- [<span data-ttu-id="efd0f-121">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="efd0f-121">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="efd0f-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="efd0f-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
