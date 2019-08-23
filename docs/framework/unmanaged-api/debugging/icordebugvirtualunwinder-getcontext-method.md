---
title: 'ICorDebugVirtualUnwinder:: GetContext yöntemi'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6a8be489ff2a99bb9da393577514b2442d50db8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967946"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="dd4db-102">ICorDebugVirtualUnwinder:: GetContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd4db-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="dd4db-103">Bu unwinder 'in geçerli bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="dd4db-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd4db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd4db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd4db-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="dd4db-106">'ndaki İçeriğin hangi bölümlerinin döndürüleceği (WinNT. h içinde tanımlanır) belirleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="dd4db-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="dd4db-107">'ndaki İçindeki `contextBuf`bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dd4db-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="dd4db-108">dışı Gerçekten üzerine `contextBuf`yazılan bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dd4db-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="dd4db-109">dışı Bu unwinder 'in geçerli bağlamını içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="dd4db-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd4db-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dd4db-110">Return Value</span></span>  
 <span data-ttu-id="dd4db-111">Mscordbi tarafından alınan başarısız olan HRESULT değeri, önemli olarak değerlendirilir ve ICorDebug API 'Lerinin dönmesini `CORDBG_E_DATA_TARGET_ERROR`sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd4db-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd4db-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd4db-112">Remarks</span></span>  
 <span data-ttu-id="dd4db-113">`contextBuf` Bağımsız değişkenin başlangıç değerini [ıcordebugstackyürüme:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemini çağırarak döndürülen bağlam arabelleğine ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="dd4db-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd4db-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd4db-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="dd4db-115">Geri sarma, yalnızca geçici olmayan Yazmaçları gibi yazmaçların bir alt kümesini geri yükleyebilir, çünkü bağlam gerçek Yöntem çağrısı sırasında kayıt durumuyla tam olarak eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="dd4db-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd4db-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd4db-116">Requirements</span></span>  
 <span data-ttu-id="dd4db-117">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd4db-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd4db-118">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dd4db-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd4db-119">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dd4db-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd4db-120">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd4db-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4db-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd4db-121">See also</span></span>

- [<span data-ttu-id="dd4db-122">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd4db-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="dd4db-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dd4db-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
