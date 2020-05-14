---
title: 'ICorDebugVirtualUnwinder:: GetContext yöntemi'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: e203db78b40bf4305316046cfcd679f3d10d1876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396442"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="a68b6-102">ICorDebugVirtualUnwinder:: GetContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="a68b6-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="a68b6-103">Bu unwinder 'in geçerli bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="a68b6-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a68b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a68b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a68b6-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="a68b6-106">'ndaki İçeriğin hangi bölümlerinin döndürüleceği (WinNT. h içinde tanımlanır) belirleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="a68b6-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="a68b6-107">'ndaki İçindeki bayt sayısı `contextBuf` .</span><span class="sxs-lookup"><span data-stu-id="a68b6-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a68b6-108">dışı Gerçekten üzerine yazılan bayt sayısına yönelik bir işaretçi `contextBuf` .</span><span class="sxs-lookup"><span data-stu-id="a68b6-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="a68b6-109">dışı Bu unwinder 'in geçerli bağlamını içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="a68b6-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a68b6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a68b6-110">Return Value</span></span>  
 <span data-ttu-id="a68b6-111">Mscordbi tarafından alınan başarısız olan HRESULT değeri, önemli olarak değerlendirilir ve ICorDebug API 'Lerinin dönmesini sağlar `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="a68b6-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a68b6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a68b6-112">Remarks</span></span>  
 <span data-ttu-id="a68b6-113">`contextBuf`Bağımsız değişkenin başlangıç değerini [ıcordebugstackyürüme:: GetContext](icordebugstackwalk-getcontext-method.md) yöntemini çağırarak döndürülen bağlam arabelleğine ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a68b6-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a68b6-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a68b6-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="a68b6-115">Geri sarma, yalnızca geçici olmayan Yazmaçları gibi yazmaçların bir alt kümesini geri yükleyebilir, çünkü bağlam gerçek Yöntem çağrısı sırasında kayıt durumuyla tam olarak eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a68b6-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a68b6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a68b6-116">Requirements</span></span>  
 <span data-ttu-id="a68b6-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a68b6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68b6-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a68b6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a68b6-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a68b6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a68b6-120">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a68b6-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68b6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a68b6-121">See also</span></span>

- [<span data-ttu-id="a68b6-122">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a68b6-122">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="a68b6-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a68b6-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
